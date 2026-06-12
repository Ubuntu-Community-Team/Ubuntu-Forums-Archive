---
title: "ATI Drivers on Ubuntu 8.04?"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by whitedays81 on 2008-06-20
Hi

I've Downloaded **Ubuntu 8.04** yesterday, and its my first Linux OS I've ever used. So im a newbie when discussing about Terminals and such.

I've spend all day yesterday looking for a solution to install my **"Radeon X1650 512mb AGP"** video card. so far heres my problems.

-In System> Administration> Hardware Drivers, i can see my video cards "not in use", but when i enable it. then reboot, it would give me a black screen after ubuntu's boot screen. and using EnvyNG results in the same problem.

-I've followed the instructions posted on a thread [http://www.uluga.ubuntuforums.org/showthread.php?t=603595]("http://www.uluga.ubuntuforums.org/showthread.php?t=603595")

it did help enable my visual effects, but the screen flickers and slows everything down. and scrolling down on websites are unbearably slow (and this is with the visual effects off) and yet "Hardware Drivers" shows video card is still "not in use"

I followed a bunch of HOWTO's and ATI instructions on drivers install. but failed. i wanted to try linux because i wanted something new. I've been a Windows user for years. 

My question is, is there anyway to install ATI drivers on ubuntu 8.04?

_**My System Specs**_
AMD Sempron 1.75gh
768mb of RAM
ATI Radeon X1650 Pro AGP 512mb
2-30gig hard drives
Windows Xp Pro (duel booted with ubuntu 8.04)

please help!

Many thanks in advance.

---

### Post by Titan8990 on 2008-06-20
Try this:

$sudo apt-get install envy

Envy will uninstall your existing drivers, download new ones from the ATI website and install them for you. Makes things much easier.

---

### Post by whitedays81 on 2008-06-20
> **Titan8990 said:**
> Try this:

$sudo apt-get install envy

Envy will uninstall your existing drivers, download new ones from the ATI website and install them for you. Makes things much easier.

thank you so much for replying, 

Tried it, but I'm afraid it didn't work.

after i used "sudo apt-get install xserver-xgl" on the terminal, its started to slow down ubuntu (and right now, its ungodly slow), how should i uninstall xserver? 

I really hope theres a solution for this problem. Yesterdays been a pain to find an answer. looks like ATI and Linux don't go hand n'hand.

---

### Post by issih on 2008-06-20
"sudo apt-get remove xserver-xgl"

That will get rid of xgl for you.
As for installing the driver, this thread:

[http://ubuntuforums.org/showthread.php?t=800535](http://ubuntuforums.org/showthread.php?t=800535)

Suggests using a specific version of the driver, namely 8.42.3
Try using envy to install that specific driver version.

Hope that helps

---

### Post by whitedays81 on 2008-06-20
> **issih said:**
> "sudo apt-get remove xserver-xgl"

That will get rid of xgl for you.
As for installing the driver, this thread:

[http://ubuntuforums.org/showthread.php?t=800535](http://ubuntuforums.org/showthread.php?t=800535)

Suggests using a specific version of the driver, namely 8.42.3
Try using envy to install that specific driver version.

Hope that helps

thanks for the reply!

looks like this might work. I'll give this a shot. thanks :)

EDIT: thanks for helping me get rid of xgl. its back to normal. and the thread that you provided me help get rid of the black/white screen issue (AGP aperture size in BIOS to 256). thanks a bunch. :D

---

### Post by chewit on 2008-06-20
If you use the "radeon" driver which comes with Ubuntu, it will give you 2D support for that card.

Follow these two tips that get full 3D support and better performance:

[http://edhewitt.co.uk/2008/03/24/fixing-ati-radeon-on-linux/](http://edhewitt.co.uk/2008/03/24/fixing-ati-radeon-on-linux/)
[http://edhewitt.co.uk/2008/04/07/tweaking-the-ati-radeon-in-linux/](http://edhewitt.co.uk/2008/04/07/tweaking-the-ati-radeon-in-linux/)

---

### Post by brokenhallelujah on 2008-06-20
Chewit -- I have tried everything listed here except what you have suggested.  I will let you know how it goes.

Do I need to roll back to the generic 'radeon' 2D driver beforehand?

---

### Post by whitedays81 on 2008-06-20
> **chewit said:**
> If you use the "radeon" driver which comes with Ubuntu, it will give you 2D support for that card.

Follow these two tips that get full 3D support and better performance:

[http://edhewitt.co.uk/2008/03/24/fixing-ati-radeon-on-linux/](http://edhewitt.co.uk/2008/03/24/fixing-ati-radeon-on-linux/)
[http://edhewitt.co.uk/2008/04/07/tweaking-the-ati-radeon-in-linux/](http://edhewitt.co.uk/2008/04/07/tweaking-the-ati-radeon-in-linux/)

Thanks for the reply and the information!!:)

I've tried what the article "Fixing ATi Radeon on Linux" suggested, but nothing really happened, i followed the steps and didnt see a deference. 

I've also downloaded "DRIconfig". it gave me an alert...

"Could not detect any configurable direct-rendering capable devices. DRIconf will be started in expert mode." 

I also forgot to mention that i wanted to setup my visual effects, but it tells to "enable my driver" but once i do that, reboot, and set my visual effects. it screen goes blank for a few seconds (just shows my wallpaper without the windows, icons, etc) then resumes like nothing happened. all i pretty much wanted was to use visual effects. :(

---

### Post by whitedays81 on 2008-06-20
bump, sorry for double posting :(

I've been looking for a solution to my **Visual Effect** problem all day. i cant get the thing to work.

---

### Post by chewit on 2008-06-21
You want see any visual difference when you had used the "Fixing ATi driver" article, it was only to enable 3D support. You would have seen a huge difference if you run glxgears, before and after you used the tutorial

---

### Post by Kronie on 2008-06-21
here, i had same(almost same) problem with my x600 card and i found a solution. [http://ubuntuforums.org/showthread.php?p=5215482#post5215482](http://ubuntuforums.org/showthread.php?p=5215482#post5215482)

---

### Post by whitedays81 on 2008-06-21
> **chewit said:**
> You want see any visual difference when you had used the "Fixing ATi driver" article, it was only to enable 3D support. You would have seen a huge difference if you run glxgears, before and after you used the tutorial

thanks for the info! :)

> **Kronie said:**
> here, i had same(almost same) problem with my x600 card and i found a solution. [http://ubuntuforums.org/showthread.php?p=5215482#post5215482](http://ubuntuforums.org/showthread.php?p=5215482#post5215482)

i followed you're steps, it did help with a few issues i had, but it didnt enable Visual Effects. but thanks for the support!:)

Now when i adjust the Visual Effect to "normal" or "extra" it would hide all my icons, windows, and top/bottom bars only to show my wallpaper for a few seconds, then returns to its origial setting.(much like the white screen after i set Visual Settings, only this time its just my wallpaper) like it never happened.

is there a solution to this problem? is there anyway i can select a Visual Effect?

EDIT: right now i have the "Hardware Driver" enable, but still experiencing the same problem.

---

### Post by Dbugger on 2008-06-21
Same problem with my ATI RADEON XPRESS 200M. It worked fine with Gutsy Gibbon. If you want it badly to work. move to 7.10. This is a big bug Ubuntu made with hardy. bad ubuntu :)

---

### Post by Kronie on 2008-06-21
> Now when i adjust the Visual Effect to "normal" or "extra" it would hide all my icons, windows, and top/bottom bars only to show my wallpaper for a few seconds, then returns to its origial setting.(much like the white screen after i set Visual Settings, only this time its just my wallpaper) like it never happened.

do you have compiz/emerald running? cuz when i switch visuall effects mode, i get smae thing for 5-10 seconds or so..but then it recovers and sets me to the mode i want..

---

### Post by whitedays81 on 2008-06-21
> **Dbugger said:**
> Same problem with my ATI RADEON XPRESS 200M. It worked fine with Gutsy Gibbon. If you want it badly to work. move to 7.10. This is a big bug Ubuntu made with hardy. bad ubuntu :)
 
Thanks! i've been thinking about downgrading all day, if theres an easy solution i'll get back to hardy. if i cant solve this by tonight then i'll just downgrade. :)

It just feels empty without all those crazy windows and and rotating cubes.


> **Kronie said:**
> do you have compiz/emerald running? cuz when i switch visuall effects mode, i get smae thing for 5-10 seconds or so..but then it recovers and sets me to the mode i want..

is there a way to enable them manually? i've already installed emerald. but i dont know what to do next. :(

---

### Post by Kronie on 2008-06-22
srry i dont knwo how to enmable them.. the way i did it is i followed one manual somewhere on this forum...

---

### Post by Darkjasper on 2008-06-22
I tried for a few days straight trying to get my x1650 working. After a reinstall of 8.04 I just used the restricted drivers that are prompted for you to use at first boot. After enabling those rebooting, every thing seemed to work fine. Compiz-fusion works great and i can play games after i disable compiz-fusion with the switch on there site.

---

### Post by Lord Xeb on 2008-06-22
Try this site: [http://notes.theorbis.net/2008/02/upgraded-my-linux-ati-driver-aiglx.html](http://notes.theorbis.net/2008/02/upgraded-my-linux-ati-driver-aiglx.html)

it worked for me! And do not be afraid of command line, just copy and past the commands into the terminal (and ignore the dollar signs, they just indicate you are doing everything from the normal user). After a few reboots you should be good to go :D

---

