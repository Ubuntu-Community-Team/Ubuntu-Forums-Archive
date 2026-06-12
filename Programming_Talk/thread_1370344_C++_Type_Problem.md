---
title: "C++ Type Problem"
date: 2010-01-02
forum: Programming Talk
---

### Post by matmatmat on 2010-01-02
I am developing with the Arduino & it's C++ like language. I am trying to create something like a metronome everytime a button is pressed this functions is called:
```

//function
void setSpeed(int i){
  spd = i;
  
  odel = spd;
  odel = odel * 1000;
  odel = (float) odel / spd;
  
  del = odel;
  del = del / 100;
  del = del * 90;
  
  del2 = odel;
  del2 = del2 / 100;
  del2 = del2 * 10;
  
  Serial.println(del); //Print del out
}

//--snip--//
//call

//if the button is pressed:
setSpeed(spd + 1);

```
when I call the function it outputs the same number each time, 900. I think this is something to do with the division:
```

odel = (float) odel / spd;

```

---

### Post by MadCow108 on 2010-01-02
your code is missing all types, its that a feature of Arduino?

if the missing types are not the problem then I guess this is:
setSpeed(spd + 1);
this (in normal C++) creates a temporary with spd + 1 and passes that to the function but does not alter spd
you probably want this:
setSpeed(++spd);

this first increases speed and passes the increased spd to the function. (contrary to spd++ which first passes the unaltered spd to the function and then increases it)

---

### Post by matmatmat on 2010-01-02
Sorry forgot to post them, full listing:
```

int pin = 9;
int switchPin = 2;

int buttonState;

int val, val2;

int interval = 0;
int value = LOW;

long previousMillis = 0;

int spd;
long odel;
float del;
float del2;

void setSpeed(int i){
  spd = i;
  
  odel = spd;
  odel = odel * 1000;
  odel = (float) odel / spd;
  
  del = odel;
  del = del / 100;
  del = del * 90;
  
  del2 = odel;
  del2 = del2 / 100;
  del2 = del2 * 10;
  
  Serial.println(del);
}

void setup(){
  pinMode(pin, OUTPUT);   
  Serial.begin(9600);
 
  setSpeed(60);
  
  buttonState = digitalRead(switchPin);
}

void loop(){
  val = digitalRead(switchPin);   
  delay(10);                         
  val2 = digitalRead(switchPin);     
  if (val == val2) {                 
    if (val != buttonState) {          
      if (val == LOW) {    
        setSpeed(++spd);
      }
    }
    buttonState = val; 
  } 

  if(millis() - previousMillis > interval){
    if (value == LOW) {
      value = HIGH;
      interval = del2;
    } else {
      value = LOW;
      interval = del;
    }
    //Serial.print(interval);
    //Serial.print("\n");
    previousMillis = millis();
    digitalWrite(pin, value);
  }
}  

```

---

### Post by MadCow108 on 2010-01-02
just saw the problem:
odel = spd;
odel = odel * 1000;
odel = (float) odel / spd;

lets rewrite that:
odel = (spd * 1000) / spd = (spd/spd) * 1000 = 1 * 1000
result: always 1000 because its independent of spd

so you always get 900 as output

---

### Post by matmatmat on 2010-01-02
Thanks, that sould of calculated the number of seconds per beat (eg 1s for 60bpm) -- to do that is it:
```

//replace
odel = (float) odel / spd;

//with
odel = odel/60;

```

---

