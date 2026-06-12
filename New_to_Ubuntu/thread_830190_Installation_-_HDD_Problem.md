---
title: "Installation - HDD Problem"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by intense.ego on 2008-06-15
I'm trying to install Xubuntu on a 3.5 year old system and am having a problem. Firstly, in preparation of the installation, I made sure there was free space on my hard drive (13.5 gb to be precise). I also cleared the recycle bin, so it was deleted not just binned.

The problem arose when, during the installation, I chose to manually partition the hard drive. The scan was performed and the results were shown. It said that dev/sda1 had 80,000 mb capacity and that the used was "unknown". It also said that i only had 8 mb of free space. I couldn't edit sda1, probably because it was "unknown." I could create a new partition, but it would only be 8mb large.

What is the problem here? Is my hard drive unscannable?

Additional info: filesystem is NTFS. the computer is a prebuilt HP. I am using the Xubuntu 8.04 Hardy Heron live disc i burned. everything else is working fine, even wireless, in the live disc mode. Only windows xp is currently on the system.

Thank you in advance.

---

### Post by shifty_powers on 2008-06-15
have ya tried to defrag the drive in windows? and with a decent defragger mind, the basic windows one is crap.

---

### Post by intense.ego on 2008-06-15
I am going to try that right now. Do you recommend any specific one? I am about to use Auslogics Disk Defrag

---

### Post by Happy_Man on 2008-06-15
Just so long as it's not the Windows defragger, you'll be fine.

---

### Post by intense.ego on 2008-06-15
But, is this known to solve the problem, or is it just a theory?

---

### Post by bobpur on 2008-06-15
I use Auslogics Disk Defrag on my machines. It is, defineately, better than what Windows provides.

---

### Post by Happy_Man on 2008-06-15
It's most likely the reason... if it's not, then I'd be surprised that Windows even boots. Besides, defragging HDDs is good. At least Ubuntu does it automatically for you so that there is none of this worry when trying to reinstall.

---

### Post by cariboo on 2008-06-15
Seeing as you are a new user I would forgo the manual partitioning and let gparted create a partition for you. It will resize your Windows partition automagically and create a root and swap partiton. The best thing to do is to follow this guide:

[COLOR="Red"]http://ubuntuguide.org/wiki/Ubuntu:Hardy[/COLOR]

Jim

---

### Post by intense.ego on 2008-06-15
> **cariboo907 said:**
> Seeing as you are a new user I would forgo the manual partitioning and let gparted create a partition for you. It will resize your Windows partition automagically and create a root and swap partiton. The best thing to do is to follow this guide:

[COLOR="Red"]http://ubuntuguide.org/wiki/Ubuntu:Hardy[/COLOR]

Jim

I am not a new user; I have been using ubuntu for about a year now. I was under the impression that partitioning it any other way than manually would result in a format and the deletion of my whole windows install et al. But I have only done this a couple of times, so I am no expert

---

### Post by intense.ego on 2008-06-15
I tried the defragging, but I got the same results. Any other ideas as to why? Should I just use gparted and partition the drive and then install?

---

### Post by shifty_powers on 2008-06-15
you can most certainly use gparted. back in my dual boot days i used to use partition magic.

However....

No partitioning is without risk. ALWAYS BACK UP YOUR DATA FIRST!

Don't get me wrong, 99/100 it'll go peachy, but you don't want to risk that 1/100 chance with your data, do you? ;)

---

### Post by Yuki_Nagato on 2008-06-15
You will want to have a Windows repair disk around.  When you resize a windows partition useing 3rd party software, this can "break" some of window's ability to boot itself (after the chainload from GRUB).  The repair CD can fix some of this.

---

### Post by intense.ego on 2008-06-16
I tried using gparted instead of the installation partition manager, but nothing new happened. What could be the problem? Could it be because I use an external DVD reader and boot off of it? (i only had blank dvds, and the computer only has a built-in cd drive)

---

### Post by intense.ego on 2008-06-16
I'm going to try and use PartitionMagic, maybe that will work better with the hdd drive.

---

