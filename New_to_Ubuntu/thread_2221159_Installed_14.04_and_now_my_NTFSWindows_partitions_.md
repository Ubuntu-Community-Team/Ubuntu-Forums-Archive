---
title: "Installed 14.04 and now my NTFS/Windows partitions are GONE"
date: 2014-04-30
forum: New to Ubuntu
---

### Post by nickniebaum on 2014-04-30
Hey all,

So somehow (I'm not sure how, I've installed Ubuntu alongside of Windows a ton of times) I managed to install Ubuntu and wipe out my two NTFS partitions by accident. I realized it after rebooting after installing Ubuntu and removing the disc when the dual-boot menu didn't appear. So I started panicking and checked my partitions and sure enough they were gone. I only have 3 now - sda1 is my boot partition which only has ubuntu, sda2 is the Linux partition, and sda3 is a swap partition I had created a few months ago. My Windows partition and recovery partition seem to be gone. So I have a few questions on where to go from here:

1) My girlfriend had a ton of pictures on the Windows partition and it'd really be great to at least be able to get those back. I don't know much about file recovery though, and from what I've read about some software out there that helps with it, you at least have to have a partition to point it to. Am I screwed here?

2) The recovery partition seems to be gone, and my computer didn't come with recovery disks or Windows installation disks, so I am kind of at a loss of how to get Windows installed back. I still have my product key stuck to the bottom of the computer, so at least there's that. Should I just download a pirated copy and use my key instead of a crack?

3) Once I do get Windows re-installed, is there any way to re-create my recovery partition in case I need it in the future?

Thanks in advance for the help!

---

### Post by papibe on 2014-04-30
Hi nickniebaum.

Sorry to hear that.

Could you open a terminal, run this command and post back the results (you can copy/paste the text)?
```
sudo fdisk -l
```
I believe you can order the installation disks from the manufacture, say, Dell Toshiba. They won't be free, but they should be a priced reasonable.
Regards.

---

### Post by nickniebaum on 2014-04-30
Sure, it is below. One other thing - I found this article: [http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/) which talks about a utility called testdisk. I've installed it and am playing around with it. My deleted partitions didn't show up with the "quick search" option, but with "deep search" they did appear, however I'm not sure how to use the tool to recovery them, if they are recoverable. If anyone has any pointers to how to use this more effectively, please let me know. In the meantime if I do anything interesting I'll update my thread.

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f30be0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1050623      524288    b  W95 FAT32
/dev/sda2         1050624   969484287   484216832   83  Linux
/dev/sda3       969484288   976771071     3643392   82  Linux swap / Solaris
```

---

### Post by LastDino on 2014-05-01
> **nickniebaum said:**
> Sure, it is below. One other thing - I found this article: [http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/) which talks about a utility called testdisk. I've installed it and am playing around with it. My deleted partitions didn't show up with the "quick search" option, but with "deep search" they did appear, however I'm not sure how to use the tool to recovery them, if they are recoverable. If anyone has any pointers to how to use this more effectively, please let me know. In the meantime if I do anything interesting I'll update my thread.

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f30be0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1050623      524288    b  W95 FAT32
/dev/sda2         1050624   969484287   484216832   83  Linux
/dev/sda3       969484288   976771071     3643392   82  Linux swap / Solaris
```

Not by ordinary means, no. However, there are professional data recovery services which can help you in this situations but they cost ''tone'' of money, enough to make you think MS charges miserly amount for their OS. I've no idea how they do it but they even recover data from dead HD. 
There are means to recover deleted files from software (Like: File Recovery, Pandora etc.) but I don't think they work on formatted drives.

---

### Post by squakie on 2014-05-01
+1.  You've already formatted new partitions and loaded data - programs, etc..  So things like the file tables, etc., from Windows have probably been long overwritten by now.  So there really won't be much of anything you can do on your own.  At best it may find some files fragments, but there is nothing left to describe how those fragments relate to each other.  As Gotten0007 said above - there are professional services that can try to do this for you, but with the state of your partitions the chance of success is not good.  These services are VERY expensive - they are expensive because they provide a very specialized service that requires some expensive specialized hardware and software, and these services are normally used by businesses that for what ever reason don't have a backup to restore and recover their business data with so they are desparately seeking anything to solve their problem.

---

### Post by mastablasta on 2014-05-01
which is why when changing, moving, deleting partitions you always need to create backup copies first. the restore partition can usually create restore disks or now even recovery/restore USB drive/stick (although that only recovers the OS not the data). but with easy tools liek Redobackup and clonezilla and with cheap external drives it is really best to just image the whole disk as backup.

what happened is probably you had more than 4 primary partitions, MBR partition scheme and then you accidentally selected to wipe the whole disk as the install next to windows option is not shown in this case..

---

### Post by WogBoy on 2014-05-01
> Should I just download a pirated copy 

No. " Pirate " copies are not safe in my opinion. These are genuine ISO's from digital river, Use your key to activate.
**Windows 7 (English) with Service Pack 1**
  Note: must match what your product key version is for.
 &#8226; [Windows 7 Home Premium (x86)]("http://msft.digitalrivercontent.net/win/X17-58996.iso") - X17-58996
 &#8226; [Windows 7 Home Premium (x64)]("http://msft.digitalrivercontent.net/win/X17-58997.iso") - X17-58997
 &#8226; [Windows 7 Professional (x86)]("http://msft.digitalrivercontent.net/win/X17-59183.iso") - X17-59183
 &#8226; [Windows 7 Professional (x64)]("http://msft.digitalrivercontent.net/win/X17-59186.iso") - X17-59186
 &#8226; [Windows 7 Ultimate (x86)]("http://msft.digitalrivercontent.net/win/X17-59463.iso")* - X17-59463
 &#8226; [Windows 7 Ultimate (x64)]("http://msft.digitalrivercontent.net/win/X17-59465.iso")* - X17-59465

Also see here.
[http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/cannot-find-digital-river-download-site/66a8439b-0d16-4b70-92f7-1c8486a46ebf](http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/cannot-find-digital-river-download-site/66a8439b-0d16-4b70-92f7-1c8486a46ebf)

---

### Post by john_nisbet on 2014-05-18
Hey,  Two weeks ago is a long time in computer land, but in case you're still looking for answers...

All is not lost, no need to worry or panic.  Your instincts that your files might be recoverable are absolutely correct.  I did the same thing almost exactly a year before you and I was able to recover almost all of my personal files.  I'm no tech wizard, either.

1. Data Recovery...  All the advice in the world, which you already knew, stings all the more when something stupid happens.  I know your pain.  Even though you've formated your hard drive, rewritten the partition table and boot record, and written new data on it, a lot of your files might still be intact.  It's true what they say, if you want to destry data you have to go out of your way and really destroy it.

**No. 1 Rule**:  Limit the amout of data you now write to the hard drive.  Every 1 or 0 you write has a chance of writing over a 1 or 0 you could recover.  It's been two weeks, so this will likely be advice for the next person.

You can use professional data recovery services.  Personally, I was more comfortable downloading software and doing it myself.  Again, I'm no wizard.  I grabbed File Recovery and Partition Recovery Pro from [LSoft]("http://www.lsoft.net/").  The interface wasn't the most intuitive but I muddled through.  I recovered appx 90% of my files.

2. Recovery Partition... You don't need it.  Only useful in a world where vendors don't give you installation media.  Create new media and you'll have all the recovery tools you need.

3. *WogBoy* (above) is absolutely right.  Legitimate ISOs are available from Microsoft, so you're golden.  Just use the ProductKey they stickered to your computer and activate.  Added bonus: none of the crappy bloatware that came with your original Windows installation.  Life's a bit harder if you're running Windows 8, but not impossible.  ([Where Can I Download Windows 8 or 8.1?]("http://pcsupport.about.com/od/windows-8/f/download-windows-8.htm"))

**No. 2 Rule:**  When you frak up your computer, always always always turn it off, grab a beer, and deal with it in the morning.  If you've potentially lost all your gf's photos, get her a beer too.

---

