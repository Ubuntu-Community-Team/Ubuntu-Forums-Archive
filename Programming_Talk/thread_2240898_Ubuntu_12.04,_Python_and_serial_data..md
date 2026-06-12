---
title: "Ubuntu 12.04, Python and serial data."
date: 2014-08-22
forum: Programming Talk
---

### Post by eightbits2010 on 2014-08-22
Using the Serial Terminal Program, with the same port, I can send data to the micro and  
 it works as expected. But, when attempting to use a Python script and pyserial module, no data is
 transmitted to the micro. This verified using a scope on the micro's receive data RS-232 line. Using the
 Serial Teminal Program, the micro displays the correct information and also is observed at the receive data line as just mentioned.
 

 I can not figure out what else must be done to allow data to be transmitted using the python script.
 The script is based on example(s) from different online searches and the pyserial web site.
 

 I am using Ubuntu 12.04 and python 2.73.
 

 

 

 ```
#!/usr/bin/bin/env/ python 

 import serial 
 import os 
  
 ser = serial.Serial('/dev/ttyUSB0',9600, timeout =1) 
 ser.open() 

  
  
  
 print ser.portstr       # check which port was really used 
 ####  ser.portstr prints /dev/ttyUSB0   ####
 s="1234\n" 
  
 #Note: neither ser.write sends data to module. 
 ser.write("1234\n")     # write a string 
 ser.close()                   # close port 

  
  
  
 """ Note: I have a miro based external hardware module that displays  numerical data received  
 at the external device serial port. It test excellent using a serial term program. 
  I would have thought this would be a simple write ? 


```

I also attached the code in the GEDIT format that runs the python script just in case the snippet embedded is a problem.

---

### Post by ofnuts on 2014-08-24
I don't see your code catching any return code or counts of bytes written that could explain things.

The pyserial doc says close() closes the port immediately, and curiously there is also a flush() method, so calling flush() before close() is worth a try.

---

### Post by eightbits2010 on 2014-08-25
Well, I was only attempting to transmit four bytes and not needing to receive anything. Does not the ser.write() send out the
argument in the call? Any return code would only send data back if the python script sent data in the first place (?).
I noticed that the ```
print ser.portstr
``` prints what appears to be the correct information. That was just to verify that the correct port is the port that opened. Do you have a simple example to just transmit out a few bytes?

---

### Post by ofnuts on 2014-08-25
> **eightbits2010 said:**
> Well, I was only attempting to transmit four bytes and not needing to receive anything. Does not the ser.write() send out the
argument in the call? Any return code would only send data back if the python script sent data in the first place (?).
I noticed that the ```
print ser.portstr
``` prints what appears to be the correct information. That was just to verify that the correct port is the port that opened. Do you have a simple example to just transmit out a few bytes?

It is fairly frequent for I/O libraries to buffer things and do the actual output only when the buffer is full, or when a line-end character is identified in the data. When they do so there is usually some flush() call to force the immediate output of the current buffer contents. I don't know pySerial, but there is a flush() method, so it could be buffering output, and adding a flush() in the code to check that out is fairly trivial, so I would look no further. If adding flush() doesn't work, then I would envision digging further. pySerial being open source, it is easy to check the code...

---

### Post by eightbits2010 on 2014-08-25
ofnuts: I posted the short script which includes:     ```
 ser.write("1234\n")
```
Isn't "\n" the newline which I thought would indicate send the data out ?

---

### Post by ofnuts on 2014-08-26
Only if the output is line-buffered... Why have you not tried flush() yet? Some kind of taboo?

---

### Post by eightbits2010 on 2014-08-26
I will give ser.flush(). It was not included in an example of code as I recall was from pyserial web site.
I will give that a try and post if any change. I have used serial devices for a long time and never had to flush the transmit buffer
to send out serial data. Usually it was applicable to clear a buffer?

---

### Post by Erdaron on 2014-08-27
I'm learning pySerial right now, too. In my experience so far, flushing the buffer is not necessary to send the data to the device.

In the examples you've seen, is the write command immediately followed by close? Serial ports are slow. Maybe it gets closed before it manages to send anything? Try adding a wait (for example, with time.sleep()) before closing the port.

---

### Post by eightbits2010 on 2014-08-30
A lot of progress. I discovered that i needed to use: ```
ser.write("1234/r/n")
``` and then the script
transmitted the data. So I guess the "/n/r" instead of the '/n' was required but not sure why. Another issue seems to be 
with the way that the external device, a Atmel AVR device handles the data it receives. I could not remember everything
I had programmed or why :mad:.
In the script, if I reset the micro external device and then execute the python script, it will display the data as sent.
However, in the script, if I send another ser.write(), it doesn't display and that is not the problem with the Python 
code as far as I can tell. I did find the original C code for the external micro, but going through it again was torture :(.
The micro program was coded in 2009 and I was using a lower cost C compiler (ICCAVR). I had modified the origianal
code to interface with a AutomationDirect PLC serial port and had kept tweaking it to faithful display the PLC serial data
which was always sent as a four byte sequence.

Also, I noticed that the script seemed to work by using a loopback plug to the Ubuntu serial port which is a USB-serial
port. I think I will stop worrying about it for the time being, getting too old to wrestle with the C complier which only
runs under windows anyhow. 

Thanks for the responses and sugestions.

---

