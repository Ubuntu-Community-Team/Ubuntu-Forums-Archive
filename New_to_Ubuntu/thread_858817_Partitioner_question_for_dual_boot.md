---
title: "Partitioner question for dual boot"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2008-07-13
I am trying to install Ubuntu 8.04 alongside an XP install. All of the directions say that whether you choose Install at the intitial menu, "Install" from the desktop, or use System/Partition Editor, that you will get a choice to either use the entire disk, or to resize the existing partition.

When I use gParted, it comes up in familiar form but shows the 80GB hdd as dev/sda 76.33 GB and as

unallocated Partition
unallocated Filesystem

By way of background, this hdd at one time had either a version 6 or maybe even a version 5 Ubuntu installed on it. So when I installed XP, I chose to use 40GB for Windows and planned on using the remaining for Ubuntu. To further complicate matters, I didn't have a working XP install CD and so borrowed one from a friend, but all he had was a very old Compaq install disk. The partition and install seemed to go fine and I was able to validate successfully and update to SP2.

Back to Ubuntu. If in the partitioner, I now choose "New" partition, it flashes a box entitled "set disklabel on /dev/sda" with a warning that "Creating a new disklabel will erase all data on dev/sda." Obviously I don't want to erase everything.

Questions:
Why is it showing only one partition of 76GB?
What happened to my 40GB XP partition?
Why is it not showing something as NTFS since that is the format that I used for the XP install?
Why am I not getting a chance to create a new partition without the necessity of setting a disklabel with the the result of erasing everything?

---

### Post by ChameleonDave on 2008-07-14
It seems to me that the partitioner really cannot see the NTFS partition.  It sees one big unformatted partition on that drive, and therefore its first action it to set a disklabel in order to make the drive readable and be able to create a filesystem.

This normally only happens if the drive has become corrupted.  I don't know why it would be.

I think that you should go back to Windows and see what you can do from there.  [CHKDSK]("http://en.wikipedia.org/wiki/CHKDSK") should be able to verify whether the drive is OK, and something like [PartitionMagic]("http://en.wikipedia.org/wiki/Partitionmagic") ought to be able to fiddle around with the partitions, hopefully putting them in a state that allows them to be readable by a Linux partitioner.

---

### Post by kansasnoob on 2008-07-14
Have you been able to successfully run the Ubuntu Live CD? Not to install, just running the desktop environment from the CD?

I must say this is a new one on me.

edit: Also, what version of Ubuntu do you have?

---

### Post by ChameleonDave on 2008-07-14
> **kansasnoob said:**
> Have you been able to successfully run the Ubuntu Live CD? Not to install, just running the desktop environment from the CD?

I must say this is a new one on me.

edit: Also, what version of Ubuntu do you have?
It seems fairly clear to me that he is running the Hardy Heron live CD, and is trying to install to the hard drive.

---

### Post by Odyssey1942 on 2008-07-14
Thanks for the responses.

To confirm, it is 8.04. And I have been successful in running the desktop (virtual) environment. In fact I found this the easiest way to bring up gparted (System/Partition Editor).

CHKDSK did not report any errors, but did give two pieces of interesting info. One is that it showed the space at 55,392,119 which indicates that either I forgot how much space I allocated during the install (my memory not as good as it never was :lolflag:) or Windoze did it' "own thing" during the install.

The other is that I did leave the earlier linux partitions (two) so XP installed into E:

One other thing. Since the install was done using a old Compaq install CD, and knowing how major companies do their own thing with installs in terms of secret partitions, re-install directories, etc., could this possibly be confusing gparted into not recognizing the NTFS or the ext2 (3? partitions?

---

### Post by kansasnoob on 2008-07-14
Sorry for the redundancy of my question, re:what version, I just wanted to verify that you're using 8.04.

Since you can run the Live CD are you able to take a screenshot of Gparted and post it? If you need some instructions to do that just ask. This is mine:

[ATTACH]77707[/ATTACH]

I'll be in and out today so my replies might be slow. I'm wondering if Windows somehow installed as a Logical Partition within an extended partition ............. something I thought was impossible:confused:

---

### Post by kansasnoob on 2008-07-14
Oh, something really simple and I think worth a try is downloading an actual Gparted Live CD:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Common sense tells me it should produce the same results, but it's a tiny download and burn, so I'd give it a try.

Edit: One more dumb question, since you say, "The other is that I did leave the earlier linux partitions (two) so XP installed into E:". I just want to verify that when you start or restart your computer you get no GRUB at all, or do you get the GRUB screen?

---

### Post by Odyssey1942 on 2008-07-14
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7e4e9e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           8        1027     8193150    c  W95 FAT32 (LBA)
/dev/sda2            1028        3067    16386300    f  W95 Ext'd (LBA)
/dev/sda3            2048        3067     8193118+   b  W95 FAT32
/dev/sda4            3068        9963    55392120    7  HPFS/NTFS
/dev/sda5            1028        2047     8193087   83  Linux
ubuntu@ubuntu:~$ 

Interesting that it shows drives c, f, and b as FAT32. I'm thinking I know why. When I went to install XP, the only disk that I had was for XP Pro which I went ahead and installed thinking that my serial number was for Pro. Turned out it wasn't, necessitating the borrowing of a Home CD. When I then installed Home, apparently it left Pro installed and now when I boot the Windows partition, I get a choice of Home or Pro. Unsure how to get rid of Pro at this stage and maybe the best thing is just to go through a reformat of the hdd and start over with Home, then 8.04? Waddyatink?

Kansasnoob, sorry I don't know how to take or post a screen shot. If you can walk me through it, I'm happy to do so.

In the interim, the gparted comes up with the normal toolbar at the top 

and on the second line, with several choice boxes underneath (New, Delete, Resize/Move etc.) and over to the right a box showing a partition with up/down arrows beside (BTW, the only partition showing in the list is /dev/sda)

Then a box extending across the width showing, in this case,
"unallocated
76.33 GiB"
I believe this box changes as you create new partitions and it gives you a visual representation of the size as you change it

The next line has several boxes:
Partition (underneath it says: unallocated )
Filesystem (underneath it says: unallocated )
Size  (underneath it says: 76.33 )

---

### Post by bumanie on 2008-07-14
I think screenshots work off a live cd. To take a screenshot, Applications --> Accessories --> Screenshot. This should go your desktop. Where you post messages here, down the page a bit, underneath the main message window, there should be a box that says manage attachments (or something similar). Browse to the desktop and attach - it's similar to attaching a photo to an email. 
Also, do you know which partition has a xp home and xp pro? I think the best thing to try and do, is save the xp you wish to keep and then reinstall ubuntu once that is achieved. A screenshot may be helpful, but not essential. If you get a screenshot, if you know, state which xp is which.

---

### Post by Odyssey1942 on 2008-07-14
bumanie,

Tried to take the screenshot and got right down to the final question box where it asked me where I wanted to put the screenshot, but then it didn't actually do it (i.e., no screnshot showed up on the desktop)

If you call up your System/partition editor and look at it beside my description, I think it will be pretty clear. But if not, ask for any clarification needed.

When I boot the computer with no Ubuntu CD in the drive, I get a Windows boot loader which gives me a choice of Home or Pro. If I choose Pro, it tells me I have to activate before I can do anything else. My serial number is for Home, so I boot the Home option, which I have already activated.

When Home comes up, it shows in E:

Hope this is answering your questions.

---

### Post by bumanie on 2008-07-14
Wasn't 100% sure whether screenshots worked off live cd's or not because I've never tried it - apparently not - I've learnt something from that. If xp home is on E\:, do you know which partition this equates to when you look at gparted gui? I doubt /dev/sda is E:\ Hopefully you can tell. Fdisk -l shows two FAT 32 partitions and one ntfs partition - do you know which partition belongs to which xp installation?
By the way your explanations are quite clear, but when I can't see things it is a bit hard to get the full picture - if you know what I mean. Really, I want to be careful and not wreck the xp you wish to keep.

---

### Post by kansasnoob on 2008-07-14
OK, sorry I didn't know you couldn't "save" screenshots from Live session. I'll fiddle around later and see if there's a way.

But something interesting: notice the LBA at the end of your first two entries:

> /dev/sda1 * 8 1027 8193150 c W95 FAT32 (LBA)
/dev/sda2 1028 3067 16386300 f W95 Ext'd (LBA)
/dev/sda3 2048 3067 8193118+ b W95 FAT32
/dev/sda4 3068 9963 55392120 7 HPFS/NTFS
/dev/sda5 1028 2047 8193087 83 Linux

Read this from Wikipedia:

> Legacy MBR (LBA 0)

The primary purpose of the MBR at the beginning of the disk is to prevent MBR-based disk utilities from mis-recognizing, and possibly over-writing, GPT disks. A single partition, encompassing the entire GPT drive, is indicated. The System ID for the partition is set to 0xEE, indicating that it uses GPT. Because of this, EFI ignores the MBR. Some 32-bit OSes which cannot read GPT disks nevertheless recognize this ID and present the disk as an inaccessible GPT disk. Older OSes will generally recognize the disk as containing one partition of unknown type and no empty space, and then they'll typically also refuse to modify the disk unless the user explicitly requests and confirms the deletion of this partition. This way, accidental erasures are prevented.

Especially this part: > Older OSes will generally recognize the disk as containing one partition of unknown type and no empty space, and then they'll typically also refuse to modify the disk unless the user explicitly requests and confirms the deletion of this partition. This way, accidental erasures are prevented.

[http://en.wikipedia.org/wiki/GUID_Partition_Table#Legacy_MBR_.28LBA_0.29](http://en.wikipedia.org/wiki/GUID_Partition_Table#Legacy_MBR_.28LBA_0.29)

Now if you're certain you chose NTFS when you installed XP Home I'd be fairly certain that sda4 is what you want to keep .......... but how:confused:

Honestly if you have nothing saved of importance it probably would be "time-wise" IMHO to just wipe the whole mess and start from scratch.

If Gparted recognizes sda4 it's possible to delete everything else, but I'd still be, at best, only somewhat sure of the outcome.

Sorry.

---

### Post by kansasnoob on 2008-07-14
Maybe, just maybe take a look at qtparted which is available in the repos.

Not sure if it would recognize anything differently than Gparted.

---

### Post by phoenix_abhi on 2008-07-14
I have an opinion. Boot in to the XP home (pro is useless for u). Give ur partition and details here. Meant Type of file system (which windows shows), what is in c,d ,E(xp home ?) and so on. we can start from scratch with out affecting the xp (possibly ?). For a while leave aside the whole Ubuntu things.

---

### Post by Odyssey1942 on 2008-07-14
Many thanks for all the very good questions and suggestions. I am a bit red-faced here as I refreshed the screen occasionally to see if there were any responses and did not notice that somewhere along the way a page 2 appeared with all your good posts. :oops:

Being an impatient sort, and not seeing the additional guidance, I went ahead and reinstalled XP Home from scratch, reformatted the entire disk during the install as NTFS, and have now installed Ubuntu 8.04 as a dual boot without so much as a hiccup. :)

Thanks again for all your help.

---

### Post by phoenix_abhi on 2008-07-15
Please make the thread solved

---

