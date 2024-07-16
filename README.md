# ESP
this program uses a PIR sensor to detect movement, and when movement is detected, it turns the LED on, and when the movement ends, it turns the LED off. It also prints messages to the serial port to inform the user about the state of the movement.
```
int led =12;            // led is connected to esp32 D12
 int pirdata =4;       // pir D is connected to D4
 int pirstate =LOW ;      // assuming no motion 
 int value =0;            // to read pin status 

void setup() {
  pinMode(led, OUTPUT);      //  Led as output
  pinMode(pirdata, INPUT);     // PIR sensor as input

  Serial.begin(9600);
}

void loop() {
  value = digitalRead(pirdata);  
  if (value == HIGH) {           
    digitalWrite(led, HIGH);  
    if (pirstate == LOW) {
     
      Serial.println("Motion detected!");
      
      pirstate = HIGH;
    }
  } else {
    digitalWrite(led, LOW); 
    if (pirstate == HIGH) {
      
      Serial.println("Motion ended!");
     
      pirstate = LOW;
    }
  }
}
```
## 1. Defines the variables:
   - led: This is the digital pin number that the LED is connected to on the ESP32 board (pin D12).
   - pirdata: This is the digital pin number that the PIR sensor is connected to on the ESP32 board (pin D4).
   - pirstate: This variable tracks the state of the PIR sensor, whether it's "active" (HIGH) or "at rest" (LOW).
   - value: This is a temporary variable used to read the digital pin value from the PIR sensor.
## 2. In the setup() function:
   - It sets the LED as an output pin using pinMode(led, OUTPUT).
   - It sets the PIR sensor as an input pin using pinMode(pirdata, INPUT).
   - It starts the serial communication at 9600 baud using Serial.begin(9600).
## 3. In the loop() function:
   - It reads the digital pin value from the PIR sensor and stores it in the value variable using digitalRead(pirdata).
   - If movement is detected (the value is HIGH):
     - It turns the LED on using digitalWrite(led, HIGH).
     - If the PIR sensor was previously at rest (`pirstate` is LOW):
     - It prints the message "Movement detected!" to the serial port.
     - It changes the PIR sensor state to "active" by setting pirstate to HIGH.
     - If no movement is detected (the value is LOW):
     - It turns the LED off using digitalWrite(led, LOW).
     - If the PIR sensor was previously active (`pirstate` is HIGH):
     - It prints the message "Movement ended!" to the serial port.
     - It changes the PIR sensor state to "at rest" by setting pirstate to LOW.
       
      ### wokwi:
      <img src="https://github.com/user-attachments/assets/5baee841-4b58-450a-baaa-21b65f9d4ae6" width="500" height="400" >


