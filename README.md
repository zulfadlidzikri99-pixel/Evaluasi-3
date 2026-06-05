#include <DHT.h>

#define DHTPIN 2       // Pin data DHT11 terhubung ke pin 2
#define DHTTYPE DHT11  // Tipe sensor

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  dht.begin();

  Serial.println("Membaca Sensor DHT11...");
}

void loop() {
  float humidity = dht.readHumidity();
  float temperature = dht.readTemperature();

  // Mengecek apakah pembacaan gagal
  if (isnan(humidity) || isnan(temperature)) {
    Serial.println("Gagal membaca sensor DHT11!");
    delay(2000);
    return;
  }

  Serial.print("Suhu: ");
  Serial.print(temperature);
  Serial.print(" °C");

  Serial.print(" | Kelembapan: ");
  Serial.print(humidity);
  Serial.println(" %");

  delay(2000);
}
