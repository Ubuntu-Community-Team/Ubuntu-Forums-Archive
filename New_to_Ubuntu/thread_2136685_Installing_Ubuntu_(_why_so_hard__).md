---
title: "Installing Ubuntu ( why so hard ? )"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by old4570 on 2013-04-18
I run Win 7 , I dont want Ubuntu on the same drive (s) I use for windows ..

I just cant install Ubuntu where I want it , it either tries to install with windows , or use all my partitions ...

Years ago I could install linux where I wanted = Chose a drive and install it there ..

It has become so much harder these days , the installers are so ?/  Nasty to use ...  I just cant pick a Drive/Partition to install it too ...   

Any chance we can go back to point and click ?   ( point to a location to install Ubuntu )   

Linux installers half a decade or more ago were better ... Why are they worse now ?  

I want a linux that installs without Drama , is there one ?

---

### Post by wildmanne39 on 2013-04-18
It is a lot easier now then it use to be unless you have windows 8.

When you try to partition are you choosing the button that says something else?

Do you have four primary parttions already?

Tell us exactly how you are trying to install, which version and what is happening when you try.
Thanks

---

### Post by grahammechanical on 2013-04-18
I do not agree with you at all. I have been installing Ubuntu since 2007. I have several versions of Ubuntu on different partitions and I never have an problem telling the installer in which partition I want it to install Ubuntu. In fact if you have a second drive that you want Ubuntu to be installed on then it is very simple indeed.

Just choose the Something Else option and select the second drive. You may need to scroll down the partitioner panel to see that drive. It is good to use the partitioner in the live session to create the partitions in advance. Then select the partition you want Ubuntu installed in and click Change and in the dialog box you can change the size, choose a file system, a mount point and if the partition should be formatted.

I only issue I found when I recently installed Ubuntu to second drive is that the installer made use of a swap partition on my old drive. Well, it would wouldn,t it. But if I removed the first drive then the Ubuntu on the second (now only) drive would not have a swap partition. I solved this simply by installing Ubuntu with the first drive disconnected. Which is perhaps the best way to do this.

Then with ubuntu installed and the first drive connected I booted into the new Ubuntu and ran```
sudo update-grub
``` and ```
sudo grub-install /dev/sdb
```. I then set the BIOS boot priority to look to the second drive (sdb) and now I have a Grub menu that lets me boot into any Ubuntu OS that I have on the two drives.

I guess, that some people should stick to buying computers with the OS already installed. Nothing wrong with that. But it does take a little bit of training to install Linux (any distribution) on a machine with an OS pre-installed.

I wonder how easy it is to install Windows 7 or 8 on a machine with Ubuntu pre-installed. It must be fairly easy provided you do not mind loosing your Ubuntu installation.

---

### Post by Mopar1973Man on 2013-04-18
Ubunrtu you can select the partitions to use or not to use. It just up to you to select the ones that will be used. There should be a option for "Something Else" and then allow you to select the partition(s) you want to use and format or not.

---

### Post by lonestranger on 2013-05-24
I don't know about how much easier or harder ubuntu is now, but I've sure messed up my computer with it.  I wanted (still do) to install ubuntu on a usb stick.  I guess I'd expect to turn on my machine, press an F- key, and get the choice to run ubuntu from my usb.  I want to load tor on it and so on.  

I tried to follow the instructions [here]("http://askubuntu.com/questions/163982/run-12-04-from-usb-with-no-hard-disk-usage") and when I turned my machine back on I get the screen to choose ubuntu or win7 so what I've done is install ubuntu on my computer, but when I try to boot win 7 it tells me there is no bootable whatever on my computer (ASUS G75W).  So, my copy of win7 is gone. grrrrrrr!

But what else is weird is that what is now on my usb is a copy of ubuntu like what you'd find on a cd "Try Ubuntu or Install ubuntu".  It didn't even succeed in loading a real OS of ubuntu!

I give up and appeal to you folks for help!  How do I accomplish this feat?  Thank you.

By the way, the ubuntu version I loaded is 13.04, 64bit.

---

### Post by Maverick Meerkat on 2013-05-24
Your Live USB sounds like it's running correctly.
Just select "Try Ubuntu" and your desktop will load in.

Rick

---

### Post by deadflowr on 2013-05-24
Even when putting an OS on a machine by itself, I always use the manual option.
In ubuntu it's 'something else'.
I never like the way an automated partitioning make my partitions.
And I could never trust it, with a machine with mutliple OS's.

---

### Post by Mark Phelps on 2013-05-24
> **lonestranger said:**
> ...  but when I try to boot win 7 it tells me there is no bootable whatever on my computer (ASUS G75W).  So, my copy of win7 is gone. grrrrrrr!

It may not actually be GONE; instead, it may just have trouble booting.

If you can get into Ubuntu, then try to mount the Windows partitions (using the Home icon) and see if the directories and files are still there.

If they are, you may be able to repair the booting operation using Boot-Repair: [http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by lonestranger on 2013-05-24
> **Mark Phelps said:**
> It may not actually be GONE; instead, it may just have trouble booting.

If you can get into Ubuntu, then try to mount the Windows partitions (using the Home icon) and see if the directories and files are still there.

If they are, you may be able to repair the booting operation using Boot-Repair: [http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Ooh, this sounds promising.  I know nothing about mounting windows partitions (using the Home icon).  Is there a resource you can point me to?

---

### Post by deadflowr on 2013-05-24
> **lonestranger said:**
> Ooh, this sounds promising.  I know nothing about mounting windows partitions (using the Home icon).  Is there a resource you can point me to?

Open up the home folder and look at the left side.
There should be a section called devices.
If windows exists still it would be listed there.
If you didn't label or name it, it will show up as something volume.

---

### Post by lonestranger on 2013-05-24
Okay, under Devices I see "Recovery, DATA, OS, SDATA2, Computer".  Under OS there is a folder "Windows".

Time to check out your boot-repair link?

---

### Post by lonestranger on 2013-05-25
(deleted)

---

