---
title: "Dual boot problem"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by jirico on 2012-01-25
Hello guys. I know this problem is common but I couldn`t find a solution looking at other threads. When I boot I just see the two windows xp I have installed but Ubuntu doesn`t appears. Here is my situation?


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb6 
                       and looks at sector 832649216 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files:        /grub/core.img

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    30,716,279    30,716,217   7 NTFS / exFAT / HPFS
/dev/sda2          30,716,280    78,220,484    47,504,205   f W95 Extended (LBA)
/dev/sda5          30,716,343    78,220,484    47,504,142   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   409,593,239   409,593,177   7 NTFS / exFAT / HPFS
/dev/sdb2         819,187,710   976,771,071   157,583,362   f W95 Extended (LBA)
/dev/sdb5         819,187,712   827,925,992     8,738,281  82 Linux swap / Solaris
/dev/sdb6         827,926,528   839,643,135    11,716,608  83 Linux
/dev/sdb7         839,645,184   956,829,695   117,184,512  83 Linux
/dev/sdb8         956,831,744   976,771,071    19,939,328  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        74B84BA3B84B632A                       ntfs       
/dev/sda5        A89492939492641A                       ntfs       Documentos
/dev/sdb1        9010A30310A2F000                       ntfs       
/dev/sdb5        f936b8fc-30e8-4670-8342-0405f6d17a97   swap       
/dev/sdb6        f5d329cb-ec51-4fc7-8a51-5fbd88237e8c   ext2       
/dev/sdb7        b9911d2c-2a74-4261-81aa-af4dc73dd0cf   ext4       
/dev/sdb8        f6d84aa0-1ac2-4f55-8589-9ca18766288a   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  1
               =                initrd.img-3.0.0-12-generic                    6
               =                vmlinuz-3.0.0-12-generic                       3

=============================== sdb8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb8 during installation
UUID=f6d84aa0-1ac2-4f55-8589-9ca18766288a /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb6 during installation
UUID=f5d329cb-ec51-4fc7-8a51-5fbd88237e8c /boot           ext2    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=b9911d2c-2a74-4261-81aa-af4dc73dd0cf /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=f936b8fc-30e8-4670-8342-0405f6d17a97 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  bd cb 1a b4 34 8c c6 36  6b 31 65 f4 69 b4 0b 32  |....4..6k1e.i..2|
00000010  b6 cd 86 b3 55 8c 7e 5b  77 0f 18 5d af 06 6f 21  |....U.~[w..]..o!|
00000020  d4 8c 95 55 b8 4d ad 87  92 87 57 a6 f2 3b 94 cb  |...U.M....W..;..|
00000030  67 b2 6d 5f 5d e8 7b d1  08 99 41 a8 48 ea 59 24  |g.m_].{...A.H.Y$|
00000040  98 29 39 42 b7 ac ab 35  20 00 05 c3 18 2c 41 40  |.)9B...5 ....,A@|
00000050  e7 00 49 a7 37 ce d6 58  4f d6 6c 9f 8c 07 4b 79  |..I.7..XO.l...Ky|
00000060  f0 a6 b6 8a 1c 70 f9 6b  d0 c9 c3 87 2d 38 5e 7e  |.....p.k....-8^~|
00000070  03 ac 2f f7 bb 9c b1 b3  f2 f1 70 fb 9b f7 13 14  |../.......p.....|
00000080  cd ac 75 54 85 a1 7e 1d  a8 53 57 89 48 25 24 e7  |..uT..~..SW.H%$.|
00000090  0d dd 7a d8 17 4c 47 89  ed 90 26 7d 76 23 5f cd  |..z..LG...&}v#_.|
000000a0  d7 b6 dc b9 75 57 62 35  b6 9e 86 9f 67 1f 8b b9  |....uWb5....g...|
000000b0  73 76 ec 98 a2 bd 19 8e  29 9d bc 1f 0f 3d 59 db  |sv......)....=Y.|
000000c0  5d 8a bf 8a d8 67 5e 6b  5c 71 dd 4c a6 24 44 06  |]....g^k\q.L.$D.|
000000d0  df 8a 26 77 f7 16 57 a6  6b 68 2e ae 83 11 16 40  |..&w..W.kh.....@|
000000e0  60 e5 48 0a 83 3a dc 64  4c ba b4 53 49 d2 2c 72  |`.H..:.dL..SI.,r|
000000f0  eb d7 07 31 2c 3c 89 31  82 e7 4a ce e3 0e 17 5a  |...1,<.1..J....Z|
00000100  a1 78 ef 13 62 7e f7 60  e7 2e 7e 5e 2a 41 d5 79  |.x..b~.`..~^*A.y|
00000110  c4 c8 6a 90 93 32 84 3c  6e 88 cc 32 ab 41 61 70  |..j..2.<n..2.Aap|
00000120  f1 78 27 34 68 52 5b b2  80 bb 54 92 22 74 50 3e  |.x'4hR[...T."tP>|
00000130  bd c5 9c b9 45 12 28 a2  9c d3 5b e2 f0 d9 31 3c  |....E.(...[...1<|
00000140  84 64 bc a0 96 b8 f4 e1  8f cf f5 3a 6d 7c 6a 3e  |.d.........:m|j>|
00000150  e5 35 31 ba 3e 94 6d a5  ad 86 1d 65 8c b2 78 1c  |.51.>.m....e..x.|
00000160  5d 1b 9c ad ed f4 11 cf  e3 24 9f d2 fb 06 ad 0e  |]........$......|
00000170  2a 06 c2 19 63 fb 0e 3c  cc 77 09 ab 5c a1 11 38  |*...c..<.w..\..8|
00000180  9e b8 7e 98 5b 3e aa 78  49 03 ce 09 f2 84 6a f6  |..~.[>.xI.....j.|
00000190  03 33 78 cf 46 11 10 0b  46 27 08 67 e8 ed e5 03  |.3x.F...F'.g....|
000001a0  ea 2a 21 9f ae 26 f9 68  8a 22 dd 21 8c 03 ae 58  |.*!..&.h.".!...X|
000001b0  d9 e2 c4 44 c1 f6 a2 b1  32 4a c9 4c 49 1b 00 fe  |...D....2J.LI...|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 0e db d4 02 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```Thanks for the help.

---

### Post by drs305 on 2012-01-25
Let's see if Grub can see the boot files. If it can, then we will know it's not a BIOS limitation.

At the Grub prompt, or if you get the Grub menu press 'c':

```
ls (hd1,6)/grub # Do you see lots of *.mod files
ls (hd1,6)/ # Do you see the kernel and initrd files?
```
If you get errors, try "ls" and make sure the (hd1) lists more partitions than (hd0). If (hd0) has more entries, use hd0 in the above commands.

If your system can see the files, we can then give you the commands to reinstall Grub from the LiveCD.

---

### Post by jirico on 2012-01-25
> **drs305 said:**
> Let's see if Grub can see the boot files. If it can, then we will know it's not a BIOS limitation.

At the Grub prompt, or if you get the Grub menu press 'c':

```
ls (hd1,6)/grub # Do you see lots of *.mod files
ls (hd1,6)/ # Do you see the kernel and initrd files?
```If you get errors, try "ls" and make sure the (hd1) lists more partitions than (hd0). If (hd0) has more entries, use hd0 in the above commands.

If your system can see the files, we can then give you the commands to reinstall Grub from the LiveCD.

Sorry for being a newbie, but I`m using the live Ubuntu CD now. How do I open the Grub prompt?

When I type grub it appears ~Ther program `grub` is currently not installed. You can install it by typing: sudo apt-get install grub

---

### Post by drs305 on 2012-01-25
When you boot, and you see the two Windows entries, are they located in the Grub menu? (Grub's menu will show the Grub version at the top of the screen; or it simply *won't* be the Windows bootloader).

Windows is still the bootloader in sda (which is good). Grub is (supposed to be) installed in the sdb MBR. Have you changed your BIOS so that sdb (500GB) boots first? Even if Grub is working, as your system stands your system needs to boot the sdb drive first to find the Grub files. The drive boot order is set by the BIOS, which you should be able to access during the early stages of the boot process by pressing a special key (often one of the Fn keys, or DEL).

---

### Post by jirico on 2012-01-25
> **drs305 said:**
> When you boot, and you see the two Windows entries, are they located in the Grub menu? (Grub's menu will show the Grub version at the top of the screen; or it simply *won't* be the Windows bootloader).

Windows is still the bootloader in sda (which is good). Grub is (supposed to be) installed in the sdb MBR. Have you changed your BIOS so that sdb (500GB) boots first? Even if Grub is working, as your system stands your system needs to boot the sdb drive first to find the Grub files. The drive boot order is set by the BIOS, which you should be able to access during the early stages of the boot process by pressing a special key (often one of the Fn keys, or DEL).

You are right. I just changed the BIOS because sdb wasn`t booting first. Now it appears `File not found` and below that it appears a prompt  with the message `Grub rescue>`. It doesn`t show any OS to load...

---

### Post by drs305 on 2012-01-25
> **jirico said:**
> You are right. I just changed the BIOS because sdb wasn`t booting first. Now it appears `File not found` and below that it appears a command line  with the message `Grub rescue>`. It doesn`t show any OS to load...

Now we have to do the sleuthing. I suspect your BIOS isn't seeing the files, but to confirm this run the "ls" commands I gave earlier and let us know what the system sees.

You can also try the Boot Repair tool - you can install and run it from the LiveCD and let it try to fix things although it won't fix a BIOS limit problem.  Link in my signature line.

---

### Post by jirico on 2012-01-25
> **drs305 said:**
> Now we have to do the sleuthing. I suspect your BIOS isn't seeing the files, but to confirm this run the "ls" commands I gave earlier and let us know what the system sees.

You can also try the Boot Repair tool - you can install and run it from the LiveCD and let it try to fix things although it won't fix a BIOS limit problem.  Link in my signature line.

I just ran the commands, it worked with hd0 and hd0 also has more entries when I type ls.

The first one 'ls (hd0,6)/grub' returned a lot fo .mod files like terminal.mod, pci.mod and probe.mod.

The second 'ls (hd0,6)/'  besides .mod gave me others like: terminal.lst, kernel.img. But I didn't see the initrd file.

I also remember an error with grub while finishing Ubuntu instalation, it asked me to choose another sdb, because sdb6 wasn't avalaible, I chose sdb7, but it seems it's  still in sdb6...

---

### Post by drs305 on 2012-01-25
> **jirico said:**
> I just ran the commands, it worked with hd0 and hd0 also has more entries when I type ls.
Ok, then as far as initial booting the system regards sdb (500GB) as hd0. Grub normally designates the system drive as hd0, so this makes sense.

> 
The first one 'ls (hd0,6)/grub' returned a lot fo .mod files like terminal.mod, pci.mod and probe.mod.
This is also good, in that the system is seeing the grub folder.

> 
The second 'ls (hd0,6)/'  besides .mod gave me others like: terminal.lst, kernel.img. But I didn't see the initrd file.
We are starting to get to a problem. (hd0,6)/ would in your case be the /boot folder. You should have kernels, initrds, but not the *.mod files which are normally in the grub folder.
Added: Actually, reviewing your RESULTS.txt, it *did* find the initrd file therein.

> 
I also remember an error with grub while finishing Ubuntu instalation, it asked me to choose another sdb, because sdb6 wasn't avalaible, I chose sdb7, but it seems it's  still in sdb6...
This means that we really don't know what we are dealing with. Partition 7 is supposed to be /home according to how fstab was initially set up. None of the root system files should be there.

What to do:
Since you got the error message during installation, my recommendation would be to simply reinstall. It would probably be faster and less prone to errors. However, if you have already placed data files within the installation or made lots of modifcations (doubtful since I think you've never been able to use it) or don't want to use the bandwidth this may not be what you want.

Your BIOS doesn't appear to be limited, so there isn't normally a lot of reason to have a separate /boot partition. You may have a reason for it, but if not, I'd just reformat the linux partitions [noparse] (sdb5,6,7,8) [/noparse] and reinstall with just /, /home and /swap. But that's up to you. 

Added: Since it did find the initrd file, there may be a better chance of a successful repair...

Before reinstalling, we could try to reinstall Grub on the slight chance that it will work thereafter, but I would expect the chances to be slim.

---

### Post by jirico on 2012-01-25
> **drs305 said:**
> Ok, then as far as initial booting the system regards sdb (500GB) as hd0. Grub normally designates the system drive as hd0, so this makes sense.


This is also good, in that the system is seeing the grub folder.


We are starting to get to a problem. (hd0,6)/ would in your case be the /boot folder. You should have kernels, initrds, but not the *.mod files which are normally in the grub folder.
Added: Actually, reviewing your RESULTS.txt, it *did* find the initrd file therein.


This means that we really don't know what we are dealing with. Partition 7 is supposed to be /home according to how fstab was initially set up. None of the root system files should be there.

What to do:
Since you got the error message during installation, my recommendation would be to simply reinstall. It would probably be faster and less prone to errors. However, if you have already placed data files within the installation or made lots of modifcations (doubtful since I think you've never been able to use it) or don't want to use the bandwidth this may not be what you want.

Your BIOS doesn't appear to be limited, so there isn't normally a lot of reason to have a separate /boot partition. You may have a reason for it, but if not, I'd just reformat the linux partitions [noparse] (sdb5,6,7,8) [/noparse] and reinstall with just /, /home and /swap. But that's up to you. 

Added: Since it did find the initrd file, there may be a better chance of a successful repair...

Before reinstalling, we could try to reinstall Grub on the slight chance that it will work thereafter, but I would expect the chances to be slim.

Got it. I will reinstall without /boot partition. But what partition do I choose then to put on `Device for boot loader installation` option?

---

### Post by drs305 on 2012-01-25
> **jirico said:**
> Got it. I will reinstall without /boot partition. But what partition do I choose then to put on `Device for boot loader instalation` option?

Since you have decided to reinstall, I'd recommend making your partitions before you install. It's not required, but it may be easier to see what you are doing if you use Gparted and then select 'Manual partitioning'.  If you allowed Ubuntu to create the partitions the first time and are comfortable with the process don't let me convince you otherwise.

Now to your question...

When you are asked to install Grub, select the same **drive** as you are installing on. Choose the drive, *not* the partition. This will allow Grub to write to the MBR of the drive, and point to the files on the Ubuntu partition. It looks like you installed Grub to a partition the first time, but you should only install to sdX (sdb probably) and not sdXY (a partition).

By selecting your Ubuntu drive, it should leave your other drive alone. This could be helpful in the future if Grub fails, since you could change the boot order to the other drive and you should get the Windows menu. You would then be able to use Windows until before you fix Grub/Ubuntu.

---

### Post by jirico on 2012-01-25
> **drs305 said:**
> Since you have decided to reinstall, I'd recommend making your partitions before you install. It's not required, but it may be easier to see what you are doing if you use Gparted and then select 'Manual partitioning'.  If you allowed Ubuntu to create the partitions the first time and are comfortable with the process don't let me convince you otherwise.

Now to your question...

When you are asked to install Grub, select the same **drive** as you are installing on. Choose the drive, *not* the partition. This will allow Grub to write to the MBR of the drive, and point to the files on the Ubuntu partition. It looks like you installed Grub to a partition the first time, but you should only install to sdX (sdb probably) and not sdXY (a partition).

By selecting your Ubuntu drive, it should leave your other drive alone. This could be helpful in the future if Grub fails, since you could change the boot order to the other drive and you should get the Windows menu. You would then be able to use Windows until before you fix Grub/Ubuntu.

I see. Just reinstalled and it works, thanks!! I chose sdb as the place to Grub( instead of a partition inside sdb ) and now worked! Now the WindowsXP in the same Ubuntu HD( sdb ) doesn't appear, grub just shows Windows XP in sda, any idea? I'm very grateful to you man, saved my day, I'm like 16 hours at this. Thanks!!

---

### Post by drs305 on 2012-01-25
Glad things are working better now. 

As for your Windows issue, you can try running "sudo update-grub" again but I don't think it will have any effect. I don't use Windows but from what I understand Grub looks for Windows boot files. Windows 'piggybacks' it's installations so it retains only one full set of boot files - usually on the original partition. 

If you select Windows from the Grub menu and it transfers control to the Windows bootloader I think Windows will then give you options for each Windows installation.

I think to get separate listings you would have to manipulate the Windows boot files and have some of them installed into your sdb Windows as well, but it's not something I'm familiar with. 

Happy Ubuntu-ing !

---

### Post by jirico on 2012-01-25
> **drs305 said:**
> Glad things are working better now. 

As for your Windows issue, you can try running "sudo update-grub" again but I don't think it will have any effect. I don't use Windows but from what I understand Grub looks for Windows boot files. Windows 'piggybacks' it's installations so it retains only one full set of boot files - usually on the original partition. 

If you select Windows from the Grub menu and it transfers control to the Windows bootloader I think Windows will then give you options for each Windows installation.

I think to get separate listings you would have to manipulate the Windows boot files and have some of them installed into your sdb Windows as well, but it's not something I'm familiar with. 

Happy Ubuntu-ing !

I will try it later! Thanks a lot!

---

