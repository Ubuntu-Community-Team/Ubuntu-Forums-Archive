---
title: "Serial Port: Custom baud rate?"
date: 2006-05-12
forum: Programming Talk
---

### Post by Joel B on 2006-05-12
I'm trying to make a program to communicate with the serial port at 8192 baud.  I can't get this exact baud rate, but I know if you set the UART divisor in a computer to 14 it will work since 115200/14 = ~8228 baud. 

 I can't seem to find an easy way to set this in linux though.  I tried using setserial but it doesn't work at all (keeps the baud rate at 9600).  

I know for windows you can set this in c but I can't figure out how to do this with linux. 

what i've tried:
```
sudo setserial /dev/ttyS0 spd_cust baud_base 115200 divisor 14
```

but that has zero effect.  Anyone run into this before? :confused:

---

### Post by IYY on 2006-05-12
I don't know what it is you want to be sending through this serial port, but this:

screen /dev/ttyS0 8192

can be used if you want to open a terminal to another machine connected through the serial port at that specific baud rate.

---

