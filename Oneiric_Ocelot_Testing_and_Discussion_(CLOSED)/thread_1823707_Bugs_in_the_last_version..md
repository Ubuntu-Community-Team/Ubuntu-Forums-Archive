---
title: "Bugs in the last version."
date: 2011-08-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by exiledangel420 on 2011-08-12
I have to ask with the bugs I've encountered in natty as far my graphic card goes.
Their nvadia accelerated graphic problems to be specific.
Will they be fixed in the ocelot version?
I'm using nvadia geforce fx 5500 128 mb dual display card.
I have an alternative ati 256 mb card but in maverick their was no driver for it.
And I haven't tried it since then.
I can't use unity cause of the bugs.
Oh will the wubi installation through windows allow you to put manually a specific size to your installation.
I used a work around to resize my installation. 
A limitation of 30 gigs just doesn't make sense.
I mean I could have used the alternative installation on boot which I have used in the past. 
And I would have used that If I knew I was gonna use more then 30 gigs.

---

### Post by cariboo on 2011-08-12
What nvidia driver are you using, you should be using nvidia-173 with that video card if you want to use the closed source driver. How does your system work with the nouveau driver that is installed by default?

---

### Post by exiledangel420 on 2011-08-12
Doesn't work either. Either way I can't use unity. and yeah its the 173 driver. you need accelerated graphics for it which my driver is suppose to have but they don't work cause driver is not initialized.

---

### Post by cariboo on 2011-08-12
You may need to run:

```
nvidia-xconfig
```

then reboot. It sounds like your monitor isn't being detected properly.

---

### Post by exiledangel420 on 2011-08-12
tried it. even in the boot up recovery mode.

---

### Post by exiledangel420 on 2011-08-12
by the way my maverick driver works...

---

### Post by exiledangel420 on 2011-08-13
its only when I update to natty when I run into the problems. Oh and all software works except that which depends on unity. I have played most of the fps on ubuntu.  Which alot of them require accelerated graphics. it is the how unity uses the driver. The driver knows it is hpmx70 monitor. it displays as  that is detected. HP MX70 (CRT-0 on GPU-0). Any information on the nvadia driver I can give you. I've tried lowering the resolution. should I do that then retry upgrading? it might be the autodetect that Deny's my monitor by unity. In maverick it starts at a lower resolution though I can take much higher maybe I should trying raising it. hmm, just maybe. oh and does anybody know what two blinking lights mean in ubuntu on the keyboard? Let be more specific a crash with number and caps lock blinking??? I ran it to it alot during installation of other linux too. I'm using a ten year old pc. this happen with the beta versions of natty.

---

### Post by mc4man on 2011-08-13
I would suggest that possibly search out some threads concerning FX5000 series cards and unity, either in the main forums or the natty dev forum (or launchpad bugs
Many of them were and probably still are unable to run unity 3d with either nvidia or nouveau drivers (& may have been blacklisted
There could be some where unity can be forced, others won't matter

If that's  the case for you  then it's 2d or get a better card.

---

### Post by exiledangel420 on 2011-08-13
I might but before I buy the card I gonna have to do some research on the card and compatibility driver of that card. I'm actually quite found of Linux since I started using it.

---

### Post by exiledangel420 on 2011-08-13
Windows lost me after XP.

---

### Post by 3rdalbum on 2011-08-13
The blinking keyboard lights indicates a kernel panic.

This could possibly be due to a buggy Nvidia driver. However, there's also a possibility that it could be due to faulty RAM. As user-space software, Unity should not be able to cause a kernel panic; I mean it might be causing it, but in theory the kernel drivers or the hardware itself is the more likely explanation for your hard crashes.

---

### Post by mc4man on 2011-08-13
here is the natty bug on FX5000 cards and nvidia (173..), I think it's been carried over 
(basically the fix is not to allow
[https://bugs.launchpad.net/ubuntu/+source/nux/+bug/768178](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/768178)

That is also duped to the natty nouveau bug on those cards but 11.10 is not inc. (though the result may be the same, if you force unity it will work but no visible icons in the launcher
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/762478](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/762478)

As far as AGP cards, here both a 7600 & 7800 work quite well (though may be hard to find at this point

---

