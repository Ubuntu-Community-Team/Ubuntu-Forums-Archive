---
title: "Ubuntu 9.10 won't boot. Please HELP"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by 3D Man on 2012-04-24
I Have an Ubuntu 9.10. It was working fine until when i tried to update  it, it warned me it was going to take a long time but my grandma saw it  running so she took maters into her own hands and shut it off. Now when i  turn it on i get like 8 different types of operating systems i can  choose from:
Ubuntu 9.10, kernel 2.6.31-22-generic
Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
Ubuntu 9.10, kernel 2.6.28-19-generic
Ubuntu 9.10, kernel 2.6.28-19-generic (recovery mode)
Ubuntu 9.10, kernel 2.6.28-13-generic
Ubuntu 9.10, kernel 2.6.28-13-generic (recovery mode)
Ubuntu 9.10, kernel 2.6.28-11-generic
Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
but none of them work (i can't get to my load up screen or  desktop). Please How can  i fix this problem and get back to my desktop?
Any information would be greatly appreciated :)

---

### Post by codingman on 2012-04-24
Can you give some more info? Like what computer your using and stuff. But most likely it's just because you interrupted the important part of the os updating.

---

### Post by 3D Man on 2012-04-24
It's a compaq presario
designed for Microsoft Windows 2000 Professional
looks like this:
[http://www.google.com/imgres?start=39&num=10&hl=en&gbv=2&biw=1280&bih=697&addh=36&tbm=isch&tbnid=Bzp2sE23c9xO4M:&imgrefurl=http://www.shopitsystems.com/store/index.php%3Fmain_page%3Dproduct_info%26products_id%3D308&docid=_snS4ruJbVr7-M&imgurl=http://www.shopitsystems.com/store/images/CompaqPresario5000lg.jpg&w=193&h=261&ei=_RWXT6SiJKXi2AWqo5jcDQ&zoom=1&iact=hc&vpx=198&vpy=357&dur=3088&hovh=208&hovw=154&tx=131&ty=124&sig=110333960755615918084&page=3&tbnh=155&tbnw=116&ndsp=20&ved=1t:429,r:0,s:39,i:52]("http://www.google.com/imgres?start=39&num=10&hl=en&gbv=2&biw=1280&bih=697&addh=36&tbm=isch&tbnid=Bzp2sE23c9xO4M:&imgrefurl=http://www.shopitsystems.com/store/index.php%3Fmain_page%3Dproduct_info%26products_id%3D308&docid=_snS4ruJbVr7-M&imgurl=http://www.shopitsystems.com/store/images/CompaqPresario5000lg.jpg&w=193&h=261&ei=_RWXT6SiJKXi2AWqo5jcDQ&zoom=1&iact=hc&vpx=198&vpy=357&dur=3088&hovh=208&hovw=154&tx=131&ty=124&sig=110333960755615918084&page=3&tbnh=155&tbnw=116&ndsp=20&ved=1t:429,r:0,s:39,i:52")

**SPECIFICATIONS:**
**Computer:**
Intel Celeron 667MHz Processor
Compaq with Intel D810E Chipset Motherboard
512MB SDRAM PC133 133MHz Memory Modules
300Watt ATX Power Supply
Quantum Fireball 20GB Hard Drive IDE 7200RPM
Compaq CDRW Optical Drive
Intel 82810E Graphics Controller
ESS Allegro Audio Controller
SMZ 10/100 Fast Ethernet Internal NIC Controller
PC TEL Platium V.90 Modem
Mitsumi 1.44MB Floppy Drive
1-Parallel Port
1-Serial Port
4-PCI Ports
4-USB Ports Back 2-USB Ports Front
[IMG]http://www.google.com/imgres?start=39&num=10&hl=en&gbv=2&biw=1280&bih=697&addh=36&tbm=isch&tbnid=Bzp2sE23c9xO4M:&imgrefurl=http://www.shopitsystems.com/store/index.php%3Fmain_page%3Dproduct_info%26products_id%3D308&docid=_snS4ruJbVr7-M&imgurl=http://www.shopitsystems.com/store/images/CompaqPresario5000lg.jpg&w=193&h=261&ei=_RWXT6SiJKXi2AWqo5jcDQ&zoom=1&iact=hc&vpx=198&vpy=357&dur=3088&hovh=208&hovw=154&tx=131&ty=124&sig=110333960755615918084&page=3&tbnh=155&tbnw=116&ndsp=20&ved=1t:429,r:0,s:39,i:52[/IMG]

---

### Post by strask on 2012-04-24
Ok, I'm going to assume that it was in the process of updating to the 2.6.31-22 kernel when the problem occurred, so maybe that one isn't working properly. Try booting the Ubuntu 9.10, kernel 2.6.28-19-generic (recovery mode) option and tell us about the errors when it stops booting.

---

### Post by 3D Man on 2012-04-24
i don't know if this is considered an error but a whole bunch of text appeared, then it stopped for a while, then more text appeared, and then the text cleared to a new page that says:

init: plymouth main process (325) killed by SEGV signal

and then some more text appeared after like 7 minutes and now i'm in recovery mode.

---

### Post by lisati on 2012-04-24
In the light of the first post, I'm guessing that the "10.9" in the title is a typo, and have renamed the thread. :D

---

### Post by codingman on 2012-04-24
Not sure whats wrong but there are some bugs filed in launchpad about it.

---

### Post by strask on 2012-04-24
> **3D Man said:**
> i don't know if this is considered an error but a whole bunch of text appeared, then it stopped for a while, then more text appeared, and then the text cleared to a new page that says:

init: plymouth main process (325) killed by SEGV signal

and then some more text appeared after like 7 minutes and now i'm in recovery mode.

And was the system completely unresponsive at that point? That last message is the boot splash controller program (the one that normally displays the ubuntu logo and little progress indicator) having a segmentation fault. Could be because it's expecting the later kernel version, maybe... so now try the same thing but with the most recent kernel version (Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)) -- boot and tell us about any errors you see once it stops booting.

---

### Post by LinuxFan999 on 2012-04-24
Ubuntu 9.10 is no longer supported. I would recommend installing Lubuntu 12.04, which will be released on the 26th of April.

---

### Post by 3D Man on 2012-04-24
ok i'm in recovery mode without any errors and if there where any errors the disappeared quickly.

---

### Post by strask on 2012-04-24
> **LinuxFan999 said:**
> Ubuntu 9.10 is no longer supported. I would recommend installing Lubuntu 12.04, which will be released on the 26th of April.
That is a sound recommendation, but we should help 3D Man get his system back first, I think. ;)

---

### Post by strask on 2012-04-24
> **3D Man said:**
> ok i'm in recovery mode without any errors and if there where any errors the disappeared quickly.

Excellent! I would suggest re-starting your updates/upgrades from there, and then when you reboot I would expect non-recovery mode to work again. Hopefully.

And as mentioned above, do plan on upgrading to a supported release, preferably 12.04 when it comes out in a couple days.

---

### Post by 3D Man on 2012-04-24
so now that I'm in recovery mode what do i press
there is six options:

resume normal boot

clean try to make free space

dpkg repair broken packages

grub update grub bootloader

netroot drop to root shell prompt with networking

root drop to root shell prompt

---

### Post by strask on 2012-04-24
Well, that kind of depends on what exactly you were doing right before the crash. You said you tried to update it, but you didn't say what part of the system you were updating or how. We want to resume this process so that the updates aren't half-way done.

Presumably this would mean use the root option to get a shell and then type some apt-get commands, but I can't say for certain without knowing more about the circumstances of your crash.

---

### Post by 3D Man on 2012-04-24
i really don't remember it was like a year ago and i gave up on trying to fix it and i just came back to it all i know is that it was updating and my grandma shut everything off, and i could never access my desktop or any load up screen after that.

---

### Post by strask on 2012-04-24
Ok then, new plan.

Do you have a thumb drive or something you can store your data on? I would do the following:

1) Wait a couple days. That's the painful part.
2) When 12.04 is released as a final (non-beta) release, download the desktop install CD image and burn a CD.
3) Boot from the 12.04 cd, go to the "try ubuntu" (not install) option.
4) You get a nice shiny desktop interface. Open a terminal window, and mount your old filesystems from your hard disk under /mnt or whatever.
5) Insert your USB thumb drive, it should automatically mount.
6) Copy any files you care about from your old home directory to your thumb drive.
7) Eject the thumb drive.
8) Install 12.04, formatting and replacing your old linux.
9) When the new system is installed and working, replace the files from your thumbdrive into your home directory.

---

### Post by 3D Man on 2012-04-24
Thank you i appreciate and I hope you will be available in a couple of days when 12.04 comes out than maybe once and for all i can go to my desktop, Thank you so much.

---

### Post by strask on 2012-04-24
Heh, yeah I will likely be around but so will about a thousand other people on these forums so I doubt you will have trouble finding help. :)

---

