---
title: "Serial Port Control"
date: 2008-03-02
forum: Programming Talk
---

### Post by Patriot1776 on 2008-03-02
Okay, I'm about to dive into C programming to write me a program that will use pins 7 (RTS), 8 (CTS), and 9 (PWR) of my DB9 serial port, COM1 to use for timing tests of a pulsing device.  I'm wondering how I would access the com port in the program and specifically how to access the pins.

Here's how I want the program to work.  At startup, it will apply power through pin 9 (PWR) and with the pulsing device idle will be seeing continuity on pin 8 and open on pin 7.  When the pulsing device is activated, continuity will appear on pin 7 to alert incoming pulses and pin 8 will be pulsed off and back on a number of times and then pin 7 will go open again to signal the end of pulsing on pin 8.

What this program is going to do is time how long in milliseconds each off-on event on pin 8 lasts during the pulsing, and during each pulsing event, also measure how long pin 8 was off, and then back on, before going off again.

It will then take the total time that pin 8 was pulsed and convert it into pulses-per-second, and also average out the times pin 8 was off during the pulses and give them as a percentage total of each pulsing event.

I hope the program getting access to the serial port and these pins is not going to be hard.

---

