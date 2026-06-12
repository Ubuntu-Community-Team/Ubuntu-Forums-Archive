---
title: "USB programming"
date: 2011-12-24
forum: Programming Talk
---

### Post by budder8818 on 2011-12-24
I just installed Ubuntu on an old 2003 dell desktop XPS. It seems like a very nice OS and I like the UI desktop. I have a question about to the possibility of something.

My experience:

First, I'm an electrical engineer just graduated and I have experience programming Java, C and C++ and alittle verilog. Most of my C programming experience comes for programming on smaller machines like micro-controllers and FPGAs and DSP. I'm very good at programming java but my expereince is mostly limited to the fundamental programming concepts of OOP as I have never actually written an application outside of the command prompt (Eclipse). However, I have written a lot in Java and am more than beginner. 

I've built,tested and designed a lot of circuitry before and understand how wireless communication systems work. 

So my question:

I want to be able to talk to my desktop using a UART chip. I wanted to know how I can write applications on Ubuntu OS that can act as standalone GUI interfaces and interface via I/O ports on my desktop like the USB, Speakers ect. Is there some IDE (For Ubuntu) I need to download that contains the libraries to interface with these I/O ports like USB? So lets say I want to write a program on my Ubuntu desktop that contains just a text box and a graphical button. The function of the program is:

1. Enter a number in the text box. 
2. Press the button --> Transmit number over USB to UART. 
3. Then the number say 5 ->101 would turn on say some LEDs. Say LED 1,2,3. 1 ->ON, 2->OFF, 3->ON corresponding to the high bits for the number "5". 

Thank you

I really just want to learn how to program on a powerful desktop machine and communicate data over USB. 

John Budd

---

### Post by memilanuk on 2011-12-24
No idea about java... but python has the [pyserial module]("http://pyserial.sourceforge.net/") that can talk to a usb port among other things.  No direct experience with it, sorry.

FWIW... would something like [Arduino]("http://www.arduino.cc/playground/Linux/Ubuntu") be of interest to you?  It is a microcontroller board that you can connect to via usb and either program directly and then have it be a stand-alone controller executing your code, or sending data back to the computer via usb (another place pyserial comes in if using python) or via ethernet, wifi, etc.

---

