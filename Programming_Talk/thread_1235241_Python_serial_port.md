---
title: "Python serial port"
date: 2009-08-08
forum: Programming Talk
---

### Post by nipunreddevil on 2009-08-08
How can i use usb-serial converter to perform serial operations using python.pySerial does not mention it ,i guess?And how can we view our ports in linux as we do using device manager in Windows?

---

### Post by jpkotta on 2009-08-08
Install the python-serial package.  Then in your program:
```

import serial
ser = serial.Serial()
ser.port = "/dev/ttyUSB0" # may be called something different
ser.baudrate = 115200 # may be different
ser.open()
if ser.isOpen():
    ser.write("hello")
    response = ser.read(ser.inWaiting())

```

In Linux, serial ports are named /dev/ttySx or /dev/ttyUSBx, where "x" is a number.

---

### Post by nipunreddevil on 2009-08-08
Thanks,so i just plug in my usb-serial cable and assume i am working with serial port.How do i  know which serial/usb port i am using

---

### Post by jpkotta on 2009-08-08
> **nipunreddevil said:**
> Thanks,so i just plug in my usb-serial cable and assume i am working with serial port.How do i  know which serial/usb port i am using

For a USB serial port adapter, they are numbered in the order that they enumerate.  I think there is a way to give a given device the same number every time, but I've never bothered to learn how.  Just after plugging it in, you will see some messages in /var/log/messages (or use dmesg) that tell you what number it got.

---

### Post by nipunreddevil on 2009-08-08
Thanks again.Now what i intend to do is write data serially and receive data serially continuously using pyGTK.How shall python programming for this be done.if i use serialin waiting ,i guess it will keep on receving but will not write

---

### Post by nipunreddevil on 2009-08-09
I tried what you told and it worked in idle but when i use it within Geany or Gedit,i get following errors
Traceback most recent call last
File "serial.py",line 3,in module
import serial
File"/home/nipun/serial.py",line 5,in module
ser=serial.Serial()
Attribute error:module object has no attribute Serial

how can i make it work?

---

### Post by jpkotta on 2009-08-09
Did you name your file serial.py?  You can't use that name*.  Python tries to import files in the current directory (i.e. serial.py) before other locations, so it's not importing the serial.py from python-serial.

* You *could* use that name, but it requires a workaround, and isn't recommended.

---

### Post by nipunreddevil on 2009-08-09
changing name has not helped,get same errors for prog.py now
Here is prog.py

import serial
ser=serial.Serial()
ser.port="/dev/tyUSB0"
ser.baudrate=9600
ser.open()
ser.write("hi")

---

### Post by nipunreddevil on 2009-08-09
Thanks,got it working
Had forgotten to delete previous file -serial.py

---

### Post by topdoguk on 2009-11-17
As a newbie i have had exactly the same problem, been tearing my hair out for days.
I had also created a file called serial.py once I deleted this file my program run perfectly.

Thanks for this posting. I bet there's plenty more people out there caught out by this one!

---

### Post by nipunreddevil on 2009-11-20
Yes such things should be mentioned in PySerial website

---

### Post by jpkotta on 2009-11-20
> **nipunreddevil said:**
> Yes such things should be mentioned in PySerial website

They really shouldn't, if you're referring to the problems caused by having a source file named serial.py.  This has absolutely nothing to do with PySerial; it has everything to do with how Python works.  It would be like library authors documenting the fact that you need to use [syntactic indentation]("http://en.wikipedia.org/wiki/Python_(programming_language)#Indentation") when you use their libraries.

---

### Post by LanceRooke on 2012-01-14
Ok, how do I use this script to get my touchscreen working?

[http://pastebin.com/yLQ1hbwt](http://pastebin.com/yLQ1hbwt)

It's from trendystephen article on getting touchscreen to work on Ubuntu on the Fujitsu B3020D.

---

