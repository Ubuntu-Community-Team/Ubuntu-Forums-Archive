---
title: "error on /dev/sda"
date: 2015-01-08
forum: New to Ubuntu
---

### Post by thivaakar on 2015-01-08
Good Day everyone. 

I'm new to Linux and I'm trying to run a home server.

However, I'm having trouble installing Linux Server (ubuntu 14). I can't get past the language selection.

I've tried using several types booting software and different pendrives but it stays the same.

Kindly advice on how to proceed from here.

---

### Post by Doug S on 2015-01-08
Hi and welcome to Ubuntu forums,

Could you tell us a little about your hardware?

Also, I wonder if your keyboard is working properly (at least as used by the installer). Can you move around the languages selection screen at all? I.E. can you select F1 or highlight another language or whatever, rather than just "enter" to accept "English"?

---

### Post by kpatz on 2015-01-08
You do know you have to use the keyboard on the language selection screen, right?  The mouse doesn't work until the live CD finishes booting.

---

### Post by thivaakar on 2015-01-08
> **Doug S said:**
> Hi and welcome to Ubuntu forums,

Could you tell us a little about your hardware?

Also, I wonder if your keyboard is working properly (at least as used by the installer). Can you move around the languages selection screen at all? I.E. can you select F1 or highlight another language or whatever, rather than just "enter" to accept "English"?

> **kpatz said:**
> You do know you have to use the keyboard on the language selection screen, right?  The mouse doesn't work until the live CD finishes booting.

I'm sorry i failed to mentioned that the I can't get to move around the language selection with my keyboard. However the keyboard is fine when I'm at bios settings, able to select boot from USB-Hdd

Hardware Specifications:
500gb Sata 
2gb ram
core2duo processor
gigabyte g41m-combo motherboard

---

### Post by Doug S on 2015-01-08
Is your keyboard a USB one? If yes, could you try a PS/2 one? Also have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=2161179") (in particular [post 5]("http://ubuntuforums.org/showthread.php?t=2161179&p=12762265#post12762265")).
Also, some references mention to try a different USB port.

---

### Post by thivaakar on 2015-01-09
ouuuu the bios settings, i did not set enable usb keyboard.

muchas gracias gentleman.

---

### Post by mörgæs on 2015-01-09
Please mark the thread 'solved'.

---

### Post by thivaakar on 2015-01-09
new issue arose. 

input/output error during read on /dev/sda

I did some googling and it may either be harddrive issue or the software corrupted.

the Hard disk is barely a week old..

Plus i've tried re-booting into a different pendrive, still having the same problem

any advice gentlemen?

---

### Post by Doug S on 2015-01-09
thivaakar,

You should have started a new thread for your new problem, rather than change the title of this thread.
Please consider the perspective of future users searching the forums for help with their own keyboard and stuck at language selection step issues. They might get hits for this thread, but then not bother to look at it because the title doesn't correlate to the issue. A good example, is the thread I found and pointed you to above.

O.K. moving on...
Please give us the details for the drive, make and model and such. Are there any more details about the error?

Edit 1: Tell us when this error occurred. Was it during installation? If yes, at what stage of installation and were you using the whole disk and making new partitions or what?

Edit 2: Perhaps have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2260147").

---

