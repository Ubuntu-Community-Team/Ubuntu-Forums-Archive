---
title: "A little advice for getting started?"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by sarahr on 2013-01-01
Greetings -
I've been a registered user of this forum since 2006, but haven't attempted to run any Ubuntu release since 2008. Now I'm back again, and the changes in that time are staggering and exciting. I've recently found my way back to Linux after getting sick and tired of the restrictions being placed on me by Apple under Mac OS X (versions of which I have used since the late 1980s). I have never been a Windows user and don't care for that OS, although my current setup for the target Ubuntu install does involve Windows.

I'm dealing with a few peculiarities that have now tested my skills beyond what I am capable of figuring out on my own, so I thought I'd come here for a bit of advice. Here's what's up:

About a month ago, my friend and I both picked up a Lenovo V570 laptop (i5, maxed it out to 8 GB of RAM, swapped hard drives to increase ours to 750 GB) at an extremely cheap price. We both wanted to run Linux, as well as have a backup machine running Windows for those situations that sometimes arise that necessitate using it.

We got a dual-boot system running on the new hard drive, which is now split 70/30, Linux Mint 14/Windows 8 (horrible OS, btw) Both of us also have the leftover hard drive that we swapped out, a 500 GB hard drive that seems to have about 50 GB reserved, presumably for recovery.

Try as we might, we cannot blast this hidden partition away. We've also had trouble getting this disk formatted using GParted under Linux Mint. Mac OS also had trouble even seeing it (it can't mount it due to a lack of support for NTFS). Anyway, we had to strongarm the formatting of the 500 GB disk by running diskpart in Windows/DOS and formatting it as raw, then trying to get it partitioned in GParted - which failed.

Finally, we decided to see if we could get it formatted during the Ubuntu installation process. Just to be safe, I yanked the hard drive out of the laptop and booted off the Ubuntu disk, with the target hard drive connected via USB. Once in the Ubuntu installer, I formatted the disk and created the following drive map: 
 
/boot 200 MB ext2
/swap 2 GB 
/     15 GB ext3
/home ~430 GB ext3

[unallocated] ~20 GB <-- plan to format this as NTFS and use it as a shared partition between OSes
 
Unfortunately, the install fails right after I am supposed to choose a time zone, and gives me the ??? ??? OK error/dialog box. I can't actually choose OK or get out of this error unless I reboot.
 
So, my questions are:
 
- Are there any special considerations I should be aware of when trying to install and run Ubuntu on an external USB HD? 
 
- Am I really out of luck in ever succeeding in getting this Lenovo HD with the hidden partition truly reformatted and ready for use for an Ubuntu install? 

- Does anything else I mentioned sound fishy?

Thanks so much for reading this. I cannot wait to be up and running in Ubuntu again.

---

### Post by Paqman on 2013-01-01
Has the drive ever worked properly? What sort of error does Gparted spit out?

---

### Post by sarahr on 2013-01-01
> **Paqman said:**
> Has the drive ever worked properly? What sort of error does Gparted spit out?

The drive worked properly, yes. It was the original drive that my laptop shipped with, running Windows 7, with an additional "Lenovo" recovery partition.

GParted doesn't issue any error; it seemingly formats the drive, but upon mounting the drive again, the formatting has not held and we're back to ground zero with a seemingly unformatted drive. 

The whole thing is really annoying. If I'm just screwed because there's no way to get rid of this rescue partition that insists on wreaking havoc, I guess I can move on and get another 2.5" disk to install onto, but it's such a waste of 500 GB that I can hardly stand it.

What's the general word, otherwise, on best practices for installing on an external USB HD? I have some concerns. 

For example, when I partitioned and started the (failed) install under Ubuntu, the drive showed up as /dev/sda - seems like this will cause problems once I reinstall the internal HD, which is also /dev/sda. Is there a way to tell the USB external to be /dev/sdb?

---

### Post by sudodus on 2013-01-01
> **sarahr said:**
> 
 
So, my questions are:
 
- Are there any special considerations I should be aware of when trying to install and run Ubuntu on an external USB HD? 

It is extremely slow to write many small files to USB 2.
It may be confusing to determine which drive to select and where to write grub. So if you disconnect the internal drive (or swap the drives), it will be faster and simpler.

I know there have been issues to boot from USB 3, and I haven't found much evidence of success. It works well with eSATA.

Furthermore, if you don't install any proprietary drivers, an Ubuntu desktop system (not a plain mini-iso installation and maybe not a server) will be truly portable (as long as the hardware is modern and powerful enough). So you could also use a desktop, where it is more convenient to connect/disconnect internal drives.
> 
- Am I really out of luck in ever succeeding in getting this Lenovo HD with the hidden partition truly reformatted and ready for use for an Ubuntu install? 

If there is something strange on the HDD, you can wipe it with dd (write zeros to all positions including the MBR). dd is nick-named 'disk destroyer' because it does what you tell it to do, not what you intend to do. It asks no questions. But set correctly it does marvelous things. If you want to, I can help you with a command line. In that case, post the output of ```
sudo fdisk -lu
``` to identify which drive to wipe.
> 
- Does anything else I mentioned sound fishy?

Thanks so much for reading this. I cannot wait to be up and running in Ubuntu again.
I have read about some special features of Lenovo's new laptops, that might need to be switched off before Ubuntu will install properly. But it is outside my skill.

---

### Post by sarahr on 2013-01-01
Indeed, I did disconnect and remove my machine's primary/internal hdd. There is nothing suspicious in the BIOS that I can find. I would be happy to try a low-level format, although I'm still not sure that that will do it.

---

### Post by sudodus on 2013-01-01
> **sarahr said:**
> Indeed, I did disconnect and remove my machine's primary/internal hdd. There is nothing suspicious in the BIOS that I can find. I would be happy to try a low-level format, although I'm still not sure that that will do it.
Please post the output of
```
sudo fdisk -lu
```
And connect the HDD internally to boost speed a lot (several times).

---

### Post by davidtrounce on 2013-01-01
Welcome back to Ubuntu. You may have to brave it and wipe your Lenovo clean.

---

### Post by HermanAB on 2013-01-01
Wipe the start of the disk so that it looks like new then use gparted. 

For example:
$ sudo dd if=/dev/zero of=/dev/sda bs=1024 count=1024

Read the data definition man page:
$ man dd

---

### Post by sudodus on 2013-01-01
> **HermanAB said:**
> Wipe the start of the disk so that it looks like new then use gparted. 

For example:
$ sudo dd if=/dev/zero of=/dev/sda bs=1024 count=1024

Read the data definition man page:
$ man dd
+1
And check twice with for example
[FONT="Courier New"][SIZE="3"]sudo fdisk -lu [/SIZE][/FONT]
that you are wiping the correct drive. There is no undelete!!! And you should
***run dd when booted from another drive,***
for example your Ubuntu install CD/DVD/USB drive.

---

### Post by sarahr on 2013-01-01
> **sudodus said:**
> In that case, post the output of ```
sudo fdisk -lu
``` to identify which drive to wipe.

Well, I only have one hdd installed, because I yanked the other one that I normally use in order to avoid accidentally wiping a functional disk, and I installed the disk I hope to have Ubuntu on that is giving me problems so it will be on a much faster internal SATA bus. I'm currently booted off the Ubuntu install DVD.

Here's the output:
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

```

---

### Post by sarahr on 2013-01-01
> **sudodus said:**
> +1
And check twice with for example
[FONT="Courier New"][SIZE="3"]sudo fdisk -lu [/SIZE][/FONT]
that you are wiping the correct drive. There is no undelete!!! And you should
***run dd when booted from another drive,***
for example your Ubuntu install CD/DVD/USB drive.

I just did this. Here's the output:

```
ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda bs=1024 count=1024
1024+0 records in
1024+0 records out
1048576 bytes (1.0 MB) copied, 0.0519496 s, 20.2 MB/s
ubuntu@ubuntu:~$

```

---

### Post by sarahr on 2013-01-01
So I ran dd and just launched Gparted, and the disk is still showing up as 465.76 GB, meaning that Lenovo rescue partition is still there. This is what is causing all the trouble. I cannot believe I can't reformat my own hard drive because of some silly factory-installed Windows rescue crap. This is ridiculous!

---

### Post by sudodus on 2013-01-01
> **sarahr said:**
> So I ran dd and just launched Gparted, and the disk is still showing up as 465.76 GB, meaning that Lenovo rescue partition is still there. This is what is causing all the trouble. I cannot believe I can't reformat my own hard drive because of some silly factory-installed Windows rescue crap. This is ridiculous!
It is probably the difference in units. GiB vs GB:

```
465.76*1.024*1.024*1.024 = 500.1
```

---

### Post by sarahr on 2013-01-01
Oh, jeez. Duh. 

Well, I'm going to try to run the Ubuntu installer and I'll set up the disk in the install process.

I'll report back!!

---

### Post by sudodus on 2013-01-01
Good luck and welcome back :-)

---

### Post by sarahr on 2013-01-01
Well, I'm thrilled to say that I got the disk partitioned properly and the install seem to run perfectly. I chose sda1 (/boot)  for my boot loader and all seemed to go well. Now, upon reboot, I'm caught in an endless cycle of not being able to boot off the internal hard drive. The boot menu defaults to my CD, which is my first choice in my boot menu, but I think the problem must be something to do with GRUB.  Any ideas on what I need to do to make sure I have a boot loader where I need to have it on the Ubuntu disk?

Almost there - thank you!!

---

### Post by sudodus on 2013-01-01
> **sarahr said:**
> Well, I'm thrilled to say that I got the disk partitioned properly and the install seem to run perfectly. I chose sda1 (/boot)  for my boot loader and all seemed to go well. Now, upon reboot, I'm caught in an endless cycle of not being able to boot off the internal hard drive. The boot menu defaults to my CD, which is my first choice in my boot menu, but I think the problem must be something to do with GRUB.  Any ideas on what I need to do to make sure I have a boot loader where I need to have it on the Ubuntu disk?

Almost there - thank you!!
Did you choose any partition for / (the root file system)?

/boot can be within /, but can also be a separate partition.
Do you know where the installed root file system was written, and where /home was written?

---

### Post by sarahr on 2013-01-01
I was only prompted to select where to put the boot partition. The drive map looks like;


/boot ext2 primary
/swap logical
/ ext3 logical
/home ext3 logical
 
[about 20 gigs in unallocated space for a shared partition to be formatted as NTFS later]

---

### Post by sarahr on 2013-01-02
So we're still having trouble with getting a bootloader installed/functional. The problem is very similar to the one we had under Mint, running on a 12.10 base. Here is a link to that discussion:  

[http://forums.linuxmint.com/viewtopic.php?f=90&t=120279]("http://forums.linuxmint.com/viewtopic.php?f=90&t=120279")

We are now going to attempt to get things rolling using the procedures outlined here:

[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

Will report back. Thanks.

---

### Post by sarahr on 2013-01-02
The commands listed in that post for people who have a separate /boot partition are failing, so I've moved on to trying to use the GUI tool referenced here:

[http://ubuntuforums.org/showthread.php?p=10871917#post10871917]("http://ubuntuforums.org/showthread.php?p=10871917#post10871917")

I'm told it has successfully repaired my GRUB installation, with a URL reference of:

[http://paste.ubuntu.com/1487349]("http://paste.ubuntu.com/1487349")

---

### Post by sarahr on 2013-01-02
And that did it. I just rebooted from the hard drive, no disc in the DVD drive, and I'm in.

Good Lord.

---

### Post by sudodus on 2013-01-02
> **sarahr said:**
> I was only prompted to select where to put the boot partition. The drive map looks like;


/boot ext2 primary
/swap logical
/ ext3 logical
/home ext3 logical
 
[about 20 gigs in unallocated space for a shared partition to be formatted as NTFS later]
There is a root partition /, where the system is located. Good :-)

---

### Post by sudodus on 2013-01-02
> **sarahr said:**
> And that did it. I just rebooted from the hard drive, no disc in the DVD drive, and I'm in.

Good Lord.
Congratulations :KS

If you feel that the problem of this thread is solved, please click on **Thread Tools** at the top of this page and mark this thread as SOLVED.

Otherwise we are here to continue helping are encouraging :-)

If you have a new problem to solve, please make a new thread with a good descriptive title to attract those Ubuntu Forum members who know a lot about that kind of problem.

---

### Post by sarahr on 2013-01-02
Yes, I'll be happy to do that. I'm also going to post a summary of the problems discussed, so people can find it.

---

### Post by sarahr on 2013-01-02
On this thread, I worked through a number of issues that were hampering my install of 12.10.

1. The on-board hdd that shipped with my Lenovo laptop had a hidden partition that couldn't seem to be eliminated reliably with the various tools I'd tried. 

Solution: 
Boot off the live DVD.

use dd at the command line to wipe the drive. 

Then launch Gparted and create a new MS-DOS partition map.

Next, launch the Ubuntu installer from the live DVD.

2. The custom install that I was attempting, separating the /boot, root and /home partitions, could not be booted due to problems with GRUB that seem to be introduced when doing this kind of a setup (an error reproduced in the current version of the Ubuntu variant, Linux Mint 14 - the "COW" error.

Solution:
After trying to run the terminal commands listed at the following URL without success, I switched to the GUI option also listed there and was able to repair my GRUB install ([http://ubuntuforums.org/showthread.php?p=10871917#post10871917]("http://ubuntuforums.org/showthread.php?p=10871917#post10871917")).

I ran the utility, rebooted and Ubuntu successfully launched.

---

