---
title: "Serial Communications - Aquacontroller JR"
date: 2008-11-28
forum: Programming Talk
---

### Post by DirtyBirdNJ on 2008-11-28
Hello, I'm currently trying to figure out how to communicate with my Aquacontroller JR over a serial connection.

[IMG]http://www.f3images.com/IMD/250/NS1165/NS1165_1.jpg[/IMG]

It's a really neat little box that controls an 8 socket power strip I plug my lights, heaters, pumps etc, into and can then control. I designate variables for the channels, and then I can set up simple conditional rules for heat control, daylight simulation, and all sorts of neat stuff. The more expensive Aquacontroller 3 has a built in ethernet port, the JR (what I have) only has a serial port.

The manual that comes with it actually explains how to send commands to it, so I looked in synaptic for a serial terminal so I could try it out. I found GtkTerm and it's worked pretty well so far. Here's some of the commands:


AquaController> c

Current Status is:



Nov 28 2008 21:36:20

Temp pH   

78.8 8.26 

 HET is OFF Auto

 FAN is ON  Auto

 LT1 is OFF Auto

 LT2 is ON  Auto

AquaController> l

HET$-A01

FAN$-A05

LT1$-A02

LT2$-A04





If Temp  < 77.0      Then HET ON 

If Temp  > 78.5      Then HET OFF

If Temp  > 79.0      Then FAN ON 

If Temp  < 77.0      Then FAN OFF

If Time > 08:00       Then LT1 ON 

If Time > 21:00       Then LT1 OFF

If Time > 00:00       Then LT2 ON 

If Time > 02:30       Then LT2 OFF

If Time > 21:00       Then LT2 ON 

The two commands, c and l only print information. The documentation shows how to turn the channels on and off, but the documentation is suspiciously lacking when it comes to how the program gets transmitted to the ACJR, or how to set the time.

The software that the company provides runs only under windows. It's called Aquanotes, and it's a Windows 98 Style Access app. This app is the reason I'm writing this post actually. Aquanotes is the only way to send the program to the device, and the only way to set the time.

[IMG]http://www.championlighting.com/pics/controllerpics/AquaNotesFull.jpg[/IMG]

 My next step is to boot up this software in windows with a serial logger set up, and see if I can figure out what commands it uses to send the program and other "admin" features. Once I have a way to communicate with the ACJR, I will make an Adobe AIR interface to recreate the same functionality in the Aquanotes software. I really want to learn more about AIR, and it seems like a fun hobby project.

I'm new to running ubuntu as a desktop , and I'm not sure how to go about creating an interface to the serial port. I'm a web developer at work using PHP, and I have heard a lot of cool things about python. I found this article about interfacing with the ardiuno:

[http://www.arduino.cc/playground/Interfacing/Python](http://www.arduino.cc/playground/Interfacing/Python)

I'm using a different device, but the principal is the same. I'm really not concerned what language I use, but what I need to be able to do is send a series of commands and know when to listen to the serial port. 

I'm curious if anybody knows of or has a good way to script this process.

---

