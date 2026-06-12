---
title: "Problems after installation"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by jaklumen on 2008-05-10
Disclaimer: I did a LOT of research and spent hours just getting 8.04 downloaded and installed.  I have already tried searching for solutions with no luck.

On to the specifics:

I installed Hardy from the alternate CD version, using the text installer.  I had previously tried installing from a Gutsy LiveCD, and the live distro would not work.

First attempt was to install it to the drive with the Windows (XP SP3) partition.  This drive is a SATA type drive.  Nothing.  The Windows boot loader did not detect it.  It is labeled "F:" because I screwed up some partitioning on my last install of Windows.

On the second attempt, I installed it to the IDE (C:) drive.  As XP was not on this drive specifically, it was not detected by the installer -or- the GRUB boot loader.  I have about seven options for boot load-- the first three or so work, while the others (probably for the partition on the F: drive) do not.

It was actually more than two attempts, but suffice it to say, I got things working well enough that I am writing this from Hardy.

I tried migrating my profiles from Firefox and Thunderbird (couldn't get Sunbird configured yet) from XP but to no avail.  I finally found out about the migration tool in the installer, but I had NO such options during the installation.  I was quite pleased that setting up Gmail in Thunderbird for Ubuntu was such a snap compared to things in XP, but I am not looking forward to setting up the e-mail account with my ISP (as I still use it).  It also seems a hassle to rebuild profiles in all three Mozilla apps.

As I implied earlier, I cannot boot into Windows anymore.  The BIOS for my machine does not distinguish between my two drives on boot time, so I can't switch back and forth in the settings.  Granted, it is very unhappy with my SATA drive (F:) and is not currently detecting it-- SpinRite was also unhappy-- but that's another story.

I did make backups to an external drive-- a Western Digital 320GB MyBook.  I could read from it fine until a few reboots later (after installing nVidia drivers, attempts to access Windows, etc.) and then Hardy said it failed to mount the drive.  I'm not sure what's going on-- my only guess is the Windows executables on it, or something like that.  I would be willing to let go of XP, but I need the data on that external drive.  I kept the drive format to FAT32, so I'm positively stumped.

For some reason, I was able to mount that F: drive within Ubuntu.

I apologize for the lack of technical information-- I'm still learning how Ubuntu does things.  I'm a hobbyist hack and not a professional, and my system is a veritable Frankenstein-- it was built with parts I could scrounge, or ones I could afford to buy new a piece at a time.  In short, I'm sure I don't have an ideal hardware configuration, but I've managed to keep it together myself.

I'll provide as many details as I can.  Reinstallation of XP and Ubuntu isn't terribly feasible right now-- I've misplaced my installation disk and key.  I do have Windows 98 with key right at hand-- one of those little scrounged gifts doing tech support for my folks.  Hmmmm... no, I'm having a hard time picturing 98 working on that SATA drive.

Ubuntu is great-- glad to be here-- I'm just hoping I can recover some of the old settings in XP.  It was a good thing I made the switch to open source software early in the game!

---

### Post by spiderbatdad on 2008-05-10
perhaps this will help in mounting your fat partition.[http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

---

### Post by jaklumen on 2008-05-18
*facepalms* Ooops... I realized that I installed a Ubuntu partition to the external hard drive, not the SATA.

The latter somehow mounted fine later-- I'm not sure what I did to enable it.  No problems now :S

---

