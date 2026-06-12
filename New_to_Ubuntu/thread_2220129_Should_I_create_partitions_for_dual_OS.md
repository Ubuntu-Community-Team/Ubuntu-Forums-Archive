---
title: "Should I create partitions for dual OS?"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by LizzyJean on 2014-04-26
I have been test driving Ubuntu 14.04 from a USB stick for the last week and it's working really well!  My goal is to get totally away from Windows.  (I have XP.)  

My next step is to do a dual install.  When I boot from  my USB stick and choose a dual install, does Ubuntu automatically partition my drive?  Also, I've read that it's good to create a third partition for my files so that both Ubuntu and Windows can easily access them.  Any advice about this?

---

### Post by pfeiffep on 2014-04-26
Ubuntu Installer will perform the partitioning for you - I suggest performing a Windows chkdsk and defrag and backing up files prior to installing Ubuntu.

---

### Post by Vladlenin5000 on 2014-04-26
As already mentioned, the installer default options are sufficient for most users, hence the 'best practices' manual recommends leaving the space unallocated and let the installer work its magic. 
Whether or not to create a 'shared' partition is up to you. It'll benefit Windows mostly because it can't "see" Linux partitions while Ubuntu will be able to read all. As such, if you need to make certain files created/downloaded while in Ubuntu available to Windows as well then you either save them directly in same Windows partition or in the additional shared one which must be formated as NTFS or FAT.

---

### Post by WogBoy on 2014-04-26
>  I've read that it's good to create a third partition

As a novice Linux user ( that would be me ) I would recommend this option, I have all my music, movie's doc's etc on a 3rd partition, That way if I mess up I do not have to copy all the stuff over again.

My set up was.
1st  partition 100 GB for Whingedows ( Windows) Now Deleted.
2nd Partition  60 GB for Kubuntu. It's my Fav OS, so much so I deleted MS.
3rd Partition  240 GB for music, movies etc, Must be FAT or NTFS for it to work.

My set up now
1st partition 100 GB for Linux OS. Only software on this partition, Nothing else, I do not have or need a swap partition.
2nd  Partition 400 GB Movie's music photo's etc.

---

### Post by bob73 on 2014-04-26
I installed Lubuntu ("light" Ubuntu) in a Dual-Boot configuration with Win XP a few weeks ago.  The partitioning is automatic, and the startup choice of OS is simple (default will be Ubuntu).  Both systems work fine.  One thing I discovered is that the Lubuntu "hijacked" the driver for both my two in-case optical drives (CD & DVD) and also the outboard optical drive that connects via USB.  Now none of the three will work in Windows, but work fine in Lubuntu.  So expect this following your dual install.  (I haven't found a way to reverse this situation, which is the subject of my own thread.)

---

### Post by LizzyJean on 2014-04-26
> **pfeiffep said:**
> Ubuntu Installer will perform the partitioning  for you - I suggest performing a Windows chkdsk and defrag and backing  up files prior to installing Ubuntu.

That is a really good idea!  Thanks for the suggestion.

> **Vladlenin5000 said:**
> As already mentioned, the installer  default options are sufficient for most users, hence the 'best  practices' manual recommends leaving the space unallocated and let the  installer work its magic. . . . 

Yeah.  I'm getting the feeling that I'll just use the default options this time around.  I also learned that I can use an application called GParted to adjust the sizes or add another partition later. 

> **Vladlenin5000 said:**
> Whether or not to create a 'shared' partition is up to you. It'll  benefit Windows mostly because it can't "see" Linux partitions while  Ubuntu will be able to read all. As such, if you need to make certain  files created/downloaded while in Ubuntu available to Windows as well  then you either save them directly in same Windows partition or in the  additional shared one which must be formated as NTFS or FAT.

Thanks for pointing out how I should format the shared partition so both operating systems can read it.

> **bob73 said:**
> One thing I discovered is that the  Lubuntu "hijacked" the driver for both my two in-case optical drives (CD  & DVD) and also the outboard optical drive that connects via USB.   Now none of the three will work in Windows, but work fine in Lubuntu.   So expect this following your dual install.  (I haven't found a way to  reverse this situation, which is the subject of my own thread.)

Thanks for the warning about the CD and DVD drives. Maybe I'll go do one more check from my USB stick to make sure I can rely on Ubuntu for playing CDs and DVDs.

---

### Post by 3rdalbum on 2014-04-26
> **LizzyJean said:**
> 
Thanks for the warning about the CD and DVD drives. Maybe I'll go do one more check from my USB stick to make sure I can rely on Ubuntu for playing CDs and DVDs.

That doesn't actually happen. I know he has a thread about it, but I've never heard of this happening before and I don't believe it can be done by Ubuntu.

He's probably got a virus on Windows that tries to stop him installing antivirus software by forcing Windows not to recognize the DVD drives.

---

### Post by sammiev on 2014-04-26
"Quote Originally Posted by bob73 View Post
One thing I discovered is that the Lubuntu "hijacked" the driver for both my two in-case optical drives (CD & DVD) and also the outboard optical drive that connects via USB. Now none of the three will work in Windows, but work fine in Lubuntu. So expect this following your dual install. (I haven't found a way to reverse this situation, which is the subject of my own thread.)"

Not possible, the Windows problem was not caused by Ubuntu or any Linux OS.

---

### Post by mansonfan78 on 2014-04-26
I've found that a separate partition for your files is a good idea even if you only have one operating system.  I also have always had a separate partition for windows programs and a separate /home for linux.  Backup your hard drive frequently and if your os ever fails you can just restore that one partition and not lose anything else.

---

### Post by stinger30au on 2014-04-27
this might help you out too when you next decide to install an ubuntu o/s as dual boot.

after you have configured windows on the pc and its working fine , then install the ubuntu o/s you want and tell it to dual boot the hdd in the setup.

once this is done and you restart the pc you will see boot screen to choose either windows or ubuntu and choose and off you go.

but what happens when next ubuntu comes you & you want to install new ubuntu to hdd that already has got ubuntu on it.

where is what i do. download the new ubuntu versoin and burn to dvd and boot from it.and tell it you want to try the new o/s. when desktop comes up, goto "gparted" and then select the linux partition and set the "swap" to "off" and delete it and the ubuntu partition. you did do a back up first didnt you? i hope so.

then run the install ubuntu icon on the desktop after gparted run. tell it to dual boot windows. ubuntu is smart enough to see the free space you left for it from the previous install but it now blank from gparted and it will install ubuntu there and reboot and again you can choose between windows or ubuntu and off you go.

hope this helps

---

### Post by mansonfan78 on 2014-04-27
> **stinger30au said:**
> this might help you out too when you next decide to install an ubuntu o/s as dual boot.

after you have configured windows on the pc and its working fine , then install the ubuntu o/s you want and tell it to dual boot the hdd in the setup.

once this is done and you restart the pc you will see boot screen to choose either windows or ubuntu and choose and off you go.

but what happens when next ubuntu comes you & you want to install new ubuntu to hdd that already has got ubuntu on it.

where is what i do. download the new ubuntu versoin and burn to dvd and boot from it.and tell it you want to try the new o/s. when desktop comes up, goto "gparted" and then select the linux partition and set the "swap" to "off" and delete it and the ubuntu partition. you did do a back up first didnt you? i hope so.

then run the install ubuntu icon on the desktop after gparted run. tell it to dual boot windows. ubuntu is smart enough to see the free space you left for it from the previous install but it now blank from gparted and it will install ubuntu there and reboot and again you can choose between windows or ubuntu and off you go.

hope this helps

Alternatively, if you need to reinstall (as opposed to upgrading in place), you could choose the "something else" option which will bring up a screen that allows you to specify your partitions.  Choose the partition that has Ubuntu already installed, select "ext4" as the format, "/" as the mount point, and check the box next to "format".  If you created a seperate /home when originally installing you can mount that as "/home", "ext4", but DON'T check "format" (then, when installing, when it asks to create a user you just use the same user name and password as before).

---

### Post by pfeiffep on 2014-04-27
+1> **mansonfan78 said:**
> Alternatively, if you need to reinstall (as opposed to upgrading in place), you could choose the "something else" option which will bring up a screen that allows you to specify your partitions.  Choose the partition that has Ubuntu already installed, select "ext4" as the format, "/" as the mount point, and check the box next to "format".  If you created a seperate /home when originally installing you can mount that as "/home", "ext4", but DON'T check "format" (then, when installing, when it asks to create a user you just use the same user name and password as before).Choosing /home and not formatting  also works for another version install, ie Xbuntu; swap space can also be multiple version purposed.

---

### Post by bob73 on 2014-04-28
Cancel my warning about optical drive hijacking - it probably wasn't the Lubuntu installation, although Internet research revealed the same thing happening to a number of people who just installed a new Windows program in XP - including Norton Anti-Virus!  The problem isn't recent, either, as some "hijacks" occurred back in the early 2000's.

---

### Post by LizzyJean on 2014-04-29
> **stinger30au said:**
> but what happens when next ubuntu comes you & you want to install new ubuntu to hdd that already has got ubuntu on it.

I have been thinking about that very question, stinger30au, so thanks for addressing it!

---

