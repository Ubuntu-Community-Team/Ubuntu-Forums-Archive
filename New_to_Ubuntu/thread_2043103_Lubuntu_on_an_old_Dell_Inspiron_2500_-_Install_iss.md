---
title: "Lubuntu on an old Dell Inspiron 2500 - Install issue"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by zuren on 2012-08-15
I successfully put Lubuntu on an old desktop computer of mine so that gave me the courage to try my old laptop:

Dell Inspiron 2500 (circa 2001)
Celeron 700Mhz
318MB RAM (512MB max)
Intel 82815 Graphics Controller
LCD screen - 1024x768
DVD-RW drive
CD-ROM drive
D-Link DWL-650+ PCMCIA wireless adapter
currently running Windows XP

Due to the age and low RAM I used the same Alternate Install disc that I successfully used for the desktop.  BIOS is set to boot from the CD drive.  I insert the disc, reboot and get the following prompts:

> Language - select English
Select "Install Lubuntu"All seems normal, the CD spins up but I get the following:

> Undefined video mode number: 314
Press <Enter> to see video modes available, <Space> to continue or wait 30 sec.I've tried almost every combination of options possible here.  All result in a blank, black screen with a flashing cursor:

- I've hit Enter and tried every video mode 0-6
- I've hit the space bar
- I've waited well over an hour for a couple of the video options
- I've tried using "nomodeset"

All result in the black screen with the cursor.

I'm searching the error in the forum and across Google but if anyone can offer a suggestion, I would appreciate it!

Thank you!

---

### Post by Kickinthedoor on 2012-08-15
You could always try downloading the iso file and make a new live cd. Does the cd allow you to run a live session? you specs seem fine to me but hey, im no expert

---

### Post by Bashing-om on 2012-08-15
Hi zuren;
 Here is one possiblity to try... on you kernel command line:
```
vga=normal
```
reference this site:
[http://gusantov.blogspot.com/2008/05/undefined-video-mode-number.html](http://gusantov.blogspot.com/2008/05/undefined-video-mode-number.html)

responses indicate it works!

[INDENT]HTH <==BDQ 
[/INDENT]

---

### Post by madjr on 2012-08-15
you can also try a live-usb instead of cd.

or wubi inside XP.

old CD rom drives tend to fail a lot.

---

### Post by zuren on 2012-08-16
> **Kickinthedoor said:**
> You could always try downloading the iso file and make a new live cd. Does the cd allow you to run a live session? you specs seem fine to me but hey, im no expert

The Alternate Install disc does not have the option to try Lubuntu first.  I could make a new one.

> Hi zuren;
 Here is one possiblity to try... on you kernel command line:
     Code:
     vga=normal 
reference this site:
[http://gusantov.blogspot.com/2008/05...de-number.html]("http://gusantov.blogspot.com/2008/05/undefined-video-mode-number.html")

responses indicate it works!
HTH <==BDQ I did some searching on this and found additional info supporting the method.  I replaced "vga=788" in the command line (pressing F6) with "vga=normal".  The result is the same, a black screen with cursor but the "314 error" message is gone.  

I even removed the 64MB stick of RAM, leaving the single 256MB stick wondering if the mismatch might be causing an issue.  Same result.

> old CD rom drives tend to fail a lot.     I won't rule it out but I don't have reason to believe the CD drive is bad.  It was reading other discs as well as browsing this install disc just fine.

---

### Post by mastablasta on 2012-08-16
you could try an older kernel (for example from 10.04).

---

### Post by anewguy on 2012-08-16
Many years ago I had a 2550 I installed ubuntu to - but that was a long time ago.  About 1 year ago I picked up a couple Dell's real cheap and one was another 2550.  Ubuntu did run on it as well, but again, an older version.  The only thing that comes to mind is I *think* I had to boot with either noapic or something like apci=off otherwise I seem to remember having a similar problem.  I did, however, have both max'd out at 512mb of memory.

---

### Post by kansasnoob on 2012-08-16
When you first booted the CD did you run "check disc for defects"?

---

### Post by NikTh on 2012-08-16
Hi , 
you could always try the Lubuntu 10.04 , I think is lighter. (compared to Lubuntu 12.04)

Download it from here --> [http://lubuntu.net/blog/lubuntu-1004-now-available-download](http://lubuntu.net/blog/lubuntu-1004-now-available-download)

Be aware that Lubuntu 10.04 or 12.04 is not LTS version so in 10.04 you will have an older LXDE version and Ubuntu 10.04 (which Lubutu based) will end of life in about 9 months. 

Aggregated : You will have a supported - updated Ubuntu version (for 9 months) with an outdated LXDE environment (and packages followed LXDE , e.g: leafpad , lxdm , PCmanFM). 
I think it is  a good choice. 
Thanks

---

### Post by zuren on 2012-08-16
> **anewguy said:**
> Many years ago I had a 2550 I installed ubuntu to - but that was a long time ago.  About 1 year ago I picked up a couple Dell's real cheap and one was another 2550.  Ubuntu did run on it as well, but again, an older version.  The only thing that comes to mind is I *think* I had to boot with either noapic or something like apci=off otherwise I seem to remember having a similar problem.  I did, however, have both max'd out at 512mb of memory.

This worked!  I switched to "vga=normal" in the command line, chose "apci=off" and Lubuntu installed.  As a newbie, I was a little afraid to randomly try different install modes without knowing what they do.

There are 2 things that I may need to straighten out now:

1.  My PCMCIA wireless card was not deteched nor was the onboard wired network card (modem/ethernet). I don't care about the PCMCIA card.  I just used the USB wireless adapter that I'm using on the Lubuntu desktop and it connected to my network.  This is an extra/beater computer for the garage so it isn't critical that it is connected to the network all the time. However, I will be looking into getting the wired connection recognized.

2.  The display looks great at the login screen.  After login, the desktop has concentric circles starting at the middle of the screen.  I had the same thing on my desktop before I was able to switch to the graphics card with a DVI connection.  The system is functional but I'm sure there is a setting that needs to be tweaked to make it look better.

Thanks for the help!

---

### Post by mmuldoor on 2012-09-28
Thanks guys! I had the same problem, did the same tweaks, and it worked for me too! Ubuntu forums awesomeness

---

### Post by xmrkite on 2012-10-19
Where do you make this tweak? I did an lubuntu 12.10 install via the alternate disc. The install completes, but you can't boot the system. How do I apply this vga=normal after installation?

---

### Post by Bashing-om on 2012-10-19
@ xmrkite; If the "tweak" works for you from the kernel boot line...then all that is needed is a simple edit to the /etc/default/grub file.
see these tutorials for full explanations:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

any difficulties or questions, we are here, but please start a new thread to get greater attention for help.
[INDENT]it's all good <==BDQ

[/INDENT]

---

### Post by mmuldoor on 2013-02-13
I'd also like to report that these command-line arguments, or "tweaks" appear to work on any Debian-based cd. I just used it to install XFCE Debian wheezy via the net install disc. Of course, I'm up to the full 512 mb ram now. If you're at 128 mb or 256 mb still, the alternative cd might be more prudent. But heck, Debian is installing now via ethernet. Hope it turns out ok!

---

