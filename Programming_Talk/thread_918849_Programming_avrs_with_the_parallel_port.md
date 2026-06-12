---
title: "Programming avrs with the parallel port"
date: 2008-09-13
forum: Programming Talk
---

### Post by nerdpride on 2008-09-13
I am just starting programming avrs. I installed avr-libc and avr dude. I am having problems with both but right now my main concern is that I can't find my parallel port. It should be lpt1 but I can't find anything like it. I don't really want to get a usb programmer. Can any body help?

---

### Post by skullmunky on 2008-09-14
try /dev/lp0 

i think lpt1 is the MS name for it.

similarly, for the serial port: in MS, you have COM1, COM2.  in *nix, /dev/ttyS0, /devttyS1, etc.

if you get a usb->serial adapater (e.g., for the Arduino/AVR), it'd likely be /dev/ttyUSB0, /dev/ttyUSB1, etc.

---

### Post by cszikszoy on 2008-09-14
What programmer are using?  I'm curious because I do a lot of work with AVRs, mainly with the dragon and STK500.

I use virtualbox right now to load Atmel Studio and progam / compile / flash my AVRs but I'd like to get into using avr-dude.

Also, in case you don't already know, the AVR Freaks forums are more than a wealth of information.

[http://www.avrfreaks.net/](http://www.avrfreaks.net/)

---

### Post by barney_1 on 2008-10-28
Just to interject my two cents.  I use avr-dude for my programming, I develop with the editor program "kate".  The only thing I miss from AVR studio is the ability to step through your code (simulate).  I know there are some rudimentary simulation programs out there for linux, but I've not been able to get them working in a useful manner.

---

### Post by nerdpride on 2008-10-30
Thanks a ton guys. But the C compilers for avr are over complicated and it is not that much more money to switch to PIC

---

### Post by nerdpride on 2008-10-30
Oh and by the way I am using a parrallel port bit-banging thing a got for $17 at Sparkfun

---

### Post by Keen101 on 2008-11-08
try looking at this:

[http://www.ladyada.net/learn/avr/programmers.html](http://www.ladyada.net/learn/avr/programmers.html)

and

[http://www.ladyada.net/learn/avr/avrdude.html](http://www.ladyada.net/learn/avr/avrdude.html)

---

