---
title: "I have Two Video Cards But I cant install the second one"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by racsracs on 2012-08-28
Hi, I am racsracs, and I have installed

Edubuntu Versión 12.04 (precise)  64-bit
Núcleo Linux 3.2.0-29-generic
Intel® Core™ i3-2100 CPU @ 3.10GHz × 4
Ram 5,7 GiB

and recently I bought a second video card to use it with a datashow or monitor, 
 I use this comand that I found to see If my sistem recognize the second card I got this:

spci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 8400 GS] (rev a2)

I already installed the drivers for both, and I cant active both screens at the same time to proyect and use my monitor,
is there any other further info required for you to helpme??
since now THANKS!!!

---

### Post by miegiel on 2012-08-28
AFAIK the chipset (where the integrated GPU resides) disables the integrated GPU when a PCIe graphics card is used.

btw. welcome to ubuntu forums

---

### Post by SJR Dorset on 2012-08-28
Does your new graphics card have more than one output? If so you should use this to connect your second display.

I have always used graphics cards with multiple outputs to connect two displays on both Windows and Ubuntu for several years.

---

