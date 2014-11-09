// this is set up for an attiny45/85 using the internal 1mhz clock speed.

const int SCAN_button = 2;         // scan button on digital 2, pin #7
const int REWIND_button = 1;       // rewind button on digital 1, pin #6
const int SCAN_motor_control = 3;  // motor drive forward on digital 3, pin #2
const int REWIND_motor_control = 4;// motor drive backward on digital 4, pin #3
const int SIGNAL_arduino = 0;      // arduino digital signal on digital 0, pin #5

// attiny pinout is vastly different than atmega pinout, so digital pins are completely different.

void setup()
{
  // define pin data directions.
  pinMode(SCAN_button, INPUT);
  pinMode(REWIND_button, INPUT);
  pinMode(SCAN_motor_control, OUTPUT);
  pinMode(REWIND_motor_control, OUTPUT);
  pinMode(SIGNAL_arduino, OUTPUT);
}

void loop()
{
  // a proper treatment would include debounce code, but this appears to work fine.
  if ((digitalRead(SCAN_button))== 0)        // scan button = 0 means it's been pushed because buttons are weakly tied to +5V, and ground when pushed.
    scan();
  if ((digitalRead(REWIND_button)) == 0)     // rewind button = 0 means it's been pushed
  {
    while(digitalRead(REWIND_button) == 0)   // still pressed: keep rewinding
      digitalWrite(REWIND_motor_control, HIGH);
  }
  digitalWrite(REWIND_motor_control, LOW);   // not pressed: stop rewinding
}

void scan()
{
  digitalWrite(SIGNAL_arduino, HIGH);        // signal arduino
  delay(50);                                 // wait 50 milliseconds
  digitalWrite(SCAN_motor_control, HIGH);    // drive motor control high in scan dir
  delay(4000);                               // run motor for four seconds.
  digitalWrite(SIGNAL_arduino, LOW);         // unsignal arduino
  digitalWrite(SCAN_motor_control, LOW);     // turn off motor
}
  
