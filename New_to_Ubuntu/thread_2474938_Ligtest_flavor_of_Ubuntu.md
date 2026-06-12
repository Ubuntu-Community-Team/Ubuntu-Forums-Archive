---
title: "Ligtest flavor of Ubuntu"
date: 2022-05-11
forum: New to Ubuntu
---

### Post by beetlebailey2 on 2022-05-11
For an old computer with minimum specs, what would be the lightest flavor of Ubuntu to install?

---

### Post by oldfred on 2022-05-11
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
[https://opensource.com/article/20/5/linux-desktops](https://opensource.com/article/20/5/linux-desktops)
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

As a test I installed Kubuntu (more mid-wieght) 20.04 to my old laptop which I had retired. Its from 2006 with 64 bit core2 duo & 1.5GB of RAM. Ubuntu would not install. Server did install and I was able to add lightweight gui. But then I tried Kubuntu which I now use on desktops. I was surprised it worked and while not fast was functional.

---

### Post by poorguy on 2022-05-11
[https://www.bodhilinux.com/](https://www.bodhilinux.com/)

---

### Post by maketopsite on 2022-05-12
IceWM or openbox window managers are much lighter than that in Lubuntu,  xubuntu, Ubuntu MATE, Budgie and can be installed from any flavor.

---

### Post by guiverc on 2022-05-12
From what I've seen reported in many articles; the *lightest* Ubuntu *flavor* when booted with *live* media or from an *installed* system has Lubuntu as the *lightest*.

Maybe my response is biased given I'm a Lubuntu member, in fact on the Lubuntu Council, but here I'm reporting what I've read in blogs. You can find & read them yourself, or test for yourself if you so wish.

**Myself - I don't think the *lightest* flavor actually means anything**.  As I always consider how the machine will be used and I'd likely not always choose Lubuntu.

Modern Lubuntu uses the LXQt desktop and is thus Qt5 based. If you're wanting to use only GTK3 apps, the *lightness *of Lubuntu won't really be of benefit as you'll need to waste memory having Qt5 *libs/toolkits* in ram for your desktop, then GTK3 *libs/toolkits* in ram as well for your apps - ie. in this case I'd likely suggest Xubuntu instead.

Myself; if I wanted the lightest Ubuntu *flavor* & desktop; I'd say Lubuntu. It's best with Qt5 apps of course; though if you're needing to use apps that need Qt5 + KF5 then Kubuntu won't be that much heavier anyway, but still is heavier.

If you're wanting to use GTK3 apps though; Xubuntu will *generally* win out.  Next I'd likely go for Ubuntu-MATE if using GTK3 apps.  The difference between Xfce & MATE isn't that great; so don't forget tastes.

Don't forget your tastes though...  Use something that will make you happy !

The box I'm typing this on is a 2009 dell; and whilst yes I'm using Lubuntu/LXQt, I also have Xubuntu/Xfce installed, as well as Ubuntu/GNOME & others... and use them too on it.

I personally still use devices with 1GB of RAM only; and generally go for WM's on them, but to get the *lightest* you really need to match up for desktop, apps & everything.. not just consider the desktop itself & except it to remain light with allapps.  I usually bloat my boxes with multiple desktops installed; and decide what I login & use (*esp. if box has limited resource**s*) what will be lightest given what I'll be doing that session; ie. having multiple installed uses extra disk space, but with 1GB of RAM I care most about being *light *on ram usage.

FYI:[ Lubuntu don't provide minimum specs]("https://lubuntu.me/taking-a-new-direction/"), but I've tested all releases up to Lubuntu 22.04 LTS on boxes from 2006 & newer (FYI: Xubuntu too runs on those boxes)...  I used older boxes up to 19.04 when we *dropped* i386.

---

### Post by grahammechanical on 2022-05-12
I suggest that you take into account the video adapter. Integrated graphics will some system memory (RAM) which if in short supply will affect what we perceive as performance. A discrete video adapter will have some RAM of its own. The more video memory a graphic adapter has the better the perceived video performance.

Regards

---

### Post by GhX6GZMB on 2022-05-12
I'm with guiverc here. It depends on your usage.
I'm running five HP 6910p laptops (2008 vintage) with Core 2 Duo 2 GHz and 2...4 GB RAM, four with integrated graphics (Intel, 1280x800), one with Radeon X2300 (1440x900).
All five are on Lubuntu 20.04 and are fast and reliable and over 5 times faster than my 4 years old Win10 Dell laptop. No comparison at all.
2 GB is the lower RAM limit, 4 GB is optimal. Apart from that, the biggest favour your can do to your machine is to change to an SSD. This alone increases speed 4...5 times.
RAM usage after boot is around 350 MB, rising to 800 MB when opening a browser with 5 tabs (I use Brave as browser).
Cold boot time to login screen: 25 s with SSD. Shutdown time: 2 s.

I first tried installing "normal" Ubuntu on the 4 GB laptop, but this bogged down the system completely. That's why I changed to Lubuntu and never regretted it.

Hope this gives you an idea and helps you quantify the issue.

---

### Post by keylowmike on 2022-05-12
My answer might come off a little biased or noob, but here goes: 
As far the "lightest" flavor to run on older hardware, IMO you can't go wrong with Lubuntu.  Why do I feel that way?  My "Ol' Reliable" laptop that I'm typing this out on right now is a Dell Latitude D820, with a Intel Core 2 Duo, 4GB of RAM, 160 GB hd, and a "Designed for Windows XP" sticker that won't stay there long once I make a trip to Ebay.  Anyway, I made the decision to jump back into Linux after a long hiatus (my first foray was Red Hat Linux 7.3, not to be confused with RHEL, just old Red Hat), and I originally installed Ubuntu 22.04 on Ol' Reliable.  That didn't work out, the hardware was not able to handle 22.04 at all.  So, I did some research and installed Lubuntu 22.04 instead.  It runs smooth as silk and I'm impressed with how much more life Lubuntu gave Ol' Reliable.  Now there might be flavor out there that's lighter and makes your hardware a little more zippy, but for me I would have to suggest give Lubuntu a try.

---

### Post by TheFu on 2022-05-13
Lubuntu is pretty light compared to other Ubuntus, but not when compared to many other Linux desktop distros.  And, if your CPU isn't 64-bit, none of the current LTS you should install will run.  

So, the lightest Ubuntu desktop is debian or mx Linux or PopOS if you want a 'reasonable' desktop.  If you are nerdier, you can get at least a factor of 10x lighter with a desktop that uses a different package management system than APT.

The workload, CPU, RAM and storage size/speed are what matter most. If you are doing GPU intensive stuff, then that can be the most important.  Computers from 2012 and later generally have GPUs that handle decoding of hidef video in hardware, so as long as you aren't going above 1080p resolution and just want to watch a few videos, it should be fine.

---

### Post by GhX6GZMB on 2022-05-13
It doesn't seems to interest the OP anymore.
Efforts wasted.

---

