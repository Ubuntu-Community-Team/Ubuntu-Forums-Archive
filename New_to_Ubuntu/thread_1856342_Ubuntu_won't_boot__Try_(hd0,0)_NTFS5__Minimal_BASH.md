---
title: "Ubuntu won't boot | Try (hd0,0): NTFS5: | Minimal BASH-like line editing is supported"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by deckerry on 2011-10-08
I have an HP computer with Vista Ultimate. I installed Ubuntu 10.04 LTS via CD directly within Windows (without partitioning the hard drive I think.) It was working fine for months and out of nowhere, right when I need it for college, I can't boot into Ubuntu anymore. Very confusing.

Grub seems to be 1.98

I get the following errors:
```
Try (hd0,0): NTFS5
```
and
```
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.
```

I will attach images of the errors shortly.

Can somebody help me get back into Ubuntu? I have files stuck on there for my homework.

---

### Post by deckerry on 2011-10-08
[IMG]http://dl.dropbox.com/u/43610008/UbuntuError1.jpg[/IMG]
[IMG]http://dl.dropbox.com/u/43610008/UbuntuError2.jpg[/IMG]

---

### Post by Rubi1200 on 2011-10-08
Hi,
when you get the grub> prompt please type in ls and post back here with the output.

I also recommend that you post the results of the boot info script so we can get a better idea of what is going on.

There is a link at the bottom of my post with instructions.

---

### Post by deckerry on 2011-10-08
At the grub after entering ls, I get this:
```
(hd0) (hd0,2) (hd0,1)
```

Here are the results of the boot info script:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => HP/Gateway is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /boot/bcd /wubildr /ubuntu/winboot/wubildr 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOT/BCD

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   292,093,829   292,093,767   7 NTFS / exFAT / HPFS
/dev/sda2         292,093,830   312,576,704    20,482,875   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mmcblk0p1   7481-7F9B                              vfat       NO LABEL
/dev/sda1        6EE20EF3E20EBEF9                       ntfs       
/dev/sda2        2C88743C8874071C                       ntfs       HP_RECOVERY

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)




```

I'm guessing you're probably going to suggest that I look at Problem #2 Solution #1 in the Wubi Megathread, right?

If so, could you please tell me the correct code to enter here anyway just to make sure I don't screw something up?

---

### Post by Rubi1200 on 2011-10-09
Thanks for the results.

Actually, I am more concerned that the script is not showing the root.disk which Wubi needs to boot.

This blog post by forum member bcbc, a Wubi expert, should help you find and restore the root.disk:
[http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

If you have any questions or run into difficulties, let us know.

---

### Post by deckerry on 2011-10-09
I ran Vista's disk checker and it told me everything was fine. But that's obviously not right because Ubuntu still won't boot. So I continued the next steps...

     I couldn't access the directory [COLOR="Red"]C:\found.000[/COLOR] without the command prompt, so that's the first thing I did after using the disc check thing.

     I found 2 files and 1 directory:
[COLOR="red"]dir0000.chk
file0000.chk
file0001.chk[/COLOR]

     The directions here ([http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html]("http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html")) told me to move [COLOR="red"]file0000.chk[/COLOR] to [COLOR="Red"]C:\ubuntu\disks[/COLOR] but it also told me to move [COLOR="red"]dir0000.chk[/COLOR] to [COLOR="red"]C:\ubuntu[/COLOR].

I didn't know what to do, so I just moved [COLOR="Red"]dir0000.chk[/COLOR] first with this command:
```
C:\found.000>move dir0000.chk \ubuntu\disks
```
Then I restarted my computer with my fingers crossed, booting into Ubuntu, and received the same errors in the first post and restarted my computer, booting into Vista.

     Still confused, I moved [COLOR="Red"]file0000.chk[/COLOR], thinking that maybe I should have done that instead. I used this command:
```
C:\found.000>move file0000.chk \ubuntu\disks\root.disk
```
I restarted again, booting into Ubuntu with my fingers crossed and I was disappointed again. Same error messages as in the first post appeared again.

     After all that, I ran the disc check again, but that didn't help anything.

     Now, I'm officially stumped. While trying to fix this problem, I noticed another directory looking similar to [COLOR="red"]found.000[/COLOR], named [COLOR="red"]found.001[/COLOR].

     After looking at the directory [COLOR="red"]found.001[/COLOR] in the command prompt, I noticed that this directory also has a file named [COLOR="red"]dir0000.chk[/COLOR].

I'm so confused.

Anyways, I ran the bootscript again and here's the results:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => HP/Gateway is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /boot/bcd /wubildr /ubuntu/winboot/wubildr 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

sda1/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOT/BCD

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   292,093,829   292,093,767   7 NTFS / exFAT / HPFS
/dev/sda2         292,093,830   312,576,704    20,482,875   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mmcblk0p1   7481-7F9B                              vfat       NO LABEL
/dev/sda1        6EE20EF3E20EBEF9                       ntfs       
/dev/sda2        2C88743C8874071C                       ntfs       HP_RECOVERY

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1/Wubi

00000000  7b 0d 0a 20 20 20 22 61  70 70 73 5f 70 72 6f 6d  |{..   "apps_prom|
00000010  6f 5f 63 6f 75 6e 74 65  72 22 3a 20 31 31 2c 0d  |o_counter": 11,.|
00000020  0a 20 20 20 22 61 75 74  6f 66 69 6c 6c 22 3a 20  |.   "autofill": |
00000030  7b 0d 0a 20 20 20 20 20  20 22 65 6e 61 62 6c 65  |{..      "enable|
00000040  64 22 3a 20 66 61 6c 73  65 0d 0a 20 20 20 7d 2c  |d": false..   },|
00000050  0d 0a 20 20 20 22 62 6f  6f 6b 6d 61 72 6b 5f 62  |..   "bookmark_b|
00000060  61 72 22 3a 20 7b 0d 0a  20 20 20 20 20 20 22 73  |ar": {..      "s|
00000070  68 6f 77 5f 6f 6e 5f 61  6c 6c 5f 74 61 62 73 22  |how_on_all_tabs"|
00000080  3a 20 74 72 75 65 0d 0a  20 20 20 7d 2c 0d 0a 20  |: true..   },.. |
00000090  20 20 22 62 72 6f 77 73  65 72 22 3a 20 7b 0d 0a  |  "browser": {..|
000000a0  20 20 20 20 20 20 22 63  6c 65 61 72 5f 64 61 74  |      "clear_dat|
000000b0  61 22 3a 20 7b 0d 0a 20  20 20 20 20 20 20 20 20  |a": {..         |
000000c0  22 70 61 73 73 77 6f 72  64 73 22 3a 20 74 72 75  |"passwords": tru|
000000d0  65 2c 0d 0a 20 20 20 20  20 20 20 20 20 22 74 69  |e,..         "ti|
000000e0  6d 65 5f 70 65 72 69 6f  64 22 3a 20 34 0d 0a 20  |me_period": 4.. |
000000f0  20 20 20 20 20 7d 2c 0d  0a 20 20 20 20 20 20 22  |     },..      "|
00000100  73 68 6f 77 5f 68 6f 6d  65 5f 62 75 74 74 6f 6e  |show_home_button|
00000110  22 3a 20 74 72 75 65 2c  0d 0a 20 20 20 20 20 20  |": true,..      |
00000120  22 77 69 6e 64 6f 77 5f  70 6c 61 63 65 6d 65 6e  |"window_placemen|
00000130  74 22 3a 20 7b 0d 0a 20  20 20 20 20 20 20 20 20  |t": {..         |
00000140  22 62 6f 74 74 6f 6d 22  3a 20 37 31 35 2c 0d 0a  |"bottom": 715,..|
00000150  20 20 20 20 20 20 20 20  20 22 6c 65 66 74 22 3a  |         "left":|
00000160  20 35 34 2c 0d 0a 20 20  20 20 20 20 20 20 20 22  | 54,..         "|
00000170  6d 61 78 69 6d 69 7a 65  64 22 3a 20 74 72 75 65  |maximized": true|
00000180  2c 0d 0a 20 20 20 20 20  20 20 20 20 22 72 69 67  |,..         "rig|
00000190  68 74 22 3a 20 37 39 34  2c 0d 0a 20 20 20 20 20  |ht": 794,..     |
000001a0  20 20 20 20 22 74 6f 70  22 3a 20 31 2c 0d 0a 20  |    "top": 1,.. |
000001b0  20 20 20 20 20 20 20 20  22 77 6f 72 6b 5f 61 72  |        "work_ar|
000001c0  65 61 5f 62 6f 74 74 6f  6d 22 3a 20 37 34 30 2c  |ea_bottom": 740,|
000001d0  0d 0a 20 20 20 20 20 20  20 20 20 22 77 6f 72 6b  |..         "work|
000001e0  5f 61 72 65 61 5f 6c 65  66 74 22 3a 20 30 2c 0d  |_area_left": 0,.|
000001f0  0a 20 20 20 20 20 20 20  20 20 22 77 6f 72 6b 5f  |.         "work_|
00000200
```

---

### Post by bcbc on 2011-10-10
Windows will create new found.xxx directories for different recoveries. So found.001 is later than found.000. Look inside the dir0000.chk before moving - there should be a root.disk and swap.disk. 

If that fails, then note that the root.disk is between 5 and 30GB in size.

So you've copied some dir000.chk to \ubuntu\disks and renamed some chk000.chk file to root.disk but it's not the real root.disk, it's something else. Look in found.001 instead.

---

### Post by deckerry on 2011-10-10
Just now, I moved the dir0000.chk directory from c:\found.00[COLOR="Red"]1[/COLOR] (which was the only item in that folder), rebooted, and now I'm replying from Ubuntu. Now I have 3 questions.

1) What do I do with the old file and directory I moved from c:\found.00[COLOR="red"]0[/COLOR] earlier?

2) Should I delete the directories c:\found.000 and c:\found.001 since my stuff is recovered?

3) How do I prevent this whole thing from happening again?

---

### Post by jwbrase on 2011-10-10
> **deckerry said:**
> 3) How do I prevent this whole thing from happening again?

I'm going to give two bits of advice, one is more general, the other is specific to Ubuntu:

1) Backups, backups, backups.

2) Migrate your Ubuntu install from Wubi to a dedicated partition. Wubi isn't designed for long-term use, just for being an easy and easily reversible way for Windows users to install Ubuntu and try it out. Because of the way it's put together, it is especially vulnerable to data loss compared to an install on a dedicated partition. If you plan to be using Ubuntu in the long term, you really should have it on a dedicated partition.

That said: It's probably good to make a backup of any important data anywhere on your computer (Windows or Ubuntu) before migrating. Repartitioning a drive with data on it can be a bit dangerous. You don't normally need to worry about it, but "better safe than sorry" applies.

Also, having data on a dedicated partition makes data loss less likely to happen, but you can still have a hard drive crash, or have water spilled on your computer, or have a three year old playing with fridge magnets come a bit too close. See 1).

---

### Post by bcbc on 2011-10-10
> **deckerry said:**
> Just now, I moved the dir0000.chk directory from c:\found.00[COLOR="Red"]1[/COLOR] (which was the only item in that folder), rebooted, and now I'm replying from Ubuntu. Now I have 3 questions.

1) What do I do with the old file and directory I moved from c:\found.00[COLOR="red"]0[/COLOR] earlier?

2) Should I delete the directories c:\found.000 and c:\found.001 since my stuff is recovered?

3) How do I prevent this whole thing from happening again?

1) those files were recovered by chkdsk due to corruption. They could be anything - you'd have to examine them to see whether they are worth keeping. 

2) If you copied the directory from found.001 to \ubuntu\disks then there is no reason to keep found.001. (The root.disk is large and unless you are keeping it as a backup there's no point in leaving it lying around there).

3) First try to avoid hard shutdowns when using Wubi - it's particularly vulnerable to these as the virtual disk is a single file and losing it means everything on Ubuntu is gone. If the system is hanging use Alt+SysRq R-E-I-S-U-B instead to safely reboot.
But the best thing is - as suggested - to switch from a Wubi install to a normal dual boot. Either [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") or install fresh.

Whatever you choose, keeping data backed up is a good idea.

---

### Post by deckerry on 2011-10-11
Rubi1200, bcbc, and jwbrase,

Thank you so much for your help. It's easy to tell when somebody is very passionate about something they do. It amazes me how strong the Ubuntu community is when I see people are helping entirely out of passion instead of pay.

YOU GUYS ROCK!

---

### Post by Rubi1200 on 2011-10-11
You're more than welcome :-)

Glad things worked out and that you can enjoy the Ubuntu experience.

---

