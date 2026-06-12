---
title: "I've made too many partitians on my Netbook and need help removing them."
date: 2012-06-29
forum: New to Ubuntu
---

### Post by dylanb2cm on 2012-06-29
Hey Folks,

I'm very new to Ubuntu and Linux so I'm not sure how to word this next question very well.  

Recently a friend of mine partitioned my Samsung Netbook (originally with Windows 7 Starter on it).   Ubuntu was put onto it.  

It was sweet, when the netbook booted up, I could choose to pick windows or Ubuntu.  

Then I screwed it all up,  not exactly sure what I did (I was playing around in the Phoenix Secure Setup Utility, I think).   I screwed up the boot operation.  When I rebooted the netbook it just kept cycling threw the Samsung logo at the beginning.

Having backed up my data recently, I wasn't too concerned, so I played around with the computer more.  I made usb stick with Linux live on it (this took me a while to learn).

I went back into the Setup Utility and told the netbook to boot from the USB Flash Memory.  Upon reboot, I got ubuntu 12 to install on a new partition (making 3 operating systems on the netbook).   

Because I had nothing to loose at this point, I also made a bootable windows 7 usb and installed that (rewriting the original windows 7, partitioned on 50G


Now if i boot from the hard drive it gets past the Samsung screen, but it goes to windows right away.

If I boot from the usb stick, it goes to the OS choosing screen, allowing  me to choose from windows, ubuntu 9 or ubuntu 12.  

Long story short.  

Here's what I'd like to do.  

1. I'd like to get the windows 7 operating system on a small partition (10 gig or less)
2. Have ubuntu 12 be on the rest of the hard drive
3. When I boot up from the hard drive, have the option to choose one or the other.  

Thanks everyone.

---

### Post by Skydiel on 2012-06-29
First of all, after all this mess with partitioning, I would perform a physical formatting, just to guarantee a fresh start. 
I think 10GB for windows 7 is to small, unless you aren't planning to install anything on it (or you gonna use the Linux partition to install windows programs?). When I do a dual boot, I always install windows first, so I don't have to mess with grub as it will detect the presence of Windows and will make the proper adjustments. The cons of this is you gonna reserve the best part of the disk to your secondary system (well, I am assuming Linux is the primary).

---

### Post by cortman on 2012-06-29
+1 for installing Windows first. And you should probably allow at least 20-30 GB for it- it's huge, but it's just the nature of the beast.
Then install Ubuntu 12.04, with either a single / (root) partition and swap, or a / partition, /home partition and swap, your choice.

---

### Post by dylanb2cm on 2012-06-29
@[Skydiel]("http://ubuntuforums.org/member.php?u=1688569")

I'm a newb in pretty much every sense of the word.  How do i perform a physical physical formatting?

---

### Post by black veils on 2012-06-29
that is some crazy stuff!

yes the best is to wipe the drive clean, using the ubuntu live usb, choose Try instead of Install, and then open Gparted to delete all partitions. delete one at a time via right-clicking them, and press Apply after. there may be Swap partitions in use (they will show a key symbol) you need to right-click and select swap-off, then you can delete them too.

install windows.

install ubuntu. the wizard should see your windows and give you the option to install along-side it. move the slider to make windows smaller (on the left), but as stated, to 20-30GB. the right side of the slider will be your ubuntu system.

---

### Post by Mark Phelps on 2012-06-29
Do NOT use the slider to shrink the Win7 OS partition -- to install Ubuntu.  That risks corrupting the Win7 OS and rendering it unbootable.

Instead, do the following:
1) Shrink the Win7 OS partition using the Win7 Disk Management utility.  And, do not shrink it to less than 30GB.
2) Reboot into Win7 a couple of times after that to allow the filesystem to make adjustments
3) When you then boot into the Ubuntu CD, use the Something Else option to create the partitions needed in the unallocated space.

---

### Post by Skydiel on 2012-06-29
> **dylanb2cm said:**
> @[Skydiel]("http://ubuntuforums.org/member.php?u=1688569")

I'm a newb in pretty much every sense of the word.  How do i perform a physical physical formatting?

Dylan, you don't necessarily need to do this. But if you wanna try, find out  the brand of your hard drive, go to its website and download its HD checkup utility. Samsung, Seagate, WD, all have an utility like this. They usually distribute it as a bootable ISO. All  you have to do is burn a cd using this image.
This utility will allow you perform a physical formatting.

Hope I didn't confuse you more.

---

