---
title: "hiddev getting the wrong vendor ID &amp; product ID"
date: 2009-09-04
forum: Programming Talk
---

### Post by sparker256 on 2009-09-04
I am trying to write a driver for a Saitek radio panel. It has 20 seven segment leds and about 20 switches. I tried to use some of the example programs to get vendor and product info but am not getting the correct numbers. 

The one thing that I have noticed is that I do not get any dev/hiddev* generated but hiddev in set to yes in my config. I am thinking that until I can get hiddev* to generate I cannot use hiddev. I have looked all over this forum and the net and have not found a answer this question. 

Thanks Bill

---

### Post by forscher on 2009-10-19
Hi, I work on an daemon expansion of g15tools for Logitech G13 Gaming Keyboard. I am new to driver programming, but maybe I have some hints.

with lsusb you can see your panel device: idVendor and idProduct
with lsusb -v idVender:idProduct you see more details of the usb descriptor of your panel

If I understand the kernel documents correct (hiddev.txt, input.txt): then a hiddev is only created if udev or hal (I'm not sure) detect an input device (I don't know how). I think your output file should be deep in the dev path. At the moment I don't remember the command to find it. 

If you have found a document or so which describes how hiddev and input event are mapped, please give me the link.

Thx forscher

---

### Post by Rayve on 2010-01-28
Hey forscher, any luck on the g13 yet?  :)

---

### Post by Miscni on 2010-04-28
I dont know, if this here can help, I'm using this information myself, and I found out some things. But I havn't got it to work yet.

[http://wiki.jarfil.net/Logitech_G13#Enlaces](http://wiki.jarfil.net/Logitech_G13#Enlaces)

I also working on a Thread, step by step, what I am doing, but it still needs alot of work [http://ubuntuforums.org/showthread.php?t=1253153&highlight=Logitech+G13](http://ubuntuforums.org/showthread.php?t=1253153&highlight=Logitech+G13)

---

