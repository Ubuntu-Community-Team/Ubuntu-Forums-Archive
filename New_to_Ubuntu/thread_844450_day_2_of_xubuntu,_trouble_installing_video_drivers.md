---
title: "day 2 of xubuntu, trouble installing video drivers"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Topple on 2008-06-29
Hello, I am only a day into linux and have come across a problem installing drivers for my Geforce FX go5200 graphics chip.

I found the driver I need at [http://people.freedesktop.org/~aplattner/nv]("http://people.freedesktop.org/~aplattner/nv")

I downloaded the file xf86-video-nv-2.1.9.tar.gz and extracted it with tar. 
I entered the file in terminal and tried to ./configure and after a while I got the following message:

> checking pkg-config is at least version 0.9.0... yes
checking for XORG... configure: error: Package requirements (xorg-server >= 1.2 xproto fontsproto ) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'fontsproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I then try to install those three packages and here is what happens:

> /home/user/Desktop/xf86-video-nv-2.1.9# apt-get install xorg-server xproto fontsproto
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-server


If I should be asking someplace else please let me know, but I have been browsing the web for hours trying to find some more information or something I can do. I will probably need fairly low-level advise. 

Thanks.

---

### Post by billgoldberg on 2008-06-29
I don't know if you tried this before, but it can't hurt to ask.

Did you go to "system -> administration -> hardware drivers"?

Your nvidea driver should be mentioned there and it will be downloaded and install automatically.

If there isn't a driver there (not very likely), you can use the program called "envy" to download and install it for you.

For hardy: [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

However, if you use option 2 or install the driver manually, you are going to have to remove it before any kernel update and then reinstall it. *(but I see there is now an envyNG, I'm not sure what that is, so it could be that you won't need to remove/reinstall before/after every kernel update, not sure).*

---

### Post by jimrz on 2008-06-29
Seems some folks have had problems installing nvidia drivers using "system -> administration -> hardware drivers". In that case, many have had success by FIRST installing your driver via Synaptic and THEN using "system -> administration -> hardware drivers" to enable it. This worked for me on several machines, each with different nvidia cards.

---

### Post by Topple on 2008-06-29
I have the Hardware Drivers open right now and the message at the top says:
> No proprietary drivers are in use on this system.
This is fitting, the graphics processor I have is not supported on nvidia's site. I tried to download from them first. Maybe one of the other suggestions will help.

I will try to use Envy as suggested. 

Thanks for the feedback so far.

---

