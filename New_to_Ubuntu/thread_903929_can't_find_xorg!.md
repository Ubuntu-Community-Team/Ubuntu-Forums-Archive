---
title: "can't find xorg!"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by GlennW on 2008-08-28
Hi,
I don't know if this is the right thread but being the n00b that I am, I think I've buggered hardy good, at least for my skill level.

I have a nvidia geforce 6200 graphics card. It has been working fine even after upgrading to hardy. But after the upgrade, I couldn't find any way to tweak any nvidia settings. Every time I wanted to access the nvidia settings via the applications menu, it said something to the effect that it couldn't find the directory or path... So, I thought that either upgrading via envy or synaptic would give me access. Well, to make a long and frustrating story short, I've managed to get xorg so screwed up that boot up doesn't happen. If I use the recovery mode and then run through the options, I'm still at the same place. My only option appears to drop to the root shell prompt. I'm thinking that I need to edit xorg from there to at least allow me to boot up but for some reason, I'm not able to access xorg from the root prompt.

My best resolution during this crazy episode is 800x600. I have a Samsung 205bw which has a native resolution of 1680x1050. I really need some help to get it back. At this point, I can't even get past the ubuntu boot up screen.

Thanks for your help.

---

### Post by mikewhatever on 2008-08-28
Well, to access xorg from root console, use <nano /etc/X11/xorg.conf>.

---

### Post by nicedude on 2008-08-28
don't use a root console and instead use the following command

sudo nano /etc/X11/xorg.conf


People should not be telling you to use root consoles as that is supposed to be a no-no here but I see people say it all the time. while using a root console to open that file would not be so bad and no different then what I say to do, it gets people in the habit of logging in as root and they will more than likely break their system by so doing.

and one solution if you can't get it to graphically boot up is to while in Grub boot menu press "e" and then select the kernel you want to boot and hit "e" again to edit the boot command and add vga=ask and then press "b" to boot with the modifies command and you should get a press enter to see available resolutions message and you can choose one and boot into vga mode with graphics so you can fix whatever.

---

### Post by GlennW on 2008-08-29
Thanks guys, for our quick response. 

I think that I must not have made my situation clear. The only way I can get anything to happen is to start in recovery mode. And then, after having run through the other options, is to drop to the root shell. I am attempting to access xorg.conf to change it back to where it becomes a usable file for hardy. At this point, it's quite broken. 

Re-installing is the absolute last resort since there some files that haven't been backed up - my bad! I can't believe that there is no way to access xorg.conf. 

When I do run <nano /etc/X11/xorg.conf>, I don't get the file that I messed up. It's a very basic file with none of the details concerning the monitor settings or nvidia settings or anything like that. 

Guys, I need some help here! Please be patient with this dangerous n00b!!

---

### Post by kellemes on 2008-08-29
Have you chacked for old backups of xorg.conf?
Like so..
```
ls /etc/X11
```

To generate new xorg.conf you can reconfigure xorg like so.. (from single mode)
```
dpkg-reconfigure xserver-xorg
```

---

### Post by GlennW on 2008-08-29
Hey guys,

For whatever reason, I am now able to access my desktop (hardy) but am still at 800x600 rez. How can I get back to using my beautiful Samsung 205bw's 1680x1050?

---

### Post by kellemes on 2008-08-29
> **GlennW said:**
> Hey guys,

For whatever reason, I am now able to access my desktop (hardy) but am still at 800x600 rez. How can I get back to using my beautiful Samsung 205bw's 1680x1050?

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu%208.04%20Hardy%20Heron]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu%208.04%20Hardy%20Heron")

---

### Post by kellemes on 2008-08-29
> **GlennW said:**
> (..) my beautiful Samsung 205bw's 1680x1050?

I have a 225bw, these are pretty cool monitors indeed. ;-)

---

### Post by GlennW on 2008-08-29
> **kellemes said:**
> [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu%208.04%20Hardy%20Heron]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu%208.04%20Hardy%20Heron")

Hi kellemes,

My nvidia card (GeForce 6200) is recognized by Ubuntu 8.04 and therefore is listed on the link that you provided. Under System>Adminstration>Hardware Drivers, my card is listed and is enabled. But still, no joy. 

Under System>Preferences>Screen Resolution, the highest option available is 800x600. The Detect Displays option does not detect my Samsung 205bw. 

What now?

---

### Post by GlennW on 2008-08-29
Sorry I didn't include this earlier but this may be of some help. When I do boot up, there is a box that comes up saying Ubuntu is running in low graphics mode. I then have the choice to configure, shutdown, or continue. I've lately been "continuing" since configuring (where I choose my monitor and graphics card over and over and over to no avail) doesn't seem to do any good.

---

### Post by bcschmerker on 2008-08-29
> **nicedude said:**
> don't use a root console and instead use the following command

sudo nano /etc/X11/xorg.conf


People should not be telling you to use root consoles as that is supposed to be a no-no here but I see people say it all the time. while using a root console to open that file would not be so bad and no different then what I say to do, it gets people in the habit of logging in as root and they will more than likely break their system by so doing.

and one solution if you can't get it to graphically boot up is to while in Grub boot menu press "e" and then select the kernel you want to boot and hit "e" again to edit the boot command and add vga=ask and then press "b" to boot with the modifies command and you should get a press enter to see available resolutions message and you can choose one and boot into vga mode with graphics so you can fix whatever.

I concur with nicedude; I administer my own Everex from Enlightenment, the GTK application automatically requesting an Admin password when a SUDo call is identified.  One of the only situations where I KNOW I'll need the root shell is building and installing an upgrade kernel, which is fully protected during normal operation and only accessible via GRUB on my particular system.

Addendum:  GlennW, I did run into your particular problem once; my Everex also requires a specific Xorg server for its VIA graphics processor.  Sorry, can't remember how I fixed it, but the correct server adapted well to the succession of display units I have used in the past few months, e.g., the Impression 5 5528G (a non-PnP 1280x1024 CRT unit) I'm running as of this post.  The same issue exists with your GeForce, as nVIDIA keeps a lot of hardware information private, unlike ATI/AMD and Matrox.

---

### Post by GlennW on 2008-08-29
> Addendum:  GlennW, I did run into your particular problem once; my Everex also requires a specific Xorg server for its VIA graphics processor.  Sorry, can't remember how I fixed it, but the correct server adapted well to the succession of display units I have used in the past few months, e.g., the Impression 5 5528G (a non-PnP 1280x1024 CRT unit) I'm running as of this post.  The same issue exists with your GeForce, as nVIDIA keeps a lot of hardware information private, unlike ATI/AMD and Matrox.

The issue is that I had things running very nicely even after upgrading to hardy despite hardy "hiding" things on me. I just don't understand why (under Screen Resolutions) there would be a Detect Displays tab when it certainly isn't detecting!!!

Thanks for the input though...

---

