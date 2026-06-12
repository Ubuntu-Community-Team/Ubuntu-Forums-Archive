---
title: "Wireless adapter"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by KhalRha on 2012-01-29
Hi. I am new to Linux and I  just installed ubuntu 11.10 alongside widows 7 on my desktop and I'm enable to detect any wireless networks. I'm using a  linskys wusb54gsc ver 2 wireless adapter and it seems that my computer is not detecting my network adapter. Any suggestions? Thnx.

---

### Post by UltimateCat on 2012-01-29
I have the WUS54GC too and I had to go and get the " inf file" for it to work.

I also had to go and get the driver for the WUSB54GC in order for it (inf file) to work with the Ndiswrapper that I installed.  Not sure if that's your case because I don't know if you intent on using Ndiswrapper.

You can use that "inf" file on the cd that came with the adapter; that's another way.

If that doesn't work shut down your computer wait 30 seconds; unplug the adapter and then plug it back into your tower and reboot. 

This is the website where I downloaded the driver to accommodate my adapter. 

[http://help.ubuntu.com/community/](http://help.ubuntu.com/community/)

[http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers)

[http://sourceforge.net/apps/media](http://sourceforge.net/apps/media)

---

### Post by anewguy on 2012-01-29
going that way you'll need the Windows XP driver files - .inf and .sys, and they must match your ubuntu architecture (32 or 64 bit).

To start, though, please leave your adapter plugged in and do the following:

- open a terminal window

- type:

echo "****  lsusb  ****" > dwetest.txt
lsusb >> dwetest.txt
echo "****  lsmod  ****" >> dwetest.txt
lsmod >> dwetest.txt
echo "****  ifconfig  ****" >> dwetest.txt
ifconfig >> dwetest.txt
echo "****  iwconfig  ****" >> dwetest.txt
iwconfig >> dwetest.txt
echo "****  lshw -C network  ****" >> dwetest.txt
lshw -C network >> dwetest.txt

This will create a file called dwetest.txt in your home folder with additional information we can check.

Please reply back and attach that file to the reply.

Dave ;)

---

