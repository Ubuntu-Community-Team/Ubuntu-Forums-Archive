---
title: "Cannot Install - &quot;No root file system defined&quot;"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by Jeremini on 2012-02-19
Hello,

I got Ubuntu to run off of my USB drive, but I cannot get it to install onto my hard drive.

The installation guide shows a step where the user gets to choose  between "Install Ubuntu alongside Windows", "Replace Windows with  Ubuntu", or "Something else".

I don't get that option.  Instead I am just pushed into the partition  table, except all of the buttons, like "New Partition Table", "New  Partition", "Edit Partition", "Delete Partition" are grayed out.

If I try to continue, I get the error "No root file system defined"

I got the same problem with Ubuntu 11.10 and 10.04 LTS.

Another guy posted a video of the same problem on youtube if you want to know what I'm looking at.

[http://www.youtube.com/watch?v=l5cTNg0gs7A](http://www.youtube.com/watch?v=l5cTNg0gs7A)

Please keep in mind that I'm new to this, and don't really know what I'm doing.

Any ideas?

Thanks in advance

---

### Post by jimv on 2012-02-19
Well, if you're wanting to install it and keep Windows as well, you could try using the Wubi installer.  You won't have to worry about partitions: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by winh8r on 2012-02-19
There is a step by step thread here:

[http://ubuntuforums.org/showthread.php?t=1753447&highlight=root+file+system+defined]("http://ubuntuforums.org/showthread.php?t=1753447&highlight=root+file+system+defined")

closely related to your issue.

You did not say if you are actually installing alongside W*ndows (called Dual Booting) or doing a clean install of Ubuntu.

That thread should help you along in the right direction anyway.

Hope this helps you.

---

### Post by bcbc on 2012-02-19
The ubuntu installer will sometimes do this if you have minor partition table errors, or stray GPT partition table data when you're using a MBR partition table (e.g. if you're reusing a drive from a mac). It could also be some unsupported fakeraid setup.

I would select "Try Ubuntu" and then post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). That will likely have some answers.

---

### Post by Jeremini on 2012-02-20
Thanks for all the help.

Someone mentioned that I try Wubi.  That was actually what I wanted to do in the first place, but wound up with problems, so another forum member suggested that I try a straight install.  That thread is here

[http://ubuntuforums.org/showthread.php?p=11704273#post11704273](http://ubuntuforums.org/showthread.php?p=11704273#post11704273)

Sorry for not being clear, I am trying to dual-boot Windows and Ubuntu.  It's important to me that I do not lose my current Windows Operating System.

I ran the bootinfoscript.  The results are below:

```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================


sda: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 8440040 of /dev/sda for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

no valid partition table found
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda         0391-751C                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================== sda/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================== sda: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

=============== sda: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

no block devices found 

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected



```

 built this computer about 6 months ago and installed windows 7 on it.  It should not have any partitions on it. 

My computer has a single Seagate Barracuda ST31000524AS 1TB hard drive.

I'm still working through Winh8tr's suggestion.  I'm brand new at this so I'm trying to be careful and make sure I'm not screwing something up.

Thanks again

---

### Post by bcbc on 2012-02-20
Your internal drive is not present according to bootinfoscript. Why this might be, I have no idea. Somehow BIOS can see it, Windows can see it, but Ubuntu cannot? :confused:

---

### Post by Miljet on 2012-02-20
That error message usually means that you skipped a small, but important step. You have not defined the mount point for the partition. It should be "root", indicated by a single forward slash "/".

---

### Post by Jeremini on 2012-02-21
Neither GParted nor Disk Utility could "See" my Hard Drive.

I'm gonna see if I can get my hands on another hard drive.  Maybe that will solve my problem

Thanks for all your help

---

### Post by wildmanne39 on 2012-02-21
Hi, here is a link for when gparted cannot see your drive, I am not sure it will help.
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
Thanks

---

### Post by samitharansara on 2012-05-27
> **Miljet said:**
> That error message usually means that you skipped a small, but important step. You have not defined the mount point for the partition. It should be "root", indicated by a single forward slash "/".

Exactly.. If you are going to partition manually, you'd have to have at least 2 partitions.
1. Root (Mount point /)
2. Swap 

I'd go for the /boot as well.

---

### Post by wildmanne39 on 2012-05-27
Hi, actually it is not recommend to make /boot anymore on newer versions of ubuntu.
Thanks

---

