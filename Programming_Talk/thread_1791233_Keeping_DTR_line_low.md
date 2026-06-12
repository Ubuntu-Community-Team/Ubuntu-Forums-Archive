---
title: "Keeping DTR line low"
date: 2011-06-26
forum: Programming Talk
---

### Post by electrojustin on 2011-06-26
Hello all!

I am trying to write a proof-of-concept test program in C/C++ on Ubuntu 11.04 that will communicate with a BASIC Stamp via a Keyspan USB to Serial Adapter. I've programmed the Stamp to blink an LED if it receives the number one through serial input. For some reason, the C/C++ test program I wrote causes the "running" light on the Stamp to simply flicker, implying that it was just reset. After searching the internet for quite a few hours, I came to the conclusion the DTR line being high was causing the reset. My question is, does anyone know how to set the DTR line to low in C/C++?

Thanks in advance,
electrojustin

---

### Post by electrojustin on 2011-07-04
Bump?

---

### Post by electrojustin on 2011-07-11
Bump again?

---

### Post by Zugzwang on 2011-07-11
I don't really know if it helps you, but searching using google for serial port programming tutorials brought up [this tutorial]("http://www.easysw.com/~mike/serial/serial.html#advanced"), which has information on how to set the control signals in chapter 4.

---

### Post by electrojustin on 2011-07-12
Yes it does actually. Thanks. Hope this works......

---

### Post by electrojustin on 2011-07-12
No such luck, but now that I can set individual pins to high and low thanks to this site, I can do an alternative method of performing the functions I need the BASIC stamp to do. Thanks again!

---

