---
title: "Arduino EEPROM writer help please"
date: 2013-04-17
forum: Programming Talk
---

### Post by fret669 on 2013-04-17
Hello again,

I'm almost finished with my arduino eeprom programmer. The only thing left is to send bytes to the arduino for writing... My PC program is written in python 3, and I am using pyserial for the transfer.
I have a loop:

```


self.bytes_read.seek(0)

for b in self.bytes_read.read():
            self.ser.write(bytes(b))
            
            #To read and print what the arduino should have received
            rdd = self.ser.read(20)
            print(rdd)
            
            #A test to see what I should be sending
            #print(b)

```

self.bytes_read is a .bin file, and when the print line is uncommented, I get the value of the byte in integer form.

I'm trying to modify the arduino code from a Gameboy ram writer, but I haven't gotten anywhere...
This is the arduino loop for receiving the data, and sending it back to python:

```

int waiting = 0;
      if (Serial.available() <= 0) {
        delay(1);
        if (waiting == 0) {
          Serial.println("WAITING");
          waiting = 1;
        }
      }
        
        // Decode input


      byte bval = 0;
      delay(20);
      if (Serial.available()) {
        char c = Serial.read();
        bval = (int) c;
        Serial.print(bval);
      }

```

If I'm lucky all I get is 'WAITING' followed by b' ' until I shut down the program, but since I'm sending data to the arduino, shouldn't it be receiving it? It seems like "Serial.available()" isn't getting anything. I'm thinking it's too fast for the serial connection, and the data doesn't have time to get to the Arduino, but I'm not sure. Any help is much appreciated. :confused:

---

