// C++ code
//
#define TRIG 13
#define ECHO 12

int led_R = 7;
  
void setup()
{
  Serial.begin(9600);
  
  pinMode(led_R, OUTPUT);
  pinMode(8, OUTPUT);
  
  pinMode(TRIG, OUTPUT);
  pinMode(ECHO, INPUT);
}

void loop()
{
  long duration, distance;
  
  digitalWrite(TRIG, LOW);
  delayMicroseconds(2);
  digitalWrite(TRIG, HIGH);
  delayMicroseconds(2);
  digitalWrite(TRIG, LOW);
  
  duration = pulseIn(ECHO, HIGH);
  distance = duration / 58.2;
  
  Serial.print(distance);
  Serial.println("\nDistance : ");
  delay(1000);
    
  if(distance >= 100){
    digitalWrite(led_R, HIGH);
    digitalWrite(8, LOW);
  }
  
  else {
    digitalWrite(led_R, LOW);
    digitalWrite(8, HIGH);
  }
  
  delay(1000);
}
