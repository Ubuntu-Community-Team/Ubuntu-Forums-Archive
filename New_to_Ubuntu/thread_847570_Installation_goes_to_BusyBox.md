---
title: "Installation goes to BusyBox"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by G0ggy on 2008-07-02
I'v checked the forums, but if this is a duplicate topic then I apologise.

I've downloaded the Ubuntu 64 ISO and burnt it to a DVD. MY system is:

RAID 0 partitioned:

Drive C: Windows Vista 64
Drive D: Ubuntu

When the system reboots or is restarted I get the option to start Vista or Ubuntu, the graphical Ubuntu image appears, I then get a black screen with:

BusyBox v1.1.3 (Debion 1:1.1.3-suBuntu12) Builtin Shell (Ash)

Any ideas how to proceed?

---

### Post by G0ggy on 2008-07-03
So I should just abandon Ubuntu?

---

### Post by natirips on 2008-07-03
I'm not sure when/why does busybox appear as I've never seen it myself. I usually get bash (not ash as you got it) to login to when I insist on using the textual (non-gui) user interface.

By the way, what do you mean by "Drive D: Ubuntu" (I'm not familiar with Vista, but XP wasn't able to see ext (linux) partitions so far as I remember)? Did you format it properly?

Or maybe just try CTRL+ALT+F7 at that black screen with busybox. If I'm not mistaken, BusyBox is a set to command-line tools.

---

### Post by G0ggy on 2008-07-03
Thank you for replying!

As you can guess, this is my very first time with Ubuntu, well first time with Linux actually, but I'm really keen to give it a try.

I will give the key combination a try tonight when I get home. I wrote "Drive D: Ubuntu" as that is where I told the installer to install it from the CD, hopefully that is right? I do get the choice of Windows Vista or Ubuntu when the system boots, sadly the Ubuntu never boots/completes installation.

The D partition was already formatted as NTFS is this incorrect?

---

### Post by natirips on 2008-07-03
> **G0ggy said:**
> Thank you for replying!

As you can guess, this is my very first time with Ubuntu, well first time with Linux actually, but I'm really keen to give it a try.

I will give the key combination a try tonight when I get home. I wrote "Drive D: Ubuntu" as that is where I told the installer to install it from the CD, hopefully that is right? I do get the choice of Windows Vista or Ubuntu when the system boots, sadly the Ubuntu never boots/completes installation.

The D partition was already formatted as NTFS is this incorrect?
DOS (and some older Windowses) used FAT16, later versions of Windowses used FAT32, and the lates use NTFS. Linux, however, is not Windows, it is a genuine operating system of it's own, and was built upon Unix, while Windows were built upon DOS. It uses ext file system. Ubuntu (as a distribution of Linux) uses ext3. Now, there are quite a few differencies between NTFS and ext3.

Although, Ubuntu probably reformatted it from NTFS into ext3 during installation proccess. You can check that easily by booting into Windows (if you can boot Windows), then checking if there is still a D: drive in your My Computer. If it is there, right click on it and select properties, and check it's filesystem type.

If it isn't there, that's also fine (I think, I'm not sure what Vista is alike as I've never used it).

If it either isn't in the My Computer, or you can't boot Windows, try using the following command in the busybox:
```
cat /etc/fstab
```Notice that you might need to log in before you can enter that command. It will list all drives adn some of their characteristics, like their filesystem. There should be at least one "NTFS" (for Windows) and one "ext3" (for linux). Most likely there will be one formatted as "swap"*.

*As linux prefers using swap as seperate partition to prevent swap fragmentation (usually files on your hard drive become fragmented (torn into pieces) after a while, and are thus slower). Note however, it you have enough RAM you don't really need swap on newer computers running Linux, but it is still recomended to make some small swap just for the sake of compatibility with some older programs.

Edit: Geebus, I wrote a whole essay... XD

---

### Post by G0ggy on 2008-07-03
Thanks again. I will try your suggestions tonight. One thing I know already:

I can still see the D drive from within Vista and browse the files, so from what you're saying the installation may not have gone correctly.

---

### Post by unutbu on 2008-07-03
G0ggy, please describe how you installed Ubuntu. Are you using Wubi? or did you boot from the LiveCD and launch the installer from there?

---

### Post by natirips on 2008-07-03
> **unutbu said:**
> G0ggy, please describe how you installed Ubuntu. Are you using Wubi? or did you boot from the LiveCD and launch the installer from there?

If he gets the options to start Vista or Ubuntu I guess it's a dual-boot.

---

### Post by unutbu on 2008-07-03
Yes, but then why can he see his Ubuntu installation from within Vista?

---

### Post by natirips on 2008-07-03
> **unutbu said:**
> Yes, but then why can he see his Ubuntu installation from within Vista?

Because he probably never was able to boot Ubuntu, because the installation went wrong with NTFS used instead of ext3. Although, I've never seen/used an Ubuntu installaion via Wubi, so I don't really know how exactly it works.

@G0ggy: But the question is good... How did you install Ubuntu? Did you install it under windows, or as a separate OS?

---

### Post by unutbu on 2008-07-03
G0ggy, assuming you are not using Wubi, please boot from your LiveCD. Select "Start or Install Ubuntu". 
Open a Terminal by Selecting Applications>Accessories>Terminal from the GNOME menu bar at the top of the screen. Then type (and please post the output of)
```

sudo fdisk -l
```
The output will show us if Ubuntu has been installed in a separate partition and what type of filesystem is on that partition.

---

### Post by G0ggy on 2008-07-03
Will do fellas.

My installation process was this:

Downloaded Ubuntu.
Burnt the ISO to a DVD.
Ran the executable in Windows Vista and pointed the installation path to the D drive.
Ubuntu ejected the DVD after the first part of the installation and said it would continue after rebooting, however, it didn't...

That's where I am up to...

---

### Post by unutbu on 2008-07-03
From your description, I think you are using Wubi. 
Unfortunately, I know next to nothing about Wubi, nor RAID 0. I also have no direct experience with 64-bit Ubuntu. Put the three together and I'm pretty much clueless.

The web page
[https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b](https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b)
states 
> 
Common problems in Wubi 8.04:

      Software raid arrays and encrypted disks are not supported at the moment, you have to install into a normal partition. Note that some "hardware" raids, are in fact software ones. Windows ME is not supported. This should be addressed in Wubi 8.10.



These pages address how to install Ubuntu from the LiveCD, rather than thru Wubi, when you are also using raid:

[http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758)
[https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks](https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks)

Well, that's my brain dump. Sorry I can't be more help.

---

### Post by natirips on 2008-07-03
Concerning 64-bit Ubuntu, there ain't much difference, from the 32-bit one. I've used both up till now, and they both seem to be the same thing, although people say that 64-bit is faster (which makes sense), I've never tried a 32-bit one on a 64-bit machine.

Concerning normal/dual boot install, G0ggy, notice that Windows probably won't be able to see the linux partition any more (by default at least), but linux will be able to see the Windows partition.

I suggest you have an **_empty_** D: drive (or any other) ready in windows, and during the installation of Ubuntu, select manual partitioning, and just reformatt that empty drive into ext3 format. Remember to mark it as root (/ (a single slash sign)) under it's mount point. Also, I would advise you to make it little bit smaller than the empty D: drive, and use the remainder for the swap partition.

As for the swap, if you have Vista running (having at least 2GB of RAM), I guess 512MB would be quite enough. I have 2GB of RAM, and only once have I expirienced the swap being used: when a buggy version of firefox's flash plugin ate ALL the memory + ALL the swap lol.

So if your empty D: drive is like 20GB in size, make the ext3 drive 19.5GB, and use the remaining 512MB for swap.

---

