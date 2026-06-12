---
title: "New Guy, Old Machine, What next?"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by Bugscuffle on 2012-10-18
I'm the newbie here. My new (to me) machine has finally arrived. Now what do I do with it to get it to speak Ubuntu? The machine is a Dell E310 with a Pentium 4 processor at 3.06 GHz. and 2 GB RAM. The disk has been wipred clean. There isn't so much as a bit on it. 
 
I have the following harware on the way for it. 
1. PCIe X1 graphics card. It has a chipset on the mother board with pitiful performance and the X1 slot is the only empty slot in the machine.
2. 250 GB SATA hard drive. It has an 80 GB SATA drivein it and I'll use that to load up XL and the new drive to load up Ubuntu.
3. A New 550 W. power supply. It has a 230 watt supply now, but I fear that the additional grahics card and H.D. will overwhelm the [SIZE=2]little[/SIZE] 230 W. supply.
4. A mounting caddy and data cable for the HD.
5. USB WiFi card and software.
 
I also have the following software coming.
1. Ubuntu 12.4 on a bootable disk.
2. HD partitioning and formating disk. (GParted - Partition Manager/editor)
 
Now we get into the whole universe of stuff I don't know about. 
1. I am assuming that a format is a format irrespective of whether it is on a Windows machine or a Linux machine. Is that correct or do I have to do things differently for each OS?
2. I don't have to worry about partitioning the HDs because they are seperate and each one will own it's own OS and they won't interfere with eaqch other. Is that correct, or do I need to do swomething to keep them apart?
3. I can arrange the boot sequence to boot from either HD and simply switch between them or do I have to shut down the machine or the OS and then go to the other OS?

---

### Post by Gnawnsense on 2012-10-18
> **Bugscuffle said:**
> I'm the newbie here. My new (to me) machine has finally arrived. Now what do I do with it to get it to speak Ubuntu? The machine is a Dell E310 with a Pentium 4 processor at 3.06 GHz. and 2 GB RAM. The disk has been wipred clean. There isn't so much as a bit on it. 
 
I have the following harware on the way for it. 
1. PCIe X1 graphics card. It has a chipset on the mother board with pitiful performance and the X1 slot is the only empty slot in the machine.
2. 250 GB SATA hard drive. It has an 80 GB SATA drivein it and I'll use that to load up XL and the new drive to load up Ubuntu.
3. A New 550 W. power supply. It has a 230 watt supply now, but I fear that the additional grahics card and H.D. will overwhelm the [SIZE=2]little[/SIZE] 230 W. supply.
4. A mounting caddy and data cable for the HD.
5. USB WiFi card and software.
 
I also have the following software coming.
1. Ubuntu 12.4 on a bootable disk.
2. HD partitioning and formating disk. (GParted - Partition Manager/editor)
 
Now we get into the whole universe of stuff I don't know about. 
1. I am assuming that a format is a format irrespective of whether it is on a Windows machine or a Linux machine. Is that correct or do I have to do things differently for each OS?
2. I don't have to worry about partitioning the HDs because they are seperate and each one will own it's own OS and they won't interfere with eaqch other. Is that correct, or do I need to do swomething to keep them apart?
3. I can arrange the boot sequence to boot from either HD and simply switch between them or do I have to shut down the machine or the OS and then go to the other OS?

Hello! Fellow Linux newbie here (:

1) I'm not sure exactly what you're referring to as a format. If you're referring to file types, most Windows file types aren't Linux friendly and will have to be opened via a utility like Wine. The actual file system on Linux is completely different from Windows, as well. The best thing I can tell you is don't go into this expecting a Windows experience. While some of the basic cosmetic functions are the same, trust me when I say that it's just a completely different world; from installing/uninstalling software and drivers, to the more advanced changes and tinks.

2) There's definitely going to be someone else who can give you good, accurate information. However, do know that the Ubuntu install CD has a built-in partitioning tool that is absolutely easy to use. If you're using two hard-drives, I wouldn't think you would need to partition it. You would only need to partition your system if you were running the two operating systems on one hard-drive in a dual boot scenario, from my understanding.

3) There's a few different ways to install Ubuntu. You can install it inside of Windows using Wubi. You might get some performance issues, and if Windows tanks, so does your Linux installation. Or you can install it along side windows. What happens here is when you boot your computer, you get a list of operating systems to choose from (Ubuntu, Ubuntu Safe Mode, Windows, etc). So if you were inside Ubuntu and needed to switch to Windows for an application, you would need to reboot your computer and boot into Windows. I have also found that most of the programs/games I personally use on Windows I can run on Linux via PlayOnLinux/Wine with performance good enough to where I don't need to actually log into Windows.

Hopefully I was of some assistance. I'm definitely not the most knowledgeable, but sometimes it's good to see insight from another new soul. So far I'm loving Ubuntu and am in the process of switching (95%) to Ubuntu for all my primary computing needs.

---

### Post by GaryTheCat on 2012-10-18
Here goes (I'm by no means an expert) - 

1. A format is a format:

I'm guessing you're thinking file types? i.e. MS Word Documents, JPEGs, MP3s etc? If so, these will open with Linux Applications with no problem

2. Partitioning can be done during installation - it might not necessarily follow that it's one OS per HDD.  What I did with my PC was to create a partition in windows for all of my files (my documents, pictures, music, videos, etc etc) and then mounted this partition in Ubuntu so you can access this stuff irrespective of your chosen OS.

3. You'll need to shut down, but with Ubuntu it only takes < 10 seconds (unlike windows - your frustration will come with waiting for windows start up).

I started out dual booting my PC with ubuntu 10.04 and haven't really looked back - I only used windows now to update my TomTom and use iTunes with my iPhone ... the rest I do on ubuntu.

---

### Post by Bugscuffle on 2012-10-18
Fellow Linux newbie - Thanks for the quick reply. As regards to "format" I was referring to the HD. Am I wrong in thinking that the HD must be formatted before you can load files onto it, and if the HDis wiped clean, won't I have to format it first? And as to the install, I want to put XL on the small drive and Ubuntu on the larger drive. How do I keep the machine from rerading from the wrong drive when operating, or does it keep track of that all by itself?
 
I can say one thing about all of this. I am having fun, fun, fun! I'm like a kid in a toy store. The thing that impresses me most is that it doesn't cost all that much. I have a new (to me anyway) machine a 19" monitor, a new keyboard and all of the stuff that I mentioned above and I have yet to spend $200.00 . Heck, my flower bed out front cost me more than that and this is a lot less work!
 
As far the difference between ubuntu and windows goes. I'm glad for it. Many, many years ago I worked in DOS. When Windows came out I, like just about everyone else, decried it as a copy of Macintosh, which it was and is as far as the operation goes. However every one of us quickly adopted Windows. I see the Ubuntu as being sort of a halfway house between Dos and Windows. There is still enough script writing in Ubuntu and it is still young enough to keep it interesting.

---

### Post by offgridguy on 2012-10-18
Hello Bugscuffle;  Just a couple of points, if you intend to do a dual boot, windows and ubuntu,
I would install windows first as windows is fussy about being installed alongside another OS.
When you install ubuntu it should recognize the drive you have allocated for it, just follow the prompts , it should go smoothly.  I really like the sound of the way you are setting this up, if you can arrange to boot from  either HD without shutting down, that is the way to go, it will
work the other way as well but I'm sure you will find it more convenient with the former.
You will have to plug in your wifi card after install, use the network icon at the top of your screen to bring the drop down menu, it's pretty self explanatory after that to set up your
network.   I did this myself with zero prior experience, so I'm betting you will have no problems, I think you are avoiding potential problems by using the bootable disk from 
ubuntu. I did the same and it installed without a hitch.  Good luck with the install, if you do
hit a glitch, there's a lot of help available in this forum.

---

### Post by Gnawnsense on 2012-10-18
> **Bugscuffle said:**
> Fellow Linux newbie - Thanks for the quick reply. As regards to "format" I was referring to the HD. Am I wrong in thinking that the HD must be formatted before you can load files onto it, and if the HDis wiped clean, won't I have to format it first? And as to the install, I want to put XL on the small drive and Ubuntu on the larger drive. How do I keep the machine from rerading from the wrong drive when operating, or does it keep track of that all by itself?

Ohhh! Okay! I get what you meant now. I believe the reply right above this one explained a bit more about the order in which to install your operating systems and whatnot.

As far as formatting your hard-drive goes, I don't want to give you any information that I'm not 100% confident in, and being new to Ubuntu, probably best if someone else answers. However, if you're worried about the filesystems I'd go read through [this link]("https://help.ubuntu.com/community/LinuxFilesystemsExplained").

---

### Post by Elfy on 2012-10-19
I was running a pentium4 with a couple of gigs of RAM up until a few weeks ago. Ubuntu 'worked', Xubuntu flew ;)


I would certainly point you at installing that rather than Ubuntu for the time being.

---

### Post by kurt18947 on 2012-10-19
> **Elfy said:**
> I was running a pentium4 with a couple of gigs of RAM up until a few weeks ago. Ubuntu 'worked', Xubuntu flew ;)


I would certainly point you at installing that rather than Ubuntu for the time being.

It seems like that machine should be adequate for basic usage, both with Ubuntu & XP.  And in addition to being 'lighter',  the alternative *butus might present less of a culture shock. Unity and Gnome 3 are a significant departure from traditional desktops.  They can all be test driven as a live install if you have a means to download .iso files and create live CD/DVD or live USB.  I assume a P4 machine would boot a live USB as a USB HDD but it'd be wise to make sure.  I have a P3 laptop which will only boot from a USB floppy, not a USB flash drive.  

Yet another alternative would be Mint.  It's a close relative of the *buntus with a reputation for most hardware working 'out of the box'.  It also has 2 alternative desktops, Cinnamon & Mate.  Each has its adherents.

---

### Post by offgridguy on 2012-10-19
Since you already have ubuntu 12.04 coming Bugscuffle, i would give it a try first, thats what i did
and I'm still using it.   In regard to your wifi card, does it have to be activated by your ISP?  Or are you in an area where you simply need something to access an open network?     The idea of the separate
drives intrigues me.  My experience with, dual boot was on the same drive in a separate partition ,
easy to install, lots of issues to uninstall, but hopefully you will you won't have to deal with that.

---

### Post by Mark Phelps on 2012-10-19
> **Bugscuffle said:**
> 5. USB WiFi card and software.

WiFi tends to be tricky to get working, sometimes -- which is why I would recommend creating an Ubuntu LiveCD and, once you have the PC completely assembled, booting from that and seeing how well it detects the hardware and installs the drivers -- especially, the WiFi drivers.

However, that said, you will have a better experience if you install using WIRED ethernet, not wireless.
 
> 
Now we get into the whole universe of stuff I don't know about. 
1. I am assuming that a format is a format irrespective of whether it is on a Windows machine or a Linux machine. Is that correct or do I have to do things differently for each OS?
2. I don't have to worry about partitioning the HDs because they are seperate and each one will own it's own OS and they won't interfere with eaqch other. Is that correct, or do I need to do swomething to keep them apart?

In my experience, the most trouble-free setup, when you have multiple physical drives, is to have MS Windows on one drive and Linux on the other drive.  This allows each drive to be bootable and usable on its own -- and prevent problems that come from overwriting MBRs and/or boot loaders.

So, have only ONE drive connected at a time, install one OS to that drive. Then, disconnect that drive, connect the other drive, and install the other OS to that drive.

As to partitioning, if you want to share data between the OSs, I recommend creating a large NTFS data partition on the big drive.  Both Windows and Ubuntu can use NTFS partitions.

> 3. I can arrange the boot sequence to boot from either HD and simply switch between them or do I have to shut down the machine or the OS and then go to the other OS?

Once you have both OSs installed, connect BOTH drives but boot from the Ubuntu drive. Open a terminal and enter "sudo update-grub".  That will regenerate the default GRUB configuration file and should add an entry for Windows.

When you reboot, you will then be presented with a menu, from which you can then select Windows or Ubuntu.

---

### Post by offgridguy on 2012-10-19
> 
Once you have both OSs installed, connect BOTH drives but boot from the Ubuntu drive. Open a terminal and enter "sudo update-grub".  That will regenerate the default GRUB configuration file and should add an entry for Windows.

When you reboot, you will then be presented with a menu, from which you can then select Windows or Ubuntu.

I just wanted to add, when the grub menu comes up at this point it doesn't stick around long and only gives you a few seconds before it boots ubuntu automatically. you may have to restart about 3 times if you wanted to read everything there. Typically though
you will have about 5 lines at the top of the screen, the top line being highlighted
or selected for ubuntu, your windows line will proably be the 4'th line down, you have to select it instead.  lots of time once you know what to look for.  :P

---

### Post by mastablasta on 2012-10-19
> **Mark Phelps said:**
>   Both Windows and Ubuntu can use NTFS partitions.
.
true for data but for the part where the OS is it is better to use Ext4 or one of other linux file systems. as installing Ubuntu on NTFS file system could cause some unwanted behaviour.

---

