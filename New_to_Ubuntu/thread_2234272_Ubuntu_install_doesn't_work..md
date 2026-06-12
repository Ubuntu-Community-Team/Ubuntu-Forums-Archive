---
title: "Ubuntu install doesn't work."
date: 2014-07-13
forum: New to Ubuntu
---

### Post by David_Navratil on 2014-07-13
I have a 4 yr old HP desktop, 3gb ram and 500 gb HD.  I was using windows 7 and worked perfectly.  I wanted to try Elementary OS and tried to dual boot with something call "Grub"
I missed up the partition installation and lost Windows!  That's ok because I wanted to turn the desktop into a Linux machine.  Elementrary os worked but everyone says to use Ubuntu.  I downloaded the iso file this morning and put it on a USB and also a DVD.  I set it up to install Ubunto only on the C Drive.  I should not have anything on it anymore after the installation of Ubuntu.  However I'mhaving a nightmare booting into Ubuntu.  Sometimes I get a blue screen only, other times the icons on the left of the screen don't work when I click on them.  I have not use Ubuntu yet since nothing seems to work.

I think some of that "Grub" boot mgr is left over fromElementary OS.  How do I do a complete reformat of my C drive so I can try again to install Ubuntu.  Everyone says this is a great program but nothing works for me- I'm a newbie, any help will be appreciated- David

---

### Post by mooreted on 2014-07-13
The Ubuntu installer should have formatted the hard drive if you chose to install Ubuntu only. 

What video card does your computer have?

---

### Post by cmcanulty on 2014-07-13
you say you installed it to the C: drive. I don't think that will work you need to format a partition preferably to ext4. I would do 3 partitions 1)for / for all programs and system files 10-20GB, 2) rest except for swap for /home, 3) for swap at least size of ram. Then you can reinstall without losing all your configs and docs as they are in the separate /home partition

---

### Post by David_Navratil on 2014-07-13
I thought that the installation of Ubuntu did all the partitions automatically!  When I originally installed Elementary OS I think I messed up the installation with the part about partitions!!
Tks,David

---

### Post by buzzingrobot on 2014-07-13
When you install Ubuntu, the installer should present you with a few options about how to use the drive (I'm guessing there's a single drive in the HP).  One of those is to replace the OS it finds there, ElementaryOS in your case.

Something about ElementaryOS and Ubuntu:  Ubuntu cranks out new releases every six months that are supported for 9 months. (That means updates and bug and security fixes for 9 months.)  Every two years, Ubuntu makes available a Long-Term-Support release, which is supported for 5 years.  ElementaryOS is based on Ubuntu 12.04, a Long Term Support release from about two years ago.  The current Long Term Support release is 14.04, which is a few months old.

In addition to its own software, Elementary gives you access to the same software available for Ubuntu 12.04, from the same servers.  The fundamental differences between Elementary and Ubuntu are essentially style and design. 

Elementary is working on its next release, which will be based on Ubuntu 14.04.  They haven't, and won't, announce a release date, but a beta can't be too distant. 

So... if something keeps Ubuntu from installing, Elementary is a very close relative.

The Ubuntu installer will offer an option to run in Live Mode (off the DVD or USB stick).  That's a good way to check for compatibility issues with hardware, expecially the video card. 

As a point of reference, Unix/Linux/OS X don't use terminology like "C: Drive".  That's Windows-only, from its DOS heritage.

---

### Post by craig10x on 2014-07-13
I would re-install using the dvd iso disc and select the automatic option of having 14.04 completely replace everything you have on there...it will wipe the drive totally clean, set up the proper partitions and the grub as well...since you are going to run ubuntu by itself on the computer, that is the best way to go...Back up any important data you want to save to an external drive (like a usb flash drive for example) because the entire drive will get wiped...but this way, everything will get properly set up for you...ubuntu will do all the work!

---

### Post by cmcanulty on 2014-07-13
you can do it automatically I was just recommending a separate home to make reinstalls or disaster recovery easier. If you want a detailed answer send me a private message

---

### Post by craig10x on 2014-07-13
If he does manual partitioning, things could get messed up, that is why i suggested he just let ubuntu set everything up automatically...this will result in a much better experience for a linux newbie... ;)

---

### Post by David_Navratil on 2014-07-14
Nothing works!!  When I was having trouble originally and tried to set up a dual boot, when I booted up I would get two words "PC" one under the other in the upper left corner of screen.  Now that Elementary OS and Windows are off of my drive and I try to boot into Ubuntu I still see the 2 words left over from last week.  I know it has something to do with that "Grub" from last week.   Can anyone try to tell me how I can go into my system and reformat and remove all petitions from my hard drive on the pc.  I only have 1 drive.  Tks so much and many tks to all who have tried to help - David

---

### Post by mastablasta on 2014-07-14
boot into live CD (this should have nothing to do with grub) then you run gparted and delete, move or whatever you want with partitions.

grub is boot manager that Ubuntu uses as well. so one way or the other it will be there (unless you plan to manually replace it). an issue could have appeared if elementary OS used older version and that one stayed there for some reason. 

if you can it would also be better to trigger install from live boot. - that is boot from CD, select try it and then once loaded click on install icon.

---

### Post by buzzingrobot on 2014-07-14
> **David_Navratil said:**
> ...I try to boot into Ubuntu I still see the 2 words left over from last week...

Do you see the "PC" when you boot an install image? If you are booting a Ubuntu install ISO, and that install image is error-free, and if you are telling the BIOS to boot from the DVD/USB stick you're using, then the drive in the machine won't be accessed until you actually begin the install process.

All operating systems have a bootloader. (It's usually Grub in Linux.) When you start up a machine, the BIOS passes control to the bootloader, which then starts the sequence of events that load the OS. 

If a bootloader is damaged, improperly installed, not the right one for the OS, etc., then the boot very likely will fail and you could easily see some random info on screen. But, again, the bootloader on the hard drive shouldn't come into play when you boot an install image.

---

### Post by craig10x on 2014-07-14
Agree with mastablasta...Your best bet is to set your bios to boot off cd/dvd then insert the live iso....the computer will then boot off the iso disc instead of your drive, let it go to live session and once it is loaded in hit the "install ubuntu 14.04" icon you will see on the desktop...click that on and in the installer select to have ubuntu 14.04 REPLACE everything you got on your drive...

It will then wipe the drive clean, set up partitions, install ubuntu and properly set up the grub bootloader....and you should be all set ;)

---

