---
title: "Configuring Display Settings?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by ap659 on 2008-11-04
Hi folks,

   g'day to all ... and especially to those in the US. Straight onto topic now .... I installed Hardy yesterday, and then did an upgrade over the network today to 8.10 ( just to see the how the whole act played out ). 

So, now my question is what is the right tool to configure display settings in 8.10 once i've installed the proprietary ATI driver? Things like how many colors ( 16vs 24 bit, etc ). 

Also, are we supposed to use /etc/X11/xorg.conf at all now? How about another graphical utility ( i forget the program name ) that allows graphics card and monitor selection- is that still current? And last question- is there a utility that can be used with ATI drivers?

my thanks upfront. The network upgrade went well generally. However, my network status is no more displayed next to the clock. I've disabled wireless as of now.

cheers,
-ap659

---

### Post by mapes12 on 2008-11-04
It depends on what graphics card you have. EnvyNG:

[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

Can be used to setup the none free ATI driver but this does not support all ATI cards (as I have found out to my peril).

The X.Org wiki 

[http://www.x.org/wiki/Projects/Drive...t=VideoDrivers](http://www.x.org/wiki/Projects/Drive...t=VideoDrivers)

Lists the supported devices.

xorg.conf is now almost none editable as you can see from your file with most settings being done by the X server which I have no idea how to configure.

---

### Post by Peter09 on 2008-11-04
xorg is basically unused now except for strange configurations. You should be able to set your display to what you want using

System->Preferences->Resolution

however that is not always the case. Also there are configuration utilities that appear with the driver (sometimes).

---

### Post by ap659 on 2008-11-04
Thank you, Mapes and PeterG. I was not aware of the EnvyNG project before and had a brief look. Turns out the proprietary ATI driver Ubuntu selected for me seems to be working alright for now with my X300 card on my IBM/Lenovo Thinkpad laptop. So, do I need EnvyNG?

So the xorg.conf goes into history book? Good riddance, although I've only dealt with it for less than a week ;-) But what configuration tool would replace it? Does the user no longer have a choice to pick his graphics card and monitor from a list of supported devices?

thx,
appy659

---

