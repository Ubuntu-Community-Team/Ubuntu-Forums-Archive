---
title: "Suggestions about using persistent USB bootable ubuntu?"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by bonedriven on 2012-02-04
Hi forum.

I have created a persistent usb bootable ubuntu on my 8Gb pendrive.
I use it mainly on the computer of my university, and it will be my main working OS in the future as I have planned. I find that the os is not very stable. Actually I have rebuilt the system 3 times coz it dies sometimes after a system update(can't boot up). But the ubuntu that I built in my vmware on my laptop works much better.

Since I'm going to build this system for a long term use as my working OS, can you give some suggestions or tips please? 

Thank you very much!

---

### Post by I2k4 on 2012-02-05
> **bonedriven said:**
> Hi forum.

I have created a persistent usb bootable ubuntu on my 8Gb pendrive.
I use it mainly on the computer of my university, and it will be my main working OS in the future as I have planned. I find that the os is not very stable. Actually I have rebuilt the system 3 times coz it dies sometimes after a system update(can't boot up). But the ubuntu that I built in my vmware on my laptop works much better.

Since I'm going to build this system for a long term use as my working OS, can you give some suggestions or tips please? 

Thank you very much!

I've gotten pretty familiar with Live USB experimenting with various distros for about a year.  

First, my experience has been that Live USB with Persistence is a great way to get familiar, but is not stable, in that it starts out great but eventually develops bugs, like suddenly refusing to find your hard drive to mount it, or suddenly demanding some password that I never needed before. If you check the forum, you'll find it's possible to do a regular installation of an Ubuntu variant onto a USB drive (as opposed to "Live USB") but be very careful to install the boot loader "GRUB" on the USB and not mistakenly install GRUB on your hard drive, where it will stay like a case of herpes forever.  The directions for doing this confused me and I leave it to others.

Second, it took me a while to figure out the best values of Peristence versus room on the USB for the OS - generally I found you should give the OS about 2GB of space and set the remainder of the thumb drive as Persistent storage. I've had good results with 4GB thumb drives, in your case I'd go for about 6GB of Persistence.

Third, in actually using Live USB, it's worth remembering that the time lapse between loading on USB and mounting the hard drive will foul up some programs (e.g. DropBox, which might be very handy in your university life) that automatically start up and want to go to the hard drive for data.  You can usually disable that automatic startup, mount the hard drive and then manually start up DropBox or any other app that wants access to that drive.

Finally, with Live USB install, it's a mistake to try to do any massive installation or updating on the slow USB.  I've simply disabled all "automatic" updating and only install a few packages at a time, to minimize the read/write confusion.  You can install or update a fairly large program like LibreOffice, but don't try to delete and reinstall ten things at at time.  As I said, since Live USB has never lasted very long for me, I don't see the point of trying any major system upgrades on it. 

So, all in all, if the intention is a long term, stable installation I suggest either figuring out how to do a regular install on a good sized USB drive, or doing a dual boot to a hard drive.  Live USB is a great test experience, but not a stable solution.  If anyone knows better, I'll be interested to learn better myself.

---

### Post by bonedriven on 2012-02-05
Thank you very much, sir.

Yeah, you are totally right about live cd is not stable. Especially for persistent live cd, it's unstable to a extend that is unusable in my opinion. I have tried reinstalling the os like 8 times in 2 days, for it's so frigile that it keeps dying on me.

I have given up the idea about persistent live cd now... I find that the os running in my vmware is much more stable. So what I'm doing now is to build the os in the vmware, and try to use remastersys to make custom distro. I have just tried once, but it turned out that it couldn't boot up, with a message of "invalid or corrupted kernel image". I have to investigate on this problem now...

---

### Post by C.S.Cameron on 2012-02-05
A persistent install is not a bad option for a small flash drive as the O/S is compressed and only takes up 1GB vs 4GB for a full install.

With a persistent install I would not suggest updating or upgrading.
Updating will quickly fill the persistence file, (casper-rw), once full the flash drive will not boot.
You can not upgrade the kernel as it is inside a compressed read only file.

Remastersys is a good solution if you want to start with the latest updates.

One problem is that persistence files are FAT32 and limited to 4GB.
If you need more persistence space you can use persistent partitions:

Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (larger size is optional)
Create a 4 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Startup Disk Creator", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and add "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.

---

### Post by dgharmon on 2012-02-06
> **I2k4 said:**
> If you check the forum, you'll find it's possible to do a regular installation of an Ubuntu variant onto a USB drive (as opposed to "Live USB")

Will this 'regular installation` be usable on different hardware or tied to a specific machine?

---

### Post by bonedriven on 2012-02-06
> **dgharmon said:**
> Will this 'regular installation` be usable on different hardware or tied to a specific machine?

By definition of live cd, it should be usable on different hardware environment.

@Cameron, Thank you for the tip! That need to be written down on my notebook! :D

---

### Post by varunendra on 2012-02-06
> **dgharmon said:**
> Will this 'regular installation` be usable on different hardware or tied to a specific machine?Yes it will, as long as you haven't installed any proprietary drivers (especially graphics) on it, in which case, you 'may' face some 'minor' issues on other hardware. But then again, you always have the option to boot into "Recovery mode" from the grub menu, which would bypass any proprietary driver (by selecting an option in the recovery menu, or by passing a boot parameter (typically "nomodeset" for graphics issues) to the normal boot line).

> **bonedriven said:**
> By definition of live cd, it should be usable on different hardware environment. Yes, the "Live cd", not a regular install. But that definition goes '*almost*' the same way for a regular installation too, thanks to inbuilt drivers in Linux kernel.

> **bonedriven said:**
> @Cameron, Thank you for the tip! That need to be written down on my notebook! :DGood idea :) How about marking the thread as [Solved] now?

---

