# ultrasonicdistancearduinosketch

//Ultrasonic Distance Module Sketch

const int triggerPin = 7; //trigger on 7

const int echoPin = 8; // ECHO on 8

int duration = 0; // hold value from pulseIn

int distance = 0; // hold value for calculated distance

void setup()

{

Serial.begin(9600);

pinMode(triggerPin, OUTPUT); //defining pin modes

pinMode(echoPin, INPUT);

}

void loop()

{

digitalWrite(triggerPin, HIGH); // start sending sound wave(s)

delay(5); //required, can be adjusted (no lower than 10us)

digitalWrite(triggerPin, LOW); // module stops sending wave(s)

duration = pulseIn(echoPin, HIGH); // determine how long the ECHO pin was high for the last complete wave

delay(10); //required, can be adjusted - carefully

distance = (duration/2) / 74; delay(500); // calculating distance ** for centimeters (cm) divide by 58 ** thanks coytar!

delay(500); // delay for stability - can play with it but can also break things doing so - use 500 for default

Serial.print(distance); // send the current value stored in distance to the serial monitor

Serial.println(" inches"); // displays the word "inches" after the distance above

Serial.println(); // creates a blank line on serial monitor for readability

}
