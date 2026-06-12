---
title: "need help with pyserial"
date: 2016-10-19
forum: Programming Talk
---

### Post by antichamber on 2016-10-19
So, I'm running IDLE 3 on ubuntu mate on a raspberry pi and have an arduino uno connected via USB. Here is the code on the arduino:
 int temp = 0; 
void setup() 
{ 
pinMode(ledPin, OUTPUT); 
Serial.begin(9600); 
Serial.setTimeout(10); 
} 
void loop() 
{ 
while (Serial.available() > 0) 
{ 
temp = Serial.parseInt(); 
if (temp == 0)
 { 
digitalWrite(13, HIGH); 
delay(1000); \
digitalWrite(13, LOW); 
delay(500); 
} 
} 
if (temp > 0) { 
temp--; 
digitalWrite(13, HIGH); 
delay(500); 
digitalWrite(13, LOW);\
delay(500); } } 

And is the first part of code on the raspberry pi: 
import time 
import serial 
import struct 
ser = serial.Serial('/dev/ttyACM0',9600) 
data = 2 
time.sleep(2) 
print("sending now") 

And now, the various attempts of sending stuff over serial, and their corresponding errors: 
code: ser.write(data) 
error: TypeError: 'int' object is not iterable 

code: ser.write(str(data)) 
error: TypeError: an interger is required 

code: ser.write(int(data)) 
error: TypeError 'int' object is not iterable 

code: ser.write(struct('>B', data)) 
error: TypeError: 'module' object is not callable 

Please tell me what I'm doing wrong or what I can do to make this work. I can't think of anything else to put in.

---

### Post by mcgbb on 2016-10-21
ser.write(str(data)) should work fine.

Only thing I can suggest is to step though the program line by line and check that when it gets to data=2 that the data variable has type 'int'

---

### Post by Olav on 2016-10-22
Perhaps you weren't aware but if you want people here to even look at your code it probably pays to put it in ```
 tags and indent it properly. Your Arduino programme is nearly illegible the way you pasted it in here. Compare:
[code]
int temp = 0;

void setup() {

    pinMode(ledPin, OUTPUT);
    Serial.begin(9600);
    Serial.setTimeout(10);

}

void loop() {

    while (Serial.available() > 0) {

        temp = Serial.parseInt();

        if (temp == 0) {

             digitalWrite(13, HIGH);
             delay(1000);
             digitalWrite(13, LOW);
             delay(500);

        }

    }

    if (temp > 0) {

        temp--;
        digitalWrite(13, HIGH);
        delay(500);
        digitalWrite(13, LOW);
        delay(500);

    }

}


```
Isn't that pretty.

Now for the Python part. You describe various errors:
> 
code: ser.write(data)
error: TypeError: 'int' object is not iterable

code: ser.write(str(data))
error: TypeError: an interger is required

code: ser.write(int(data))
error: TypeError 'int' object is not iterable

code: ser.write(struct('>B', data))
error: TypeError: 'module' object is not callable 

All these errors are telling you that serial.Serial.write() does not like the type of your 'data' variable and your conversions are not doing anything to fix the problem. So let's go back to the pySerial manual and see what the write() method actually expects as a parameter:

[http://pyserial.readthedocs.io/en/latest/pyserial_api.html](http://pyserial.readthedocs.io/en/latest/pyserial_api.html)

It says, a bit down from the top of the page:
> 
Write the bytes *data* to the port. This should be of type **bytes** (or compatible such as **bytearray** or **memoryview**). Unicode strings must be encoded (e.g. **'hello'.encode('utf-8'**).

Changed in version 2.5: Accepts instances of **bytes** and **bytearray** when available (Python 2.6 and newer) and **str** otherwise.

So in Python 3.x it wants a parameter of the Python built-in type **bytes**. You can read more about **bytes** here:

[https://docs.python.org/3/library/stdtypes.html#binary-sequence-types-bytes-bytearray-memoryview](https://docs.python.org/3/library/stdtypes.html#binary-sequence-types-bytes-bytearray-memoryview)

It looks then like you should be able to convert your variable with the method int.to_bytes() and then feed it into serial.Serial.write() like so:

```

data = 1
param = data.to_bytes(2, byteorder='little')
written = ser.write(param)

```

Or even:

```


ser.write((1).to_bytes(2, byteorder='little'))

```

We are converting to two bytes little endian because that is how the Arduino appears to like its integers.

---

