---
title: "Ethernet card not responding dualboot"
date: 2013-02-13
forum: New to Ubuntu
---

### Post by p3thead on 2013-02-13
Hello when I try to reboot to my Ubuntu partition I just get the message telling me that I have no network cable connected even though it's connected. So I reboot to Windows and the same problem occurs. I get the message telling me that I have no internet connection nor cable connected.

There is nothing wrong with the cable itself since it works fine when I plug it into my laptop. But the ethernet card just won't respond in my desktop computer the ethernet card LED is not even blinking.

The problem is fixed by just having the computer turned off for a few minutes and then when I reboot to windows the card actually responds again. But it doesn't work in Ubuntu.

The problem occurs when I try to reboot to Ubuntu, and the ethernet card just refuses to work while in Ubuntu. It only responds when I've had the computer turned off for a couple of minutes and boot into windows. It seems as if the drivers just won't work with Ubuntu or something.

It was working fine before but haven't really used Ubuntu on my desktop computer for a few months so I have no idea what actually causes the problem.

Any ideas? :confused:

---

### Post by hpkeyser on 2013-02-13
If you can find out what type of ethernet card it is, D-link, Belkin, Cisco, etc. you could try visiting the manufacturer's website to see if that card is even supported by linux.  I've had that problem before too and it was the fact that I was using a card that wasn't supported.  After that, I'd look around and see if anyone has written custom drivers for that card to make it work.  Get back to me and see if that helps

---

### Post by p3thead on 2013-02-13
I have a GA-870A-UD3 motherboard and it has a Realtek 8111D/E chip (10/100/1000 Mbit) integrated on it.

Googled something and found this [http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/](http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/)

---

