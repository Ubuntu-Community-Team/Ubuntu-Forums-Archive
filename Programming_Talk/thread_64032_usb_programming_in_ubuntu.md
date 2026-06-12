---
title: "usb programming in ubuntu"
date: 2005-09-09
forum: Programming Talk
---

### Post by ccristoo on 2005-09-09
I'm working on a project where i have to send data using the usb port to a circuit in order to move a robot's servo motors.

I've already made the program using the serial ttyS ports but never with usb. 

I read that using libusb i can make the work, but i dont know how to find out if i already have libusb installed in my system and how can i use the libusb api described on [http://libusb.sourceforge.net/doc/index.html](http://libusb.sourceforge.net/doc/index.html).

Can anyone help me?

---

### Post by LordHunter317 on 2005-09-09
Does the USB device show up as a USB serial device?  IOW, does it use a special USB protocol or does it just do serial over USB?  If it does the former, you can probably not change any of your code and just use /dev/ttyUSB0 or whatever is necessary.

OTOH, if you need libusb, then you need to install I believe you need libusb-dev for C and libusb++-dev for C++.

---

### Post by ccristoo on 2005-09-09
Nope, i dont use a special protocol, i just want to do serial over usb. don you think that i just have to change the tty ?

---

### Post by LordHunter317 on 2005-09-09
Yes, you have to change the device name, to /dev/ttyUSB0 or /dev/ttyUSB1.  But if it just shows up as a serial port, then that's all you should have to do.

That'd how my palm pliot works: when I plug it in, it shows up as a serial device at /dev/ttyUSB1, and then the software uses the same code to talk to it as it would a oridinary serial palm pilot.

---

### Post by gheorghe_pop on 2005-09-10
Offtopic:
Did you build the circuit? Because I am very interested in building something like you described above. If you builded the circuit can you post me as schematic?
10x

---

