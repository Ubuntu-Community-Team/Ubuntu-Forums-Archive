---
title: "Why can't I get in?"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by nyghthawk on 2012-07-24
I have a 500GB drive partitioned in half. One is running WinXP/SP3 and the other is running Ubuntu.
To make a long story short, both household computers decided to take a trip on us. The only way to get dh's computer working again was to give him my video card. After that, I couldn't get to Ubuntu. It wouldn't even give me the options screen during startup to choose which OS I wanted to log into.
Now I'm running a new (to me) comp with my own hard drive. It's older, but well within the specifications of what Ubuntu needs to work. The only thing that seems to be causing issues is a lack of a video card because I'm having the same trouble. It won't even show the start up screen that gives me the choices and acts like the only OS on this drive is XP.
 
Any ideas?

This is an Acer ACPI Multiprocessor PC with an Intel Pentium 4 CPU 2.93GHz
Display adapter is Intel Corporation 915G/915GV/910GL Embedded Graphics Chipset
It's running 1.99GB of RAM. 
 
If the memory on this one is an issue, can someone explain why I was having an identical problem on my old system with 4GB of RAM?
 
Thanks for any help!
Mona

---

### Post by Ubun2to on 2012-07-24
I'm not sure what model motherboard you have, but you should be able to adjust the GPU used in the BIOS. Make sure it is set to Integrated graphics. I can't really assist you in where the graphics options are in your BIOS-every motherboard is different in the layout.

---

### Post by nyghthawk on 2012-07-24
Thanks!
Right now I'm cleaning the hard drive that came with this system and then I'll see what I can do about getting into the BIOS. I'm fairly familiar with how comps work, but this issue has confused me since it started. I tried everything I could think of.

---

### Post by nyghthawk on 2012-07-24
Ok, I checked the BIOS settings and it's all set correctly.
What else could it be?

---

### Post by yuvraj23 on 2012-07-24
Maybe your pc isn't capable of supporting Unity.. Use classic look or try some other distro..

I too have an Integrated Graphics and I can easily adjust it thru BIOS. Try it

---

### Post by deadflowr on 2012-07-24
First, what was the graphics card you removed?

Second, let's try to see if we can access the boot menu using the shift key.
After the initial bios screen, repeatedly press the shift key, this will hopefully bring up the boot menu.

If that doesn't work, try this guide:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Hopefully, when you can get pass the boot problem we can fix it forever.

Unity will run just fine on those specs.

---

### Post by anewguy on 2012-07-24
Remember the 915 is also problematic with linux.  There is an option - not exactly sure of the name anymore, but something like i915.modeset=0 or i915.modeset=1 that in the past has helped get around some of these booting problems.  Indeed the first step is to be able to get to the boot menu as deadflowr suggested above.  Once to the boot menu, you can edit the boot line and add the i915 option - try the =0 first - if that doesn't work then try the =1.

---

### Post by nyghthawk on 2012-07-25
> **deadflowr said:**
> First, what was the graphics card you removed?
 
\
 
It was a GForce card. Unfortunately, I can't get at it right now to give you better information than that.
 
I recalled last night that I had reinstalled Windows. From what I've gathered in my information hunting, that messed up GRUB.

I'm currently using Super Grub Disk. No luck. It can find the partition. It can find that there is an Ubuntu installation.

BUT...it can't fix the MBR and now that I've tried all the possible options I can find, I'm at the point where nothing on the SGD is of any use at all. Even the options to automatically load Ubuntu aren't working.

I am at a complete standstill. This "new" system isn't recognizing the fact that there's a cd drive in it. It recognizes the floppy, though. It's also old enough that it won't boot from USB.

---

### Post by nyghthawk on 2012-07-25
I now have Ubuntu installed on a separate hard drive. Rather than try to recover the old installation, I'm just transferring files.
Only problem is finding my Firefox bookmarks. :-) But I'm getting there.
Thank you for the help, everyone!

---

### Post by Bufeu on 2012-07-25
> **nyghthawk said:**
> I now have Ubuntu installed on a separate hard drive. Rather than try to recover the old installation, I'm just transferring files.
Only problem is finding my Firefox bookmarks. :-) But I'm getting there.
Thank you for the help, everyone!
Bookmarks are as default saved in:```
/home/username/.mozilla/firefox/*.default/bookmarkbackups
```All Firefox-profiles will you find in:```
/home/username/.mozilla/firefox
```

---

### Post by Ubun2to on 2012-07-25
> **nyghthawk said:**
> \
 
It was a GForce card. Unfortunately, I can't get at it right now to give you better information than that.
 
I recalled last night that I had reinstalled Windows. From what I've gathered in my information hunting, that messed up GRUB.

I'm currently using Super Grub Disk. No luck. It can find the partition. It can find that there is an Ubuntu installation.

BUT...it can't fix the MBR and now that I've tried all the possible options I can find, I'm at the point where nothing on the SGD is of any use at all. Even the options to automatically load Ubuntu aren't working.

I am at a complete standstill. This "new" system isn't recognizing the fact that there's a cd drive in it. It recognizes the floppy, though. It's also old enough that it won't boot from USB.

Well, if we are forced to use floppys, that is a bummer. 3.5", I take it.
Go into the BIOS and see if you can put the CD drive in the boot order. If you can, our options are much greater. If you can, try booting into a GParted live disk. There are some tools included that could help you.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

