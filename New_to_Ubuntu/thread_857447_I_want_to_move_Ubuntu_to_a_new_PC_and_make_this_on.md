---
title: "I want to move Ubuntu to a new PC and make this one Windows"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Amablue on 2008-07-12
This computer currently dual boots Ubuntu and XP, and I'd like to have it be solely XP. However, I've lost my windows disk. What do I have to do to get this computer to just have XP?

My partitions are WinXP, Ubuntu, Swap, in that order. I think I just need to extend the windows partition to cover everything, then restore the MBR.

---

### Post by avtolle on 2008-07-12
What I'd do is first delete the partitions (Ubuntu and Swap), then extend the windows partition, and restore the MBR.

EDIT: I'm ignorant of how Windows will handle this; will extending the Windows partition also format the remaining space properly?

---

### Post by TSS on 2008-07-12
Here are a few thoughts which I hope will be helpful.  

Partitioning tools in Windows XP are somewhat limited, but they might be able to get the job done in this case.  I believe the partitioning tool in XP is called Diskpart, which is a command line utility.  You might look into how to use that.  I know it can't shrink partitions, but I'm pretty sure it is capable of extending the XP partition into unallocated space.

For deleting the Ubuntu partitions, you have a few options.  I personally like to use the GParted LiveCD ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)).  It's pretty easy to use, and there are a lot of tutorials out there.  I'm sure you could find other tools to do the job as well.

You might consider investing in a tool like Partition Magic ([http://www.symantec.com/norton/partitionmagic](http://www.symantec.com/norton/partitionmagic)).  If you'd rather not worry about finding free tools and just want to get it all done in one shot, that would be the way to go.  You can get it done with free tools though, don't get me wrong.

A final concern is the bootloader.  I assume you are using Grub/Lilo to boot both Windows and Ubuntu.  If you can find it, you can use your original Windows XP disk to repair a Windows installation.  This will fix the bootloader and allow you to boot into Windows XP.

So to recap:
0.) Back up your data...
1.) Use GParted LiveCD to erase your Ubutnu partitions
2.) Use Windows XP disk to repair your Windows installation, or find some other method to fix the bootloader.
3.) Use Diskpart to extend your XP partition.

Or:
0.) Back up your data...
1.) Invest in a tool like Partition Magic

TSS

EDIT: I've found a utility called MBRfix, which might be able to fix your MBR.  I've never used it, and it does look to user friendly, but it might be helpful ([http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)).  If you decide to go that route, you would need to run that utility from Windows BEFORE you erase your Ubuntu partitions.

---

### Post by ugm6hr on 2008-07-12
My advice - restore the XP bootloader first (if you don't have an XP CD):
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

Then, boot from Ubuntu (or any Linux with GParted) LiveCD and delete the Ubuntu and Swap partitions.

After this you have options:

1. Create a new NTFS partition to replace Ubuntu / swap and keep it as a "storage" partition separate from the main XP partition.

2. Extend the XP partition to fill the HD (using a partition editor - GParted should do this with NTFS partitions, I think).
[B]
Be warned[/B] - resizing (and potentially even deleting) partitions can cause data corruption / loss - so a backup strategy is advisable.  Consider how you would recover this backup without an XP CD if things went wrong too.  I think one option is partimage, although I have never used it myself (and am uncertain whether it will backup Windows partitions): [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by Amablue on 2008-07-13
Thanks for the help everyone. I have an external drive where I keep all my media as well as a text file listing off all the important programs to remember to install. In a worst case scenario I'll use a second computer to burn a questionably legal copy of a windows CD, and I can extract my own CD key from this computer so I'm still using a legit copy in the end (obviously I'll extract my CD key before doing any of the repartitioning).

---

### Post by ugm6hr on 2008-07-13
Couple more tips...  If you want to move the current Ubuntu to a new computer, the following will save bandwidth and time:

Backup /var/cache/apt/archives (except the lock file) and copy to new installation (as sudo) in same directory.

Then:
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

