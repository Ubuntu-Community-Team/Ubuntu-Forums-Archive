---
title: "Entire hard drive now shows up as unallocated space in GParted"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Igniteflow on 2008-08-05
I previously had my 200GB hard drive partitioned into Linux, Swap and Windows partitions.  I'm not sure what exactly caused this, but at some point something changed.  Now when I open GParted, the drive is shown as /dev/sda 186.31GB unallocated space.  I am considering just doing a reinstall, but is there anyone who could save me and tell me how to get GParted to recognise the partitions again?  
I want the partitions to be recognised because it seems weird that they aren't, and also because I wanted to give the Windows partition a boot flag so it could be accessed from the GRUB menu.
I'm 99% Linus now, so not having Windows isn't killing me, but it does have its uses.

---

### Post by PmDematagoda on 2008-08-05
Do you mean that while the hard drive still is the same and Ubuntu and Windows works like they always did Gparted somehow lost sight of everything? Or is it that Ubuntu and Windows are not working either along Gparted?

---

### Post by caljohnsmith on 2008-08-05
If you boot a Live CD, make sure that no partitions on your HDD are mounted, and then run gparted, do you see your partitions on your HDD?

In case you don't know yet how to check for mounted partitions, in a terminal just run:
```
mount
```
and it will show you everything that's mounted. Also, if you run:
```
sudo fdisk -l
```
Does it show your partitions?

---

### Post by Igniteflow on 2008-08-12
Sorry for the delayed response.  I tried mount and sudo fdisk -l and they did show my partitions, although GParted still didn't register them.  Unfortunately, I had to get back into Vista for a work project, so I went ahead and did a full reinstall.  Thanks for the advice though, normally I would have tried to fix it rather than reinstalling.

---

### Post by hyper_ch on 2008-08-12
were those encrypted partitions?

---

### Post by Igniteflow on 2008-08-14
No, they were unencrypted

---

### Post by joomlamz on 2008-09-29
i try  but is not show....

---

### Post by Elim_Garak on 2008-10-10
I am having the exact same problem.  GParted cannot find my partitions on my first drive, but fdisk can.  GParted sees them as unallocated space, but the fact that I'm able to boot into all of them shows that this is not correct.

This is my sudo fdisk -l output:

```
omitting empty partition (5)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7eddbea0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29763   239071266    f  W95 Ext'd (LBA)
/dev/sda2   *       29126       29763     5124703+   c  W95 FAT32 (LBA)
/dev/sda3           29764       30401     5124735    c  W95 FAT32 (LBA)
/dev/sda5               1       28753   230958378   83  Linux
/dev/sda6           28754       29125     2988058+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000948a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

```

This is my mount output:

```
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/second type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/jason/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jason)
```

Oddly enough, I no longer have permission to unmount my second hard drive, either.

---

### Post by caljohnsmith on 2008-10-11
> **Elim_Garak said:**
> 

```
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7eddbea0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29763   239071266    f  W95 Ext'd (LBA)
/dev/[COLOR="Red"]sda2[/COLOR]   *       29126       29763     5124703+   c  W95 FAT32 (LBA)
/dev/sda3           29764       30401     5124735    c  W95 FAT32 (LBA)
/dev/sda5               1       28753   230958378   83  Linux
/dev/sda6           28754       29125     2988058+  82  Linux swap / Solaris



```

I think I see your problem: from above, notice that fdisk give an error that partition 5 (sda5) is empty, when of course you know it isn't. Also note that sda2 is within the sda1 extended partition, so it should not be labeled as sda2 since that would mean it is a primary partition; all logical partitions within an extended partition begin with sda5 and count up from there (sda6, sda7, etc). 

So Unfortunately the bottom line is that your HDD's partition table appears to be corrupt, and that's why gparted can't handle it correctly. You're best bet at this point is to try and recover your correct partition table with testdisk. To do that, first enable all your repositories in System > Prefs > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen if you would like help recovering your partitions. Let me know how it goes or if you run into problems. :)

---

### Post by Elim_Garak on 2008-10-12
> **caljohnsmith said:**
> I think I see your problem: from above, notice that fdisk give an error that partition 5 (sda5) is empty, when of course you know it isn't. Also note that sda2 is within the sda1 extended partition, so it should not be labeled as sda2 since that would mean it is a primary partition; all logical partitions within an extended partition begin with sda5 and count up from there (sda6, sda7, etc).

[FONT="Courier New"]Your diagnosis was right on the button.  I had been messing around with WinXP, which had not been previously installed on this system.  When I bought it (Vista loaded) I didn't even boot into Windows, and just overwrote it with Hardy, no problems.  The siren song of gaming got me, and XP did a number on my MBR and my partition table.

Fortunately, before I started tinkering, I read the HOWTO on backing up a system here, and did so.  I wiped XP, reinstalled Hardy and brought everything back from my tarball.

After that, I went through my UUIDs in all the relevant places, such as the grub menu, fstab, and so forth, and made sure everything matched,  because some of them had changed.  Now, everything is back the way it should be - by that, I mean, Windoze and all its traces are history, and Hardy is working exactly as before.  You know, it's nice not to have to import all my bookmarks and address books and all that extra rubbish manually!  Once again, Ubuntu Forums users saved by bacon, this time before the pan even got hot.  Thanks to all in this thread and the many others I went through![/FONT]

---

### Post by hyper_ch on 2008-10-12
you can try *gpart* to see if it can find (and restore) partitions on that drive.

---

### Post by caljohnsmith on 2008-10-12
Elim_Garak, I'm glad you got it all sorted out, and I'm glad I could help; cheers and have fun Ubuntu-ing. :)

---

### Post by Elim_Garak on 2008-10-13
> **caljohnsmith said:**
> Elim_Garak, I'm glad you got it all sorted out, and I'm glad I could help; cheers and have fun Ubuntu-ing. :)

[FONT="Courier New"]Oh yes, all is back to normal.  Let that be a lesson to me to not dabble in Windows!  It's absolutely amazing how useful a good backup can be.  It saved a lot of frustration, and all is as it should be.[/FONT]

---

### Post by blue_sky_10 on 2009-09-30
I have had a similar problem... What I did basically is that I formatted my C drive to a NTFS filesystem and installed the latest version of Ubuntu 9.04 Desktop version. I allocated 15 GB space to this new version. I dont know what went wrong but then I couldnt see the rest of my C drive. It showed unallocated space. So I deleted the newly created partition and now it shows me the WHOLE C drive as unallocated space. I went through many forums and read that testdisk might help. So I installed that but it still didnt show the C drive partition. I tried photorec also. Like I said I had formatted the drive so I dont need to retrive data. But I'm still baffled why GParted cant recognise my C Drive.
Please help!

---

### Post by BrokenPoet on 2009-10-03
I have had similar problems with Windows Vista eliminating my partition table.  My laptop has a single hard drive (/dev/sda) partitioned to contain Vista and Ubuntu 9.04 64-bit, as well as some  Dell recovery partitions.
   I recovered my partition table utilizing testdisk on the Parted Magic Live CD and reinstalled grub using grub-install, however GParted still sees the entire hard drive as unallocated.
   There is no effect on system operation, but I prefer to upgrade Ubuntu distributions through a fresh CD installation, and without GParted recognizing my partitions I am out of luck.
   /dev/sda3 contains the Vista partition, /dev/sda5 contains my / directory, and /dev/sda6 contains my /home directory.
   My output of fdisk -lu is as follows:
```
vince@Chimera:~$ sudo fdisk -lu /dev/sda

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      176714       88326    6  FAT16
/dev/sda2          178176    21149695    10485760    7  HPFS/NTFS
/dev/sda3   *    21149696   114370512    46610408+   7  HPFS/NTFS
/dev/sda4       114382800   625153409   255385305    f  W95 Ext'd (LBA)
/dev/sda5       114382863   153436814    19526976   83  Linux
/dev/sda6       153436878   615980293   231271708   83  Linux
/dev/sda7       615980358   619884069     1951856   82  Linux swap / Solaris
/dev/sda8       619898880   625139711     2620416    c  W95 FAT32 (LBA)

```
When I run gparted from the command line I get the following error:
```
vince@Chimera:~$ sudo gparted
======================
libparted : 1.8.8
======================
Can't have a partition outside the disk!

```

   Any suggestions on getting GParted to see my partitions properly again?

Edit 03OCT09 1950CST: I realized that my Logical Partition (sda4) was extended beyond the end of the disk causing GParted to ignore the partition table in its entirety.  Using the sfdisk technique found at [http://ubuntuforums.org/showthread.php?t=1120406]("http://ubuntuforums.org/showthread.php?t=1120406") I manually shrunk the offending partition by 11000 sectors causing it to fit inside the disk limit but with enough room for sda8 to remain unaffected.

---

### Post by M. Fawzy on 2009-11-24
same prob here ! after installing windows 7 ! I don't understand what to do now ?

---

### Post by defoe on 2010-06-23
I am having the same problems identified above.  Here is the result of running sfdisk:

defoe@defoe-1:~$ sudo sfdisk -l /dev/sda

Disk /dev/sda: 24321 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+     12-     13-    102400    7  HPFS/NTFS
		end: (c,h,s) expected (12,223,19) found (13,163,19)
/dev/sda2         12+  15678-  15666- 125831056    7  HPFS/NTFS
		start: (c,h,s) expected (12,223,20) found (13,163,20)
		end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sda3      18688+  23915-   5228-  41988240   83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,239,63)
		end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sda4      23915+  24321-    406-   3258360    f  W95 Ext'd (LBA)
		start: (c,h,s) expected (1023,254,63) found (1023,239,63)
		end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sda5      23915+  24321-    406-   3258328+  82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1023,239,63)
		end: (c,h,s) expected (1023,254,63) found (1023,239,63)

when I run fdisk I get the following:

Command (m for help): p

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52b32a0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       15679   125831056    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           18689       23916    41988240   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4           23916       24322     3258360    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5           23916       24322     3258328+  82  Linux swap / Solaris


I tried some of the suggested fixes without success.  I also used test disk and no success yet.  Any ideas suggestions are welcomed.


Thanks,

defoe

---

### Post by SoFl W on 2010-06-23
I had a similar problem last week, and I received a few suggestions [here]("http://ubuntuforums.org/showthread.php?t=1513919").  I couldn't find a simple solution and I wanted to do a fresh install, make a separate /home and /var directory so I ended up reformatting the drive, redoing all the partitions, and re-installing everything.  It wasn't fun, but it wasn't as painful as I thought.
 
See if any of the advice is different or if it helps.

---

