---
title: "Low-latency serial access via Bash (?)"
date: 2013-03-04
forum: Programming Talk
---

### Post by armnewbee on 2013-03-04
I need to control a non-RS232 compliant device via the serial port on a Ubuntu box.  If I can overcome the command latency of bash scripts, I prefer that scripting solution.  I'm not adept at other scripting tools or C programming.  I am willing to control the flow control pins for this task, so I have identified the stty -F /dev/ttyS0 hup (and -hup) commands to control DTR.  However, I need to change pin state in less than 500 microseconds.  There appears to be about 16 milliseconds latency (with large variations) in executing the stty in command files.  Is there a faster, less time-variable way to control these pins from a bash script?

---

### Post by gordintoronto on 2013-03-04
You're not going to be able to do this with a bash script. When you say "non-RS232 compliant," does that mean the device can not be controlled with RTS/CTS?

What are you trying to do? What device? Perhaps a program already exists which will do what you want.

---

### Post by ofnuts on 2013-03-05
If you have these timing constraints, you are not even in the application realm but in the kernel/device driver one, so forget it.

I would be using an [Arduino card]("http://www.arduino.cc/") to handle this kind of time-constrained logic, with possibly some higher level logic in Linux. And since the Arduino connects over a USB this alleviates the need for a serial connector that is getting very rare on recent computers.. It is programmed in a C-like language. My son used on in a high-school science project, without any former programming experience.

---

### Post by conradin on 2013-03-05
+1 for ofnuts solution. is this a commercial device or something created by electrical engineering students? 
if possible I would consider doing whatever is possible to create a standard connection. 

you could integrate c functions into your bash script, in which case you could try starting a serial stream rather than trying to make and break the connection numerous times. 
the read write commands probably respond the fastest. i think there is a latency flag you can try setting. 

Also, try increasing your baud rate.

---

### Post by armnewbee on 2013-03-05
Thanks for the responses.  I get the impression that I am asking too much of scripting.  The project is partly a learning experience on low-level hardware access and partly an attempt to transmit IR commands to commercial devices.  I have a no-name piece of hardware that provides IR 38khZ carrier signalling but needs pulse-code modulation for the IR messaging.  There is a collection of software broadly called "LIRC" that appears to deliver this function.  I will investigate.  The only downside to LIRC is that, being prepackaged, it is more difficult for me to learn how to deliver the low-level hardware control.  If anyone can point me to tutorials along this line, please comment.

---

