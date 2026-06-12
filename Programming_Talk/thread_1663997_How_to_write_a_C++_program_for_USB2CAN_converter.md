---
title: "How to write a C++ program for USB2CAN converter"
date: 2011-01-10
forum: Programming Talk
---

### Post by aworld on 2011-01-10
Dear all

Like the title, I want to ask how to write a program by using USB2CAN converter in C++? 

I have ordered a USB2CAN adapter, and I think it has a FTDI chip inside. What should I do that I can communicate with another CAN device?

Any tips for this?

FYI, I am using Ubuntu lucid,32bit version.
my laptop is DELL Studio 15 (intel i5).
For compiler, I am using g++

---

### Post by wmcbrine on 2011-01-11
I assume you're talking about [this CAN](http://en.wikipedia.org/wiki/Controller_area_network)?

---

### Post by aworld on 2011-01-12
Yes, I am talking about this "CAN" bus. Any tips?

---

### Post by Zugzwang on 2011-01-12
Yes. Start by finding out which Linux driver supports this device. Then have a look which APIs it supports. Finally search for documentation for that API.

However, I had a look at the homepage of the IC manufacturer you noted. They don't seem to have CAN interfaces.

---

### Post by aworld on 2011-01-12
Hi, thanks for quick reply

I got the clue that this USB2CAN adapter has a FTDI chip, it is because in the sample program under linux in C, it includes a header file "ftd2xx.h". I have searched in Google, and it tells me this lib is provided by FTDI, then, it must be their products. 

From what i know, this FTDI company make a lot of products which is able to convert USB inferface to many other interfaces (like sierial port, IIC,etc)

I have once used a USB->serial port adapter, it also has a ftdi chip inside. But what I do in C, is by using open(), read() or write(). Nothing is written by using their libs...

Anyone has experience with this adapter?

---

