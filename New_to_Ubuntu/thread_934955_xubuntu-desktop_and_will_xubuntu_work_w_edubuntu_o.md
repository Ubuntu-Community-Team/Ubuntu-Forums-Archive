---
title: "xubuntu-desktop and will xubuntu work w/ edubuntu over the top?"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by VAinWI on 2008-10-01
I'm working with a bunch of p3s, mostly 866 w/ 256MG RAM.  Ubuntu installs OK, but runs slow. I'm trying, first of all, to switch to the xubuntu desktop (unsuccessfully, I might add), so first, I'd LOVE help with that.  A step-by-step, "click this, then click that" type of tutorial would be AWESOME right about now.  I'll figure out HOW everything works later, right now I don't have time.

Second - in researching this, I'm wondering if I should just install xubuntu on these PCs.  My issue - this is for a school and I'd really rather run edubuntu.  So... if I were to install xubuntu, could I still use the edubuntu add-on?

---

### Post by talsemgeest on 2008-10-01
So you want to install the xubuntu desktop over you existing installation? Just open up a terminal and type ```
sudo apt-get install xubuntu-desktop
``` and wait for it to do it's thing, it might take a while.

Hope this helps :)

---

### Post by ronnielsen1 on 2008-10-01
IMHO Xubuntu isn't a very lightweight distro. On anything I've tried xfce on I was NOT impressed with the speed.

> Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.
[B]
[/B]




There's LXbuntu which uses lxde and has minimum requirements of 
> [B]The hardware requirements of LXDE is similiar to Windows 98 (Maybe a little bit higher). So an old Pentium II CPU is enough.
· After X11 and LXDE are started, the total memory usage is about 45 MB on i386 machines. (This value may be higher or lower according to different system configurations.)[/B]


> [[IMG]http://distrowatch.com/images/icon-large/pud.png[/IMG]]("http://distrowatch.com/pud")         Pin-Shiun Chen just announced a special version of [PUD]("http://distrowatch.com/pud") GNU/Linux, an Ubuntu-based mini distribution based on the newest [LXDE]("http://lxde.sourceforge.net/") 0.3: "This edition of live CD is made for the Lightweight X11 Desktop Environment (LXDE), including the newest LXDE 0.3, installer and Ubuntu 8.04 packages. LXDE tries hard to get maximal usability from minimal resource usage, and provide a usable desktop for low end machines. Main Features: LXDE desktop - This live CD is based on PUD, except the full-featured live CD, it also included the newest LXDE 0.3 and pre-configured to provide an easy to use, lightweight and fast desktop. Multi-Language Support - English, both Simplified and Traditional Chinese are fully supported by LXDE live CD." Read the complete [release note]("http://pud-linux.sourceforge.net/lxde.en.html") for more information. Download: [pud-0.4.8.6-lxde.iso]("ftp://mirror.nttu.edu.tw/penk/devel/pud-0.4.8.6-lxde.iso") (259MB, [MD5]("ftp://mirror.nttu.edu.tw/penk/devel/pud-0.4.8.6-lxde.iso.md5")).
or 
fluxbox - Fluxbuntu uses 35-46mb of ram.
There's also icewm which is alot lighter than xfce. You can have more than one window manager installed. You just choose the session you want.

---

### Post by ronnielsen1 on 2008-10-01
> Second - in researching this, I'm wondering if I should just install xubuntu on these PCs. My issue - this is for a school and I'd really rather run edubuntu. So... if I were to install xubuntu, could I still use the edubuntu add-on?
It's all one big linux. You can run lxde, fluxbox, educational packages, kde, gnome in Ubuntu without having to install the ubuntu tweaked version of kubuntu-desktop or xubuntu-desktop or whatever. 
I have the educational packages of edubuntu installed on my box as well as the multimedia packages of Ubuntu studio but it's on an install of Ubuntu. I also have lxde and kde as well as gnome installed.
I really like Ubuntu and it's a great system but I think that separating and renaming the various window manager into different names actually confuses newbies. I mean if you run Suse or Mepis you can get all of the different  packages but you're not running a different operating system all of a sudden

---

### Post by VAinWI on 2008-10-01
So, if I understand correctly, I could figure out which ubuntu-esque OS will run best on the machines I'm using and still load the edubutntu package over the top?

If that's correct, keeping in mind that I really AM a newbie to linux which one would/should work the best? P3, mainly 833 with some 1.0 thrown in, w/ 256 RAM.

Also - when I try to change to the xubuntu-desktop it tells me it can't find it. I think I need to add a repository (?) which I can't figure out how to do.  It seems like running the xubuntu desktop is less resource intensive than gnome? I'm ending up with 'blocks' of closed windows on my desktop and everything takes a long time. Definitely NOT "nimble".

Thanks, all!

---

### Post by ronnielsen1 on 2008-10-01
> So, if I understand correctly, I could figure out which ubuntu-esque OS will run best on the machines I'm using and still load the edubutntu package over the top?
You could load the educational packages  that  Edubuntu uses.  For example, kstars, kalgebra, kgeography etc are all in synaptic or adept.

The best way would be one step at a time. Look at the different window managers and decide which you like.  I didn't mean to confuse you. Xfce (in my opinion) isn't much more resource friendly than gnome or kde but alot of people use it.

So, if you settle on [COLOR=Blue]icewm[/COLOR] as a window manager, you would follow a guide like this

[http://www.psychocats.net/ubuntu/icewm](http://www.psychocats.net/ubuntu/icewm)

[COLOR=RoyalBlue]Fluxbox[/COLOR]

 [http://www.howtogeek.com/howto/ubuntu/installing-fluxbox-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/installing-fluxbox-on-ubuntu-linux/)

[COLOR=RoyalBlue]Lxde[/COLOR]

[http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html](http://www.ubuntugeek.com/lxde-lightweight-x11-desktop-environment-for-ubuntu.html)

[COLOR=Blue]Enlightenment
[COLOR=Black]
[http://www.howtogeek.com/howto/ubuntu/install-enlightenment-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/install-enlightenment-on-ubuntu-linux/)


[COLOR=Blue]Afterstep

[http://www.howtogeek.com/howto/ubuntu/install-afterstep-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/install-afterstep-on-ubuntu-linux/)
[/COLOR]

[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]
(I got these links by googling "install _______ in Ubuntu"[/COLOR][/COLOR]
[COLOR=Blue][COLOR=Black]After you decide on a lightweight window manager you can then install the educational and other  packages you want. Edubuntu might work for you but with only 256 Megs of Ram the default gnome manager might be a little heavy.  
You can add different window managers and programs to either your default Ubuntu or install Edubuntu and install a lighter weight window manager to that. Just don't think to get certain programs requires a certain distribution because it doesn't. You can take a stock Edubuntu or a stock Ubuntu or a stock Fluxbuntu - add or remove all kinds of things and make them all look entirely the same or entirely different. It's your choice. 

If I've totally confused you, disregard everything I've said and download Edubuntu :guitar:


[/COLOR][/COLOR]

---

### Post by talsemgeest on 2008-10-01
> **VAinWI said:**
> So, if I understand correctly, I could figure out which ubuntu-esque OS will run best on the machines I'm using and still load the edubutntu package over the top?

If that's correct, keeping in mind that I really AM a newbie to linux which one would/should work the best? P3, mainly 833 with some 1.0 thrown in, w/ 256 RAM.

Also - when I try to change to the xubuntu-desktop it tells me it can't find it. I think I need to add a repository (?) which I can't figure out how to do.  It seems like running the xubuntu desktop is less resource intensive than gnome? I'm ending up with 'blocks' of closed windows on my desktop and everything takes a long time. Definitely NOT "nimble".

Thanks, all!
So you typed what I said into the terminal?

---

### Post by VAinWI on 2008-10-01
I did the other day.. and it said it couldn't find xubuntu-desktop (yes, I checked the spelling/formatting/etc).  I searched for it and found the file somewhere (system files?), but don't know how to access it.  I'll do it again and let you know exactly where I found it (I'd expect it to be standard? I mean.. it's not going to be in one place for my installation and somewhere else for someone else?)

---

### Post by talsemgeest on 2008-10-01
Ok go to the synaptic package manager and search for xubuntu-desktop. If it still comes up with nothing, please post the file /etc/apt/sources.list

---

