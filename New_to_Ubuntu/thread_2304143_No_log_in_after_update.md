---
title: "No log in after update"
date: 2015-11-24
forum: New to Ubuntu
---

### Post by ron3872 on 2015-11-24
I am new to Linux and here so if this is not the proper place please accept my apologies.

I just installed Ubuntu 14.04LTS. Up till now everything has been going good. 

The problem I was having is my screen kept refreshing. After some research I decided to use a fglrx propriety driver for AMD graphic driver. When I rebooted I can't log in now. 

The laptop is a HP DV7-4273us.
It's all amd hardware. Graphic card is 4250/6370m switchable 
 

I rebooted, put in password and can't go any further. It just keeps telling me to put in a password. Not sure what to do at this point other than reinstall again :(

---

### Post by ron3872 on 2015-11-24
Found this thread which is the same issue except I have AMD 4250/6370m switchable graphics [http://ubuntuforums.org/showthread.php?t=2303774&page=4&p=13396192#post13396192](http://ubuntuforums.org/showthread.php?t=2303774&page=4&p=13396192#post13396192) 
So I am still stuck since the original post turned out to be intel related.

---

### Post by QIII on 2015-11-24
The problem with installing the fglrx driver is that AMD no longer supports a Linux driver for any GPU earlier than the HD 5000 series.  With a 4200 series GPU, which your machine probably goes to at startup, the driver will not work so you get a black screen.

You will have to enter recovery mode from the GRUB menu and remove it manually in the terminal.

---

### Post by ron3872 on 2015-11-24
hmm ok I'll see what I can find then to do this. 
Is there a way to force it to only use the 6370?
Thank you

---

### Post by ron3872 on 2015-11-24
[http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Removing_Catalyst.2Ffglrx)

This worked and I am back into my system

---

