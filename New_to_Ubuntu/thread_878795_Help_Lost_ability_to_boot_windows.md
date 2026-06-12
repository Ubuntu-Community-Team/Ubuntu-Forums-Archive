---
title: "Help: Lost ability to boot windows"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by aseemmehta on 2008-08-03
I'm trying to install ubuntu (7.10) on my IBM-PC (512 Mb RAM, pentium) in the dual boot mode. The download of ubuntu was good (I checked MDSUM) and enough of the operating system has been burned on the CD to allow ubuntu to boot up from the live CD (I'm posting this from ubuntu.)

However, installation to the HD has failed twice (most likely due to bad burn.) I was installing guided using 'freed space.' I cannot start up XP anymore (I can see the BIOS and boot up ubuntu using the live CD.)  Also, OpenOffice (for instance) does not start up properly in ubuntu.

I tried this method: ([http://www.arsgeek.com/?p=3340](http://www.arsgeek.com/?p=3340)) to fix windows MBR and here is what fdisk says:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

Device Boot Start End Blocks Id System
/dev/sda1 1 3934 31599823+ 7 HPFS/NTFS
/dev/sda2 9230 9730 4024282+ 12 Compaq diagnostics
/dev/sda3 3935 6440 20129445 83 Linux
/dev/sda4 6441 9229 22402642+ 5 Extended
/dev/sda5 9042 9229 1510078+ 82 Linux swap / Solaris
/dev/sda6 * 6441 8927 19976764+ 83 Linux
/dev/sda7 8928 9041 915673+ 82 Linux swap / Solaris

Partition table entries are not in disk order

Still no luck unfortunately.  Anything else I can do to allow the PC to be rebooted with XP?

Thanks.

---

### Post by aseemmehta on 2008-08-03
> **aseemmehta said:**
> I'm trying to install ubuntu (7.10) on my IBM-PC (512 Mb RAM, pentium) in the dual boot mode. The download of ubuntu was good (I checked MDSUM) and enough of the operating system has been burned on the CD to allow ubuntu to boot up from the live CD (I'm posting this from ubuntu.)

However, installation to the HD has failed twice (most likely due to bad burn.) I was installing guided using 'freed space.' I cannot start up XP anymore (I can see the BIOS and boot up ubuntu using the live CD.)  Also, OpenOffice (for instance) does not start up properly in ubuntu.

I tried this method: ([http://www.arsgeek.com/?p=3340](http://www.arsgeek.com/?p=3340)) to fix windows MBR and here is what fdisk says:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

Device Boot Start End Blocks Id System
/dev/sda1 1 3934 31599823+ 7 HPFS/NTFS
/dev/sda2 9230 9730 4024282+ 12 Compaq diagnostics
/dev/sda3 3935 6440 20129445 83 Linux
/dev/sda4 6441 9229 22402642+ 5 Extended
/dev/sda5 9042 9229 1510078+ 82 Linux swap / Solaris
/dev/sda6 * 6441 8927 19976764+ 83 Linux
/dev/sda7 8928 9041 915673+ 82 Linux swap / Solaris

Partition table entries are not in disk order

Still no luck unfortunately.  Anything else I can do to allow the PC to be rebooted with XP?

Thanks.

The correct arsgeek reference is : [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

### Post by northern lights on 2008-08-03
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by aseemmehta on 2008-08-03
> **northern lights said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Hmm...

In grub:

grub> find /boot/grub/stage1

Error 15: File not found

grub>

---

### Post by northern lights on 2008-08-03
Yup brainfart, not the most suiting tutorial.

From Ubuntu run```
gksu gedit /boot/grub/menu.lst
```

Is the Windows entry for (hd0,0)?

---

### Post by aseemmehta on 2008-08-03
> **northern lights said:**
> Yup brainfart, not the most suiting tutorial.

From Ubuntu run```
gksu gedit /boot/grub/menu.lst
```

Is the Windows entry for (hd0,0)?

Umm...

There is no /boot/grub.

```


ubuntu@ubuntu:~$ ls -ltr /boot
total 10075
-rw-r--r-- 1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r-- 1 root root 1764280 2007-10-14 21:39 vmlinuz-2.6.22-14-generic
-rw-r--r-- 1 root root  823535 2007-10-14 21:39 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root   75311 2007-10-14 21:39 config-2.6.22-14-generic
-rw-r--r-- 1 root root  424317 2007-10-14 21:39 abi-2.6.22-14-generic
-rw-r--r-- 1 root root 7124250 2007-10-15 19:26 initrd.img-2.6.22-14-generic.bak
ubuntu@ubuntu:~$ 


```

---

### Post by northern lights on 2008-08-03
Are you for real?

When booting, do you see the menu? I.e. is this a stage 1, 1.5 or 2 error?

---

### Post by aseemmehta on 2008-08-03
> **northern lights said:**
> Are you for real?

When booting, do you see the menu? I.e. is this a stage 1, 1.5 or 2 error?

When I go into the BIOS and boot from the CD-ROM with ubuntu Live CD, then I can boot.  When booting from HD, there is a '1962' error (the boot disk is not found or some such.)

What this means, I think, is that since there is no GRUB, there is no menu when I boot.

---

### Post by northern lights on 2008-08-03
Allright. Now I got you.

I somehow had figured the failed install was XP also and Ubuntu was running from the HDD.

However you wrote that you were getting an 'Error 15' from GRUB - how and when does this happen?

[http://ubuntuforums.org/archive/index.php/t-24113.html]("http://ubuntuforums.org/archive/index.php/t-24113.html") --> go with "wernst"

---

### Post by aseemmehta on 2008-08-03
> **northern lights said:**
> Allright. Now I got you.

I somehow had figured the failed install was XP also and Ubuntu was running from the HDD.

However you wrote that you were getting an 'Error 15' from GRUB - how and when does this happen?

[http://ubuntuforums.org/archive/index.php/t-24113.html]("http://ubuntuforums.org/archive/index.php/t-24113.html") --> go with "wernst"

When I do 'sudo grub' from a terminal (btw, 'which grub' results in /usr/sbin/grub.)

```

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

```

and then 

```


       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1 

Error 15: File not found

grub> 

```

Thanks.

---

### Post by aseemmehta on 2008-08-03
Please help...

> **aseemmehta said:**
> When I do 'sudo grub' from a terminal (btw, 'which grub' results in /usr/sbin/grub.)

```

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

```

and then 

```


       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1 

Error 15: File not found

grub> 

```

Thanks.

---

### Post by northern lights on 2008-08-03
Employ the [SuperGrubDisk]("http://www.supergrubdisk.org/")

---

### Post by alzie on 2008-08-03
What is the error when you try to boot into windows?

You may be able to correct the problem using your windows disk using the recovery tools.

Regarding the bad burn.  When you get going again try burning at a low speed.  I see many recommending 4X.  It takes a while but thats what I do.

I hoep this helps

---

### Post by geogur on 2008-08-03
i agree try xp disc this should work. and try super grub as advised earlier i just was on there site (super grub) looks like they can help .

---

### Post by northern lights on 2008-08-03
Come on. An XP disc?

Fine. Let's do this step by step. From the LiveCD post the output of ```
fdisk -l
```(that's a lower-case L)

Navigate to /boot/grub on the hdd and post the output of```
cd /media/sdXX/boot/grub && cat menu.lst
```

We'll take it from there.

---

### Post by aseemmehta on 2008-08-03
> **northern lights said:**
> Come on. An XP disc?

Fine. Let's do this step by step. From the LiveCD post the output of ```
fdisk -l
```(that's a lower-case L)

Navigate to /boot/grub on the hdd and post the output of```
cd /media/sdXX/boot/grub && cat menu.lst
```

We'll take it from there.

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3934    31599823+   7  HPFS/NTFS
/dev/sda2            9230        9730     4024282+  12  Compaq diagnostics
/dev/sda3            3935        6440    20129445   83  Linux
/dev/sda4            6441        9229    22402642+   5  Extended
/dev/sda5            9042        9229     1510078+  82  Linux swap / Solaris
/dev/sda6   *        6441        8927    19976764+  83  Linux
/dev/sda7            8928        9041      915673+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

```

However,

```


ubuntu@ubuntu:~$ sudo ls -l /media
total 0
ubuntu@ubuntu:~$ 


```

The only place where I find menu.lst is

```

ubuntu@ubuntu:~$ cd /
ubuntu@ubuntu:/$ sudo find . -name menu.lst -print
./usr/share/doc/grub/examples/menu.lst
./rofs/usr/share/doc/grub/examples/menu.lst
ubuntu@ubuntu:/$ 

```

Also 

```

ubuntu@ubuntu:~$ ls -ltr /boot
total 10075
-rw-r--r-- 1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root 1764280 2007-10-15 01:39 vmlinuz-2.6.22-14-generic
-rw-r--r-- 1 root root  823535 2007-10-15 01:39 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root   75311 2007-10-15 01:39 config-2.6.22-14-generic
-rw-r--r-- 1 root root  424317 2007-10-15 01:39 abi-2.6.22-14-generic
-rw-r--r-- 1 root root 7124250 2007-10-15 23:26 initrd.img-2.6.22-14-generic.bak
ubuntu@ubuntu:~$ 

```


Thanks.

---

### Post by alzie on 2008-08-03
I googled "boot error 1962" and came up with this: [http://techrepublic.com.com/5208-11196-0.html?forumID=78&threadID=167590&messageID=1712242](http://techrepublic.com.com/5208-11196-0.html?forumID=78&threadID=167590&messageID=1712242)
> A hard disk drive boot error (error codes 1962 ...
    A hard disk drive boot error (error codes 1962 and I999030X) can be caused by the following:

    CAUSE ACTIONS
    The start-up drive is not in the boot
    sequence in configuration. Check the configuration and ensure the start-up drive is in the boot sequence.

    No operating system installed on the boot drive.

    Install an operating system on the boot drive.

    The boot sector on the start-up drive is corrupted.

    The drive is defective. Replace the hard disk drive.

    [http://www-1.ibm.com/support/docview.wss?rs=0&q1=1962&uid=psg1DDSE-43XNPV&loc=en_US&cs=iso-8859-1&cc=us&lang=en](http://www-1.ibm.com/support/docview.wss?rs=0&q1=1962&uid=psg1DDSE-43XNPV&loc=en_US&cs=iso-8859-1&cc=us&lang=en) 


I'd check the BIOS and make sure that the correct hard drive is being looked for.  I read one instance where the poster removed that hard drive and replaced it again and it booted.  You can probably boot the disk if you have a startup disk (like the floppies we made for win98 )

Either way when you get access to this drive I'd start backing up everything of importance if you haven't already as you may require a new hard drive.

I really hope I'm mistaken in this

---

### Post by kansasnoob on 2008-08-03
> **aseemmehta said:**
> ```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3934    31599823+   7  HPFS/NTFS
/dev/sda2            9230        9730     4024282+  12  Compaq diagnostics
/dev/sda3            3935        6440    20129445   83  Linux
/dev/sda4            6441        9229    22402642+   5  Extended
/dev/sda5            9042        9229     1510078+  82  Linux swap / Solaris
/dev/sda6   *        6441        8927    19976764+  83  Linux
/dev/sda7            8928        9041      915673+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

```

However,

```


ubuntu@ubuntu:~$ sudo ls -l /media
total 0
ubuntu@ubuntu:~$ 


```

The only place where I find menu.lst is

```

ubuntu@ubuntu:~$ cd /
ubuntu@ubuntu:/$ sudo find . -name menu.lst -print
./usr/share/doc/grub/examples/menu.lst
./rofs/usr/share/doc/grub/examples/menu.lst
ubuntu@ubuntu:/$ 

```

Also 

```

ubuntu@ubuntu:~$ ls -ltr /boot
total 10075
-rw-r--r-- 1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root 1764280 2007-10-15 01:39 vmlinuz-2.6.22-14-generic
-rw-r--r-- 1 root root  823535 2007-10-15 01:39 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root   75311 2007-10-15 01:39 config-2.6.22-14-generic
-rw-r--r-- 1 root root  424317 2007-10-15 01:39 abi-2.6.22-14-generic
-rw-r--r-- 1 root root 7124250 2007-10-15 23:26 initrd.img-2.6.22-14-generic.bak
ubuntu@ubuntu:~$ 

```


Thanks.

Well, you have only one hard drive, sda1 and sda2 are related to Windows/Compaq, sda3 appears to be a Linux primary partition, and sda4 is an extendedm partition that contains two swaps and another Linux OS.

How many Linux operating systems are you trying to run and what are they?

---

### Post by bwainscott on 2008-08-03
As much as I hate to admit this, I use the FIXBOOT and FIXMBR command under recovery console in XP when it won't boot.  This usually helps GRUB find my WIN drive.

---

### Post by bpowell2005 on 2008-08-03
IMHO, I'd get Windows running smooth again, and then try to install Ubuntu with a fresh burned CD. Put your XP disk in, boot from CD, go to the recovery console, select the C: drive, run fixmbr and fixroot; this should rebuild your master boot record and your root partition. After these commands, you should be able to boot into Windows no problem. Then re-burn your Ubuntu disc and try the installation again.

---

### Post by bpowell2005 on 2008-08-03
Bwainscott,

We must have been typing at the same time! 

No shame in using the Windows tools to repair a Windows installation! Sure, you could hammer a nail into a wall with a bunch of Ubuntu CD's, but a hammer is the correct tool.

---

### Post by aseemmehta on 2008-08-04
> **bpowell2005 said:**
> Bwainscott,

We must have been typing at the same time! 

No shame in using the Windows tools to repair a Windows installation! Sure, you could hammer a nail into a wall with a bunch of Ubuntu CD's, but a hammer is the correct tool.

The multiple Linux partitions are due to the multiple attempts at installing ubuntu on the HD from the bad live CD using "installing guided using 'freed space.'"

The other complication here is that I don't have the Windows XP CD!

<sigh>

---

### Post by Malac on 2008-08-04
Try running the LiveCD open Partition Editor and change the boot flag to on for /dev/sda3 turn off the boot flag on /dev/sda6 try rebooting and see if that partition is bootable.
Some BIOS won't boot from any partition higher than /dev/sda4 e.g. extended partitions.

Hope this helps.

---

### Post by muteXe on 2008-08-04
You said in your first post:
> **aseemmehta said:**
>  The download of ubuntu was good (I checked MDSUM) and enough of the operating system has been burned on the CD to allow ubuntu to boot up from the live CD 
Thanks.
but then keep saying you have a bad live cd.  How is it bad if if your checksum was fine?  And what do you mean when you say "enough of the OS has been burned on to the CD"?

---

### Post by alzie on 2008-08-04
If you can access a computer do D/L and burn there s the Ultimate Boot CD (UBCD)here :[http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

It has several boot manager programs (including super grub disk) and hopefully one of these will allow you to repair your MBR or at least boot the windows sector to get any important files off.

I've been looking and I did find another reference to removing the hard drive and cable and inspecting them for corrosion.  It appears that if a small amount of corrosion occurs it can cause the problem and simply removing the drive and cable and reassembling may solve the problem.

I just went through this with my wife's windows only comp.  We used puppy to recover what we could and I ended up wiping the HDD by writing the entire disk to zeros and doing a fresh format and install.  I have a copy of UBCD that gave me the tools to do this.  At the next sign of problems she will be getting a new drive or a new comp, what ever we can afford at that time.

<edit> If you have a floppy drive, here is an option to create a boot floppy/cd: [http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

---

### Post by aseemmehta on 2008-08-05
> **muteXe said:**
> You said in your first post:

but then keep saying you have a bad live cd.  How is it bad if if your checksum was fine?  And what do you mean when you say "enough of the OS has been burned on to the CD"?

The download of ubuntu on the Windows partition was ok (confirmed via checksum) but I suspect that the live CD burn was not ok.  While I can boot the computer up using the liveCD, my two attempts at installing ubuntu as an OS on the HD have failed.  Also, not all ubuntu features (such as openOfiice) are available via live CD.  I suspect that the failed installation has also caused the problems with the MBR such that I cannot boot up with XP.

---

### Post by aseemmehta on 2008-08-09
> **aseemmehta said:**
> The download of ubuntu on the Windows partition was ok (confirmed via checksum) but I suspect that the live CD burn was not ok.  While I can boot the computer up using the liveCD, my two attempts at installing ubuntu as an OS on the HD have failed.  Also, not all ubuntu features (such as openOfiice) are available via live CD.  I suspect that the failed installation has also caused the problems with the MBR such that I cannot boot up with XP.

Another thing to note.  On the filesystem, I found the location of BOOT.INI.  It is in the directory /media/IBM_PRELOAD and the content is:

```


[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Home Edition" /fastdetect



```

---

### Post by SlalomMan on 2008-08-09
I'm no pro at this, but I would try booting from the Ubuntu LiveCD and getting rid of all those ext2 and swap file systems using the Partition Editor, then installing in the free space. My BIOS will only allow four primary partitions, and it looks like you went way over that. I would do this:

Delete the linux partitions.

Make an extended partition in the free space.
Make an ext2 or ext3 partition in all but 1GB (or 512MB, depending on how much space you have) of the free space.
Make the rest of the extended partition a swap partition.

Go to install ubuntu.
When pointed to partitioning, select "manual" and then mount the ext partition as "/" and then select "use swap" or some similar option.

Install; that *should* work. But I've never had this kind of problem.

---

