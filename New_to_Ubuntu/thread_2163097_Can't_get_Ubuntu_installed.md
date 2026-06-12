---
title: "Can't get Ubuntu installed"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by SaraLe6 on 2013-07-17
I am brand new to a bunch of this stuff, though I've been assisted by three different people who took a class on Ubuntu, and they can't figure it out, either.

I purchased a Dell desktop that had been completely wiped and therefore had no OS.  I decided I would load Ubuntu, I've never used it but thought I'd give it a try.  The computer boots as it should, I can get into and change anything in BIOS, and can load the boot menu just fine.  The computer is around a 2003 (not positive), and doesn't have a DVD drive, just a CD drive, so it won't read an Ubuntu DVD.  The boot menu lists USB as an option but BIOS does not, and selecting it in the boot menu just prompts me to remove all disks and media.  So I downloaded and burned PLoP Boot Manager onto a CD and created a live USB, at which point it LOOKED like I might finally get to the Ubuntu installation screen... until I received a linux error message informing me that the BIOS is extremely damaged.  I used the ALT sequence to reset BIOS to factory settings but this does not help.  BIOS, however, is completely functional, so I'm not sure that it is truly damaged.  I wanted to run the Ultimate Boot CD but it is also too big for a CD and must be burned onto DVD or USB, and I couldn't for the life of me get it to extract properly for a live USB.  Am I doing something wrong, or is this computer just hopeless?  I didn't spend much, but it seems completely functional.

---

### Post by mastablasta on 2013-07-17
2003 - what is the CPU? it could be it doens't support PAE kernel. you can maybe try Lubuntu 12.04.

i doubt stock ubutnu form 2013 can run well on 10 year old maschine. it might. but you will have better results using Lubuntu or Xubuntu. but first we need to find what is causing the error.

another thing to do at boot is to use various boot options. especially acpi=off:  [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by sudodus on 2013-07-17
Welcome to the Ubuntu Forums :-)

If the computer is that old, I suggest that you try with a light-weight flavour of Ubuntu: ***Xubuntu***, or ultra-light-weight: ***Lubuntu***. You can download iso files for these flavours, that are small enough for your CD. I don't know but I think that a current version of standard Ubuntu with Unity will need more horsepower and RAM than you have in that computer from 2003.

Check the CPU and RAM in your BIOS menus, and post the result in a reply! Since it is a desktop, it might have a Pentium 4 CPU, which should be OK. If you have 512 MB RAM or more, it is OK, but you need 1 GB RAM to browse the internet in a smooth way. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware[/URL]

Get the latest LTS release: 12.04, Precise Pangolin, 32-bit from

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

or download Lubuntu 13.04, 32-bit

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Use md5sum to check that the download was successful. Compare with the posted md5sums at

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by MirrorUniverse on 2013-07-17
When I installed Xubuntu 12.04, the iso file required 707 MB. CDs have 700 MB capacity, so I had to burn it to a DVD to install.  Guess Lubuntu or other ultra lightweight versions of Linux are the way to go.

---

### Post by 3rdalbum on 2013-07-17
What is the exact error message about your BIOS? I don't think it could be "your BIOS is extremely damaged" but it may give us a clue about what boot parameter to add so your system will start up.

---

### Post by mastablasta on 2013-07-18
xubutnu image wanted 707 MB where? on CD? note CD uses different file system than hard disk. so if it says 700 MB or a bit more on hard disk it is actually about 650-680 MB on CD.furthermore you can "overburn" the CD. this can add a bit of extra data on some place on it. ofcourse if burning porgramme and hardware supports it.

---

### Post by alan9800 on 2013-07-18
> **mastablasta said:**
> xubutnu image wanted 707 MB where? on CD? note CD uses different file system than hard disk. so if it says 700 MB or a bit more on hard disk it is actually about 650-680 MB on CD.furthermore you can "overburn" the CD. this can add a bit of extra data on some place on it. ofcourse if burning porgramme and hardware supports it.Xubuntu 12.04.2 64bit has an ISO image of 707Mb, while the 32bit release has an ISO image of 689Mb: see [here](http://cdimage.ubuntu.com/xubuntu/releases/12.04.2/release/).

---

### Post by MirrorUniverse on 2013-07-18
> xubutnu image wanted 707 MB where? on CD? note CD uses different file  system than hard disk. so if it says 700 MB or a bit more on hard disk  it is actually about 650-680 MB on CD.furthermore you can "overburn" the  CD. this can add a bit of extra data on some place on it. ofcourse if  burning porgramme and hardware supports it.                 
> Xubuntu 12.04.2 64bit has an ISO image of 707Mb, while the 32bit release has an ISO image of 689Mb: see [here]("http://cdimage.ubuntu.com/xubuntu/releases/12.04.2/release/").                 
Wasn't thinking about the fact that the 32 bit version would be smaller and could fit on a CD, sorry about that.  I'm pretty sure I did try to burn it anyway on a CD, and got a disk full error.  I didn't know about overburning; what I used likely does not support it.

---

### Post by mastablasta on 2013-07-18
there are also 800MB CD, but sort of rare to find these days.... :-)

---

### Post by alan9800 on 2013-07-18
if you wish to install Xubuntu 12.04.2 but you only have a CD, you might do these steps:
[LIST]
[*]download Xubuntu 12.04.1 from [here]("http://old-releases.ubuntu.com/releases/xubuntu/releases/12.04.1/release/"); 
[*]burn that ISO on a CD; 
[*]install Xubuntu on your PC and download the updates; 
[*]finally, copy and paste in a Terminal window the following command```
sudo apt-get install --install-recommends linux-generic-lts-quantal xserver-xorg-lts-quantal libgl1-mesa-glx-lts-quantal
```as explained in [this wiki page]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"). 
[/LIST]

---

