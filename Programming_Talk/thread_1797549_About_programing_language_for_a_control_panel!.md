---
title: "About programing language for a control panel!"
date: 2011-07-05
forum: Programming Talk
---

### Post by lhjordanlh on 2011-07-05
I am curious about what kind of programing language is used for the control panel for like a real/physical engine. The use of the control panel is to increase the power input/ output and show detection from the sensors of frequencies, water level and temperature... etc.

Or better, what "kind of programing language" can be used for one of those?"
And what are the main physical components for one of those control panel?!

Thank for replying guys!!! :D

---

### Post by Hairy_Palms on 2011-07-05
embedded things like that used to be predominantly C or assembly depending.
> And what are the main physical components for one of those control panel?!
If u mean the main physical components from something like a car dashboard then its usually a combination of 7 segment LCD displays or moving coil meters, depending on the car, quite often with custom LCD displays for things like fuel level,

---

### Post by Chimes on 2011-07-05
For something that is monitoring something as delicate, sensitive, and constantly varying as a lawnmower engine or car engine, well, it depends.

On the software side, there are two parts which are necessary for the kind of "control panel" you're talking about.

First you need a back-end library which interfaces with the hardware that monitors or adjusts the engine. This part is the "driver" and API for the circuitry that ultimately receives data from sensors within the engine, and ultimately makes adjustments to connected hardware. If you do not have a back-end library already for your hardware, you will generally want to develop one using a very fast programming language, with fine-grained control, and which is commonly used to interface with circuits. C, C++, and Java are your best bets. One of the reasons to use a language like those is that functions that monitor hardware usually are called very often, so you want them to be fast.

For the front-end GUI or CLI (the application the user uses to see the results of the monitoring or tell the computer what adjustments he wants made) you can use C, C++ or Java, but you could also use any language you find convenient, as long as it can use the API of the provided library. Python, Perl, a website using PHP, all of those would work fine. A GUI or CLI doesn't have to be top of the line relative to speed, because most of its calls happen very rarely.

Strictly speaking, you could have these two parts be one in the same. And in application on customized monitoring devices, they often act like it. But even if you're doing something like that, having your hardware interface be separate from your user interface is good programming practice and will make your code cleaner.

---

### Post by ve4cib on 2011-07-05
Definitely C and/or C++ are very common choices for those kinds of embedded systems.  They're easier to write than assembler (though sometimes inline assembly is necessary, even within a C program), but they allow a very fine degree of control over the hardware.

Depending on the size and scale of the project you may have some basic backend stuff written in C (basic sensor APIs for example), with other languages layered on top of that.

Believe it or not, Java, as pointed out by Chimes, is sometimes used in very low-resource environments.  Hardware (or firmware) implementations of the Java Virtual Machine are surprisingly common, meaning a lot of the work that was previously done in C can now be done in Java, which tends to be easier for most developers to write and maintain.


In terms of physical components, you'll have some kind of CPU, obviously.  ARM and Atmel are pretty common for small electronic devices, but you'll also see MIPS, and I wouldn't be surprised if Atoms start becoming more common.

There will also be some kind of display most likely.  An LCD display (your standard 7-segment display, like a digital clock) is common.  24-segment displays are also used if you need to display letters and numbers.  (I think it's 24 segments anyway....)  For consumer devices pixel LCD displays are sometimes used (just a big matrix of LCD squares).  For a retro look, like [this watch](http://www.cathodecorner.com/nixiewatch/index.html) you might see Nixie Tubes, but they're pretty rare.

In place of a digital display you may also have a dial, in which case you may have a servo motor with the needle connected to it.  The servo motor will either be its own embedded system that communicates with the CPU over a serial line (or something similar), or will be controlled directly by the CPU using pulse-width modulation.

Obviously we need to collect the data to display, so there will be a variety of possible input devices.  Depending on what the system needs to do these will vary greatly.  Thermometers, buttons, pressure sensors, tachometers, gyroscopes, etc... could all be present.  Those will be connected to the CPU either over a direct connection to GPIO (General-Purpose I/O) pins, or through a more formal communications port (serial, USB, ethernet, etc...).  You may even see wireless communication like Bluetooth or Zigby in some instances.

Lastly, there will often be an analogue-to-digital and/or a digital-to-analogue converter to transform analogue sensor data into a digital signal and vice-versa.

---

### Post by lhjordanlh on 2011-07-06
Thank you so much guys~
There are lots of info I need to digest and learn from it! Thank!

---

### Post by ceclauson on 2011-07-06
Good question.

The previous replies mostly seem to be making assumptions about how you're going about this, but it's worth sorting these issues out explicitly.

First question:  is this going to involve a PC computer, or not?  If you are, then the question is how to interface it with the circuitry, which I think the easiest way to do would be to develop a USB peripheral.  I believe that this is a decent book on this:
[http://www.amazon.com/USB-Complete-Developers-Guide-Guides/dp/1931448086/ref=sr_1_1?ie=UTF8&qid=1309926270&sr=8-1]("http://www.amazon.com/USB-Complete-Developers-Guide-Guides/dp/1931448086/ref=sr_1_1?ie=UTF8&qid=1309926270&sr=8-1")

If it doesn't involve a PC computer, then you're probably in the market for a microcontroller.  I personally have used and like PIC microcontrollers.  Here's a page I found with some resources:
[http://mechatronics.colostate.edu/pic.html]("http://mechatronics.colostate.edu/pic.html")
I've always done PIC programming in assembly, but there exist BASIC and C compilers for it.

Atmel microcontrollers are similar to PIC and are popular at my school (University of Washington, CE/EE).  I've never used them before, though:
[http://en.wikipedia.org/wiki/Atmel_AVR]("http://en.wikipedia.org/wiki/Atmel_AVR")
I would guess has language support similar to PIC.

If you're totally new to this, something that you might want to check out is the Arduino board:
[http://www.arduino.cc/](http://www.arduino.cc/)
It's a board built around an Atmel microcontroller, and comes with a development environment with a programming language called "wiring"--which is basically a modified version of C++.  These are very popular with astronautics/aeronautics hobbyists, because it's easy to use and learn and fast to develop with.

Hopefully this is helpful, and good luck with your foray into embedded systems.

---

