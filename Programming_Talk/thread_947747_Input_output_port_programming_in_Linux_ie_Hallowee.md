---
title: "Input output port programming in Linux: ie Halloween prop control"
date: 2008-10-14
forum: Programming Talk
---

### Post by jukingeo on 2008-10-14
Hello,

As an avid user of Basic Stamp Microcontrollers, I was wondering if there was a program available for Linux in which I could access and program the computer's ports.  

The basic idea is to control props such as Halloween props.

I do not know any computer programming languages outside of the Basic Stamp 1 and Basic Stamp 2.  Needless to say in general, the Basic Programming Language is used for these devices.  It is not exact Basic, but what is called PBasic as developed by Parallax.

While I may be interested in learning a new language, I would like something that is easy to follow.

I would mostly like to talk to the USB ports on my machine, but I understand that may be difficult.   Usually the parallel port is recommended as it has 8 data lines and 4 bi-directional lines.  I can start here for starters.

I am looking for something that is easy to learn and easy to interface the machine to the outside world.

My general goal is to write a program such as this:

1) Wait for unsuspecting victim (guest).
2) A PIR sensor detects the presents of victim and sends a signal to the computer's port.
3) The computer acts on the signal in that the sensor has been triggered.
4) The computer outputs a chain of events based on the triggered signal.  I.E.
a) Flash a light in one second intervals for 5 seconds, then turn it off.
b) Then turn on a Fog machine for 5 seconds, turn it off.
c) Have a prop leap forward (via pneumatic valve) for 3 seconds.
d) Reset everything and then wait for next victim.

This is a typical program that can be easily set up on Basic Stamp controller, however, computers have much more storage capacity and can run longer programs.  Computer also have the capabililty to multi-task (run interrupts) in which Basic Stamps cannot do.

I know that programming a computer in C is usually best, but I don't know that language, nor where to begin with it.  The information on it is very overwhelming and I am looking for something easy to work with as I only want to control computer ports for right now.

Thanx in advance for any information/advice.

Geo

---

### Post by xelapond on 2008-10-15
For something that simple I would use an AVR, but because its learning curve is rather steep(you could probably pick it up pretty quick though, given your Basic Stamp experience, anyway, moving on), that's not really viable, Halloween is right around the corner:)

If you wanted to run this on the computer I would recommend Python.  Its really simple to learn, and has some libraries that do the kind of IO you need.  Take a look at PyUSB, PyParalell, and PySerial.

Good Luck!

Alex

---

### Post by jukingeo on 2008-10-23
> **xelapond said:**
> For something that simple I would use an AVR, but because its learning curve is rather steep(you could probably pick it up pretty quick though, given your Basic Stamp experience, anyway, moving on), that's not really viable, Halloween is right around the corner:)

If you wanted to run this on the computer I would recommend Python.  Its really simple to learn, and has some libraries that do the kind of IO you need.  Take a look at PyUSB, PyParalell, and PySerial.

Good Luck!

Alex

Hello Alex, 

I am sorry I have not responded sooner.  I should have clarified that I am NOT intending a computer programming project for THIS Halloween.  I also would like to control other things as well.

At any rate I did look a little bit into Python.  I decided to look up PyUSB and PyParallel in the Synaptic repositories and low and behold, there is a HUGE listing for Python.  It is labeld Python-USB and Python-Parallel respectively.  I did download them. There supposedly many Python items ticked off that say they are already on my machine, however, I cannot find any kind of link or short cut to them.

What is a good site that I can go to that I could ease into something like this.  I think I am better off starting with the parallel port since I can easily make a 4 in 8 out interface that connects directly to the port.

Another thing I would like to do is be able to access USB because I want to learn to use gamepad controllers as midi interfaces.  Overall I just need a good way to learn how to interface the computer either the USB port or the parallel port.  I do have a serial port on my machine too, but that I leave connected to my Basic Stamp module for programming.

Thanx,

Geo

---

