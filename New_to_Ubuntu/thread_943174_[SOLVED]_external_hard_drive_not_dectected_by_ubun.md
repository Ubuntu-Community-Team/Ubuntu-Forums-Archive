---
title: "[SOLVED] external hard drive not dectected by ubuntu"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by nlindz2065 on 2008-10-09
Hello, I have a Seagate external hard drive that is not being detected by ubuntu.  I talked to Seagate but they don't offer any support for linux and say that the drive only works with Mac and windows.  Any ideas?  Can I use a program such as wine to be able to access or is all hope lost?

---

### Post by SunnyRabbiera on 2008-10-09
Hmm, what model are you using?
I know newer seagate's use NTFS, do you have ntfs3g installed?

---

### Post by christianvaldes on 2008-10-09
> **nlindz2065 said:**
> Hello, I have a Seagate external hard drive that is not being detected by ubuntu.  I talked to Seagate but they don't offer any support for linux and say that the drive only works with Mac and windows.  Any ideas?  Can I use a program such as wine to be able to access or is all hope lost?

Check out this link.

[http://ubuntuforums.org/showthread.php?t=678047](http://ubuntuforums.org/showthread.php?t=678047)

Please post if it helped.

---

### Post by Gregmond on 2008-10-09
Hmm I might be on the wrong track but.... If you open partition editor (df does it see it ?
What I am getting at is, does it have NTFS and you don't have ntfs3g installed or something like that ?
What file system is used on the external disk ?

---

### Post by nlindz2065 on 2008-10-15
Hello,
I apologize for taking so long but my drive was at work and I just brought it home so that I could work on it.  
I have discovered that I have a bigger more basic issue...... I don't understand how to function in linux.  I don't know how to use the terminal or where to go to find out if my seagate has ntfs.  I believe that it does because when I set if up in windows, I think i reformatted it from a Fat to Ntfs but I'm not sure.  Long story short, where do I go for the Linux 101 class?  can anyone send me a link to a thread that will help me learn some basic task?

---

### Post by jerome1232 on 2008-10-15
> **nlindz2065 said:**
> Hello,
I apologize for taking so long but my drive was at work and I just brought it home so that I could work on it.  
I have discovered that I have a bigger more basic issue...... I don't understand how to function in linux.  I don't know how to use the terminal or where to go to find out if my seagate has ntfs.  I believe that it does because when I set if up in windows, I think i reformatted it from a Fat to Ntfs but I'm not sure.  Long story short, where do I go for the Linux 101 class?  can anyone send me a link to a thread that will help me learn some basic task?

Ok with the drive plugged in can you post the output of the following command? It'll tell us if your computer is actually seeing the drive or not.

```
sudo fdisk -l
```

---

### Post by trikster_x on 2008-10-16
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)
this will help you learn to use the terminal.  It may take a while to learn some of this stuff, but it is worth it once you do.  How is your external hooked into your computer?  If it is through the usb port run in a terminal and then copy/paste results:
 lsusb

---

### Post by think13 on 2008-10-16
Here's some links to get you started:

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)
[http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338)

As for the hard drive, try installing the NTFS configuration tool.  Go to Applications -> Add/Remove.  Search for NTFS, check the box, and click Apply Changes.  Then run it (I think it's in Accessories) with the hard drive connected, and see what happens.  I haven't tried it for an external hard drive, but it worked like a charm for my windows partition.

---

### Post by nlindz2065 on 2008-10-19
Hello,
I do not see the seagate drive.  Here is what came up.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e0824

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2784    22362448+  83  Linux
/dev/sda2            2785        9729    55785712+   5  Extended
/dev/sda5            9567        9729     1309266   82  Linux swap / Solaris
/dev/sda6            2785        9401    53150989+  83  Linux
/dev/sda7            9403        9566     1317298+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by jerome1232 on 2008-10-19
> **nlindz2065 said:**
> Hello,
I do not see the seagate drive.  Here is what came up.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e0824

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2784    22362448+  83  Linux
/dev/sda2            2785        9729    55785712+   5  Extended
/dev/sda5            9567        9729     1309266   82  Linux swap / Solaris
/dev/sda6            2785        9401    53150989+  83  Linux
/dev/sda7            9403        9566     1317298+  82  Linux swap / Solaris

Partition table entries are not in disk order

It's not even getting picked up as a drive, what about this command?
(once again with the drive pluged in)

```
lsusb
```

---

### Post by nlindz2065 on 2008-10-19
> **trikster_x said:**
> [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)
this will help you learn to use the terminal.  It may take a while to learn some of this stuff, but it is worth it once you do.  How is your external hooked into your computer?  If it is through the usb port run in a terminal and then copy/paste results:
 lsusb
Trixster_x, does this make sense to you?

nefertari@nefertari-desktop:~$ lsusb
Bus 005 Device 003: ID 0bc2:0503 Seagate RSS LLC 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:0f11 Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by jerome1232 on 2008-10-19
Well it tells me it's seeing something called seagate connected to a usb port :p

I really am not sure why it's not being picked up as a drive though, does it have some silly software on it like U3? (I've seen that prevent Ubuntu from seeing the drive as a drive) In that case formating the drive from Windows should get it working.

---

### Post by nlindz2065 on 2008-10-19
> **jerome1232 said:**
> It's not even getting picked up as a drive, what about this command?
(once again with the drive pluged in)

```
lsusb
```

Jerome1232 I did not have the thing turned on......
nefertari@nefertari-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e0824

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2784    22362448+  83  Linux
/dev/sda2            2785        9729    55785712+   5  Extended
/dev/sda5            9567        9729     1309266   82  Linux swap / Solaris
/dev/sda6            2785        9401    53150989+  83  Linux
/dev/sda7            9403        9566     1317298+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeef844d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

---

### Post by Paqman on 2008-10-19
> **Gregmond said:**
> 
What I am getting at is, does it have NTFS and you don't have ntfs3g installed or something like that ?


That's only possible if the OP was running a really old version of Ubuntu. Ntfs-3g has been in the default install for a while now.

---

### Post by jerome1232 on 2008-10-19
Ah, that makes much more sense :) I'm willing to bet it wasn't safely removed the last time it was in a Windows computer, can you connect it to a Windows computer and then shutdown while it's connected?


If not let's try and mount it manually to see if it toss's any errors

```
sudo mkdir /media/external
sudo mount /dev/sdb1 /media/external -o umask=000
```

---

### Post by nlindz2065 on 2008-10-19
Okay... not sure if I did this right but this is what I got.
nefertari@nefertari-desktop:~$ sudo mkdir /media/external
nefertari@nefertari-desktop:~$ sudo mount /dev/sdbl /media/external -o umask=000
mount: special device /dev/sdbl does not exist

---

### Post by jerome1232 on 2008-10-19
The number 1, not the letter l, sdb1

---

### Post by nlindz2065 on 2008-10-19
I'm not always this dumb lol!
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/external -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/external ntfs-3g force 0 0

What does it mean when it says "you can use the 'force' option for
          your own responsibility."  Does that mean that it could or will wip my drive clean?

---

### Post by jerome1232 on 2008-10-19
No I was right though, about removing the device safely I would either:

the best option
a) just hook it up to a windows machine then select 'safely remove hardware' in the lower right, always do this when working in windows in the future :)

next best, but works fine if your lazy or don't have a Windows machine handy
b) use ntfsfix
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
```

the worst (if the filesystem was actually damaged when you removed the drive this can worsen it)
c) force the mount
```
sudo mount /dev/sdb1 /mount/external -o force,umask=000
```

edit: After doing this unmount it, and if you want reboot, the drive should appear in your places menu and you can auto mount it from there

```
sudo umount /dev/sdb1
sudo rmdir /media/external
```

---

### Post by nlindz2065 on 2008-10-19
Not lazy, windows pc died months ago boutght a everex from walmart (no windows).
nefertari@nefertari-desktop:~$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libntfs10
The following NEW packages will be installed:
  libntfs10 ntfsprogs
0 upgraded, 2 newly installed, 0 to remove and 17 not upgraded.
Need to get 391kB of archives.
After this operation, 950kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libntfs10 2.0.0-1ubuntu2 [122kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main ntfsprogs 2.0.0-1ubuntu2 [269kB]
Fetched 391kB in 3s (117kB/s)     
Selecting previously deselected package libntfs10.
(Reading database ... 97640 files and directories currently installed.)
Unpacking libntfs10 (from .../libntfs10_2.0.0-1ubuntu2_i386.deb) ...
Selecting previously deselected package ntfsprogs.
Unpacking ntfsprogs (from .../ntfsprogs_2.0.0-1ubuntu2_i386.deb) ...
Setting up libntfs10 (2.0.0-1ubuntu2) ...

Setting up ntfsprogs (2.0.0-1ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
nefertari@nefertari-desktop:~$ sudo ntfsfix /dev/sdb1
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS volume version is 3.1.
NTFS partition /dev/sdb1 was processed successfully.

Thank you so much for your help!

---

### Post by jerome1232 on 2008-10-19
Welcome glad I could help :)

Don't forget to mark the thread as solved (upper right, thread tools)
assuming that is your up and running with that drive now.

---

