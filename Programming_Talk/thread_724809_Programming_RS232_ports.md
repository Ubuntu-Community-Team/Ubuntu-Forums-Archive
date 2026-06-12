---
title: "Programming RS232 ports"
date: 2008-03-15
forum: Programming Talk
---

### Post by firdooze on 2008-03-15
Hi!

I am doing a program to read data sent to the RS232 port on an Ubuntu machine. I hope to do it in C. I've been looking around and I can't seem to find a good guide to help me start doing the program. 

Can someone point me  to the right direction? Thanks!

---

### Post by duuchung on 2008-03-15
Have you done all the searches? I posted the same question but I used PERL several months ago here in this forum. People have given me all the clues.

---

### Post by Shin_Gouki2501 on 2008-03-15
years ago i used java and java comm api todo that worked pretty much nice for me:
[http://java.sun.com/products/javacomm/](http://java.sun.com/products/javacomm/)

---

### Post by themusicwave on 2008-03-15
> **Shin_Gouki2501 said:**
> years ago i used java and java comm api todo that worked pretty much nice for me:
[http://java.sun.com/products/javacomm/](http://java.sun.com/products/javacomm/)

I used Java and the java comm api about a month ago.  It was fairly straight forward to use, and has the benefit of being cross platform.  

I have no idea what C API to use for serial access.

---

### Post by stroyan on 2008-03-15
You want to review this document for using C to access serial ports.
[http://www.faqs.org/docs/Linux-HOWTO/Serial-Programming-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Serial-Programming-HOWTO.html)

You might also want to refer to this one for language independent background on the workings of RS232 ports.
[http://tldp.org/HOWTO/Serial-HOWTO.html](http://tldp.org/HOWTO/Serial-HOWTO.html)

---

### Post by dwblas on 2008-03-16
Find an existing-already tested and debugged app.  In Python there is pyserial [http://pyserial.sourceforge.net/](http://pyserial.sourceforge.net/)  There has to be apps already out there for other languages as well.

---

### Post by supirman on 2008-03-16
What kind of data are you planning to read?  Using a serial port in linux is quite easy.  All you really need to do is configure the port and then read the data.  You treat a serial port just like a regular file to read the data.

Essentially, you'd have a sequence like:

open() the file /dev/ttyS0 (or the device file for your serial port)

call tcsetattr() on the file descriptor to set parameters

read() from the file descriptor to read the incoming data

---

