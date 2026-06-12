---
title: "is NTFS better than ext3 &amp; ext4?"
date: 2010-09-22
forum: Recurring Discussions
---

### Post by fuzzylogic25 on 2010-09-22
I have installed Ubuntu with ext3, because I have heard of issues that ext4 has. However, it seems ext3 has alot of issues too. I saw that ext3 cant be defragmented. and even if its designed not to become defragmented, it still does over time. Then there is the issue of lack of snapshots. There are others too when I googled/wikipedia the file systems.


Also there are some limitations such as subfolder limit of 32,000. ext 4 has doubled this. But NTFS has no limit, you can have up to 2^32-1 files/folders.

It just seems to me, NTFS is far more reliable and has more features than ext3/ext4.

What do you think? I mean I hear that with ext3/ext4 if you have a system crash, you can lose some serious data and with NTFS its not as bad in many cases.

---

### Post by SmokeyThePanda on 2010-09-22
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

[http://www.phoronix.com/forums/showthread.php?t=1765](http://www.phoronix.com/forums/showthread.php?t=1765)

[http://ubuntuforums.org/showthread.php?t=1075774](http://ubuntuforums.org/showthread.php?t=1075774)

Happy reading. :)

---

### Post by dirghrabadia on 2010-09-22
> **fuzzylogic25 said:**
> 
Also there are some limitations such as subfolder limit of 32,000. ext 4 has doubled this. But NTFS has no limit, you can have up to 2^32-1 files/folders.


I don't know, but, are you ever going to need 2^32-1 files/folders?

You can read more at: [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems) :)

---

### Post by wrix on 2010-09-22
I don't think what you have heard about EXT3/4 is not so correct. I am using EXT4 since it was out for Ubuntu and I didn't had any issue till now, and to just mention my system crashed many times due to power failure. And one more thing EXT4 is faster than NTFS, and for defragmentation, I don't think EXT3/4 or any other Linux file-system is that bad to get fragmented.

---

### Post by Sef on 2010-09-22
Moved to Recurring Discussions. Another is ___________ better than ____________?

---

### Post by fuzzylogic25 on 2010-09-22
I am still getting the conclusion that NTFS is more feature rich and possibly even more reliable.

However, it seems like XFS is a better choice over ext3/4 - is there a way to convert to XFS?

---

### Post by Exershio on 2010-09-22
Neither ext3 or ext4 need to be defragged often (if at all) because unlike with NTFS, files written to ext3/4 are randomly scattered across the file system, so they rarely cause fragmenting issues (unless you don't have much free space left).

ext3/4 can be defragmented as well. Any file system can.
Here's a defragger one of the admins here wrote for Linux: [http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)

---

### Post by formaldehyde_spoon on 2010-09-22
> **fuzzylogic25 said:**
> I have installed Ubuntu with ext3, because I have heard of issues that ext4 has. However, it seems ext3 has alot of issues too. I saw that ext3 cant be defragmented. and even if its designed not to become defragmented, it still does over time. Then there is the issue of lack of snapshots. There are others too when I googled/wikipedia the file systems.


Also there are some limitations such as subfolder limit of 32,000. ext 4 has doubled this. But NTFS has no limit, you can have up to 2^32-1 files/folders.

It just seems to me, NTFS is far more reliable and has more features than ext3/ext4.

What do you think? I mean I hear that with ext3/ext4 if you have a system crash, you can lose some serious data and with NTFS its not as bad in many cases.

Not sure where you are hearing this stuff.  Ext3 can be defragmeted (but not something you do lightly) however you're very, very unlikely to ever need too. 
 Ext3 fragments far less than NTFS; Ext3 uses pre-allocation to avoid fragmentation. 

32,000 sub-folders **per folder** is a potential limit for you?  I would say (slightly tongue-in-cheek) that if you need that many then it's likely because those subdirectories have similar numbers of occupants, or at least in the same order of magnitude, and if you consider that 32,000^2 is far larger than the total number of files allowed on NTFS I think you are much more likely to hit the NTFS 2^32 limit before you hit the ext3 32k subfolder limit.

As I understand it, yes, it's possible under some extreme circumstances for ext4 to lose some data (? someone who knows ext4 better will have to comment).
But ext3 is rock solid (bearing in mind of course that ALL FSs are vulnerable to crashes to a certain extent), I personally would trust ext3 over NTFS any day.

I guess I would consider NTFS stable enough for me (I use ext3) but I would never use it, because of the fragmentation you get with it.

---

### Post by formaldehyde_spoon on 2010-09-22
> **fuzzylogic25 said:**
> I am still getting the conclusion that NTFS is more feature rich and possibly even more reliable.

However, it seems like XFS is a better choice over ext3/4 - is there a way to convert to XFS?

What are you actually doing with this system?  I'm getting the feeling it won't actually make any difference whether you use XFS, ext3, ext4, or NTFS....

---

### Post by prshah on 2010-09-22
If you are planning to use NTFS for a root "/", home "/home", "/etc", "/usr", "/boot" etc file system, this entire issue is academic: You can't.

If you are planning to use it as a shared file system on a dual boot, ntfs *might* be a better choice.

The filesystem limits in either case are not something that I will realistically approach.

Both ntfs and ext3/4 are journaled filesystems, which means that if they are not shut down cleanly, they will (on next boot) sync the journal and the actual filesystem. You can lose data only if the journal is corrupted or improperly (read: forcibly) flushed. The potential for data loss is equal in either filesystem.

Ext2 was NOT a journaled filesystem, and thus had equal potential for data loss as FAT (also not journaled).

When selecting a filesystem, I would look more at the IP/copyrights/patents angle than the performance angle. MS has already gone after TomTom for using linux's FAT implementation.

Hope this helps.

---

### Post by fuzzylogic25 on 2010-09-22
I need some help if anyone can assist me. I have created a new ext3 partition on a new hard disk. it will be used for data/backup purposes. Now under GParted, the space used so far is 30GB, even though I have not put any files on it yet.

Under the Folder properties for the drive, it says 93GB is used. 

Why are the two showing completely different used space sizes?

---

### Post by linux-hack on 2010-09-22
try a ```
tune2fs /dev/your_partition
```

---

### Post by oldos2er on 2010-09-22
I've never had any problems with either ext3 or ext4.

All file systems fragment; the difference between NTFS and ext* is that ext* fragmentation does not slow down file access unless or until the partition is nearly full. At least that's my understanding of it.

---

### Post by CharlesA on 2010-09-22
This has already been solved in another thread.

---

### Post by Bachstelze on 2010-09-22
NTFS is technically better, much more feature-rich and reliable. Of course, you'll have a problem if you want to use it on anything but Windows, but the same is true of ext if you want to use it on anything but Linux, so I guess it depends which OS you want to run. I know some people who are winning Win Server 2k8 just for the features of NTFS, and would have run Linux otherwise.

---

### Post by Roasted on 2010-09-22
I find NTFS to be inferior to EXT3 and 4. I'm a big fan and have had no issues with EXT3/EXT4. NTFS on the other hand I've had a few unfortunate situations with.

---

### Post by formaldehyde_spoon on 2010-09-22
> **Bachstelze said:**
> NTFS is technically better, much more feature-rich and reliable. ...

Not when it comes to fragmentation.

Why do you think it's more reliable?

---

### Post by Roasted on 2010-09-23
> **Bachstelze said:**
> NTFS is technically better, much more feature-rich and reliable. Of course, you'll have a problem if you want to use it on anything but Windows, but the same is true of ext if you want to use it on anything but Linux, so I guess it depends which OS you want to run. I know some people who are winning Win Server 2k8 just for the features of NTFS, and would have run Linux otherwise.

What kind of experience do you have when dealing with NTFS systems, EXT systems, etc? I deal with a wide variety of systems, different operating systems, etc. I won't lie - I had a very minor "lol" at the NTFS being more reliable comment. It's not that NTFS is unreliable, but I've *never* had a single file system issue with EXT3 or EXT4 in my years of running it. I'd have to use all fingers and toes to count NTFS issues I had along the way. Again I'm not saying NTFS is bad. For the few mishaps I had with it, I've also had a lot of success stories with it too. I just wouldn't dare say it's better...

---

### Post by perspectoff on 2010-09-23
It was NTFS that made me switch to Debian/Ubuntu/Kubuntu in the first place.

When I had a motherboard die and had to replace it, my Windows OS locked all my files using NTFS so that I could not access any of my business files. Until I paid Micro$oft another $200 for a new key (I was using a Pro version), they kept the NTFS files locked.

This happened to lots and lots of users a few years ago and caused a huge outcry.

The problem I have now with NTFS is file permissions from Linux.

NTFS does not allow Linux users to change file permissions (using Samba) very easily, and permissions are quite quirky. While I can store, access, and change files on an NTFS partition from Ubuntu, it is a quirky process for anything complex.

I now never do it (except, perhaps on consumer NAS that happen to use NTFS). That doesn't mean I like FAT32 (vfat), instead, where there are also quirks (such as 2 Gb file limits, which is a difficult limit to workaround, despite claims to the contrary). 

So, yes, I now use ext3 or ext4 for all my shared partitions. I have personally never had a problem with ext4, but neither have I noticed a significant differences in performance when changing from ext3 to ext4. 

Moving to ext4 made me update my GParted utility to a version that recognizes ext4, though, and my Grub Legacy version, too. Also, there are a few very old programs that don't recognize ext4, but I have since updated all of them, too. For the most part I am now all ext4.

My 2 cents can't buy an egg, however.

---

### Post by sydbat on 2010-09-23
> **perspectoff said:**
> When I had a motherboard die and had to replace it, my Windows OS locked all my files using NTFS so that I could not access any of my business files. Until I paid Micro$oft another $200 for a new key (I was using a Pro version), they kept the NTFS files locked.Had that happen too. Extremely frustrating.

As a side note, built a box for a customer, had some hardware problems (turned out to be a bad HDD), threw my HDD (10.04) into the new box (completely different specs) to test, booted no problem with full access to everything. Can't do that with Windows.

---

### Post by Roasted on 2010-09-23
> **sydbat said:**
> 
As a side note, built a box for a customer, had some hardware problems (turned out to be a bad HDD), threw my HDD (10.04) into the new box (completely different specs) to test, booted no problem with full access to everything. Can't do that with Windows.

Right... I remember hearing users talk about this. Is this because Windows "attaches" itself to the hardware whereas Linux probes it upon each boot to select the proper drivers preloaded in the kernel, etc.? 

I know XP is a BEAR with going from PC to PC with the same hard drive, even if the hardware is nearly identical. What about Windows 7 though? I wonder if that exhibits the same issues.

---

### Post by sydbat on 2010-09-23
> **Roasted said:**
> Right... I remember hearing users talk about this. Is this because Windows "attaches" itself to the hardware whereas Linux probes it upon each boot to select the proper drivers preloaded in the kernel, etc.?I think so. I remember changing out a DVD-RW in XP, and XP complained bitterly that I was changing the whole hardware system.

> I know XP is a BEAR with going from PC to PC with the same hard drive, even if the hardware is nearly identical. What about Windows 7 though? I wonder if that exhibits the same issues.Not sure about Win7. I'm sure it is the same, as Microsoft wants you to pay for a new copy of Windows for each machine you use.

---

### Post by CharlesA on 2010-09-24
> **perspectoff said:**
> It was NTFS that made me switch to Debian/Ubuntu/Kubuntu in the first place.

When I had a motherboard die and had to replace it, my Windows OS locked all my files using NTFS so that I could not access any of my business files. Until I paid Micro$oft another $200 for a new key (I was using a Pro version), they kept the NTFS files locked.

You can take ownership of the files on an NTFS partition as long as you are running a "non-home" version of Windows.

That's basically the same thing you do in Linux by using chown.

> **sydbat said:**
> Not sure about Win7. I'm sure it is the same, as Microsoft wants you to pay for a new copy of Windows for each machine you use.

It only requires you to reactivate if enough hardware changes in yer machine (mobo swap, etc).

---

### Post by MasterNetra on 2010-09-24
Been Using Ext4 and never have had any problems with it. Any issue I've had has been with a App or the system itself. Also Ext3 & 4 are faster then NTFS. Plus that 32,000 sub-folder limit for ext3 is not worth worrying about. After all if your nearing it for some reason you can try using a few folders to split it up/organize or just store the 32,000 in a different folder perhaps 31,999 could go into one of the other sub-folders, but really I doubt you will actually run into the limit anyway. And even if you do its nothing a little bit of re-organization couldn't fix.

---

### Post by deewatsa on 2010-09-24
In time and experience I found NFS-Plus is faster and more reliable than NTFS and ext4.

---

