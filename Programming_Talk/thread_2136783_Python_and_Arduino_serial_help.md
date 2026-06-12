---
title: "Python and Arduino serial help"
date: 2013-04-18
forum: Programming Talk
---

### Post by fret669 on 2013-04-18
Hello,

I'm working on an EEPROM programmer, using the Atmega32 and Arduino software. Right now, I'm trying to send the Arduino data using python. For now, I'm just trying to send the byte from python, read it with the
Arduino, and send it back to python over the serial port so I can make sure it's getting the right data. I'm not having any luck however... The python side is:

```

for b in self.bytes_read.read():
           
            self.ser.write(str(chr(b)).encode('latin_1'))
            #read what the Arduino sends back each loop        
            rdd = self.ser.read(20)
            #print to the terminal
            print(rdd)

```

If I just print 'b' in the python terminal, I get the integer value of the byte, so I know the loop is working there.

The Arduino code is:

```

for (uint32_t addr = 0; addr < MAX_ADDR; addr++) {
    
    D = Serial.read();
    Serial.println(D);


}

```


I get: 

b'\r\n-1\r\n255\r\n-1\r\n-1\r\n2'

or some combination, which I know is because I'm reading 20 bytes, and the new line command from the arduino is passing the extra data. The loop stops randomly, after about 2 seconds, and I get 
nothing but b' '. The first half of the file I'm reading is FF, so I don't know if I'm getting data, or the Arduino isn't getting the actual data,and returning FF... I'm not sure what's going on. I think either the 
python code or the Arduino is getting tripped up, but these are the best results I have yet... Any input is appreciated. Thank you.

---

