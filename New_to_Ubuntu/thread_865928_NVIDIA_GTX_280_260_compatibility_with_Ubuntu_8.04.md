---
title: "NVIDIA GTX 280/ 260 compatibility with Ubuntu 8.04"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by WRDN on 2008-07-21
I am planning on building a new PC within the next few weeks, and am looking to get either the GTX 280 or GTX 260 GPU.
I will be dual booting Ubuntu 8.04 and either Windows Vista or XP, which will mainly be used for gaming and some software development (in September, hopefully starting a Computer Science course at University.
From looking at the [Ubuntu Hardware Support]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia") list, nothing beyond the 8800GT is listed, and this seems outdated.
Please could someone who has used either of the graphics cards with Ubuntu confirm whether or not they they work properly.

---

### Post by drs305 on 2008-07-21
This Nvidia page indicates they released drivers for the 260/280 last month:
[Linux Display Driver - x86]("http://www.nvidia.com/object/linux_display_ia32_177.13.html")

You are correct about the Supported Hardware list being a bit out of date as I know the 9600 series works and it isn't yet listed.

---

### Post by Sawatz on 2008-07-29
I just got a new computer with a Evga E-Geforce GTX 280, Evga Nforce 750I, Intel Core 2 Quad Q9450. So far I can't seem to get Ubuntu to recognize the GTX 280. I did install Nvida-Linux-x86-177.13-pkg1.run after some working on it i finally got them installed and it looked like the Drivers working but after I restarted they didn't recognize the Graphics card anymore.

Also I am duel booting Ubuntu 8.04 with Window's XP. I installed XP first then tryed to install Ubuntu it created some error in windows that made me have to Reinstall XP but I have also been having a pile of problems with XP, it really don't seem to like this system set up.

If anyone has any sugestions on how I can get it to Recognize the Graphics card that would be much appreciated. I am a total Linux Noob so there is alot of stuff I don't understand. At this point I would say that it don't work properly.

---

### Post by hkbruvold on 2008-08-11
> **Sawatz said:**
> I just got a new computer with a Evga E-Geforce GTX 280, Evga Nforce 750I, Intel Core 2 Quad Q9450. So far I can't seem to get Ubuntu to recognize the GTX 280. I did install Nvida-Linux-x86-177.13-pkg1.run after some working on it i finally got them installed and it looked like the Drivers working but after I restarted they didn't recognize the Graphics card anymore.

I have the same problem, with my GeForce GTX 260.
I still don't know why.

---

### Post by erickghint on 2008-08-11
I'm currently using a Evga GTX260 Superclocked Edition. Works fine for me. As to the OS not remembering the card for you guys, did you remember to edit /etc/default/linux-restricted-modules-common ?

if not open a console and type :
sudo nano /etc/default/linux-restricted-modules-common 

in the editor there are a couple of quotes at the bottom. put nv in the quotes. Should look like this: 

 DISABLED MODULES - "nv"

After you do this, reinstall the drivers you got from nVidia and you're good to go.

---

### Post by keyboardslave on 2008-09-17
Greetings,

This goes out to all owners of a [COLOR="Red"]GTX260[/COLOR], I have got my [COLOR="Red"]ZOLTEX GTX260 OC EDN [/COLOR] working perfectly, after a few days of screwing around and reading i have sucessfully got Ubuntu Hardy to Reconise my GTX260. All my problems stemed from using incorrect drivers.
The drivers you _**NEED**_ are 177.68 (BETA).

Starting from a _fresh install_ i suggest the following.

[CENTER][COLOR="DarkGreen"][U]Download the Drivers.
[/U][/COLOR][/CENTER]

"wget ftp://download.nvidia.com/XFree86/Linux-x86_64/177.68/NVIDIA-Linux-x86_64-177.68-pkg2.run"
(x86_64 version)

"wget ftp://download.nvidia.com/XFree86/Linux-x86/177.68/NVIDIA-Linux-x86-177.68-pkg1.run"
(x86)

[CENTER][COLOR="DarkGreen"]_then follow this fantastic tutorial,_[/COLOR] [/CENTER]

([http://ubuntuforums.org/showpost.php?p=5086971&postcount=](http://ubuntuforums.org/showpost.php?p=5086971&postcount=))


Just make sure u use the 177.68 drivers and you will be amazed at how easy it is, those drivers even AUTO detected my GTX260, and set the resolution perfectly.

OS: Hardy
MOBO: 790i
CPU: 6600 Quad
GFX: GTX260

Regards,
:guitar:

---

### Post by OldBitByter on 2009-02-11
Finally, SUCCESS !!!!

Thank you so much keyboardslave.  That's what I've been for the last 3 days trying to get my card working,,,, again.  I spent a week the first time, got it going, and was happier than a pig in mud.  Then, I did some installs of neat sounding stuff, worked fine, and I went to bed.  Next morning, error when booting said couldn't deal with nvidia, booted in low res.  The previous time I installed didn't work, or.... more likely,... I couldn't find it.  So, for 3 days I've been trying to get installed, from 7am to 1am each day.  I was just trying to figure out how to wipe os and all and start over when I saw your post.  Everything worked just fine.  One note, when I did it, the sudo ./NVIDIA*.run failed.  It gave error msg about the x86_64 pkg.  So, I ran the x86_64 manually and it told me I didn't have 64bit system so I ran the x86. file and it installed perfect.  I followed the rest of the instructions and everything worked just fine.  

Thanks
\\:D/

---

