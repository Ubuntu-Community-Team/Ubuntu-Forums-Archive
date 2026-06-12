---
title: "Still xorg.conf doesn't let my Ubuntu boots up"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by TomErwin on 2011-10-04
Hello everyone, been a while since I had a problem :)

Yesterday I wanted to set the pinch-zoom option for my touchpad. I used a thread (which I can't find anymore) asked me to edit my xorg.conf . i did as it asked me through a terminal, except that I found that my touchpad is not "synaptic" (which I am not sure what it means). So I just ignored the whole thing and continued working on my netbook.

When I finished my work on it, I turned it off, and after an hour or something, tried to turn it back on, and it doesn't boot up! It does actually, but it freezes right before the login screen and it only shows a back screen with a frozen mouse pointer.

Please in simple English (highly appreciated) what should I do now? I have logged in with a Live CD and I still can't find an Xorg.conf file at all at /etc/X11 

All I want now is to have my beloved Ubuntu back 

(just in case it would help; I am using Asus Eee PC 900)

Shokran! (Thank you)

PS: Now I notice I have a file called xorg.conf.safemode or xorg.conf.failsafe, I can't remember. I have seen it under my live CD, but I can't modify or rename it. (by the way, I have 10.10 installed and 10.04 on the live CD, I upgraded after installing )

---

### Post by D0natell0 on 2011-10-06
I would recommend using the boot repair utility. It has a very easy to use GUI. See>>

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

[https://sourceforge.net/projects/boot-repair-cd/files/](https://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by P05TMAN on 2011-10-06
> **D0natell0 said:**
> I would recommend using the boot repair utility. It has a very easy to use GUI. See>>

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

[https://sourceforge.net/projects/boot-repair-cd/files/](https://sourceforge.net/projects/boot-repair-cd/files/)

The boot repair generally just does that, repairs the boot process. I  have not heard of it recovering your desktop environment. If you wish to  try boot repair on the live CD there is actually an Ubuntu wiki with  some detailed instructions on its installation & use: 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Let us know if that works for you; I'm curious

---

### Post by anewguy on 2011-10-06
The first thing you might want to try:

- at the boot menu, select recovery mode
- when the terminal session comes up:

sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf

and then reboot.  

If that doesn't work:

I haven't tried this so no guarantees, but I gleaned some information from some other threads and internet posts I hope might help:

- at the boot menu, select recovery mode - 
- when the terminal session comes up:

sudo X -configure

This supposedly creates a new xorg.conf file as follows:

/root/xorg.conf.new 

You could edit this file file with vim or other terminal-based editor and see if you can see something for the touchpad that shouldn't be there.  If so, modify it.

Then:

sudo cp /root/xorg.conf.new /etc/X11/xorg.conf

Normally one could restart GDM, but since this is recovery mode and since you had the problem at boot up, try rebooting now and see what happens.

There also used to be a way from the command line to reconfigure X, but I don't think it's supported any more.

I'll do some more hunting - if you don't have things solved by the time I finish I'll post back whatever else I might find.

Dave ;)

---

