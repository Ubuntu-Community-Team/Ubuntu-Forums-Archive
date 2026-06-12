---
title: "Disable and re-enable USB port?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by brennydoogles on 2008-06-10
I have a bluetooth keyboard and mouse that I use with one of my Ubuntu boxes, and every time I reboot I have to unplug the dongle and plug it back in to make it work. I was wondering if there was a command that I could put in a script (to be run on system boot before GDM starts) that would emulate this action by cutting power to a usb port and restoring it. Any ideas?

---

### Post by anystupidname on 2008-06-10
You could try:
rmmod usbcore
modprobe usbcore

check if there is another module you need to reload too: (or instead?)
lsmod | grep usb

---

### Post by galets on 2010-11-27
Disable usbcore will not work for me, first off it's not even a module, second is that Ubuntu itself is loading from a usb in my setup.

All the USB dongles I have (and all of them are cheap ones, of course) are not loading on boot in ubuntu 10.10. This becomes quite a nuisance, since every time I'm starting machine I have to crawl to the back of computer to re-plug a dongle. Have anybody resolved it yet?..

---

### Post by mmsoft on 2011-04-28
Hi guys
excuse me if my question is not in a true place and my weak english!
but I,m a beginner in ubuntu!
I have installed ubuntu 10.04 on my toshiba a665d s6059
and i like it very much!
i want to delete my win7 but some things go wrong!
my usb ports & dvd-rw not working!!!
please help me easy, complete and brief that a beginner need!
tnx alot

---

