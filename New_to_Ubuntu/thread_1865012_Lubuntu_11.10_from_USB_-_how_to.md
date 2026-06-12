---
title: "Lubuntu 11.10 from USB - how to?"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by I2k4 on 2011-10-19
I've been experimenting with Ubuntu and most recently Lubuntu for nearly a year.  I've just moved from Persistent Live USB Lubuntu 10.10 to 11.10 on my higher spec Dell laptop.

But I've found the Persistent Live installs of Lubuntu 10.10 to be  unstable, they start out great but over a couple of months seem to lose functionality, suddenly demanding passwords, or Synaptic PM "disappears" and won't open, or they lose access to the HDD on the computer.  

At this point, I'm still not interested in putting Lubuntu on my hard drives, but would be very interested in "for dummies" instructions to do a **regular installation on a USB thumb drive** instead of Persistent Live USB.  I've read posts that indicate this is doable, but clicking that "install" icon on the desktop I haven't figured out how to begin an install to anything other than the HDD.  Any guidance to a good "how to" or step by step for installing Lubuntu on USB would be appreciated.  Thanks.

---

### Post by wolfen69 on 2011-10-19
```
dd if=lubuntu.iso of=/dev/sd[x]
```
Be very careful with this command, and make sure /dev/sd[x] is the correct drive. And make sure the name of the iso matches correctly. Just put the lubuntu iso in your home folder before running command. This will give you a "live cd" on your usb drive.

---

### Post by kemtnbkr on 2011-10-19
If I understand what you're wanting to do correctly, it seems to me you'll either need 2 USB drives, or a USB drive and a Live CD.  (Your 'install' drive should be ~10G or more, 5G absolute minimum IMO).  Boot into the live USB/ liveCD session, and start the install tool.  I've never tried this, but there should be a way to install to your USB drive as a 'hard drive'; let it autopartition the drive, and MAKE SURE to select your USB drive as the drive to install GRUB on.  (I made the mistake of selecting my external HD the first time I installed).  

I think this will give you what you're looking for; you'll just have to either modify your BIOS startup device order, or select the USB from the startup device menu (as I'm sure you know having run it this way before).  

Be warned; I am mostly a n00b and have never tried this method myself; again, MAKE SURE you are installing to the correct USB drive; if it doesn't work you can try something else.  Just don't break anything else trying it.

---

### Post by tartalo on 2011-10-19
I tried a regular installation in a pendrive but it was painfully slow, the transfer rate of a pendrive is not comparable to a regular hardrive.

Live CDs are faster because they are loaded to memory. I can't find the link but someone in ubuntuforum wrote a hack that converted the regular installation to a "live" image (sorry for the inexact terminology), but he abandoned the project after buying an external SSD.

If a personalized live image can help there are some tools:

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)
[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

Debian Live project has some nice tools too, see chapter 7 of the manual:
[http://live.debian.net/manual/en/html/live-manual.html](http://live.debian.net/manual/en/html/live-manual.html)

---

### Post by I2k4 on 2011-10-20
Thanks for responses.  I blundered into Lubuntu's wizard during the live USB boot process, instead of using the desktop icon after booting to run live - it provides a choice of installation to another USB thumb drive instead of the HDD.  No idea how well it will work out, but will deal with any issues elsewhere, and consider this "solved".

---

### Post by kemtnbkr on 2011-10-20
Hey I2k4, if you're still here, I just found a thread that is a tutorial for what I was describing before.  More in depth than mine of course: [http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

### Post by amjjawad on 2011-10-20
This is how to install Lubuntu in general: [https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu)

Follow the same but make sure to choose the correct drive (USB-Drive instead of your internal HDD) from the list which will show up after you choose "Something else":

[IMG]http://i55.tinypic.com/6jde0y.jpg[/IMG]

[B]Please Note:
[/B]1) Your USB-Drive will NOT be /dev/sda

2) Please don't install GRUB2 (Lubuntu Boot Loader) to sda but instead install it to the MBR of your USB-Drive (say for example /sdb). That will leave your internal HDD untouched. 

I'll include another link. I know, I need to update my guide on the wiki and maybe include howto install to USB section but I'm too busy these days with some projects.

This will help you to understand the concept of installing to USB Drives: [http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

### Post by amjjawad on 2011-10-20
> **kemtnbkr said:**
> Hey I2k4, if you're still here, I just found a thread that is a tutorial for what I was describing before.  More in depth than mine of course: [http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

I see you beat me to it :P

---

### Post by I2k4 on 2011-10-21
Thanks for the further comments.  I succeeded in creating a USB install using Lubuntu's wizard, but didn't realize that it would create a GRUB booting menu on my HDD. I still don't quite understand how to avoid that, though I see some of you know about it and tried to help.  

I googled around to see about getting rid of GRUB, but only found directions for people who have Windows CD/ROMs while my netbook has one of those recovery partitions and no disk.

As GRUB is there every time I boot, I dropped the USB install idea and created a small partition on my netbook HDD for Lubuntu so now am a proud, if accidental, Lubuntu/W7 dual-booter.  If dual boot proves out over time (it's a new thing for me) I might stick with it and even install on my main PC.

---

### Post by amjjawad on 2011-10-21
> **I2k4 said:**
> Thanks for the further comments.  I succeeded in creating a USB install using Lubuntu's wizard, but didn't realize that it would create a GRUB booting menu on my HDD. I still don't quite understand how to avoid that, though I see some of you know about it and tried to help.  

One way to tell whether GRUB was installed on your HDD or your USB's MBR.
Just unplug your USB, reboot and if GRUB will show up, it means it's installed on your HDD.
I don't recommend that way. In my guide, I have explained how to avoid that and what's the alternative approach :)

Read it and if you have any question, I'm here :)

> I googled around to see about getting rid of GRUB, but only found directions for people who have Windows CD/ROMs while my netbook has one of those recovery partitions and no disk.

Check my previous paragraph.
Yes, there is a way to get rid of it in case it's causing problems but if it's working just fine, why not keep it?
Don't worry, myself and some good friends are good with GRUB so we'll help :)

> If dual boot proves out over time (it's a new thing for me) I might stick with it and even install on my main PC.
I have another guide for Dual-Booting. Whatever you need in Dual-Booting, let me know because that's my area too :)

---

### Post by I2k4 on 2011-10-21
Thanks, I'll certainly be looking at your guides.  Luckily I've experimented on Live USB with several Ubuntu variants nearly a year, and have pretty much settled on Lubuntu 10.10 for the netbook.

I have to say, if I was totally new, I'd be angry that the installation to a USB thumb drive actually results in GRUB installed on my hard drive, with no easy way to get rid of it.  As it is, I'm happy enough to continue working with Lubuntu on dual boot, since I like it. 

I'm not an operating system enthusiast who is willing to reinstall every few weeks - I ran XP on machines for years on end without reinstalling or any serious problems - all I want is reliability, speed and a good software selection to do the things I do.  I'm hoping Lubuntu will hold up and that this HDD install will not create nuisance challenges.

---

### Post by amjjawad on 2011-10-21
> **I2k4 said:**
> Thanks, I'll certainly be looking at your guides.  Luckily I've experimented on Live USB with several Ubuntu variants nearly a year, and have pretty much settled on Lubuntu 10.10 for the netbook.
I do my tests on two PCs but before a year, I was testing on External HDD.

> I have to say, if I was totally new, I'd be angry that the installation to a USB thumb drive actually results in GRUB installed on my hard drive, with no easy way to get rid of it.  

I see your point. Problem is, don't get me wrong though please, many users don't pay much attention to this step which is the most critical step: [B]Device for Boot Loader Installation
[/B]
[IMG]http://i52.tinypic.com/6gfmds.jpg[/IMG]

If you continue with the above option, GRUB will be installed to sda (MBR) NO MATTER where you choose to install Lubuntu.



[IMG]http://i56.tinypic.com/28j88qb.jpg[/IMG]

While if you carry on with the above option selected which is "Installing GRUB to sda6", then GRUB will be installed on the SAME Partition where your Lubuntu will be.
In this case, you must have main OS which has GRUB (if Linux) which will be controlling the whole booting process (Dual or Multi-Booting).

I have set my 9 Multi-Booting System according to this way and it's very successful, just need some attention.


> I'm not an operating system enthusiast who is willing to reinstall every few weeks - I ran XP on machines for years on end without reinstalling or any serious problems - all I want is reliability, speed and a good software selection to do the things I do.
With Linux, as long as you know what you are doing and how to do things, you'll never have to re-install unless there is something huge happened.

> I'm hoping Lubuntu will hold up and that this HDD install will not create nuisance challenges.
Even if there will be, everyone here including myself will jump to help so relax ;)

---

