---
title: "LiveCD Installation fails to detect Partitions"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by sjynteK on 2012-08-31
Hello everyone, firstly.. thanks for your time and effort to help a newcomer to this OS! Firstly, I'm running;Windows 7 Home Premium on an Acer Aspire build. I think I already know the problem though, I just need confirmation. 

Acer likes to install their Recovery Disk onto the harddrive, and then theres another 100MB reserved system, and then theres C:, and D:, thats on shipment.

This totals 3 Primary Partitions - Recovery, 100MB reserved and C:
and 1 Logical Partition - D:

From my understanding, any Operating system requires a free Primary Partition, and since Acer already uses up the 3 Allowed primary partitions and the 4th being for my Data, I'm unsure what to do.. surely some of you have more than 3 operating systems installed?

---

### Post by Bashing-om on 2012-08-31
sjynteK; Hi ! Welcome to the forum.

It is pleasing you want to install ubuntu.

You are correct in that a disk may have a max of 4 partitions.
Be advised to use windows tools to use with windows. Ubuntu tools to use with ubuntu.

Look at your hard-disk from windows disk utility. Many advise to copy the recovery partition data off to a CD (or other back-up); and using windows utilities free up some space for ubuntu to install onto. Twenty gigs will be more than enough to get your feet wet.

Get that done it is ubuntu;s turn to prepare for install/ In a simple install,when you get to the  installer. just choose the "something else" option ..make sure the set aside free space is selected, let the installer do it's thing, answer a few questions as prompted (remember your user-name and pass word !) Did I say to remember your pass word ? The last screen has a small advanced tab, click it to make sure grub will be installed where you want it (single disk system, make sure grub installs to sda) TAadah welcome to ubuntu.
but do remember your pass word.

If you have any problems or questions, we are here.

[INDENT]HTH <==BDQ 
[/INDENT]

---

### Post by oldfred on 2012-08-31
If you have d: as a logical then that is inside an extended partition already & that simplifies things greatly.

Post this from a terminal in the liveCD:

```
sudo fdisk -lu
```If d: is logical, you can shrink your c: using Windows tools, but do not create any new partitions. Then use gparted to extend the extended left into the unallocated space (assumes d: is right after c: . Then you can easily install into the unalloate that is now in the extended or manually create logical  partitions. 

Backups are important, so backup Windows and make a Windows repairCD or USB as you may need it if you have Windows issues.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by mcduck on 2012-09-01
> **sjynteK said:**
> Hello everyone, firstly.. thanks for your time and effort to help a newcomer to this OS! Firstly, I'm running;Windows 7 Home Premium on an Acer Aspire build. I think I already know the problem though, I just need confirmation. 

Acer likes to install their Recovery Disk onto the harddrive, and then theres another 100MB reserved system, and then theres C:, and D:, thats on shipment.

This totals 3 Primary Partitions - Recovery, 100MB reserved and C:
and 1 Logical Partition - D:

From my understanding, any Operating system requires a free Primary Partition, and since Acer already uses up the 3 Allowed primary partitions and the 4th being for my Data, I'm unsure what to do.. surely some of you have more than 3 operating systems installed?
..just to add this, since nobody else mentioned it already, Ubuntu is perfectly happy with a logical parttiion. Actually as far as I know Windows is the only OS that has issues with others than primary partitions... ;)

So yes, running more than 4 operating systems on same machine is definitely possible, but running more than 4 Windows installs (why would anybody even do that? :D) could be a problem...

---

