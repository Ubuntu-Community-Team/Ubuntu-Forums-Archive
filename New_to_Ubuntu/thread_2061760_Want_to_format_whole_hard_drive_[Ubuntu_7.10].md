---
title: "Want to format whole hard drive [Ubuntu 7.10]"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by tehforum on 2012-09-23
Hi,

I have been running on Ubuntu 7.10 out of sheer laziness, and I have now cleaned my computer.

However, I wish to wipe out the whole of the hard drive and install Ubuntu 12.04 which is in the form of an iso file on a usb stick.

At the moment, the computer is painfully slow, so this should fix the speed problems right?

I have gparted installed, and I have a 80gb partition which was used for windows xp which I which to delete... I can probably do that right now, by right clicking and delete, but I'll wait.

[IMG]http://i46.tinypic.com/2443bjm.png[/IMG]

All I can do for the main bit of the hard drive Ubuntu 7.10 is installed on is unmount it...

Please help.

---

### Post by OrangeCrate on 2012-09-23
> **tehforum said:**
> Hi,

I have been running on Ubuntu 7.10 out of sheer laziness, and I have now cleaned my computer.

However,** I wish to wipe out the whole of the hard drive and install Ubuntu 12.04** which is in the form of an iso file on a usb stick.

At the moment, the computer is painfully slow, so this should fix the speed problems right?

I have gparted installed, and I have a 80gb partition which was used for windows xp which I which to delete... I can probably do that right now, by right clicking and delete, but I'll wait.

<snip>

All I can do for the main bit of the hard drive Ubuntu 7.10 is installed on is unmount it...

Please help.

Go ahead and install 12.04. When the options pop up, choose the option to use the entire hard drive, and the original disk configuration will be erased and replaced with new partitions, associated with the 12.04 install.

---

### Post by blackened on 2012-09-23
The "main bit" of the hard drive can't be formatted because it's mounted (that's the partition the OS is currently booted from).

If there is no data you wish to save, boot from the 12.04 USB and the installer will ask you for partition settings. You can choose to use the entire disk from there, saving you the trouble of manually editing the partition table, though this is a useful thing to understand.

---

### Post by tehforum on 2012-09-23
Heh, before I read your posts, I deleted the 80gb partition... now I've got unallocated space of 81.94gb.

Will this matter when I put in the ubuntu 12.04 usb as it will ask for new partition settings as I wish to utilise the full 480gb or so of space

Cheers

---

### Post by hansolo4949 on 2012-09-23
Technically it wouldn't cause a ton of problems, except for the fact that 81GB of your HDD wouldn't be used for anything, even a partition. You will need to use Gparted (or the partition manager you are currently using) to resize the partition onto which you want to install ubuntu to include that space.

---

### Post by tehforum on 2012-09-23
> **hansolo4949 said:**
> Technically it wouldn't cause a ton of problems, except for the fact that 81GB of your HDD wouldn't be used for anything, even a partition. You will need to use Gparted (or the partition manager you are currently using) to resize the partition onto which you want to install ubuntu to include that space.

Hi,

Will I need to unmount /dev/sda1, then resize it to include the 80gb of unallocated space?

Thanks

---

### Post by blackened on 2012-09-23
In the installer, you can delete all partitions on the drive and choose to use the entire drive for the new install. Much simpler (and less time consuming) than growing the existing filesystem into the freed space.

---

### Post by GreatDanton on 2012-09-23
Also make sure that your computer is powerful enough to run Ubuntu 12.04, because 12.04 is really laggy on old machines.

---

### Post by tehforum on 2012-09-23
> **blackened said:**
> In the installer, you can delete all partitions on the drive and choose to use the entire drive for the new install. Much simpler (and less time consuming) than growing the existing filesystem into the freed space.

> **GreatDanton said:**
> Also make sure that your computer is powerful enough to run Ubuntu 12.04, because 12.04 is really laggy on old machines.

AMD Athlon 64 x2 Dual Core Processor 3800+ - got two of those

geforce 6100 nforce 430

and 2gb ram.

Is that good enough?


/sbin/init: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
username@usernamePC:~$ cat /proc/version
Linux version 2.6.22-16-generic (buildd@rothera) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Mon Jan 26 00:07:52 GMT 2009
username@usernamePC:~$

---

### Post by daslinkard on 2012-09-23
> **tehforum said:**
> AMD Athlon 64 x2 Dual Core Processor 3800+ - got two of those

geforce 6100 nforce 430

and 2gb ram.

Is that good enough?


/sbin/init: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
username@usernamePC:~$ cat /proc/version
Linux version 2.6.22-16-generic (buildd@rothera) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Mon Jan 26 00:07:52 GMT 2009
username@usernamePC:~$

I don't believe you will have any issue running 12.04 with the specs provided.  I definitely recommend the clean install of the OS as I have had issues in the past just by doing upgrades.

---

### Post by Hadaka on 2012-09-23
Hi, formatting a drive simply pushes the data to the outter edges
of the drive disc, its still there and with the right tools can be read or
recovered. the following command will wipe the drive by writeing zeros
across the entire drive and no data can be recovered, it also cleanes up
errors caused by use and time. but.WARNING WARNING...everything will
be wiped from the drive. So FIRST make sure you can boot from your USB
12.04 live usb and get a terminal...ctrl/alt/t.  when you are satisfied your ability
to boot from the usb is good. then...boot to the live usb, get a terminal  and issue
the command.

WARNING WARNING WARNING WARNING..THIS COMMAND WILL DELETE ALL
DATA FROM THE DRIVE....

```
dd if=/dev/zero of=/dev/sda conv=notrunc 
```You will now have a squeaky clean drive, like new to load your new OS.

this takes awhile so be patient.

---

### Post by blackened on 2012-09-24
Given that s/he's just going for a clean OS install, let's not muddy the waters by over-complicating things.

Zeroing the drive is not necessary (again read, handy thing to understand) unless you're concerned that someone will be doing forensic examination of data that existed on the drive before the clean install.

---

### Post by tehforum on 2012-09-25
Thanks for all the replies.

Other problems: 

[http://ubuntuforums.org/showthread.php?p=12259802#post12259802](http://ubuntuforums.org/showthread.php?p=12259802#post12259802)
[http://ubuntuforums.org/showthread.php?p=12259850#post12259850](http://ubuntuforums.org/showthread.php?p=12259850#post12259850)

---

