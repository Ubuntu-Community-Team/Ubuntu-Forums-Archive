---
title: "Make Mac files read and write"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by Impmaster on 2012-06-13
I am running Ubuntu 12.04 on a mac, and I am dual-booting. I want to be able to access my mac files from my ubuntu side, but whenever I try to access them, it says I don't have the right permissions. I can fix this by going over to my mac side and changing the permissions to read and write, but this is a hassle that I don't want to do every single time. Is there a way to change all the permissions on the computer at once? Also, is there a way to change the default permissions to read and write? Thank you.

---

### Post by coffeecat on 2012-06-13
There are probably two issues that you are experiencing. First, Ubuntu can only mount the journalled version of your Mac system's HFS+ read-only by default. To mount the HFS+ partition read-write, then you would need to remove the journal from the filesystem in MacOS, **or** mount the partition with a force option. For the latter I think you would need to install a couple of packages too, but I will say no more ***because I strongly advise you to contemplate neither option for your MacOS system partition***. The potential for filesystem corruption is too great.

The other problem is that of the system of Unix permissions and ownership, which MacOS and Linux both share. In MacOS, if I remember correctly, your personal file UID (user ID) will be 501. In Ubuntu, it is 1000. Unless you are in the same group, or the permissions are set for "all", Ubuntu will (correctly) deny access to files with a UID other than your Ubuntu one. My guess is that you did not change the permissions to read-write in MacOS - rather that you set them to read-write for all (others). It was the access by others/all that made them accessible in Ubuntu.

Finding a common filesystem for sharing files between MacOS and Linux is a perennial problem, and to be honest I'm not sure how most people dual-booting MacOS and Ubuntu do it, if at all. I run only MacOS on my Mac Mini and use a USB drive formatted with the non-journalled version of HFS+ (or the network) to transfer files between it and Ubuntu. Even so I have to do some permissions adjusting because of the UID issue I mention above.

As a general point, it is a bad idea to allow one operating system to have write access to another operating system's system partition. You will often see people on this forum advising against this for those who dual-boot Windows and Ubuntu. I agree with this. It is all too easy to damage the system files of the "other" operating system.

Last point:

[quote="Impmaster"]Is there a way to change all the permissions on the computer at once? [/quote]

I hope you mean change all the permissions on your personal files. I hope you don't mean change all the files, including the system files. This would break your system.

But what you could do is a recursive change of permissions of all your personal files in MacOS to make them all/other accessible. I think you can do this from Finder in MacOS. At least this would make them all accessible in Ubuntu, but you would still not be able to write to the MacOS partition from Ubuntu.

---

### Post by Impmaster on 2012-06-13
So you are saying that accessing the files of one side of the partition might destroy the files? If so, is it possible to have a shared folder between the two partitions? I like ubuntu better, but my school requires Mac OS X for our computers, for our school "image". I want to be able to have files that I can access on both sides.

---

### Post by coffeecat on 2012-06-13
> **Impmaster said:**
> So you are saying that accessing the files of one side of the partition might destroy the files?

Not quite. What I'm saying is that it is possible to accidentally delete a file in the other operating system if you have write access. Windows, for example, hides important system files by default but they are visible and erasable if you mount the Windows C: partition from Ubuntu. The same would be true of MacOS if you were able to mount it read-write, which also obfuscates its file structure, but it would be fully visible in Ubuntu.

> **Impmaster said:**
> If so, is it possible to have a shared folder between the two partitions? If you mean a shared partition, then yes. A shared folder wouldn't work if it is in one of your current partitions, because it would still be in the filesystem, and it is filesystem issues that are tripping you up at the moment. The choice of filesystem for a new partition limits you a bit. FAT32 is easy because it is read-writeable in both MacOS and Ubuntu. It also has the advantage in this situation of not supporting the Unix system of permissions and ownership, so you neatly sidestep this problem. The main disadvantage is that it limits you to a filesize of 4GB. It's also an ancient non-journalled filesystem, more prone to damage than journalled filesystems.

The alternative would be to create a separate partition formatted with the non-journalled version of HFS+. This would support files greater than 4GB, but you would still have to get around the issues arising from the different UIDs that you have in the two OSs.

You would probably need to shrink one of your existing partitions in order to make a shared data partition, but to be honest I'm a bit vague as to how you do this in MacOS's Disk Utility.

---

### Post by blueshead on 2012-06-13
He can use Boot Camp to make a small partition for file sharing.

---

### Post by Lars Noodén on 2012-06-13
Don't try to access the OS X system partition from Ubuntu.  I would recommend making a third partition for data and using unjournaled HFS+ for it.  As far as the user permissions go, you can make sure that the user account on both Ubuntu and OS X are using the same numeric UID.  That way you should be able to read and write the files from either system.

---

### Post by Impmaster on 2012-06-18
Alright, what I want to do is make an unjournaled partition to hold the files that I need to access from both sides, of about 20 gigs. I want to keep the Mac Partition, to use mac applications, and I want to install ubuntu again (I uninstalled it) on a partition. Can someone tell me how to make the unjournaled partition? For the Linux, I will use the instructions on this link: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

But I don't know how to make the unjournaled partition.

---

### Post by Lars Noodén on 2012-06-18
If you have the hfsplus, hfsprogs or hfstools installed then you should be able to use parted or gparted to make your partition.  Or in OS X, older versions have the option of formatting a partition without journalling.  With newer versions, you'll have to turn it off manually after the fact.  It should be in the Disk Utility under File or you can do it via the shell: [font=Courier New]sudo /usr/sbin/diskutil disableJournal /Volumes/Somepartition[/font]

---

