---
title: "Microcontrollers and linux"
date: 2006-09-24
forum: Programming Talk
---

### Post by MrLeviticus on 2006-09-24
Electronic engineering is a hobby of mine and I've reached the stage where I've started looking into programming my own microcontrollers/integrated circuits.

From what I can gather, Basic STAMP and OOPic have only specified a Windows development environment. 

I'd like start with a popular IC because there'll be a lot of documentation floating around. I'd also like to be able to program in C/Java. Dual-booting with Windows is NOT option.

What I basically ask, can someone sum up open source projects regarding Linux/microcontrollers and what's compatible with dapper and my needs.

Bear with me, this microcontroller stuff is still new to me ;)

---

### Post by toojays on 2006-09-24
There is some support for various types of PIC microcontrollers. Search this forum, or ask on the gnupic mailing list for more info.

I believe that AVR microcontroller development is well supported under GNU/Linux. There is an AVR port of GCC which is maintained in cooperation with the FSF. (Contrast this with Microchip's port of GCC for the PIC24/30/33 families---a fork which violates the spirit of the GPL, but stays within the letter of the license.)

There is a C compiler called SDCC which supports various types of microcontroller.

I've only ever heard of one uC which could be programmed in Java; C is much more common.

Keep in mind that the compiler is only half of the development environment. You also need a device programmer which is compatible with your OS.

---

