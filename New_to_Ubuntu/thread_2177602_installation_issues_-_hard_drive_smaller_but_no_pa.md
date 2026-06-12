---
title: "installation issues - hard drive smaller but no partitions showing"
date: 2013-09-29
forum: New to Ubuntu
---

### Post by mystmaiden on 2013-09-29
This is a bit convoluted but I'll explain it as well as I can. I just built a computer for which I have no dvd drive so I used the instructions and booted fine the first time from a usb drive. Installation went well but when I restarted, I could not log in. Apparently when I set it up I typoed the password not once but twice the same way. I tried just reinstalling but the computer would not boot from the usb again no matter what I did. (This is an N-alvorix mb, so its older) As as workaround, I deleted the Ubuntu Precise LTS partitions from the drive on another computer with g-parted. Now the drive which started as 500 gb shows 465 gigs and will not boot to the usb - instead it gives me a screen that just says 'grub-rescue'. Is there a hidden partition lurking or something else that might cause this?

thank you,
mystmaiden

---

### Post by sandyd on 2013-09-29
In most motherboards, there is a button to press to select the boot device.

Initially - since your hard disk is blank, the BIOS detects that and boots from USB.

Now that its partitioned (which is why you are missing space), the BIOS tries to boot from the HDD. (I guess the USB has a lower boot priority than the HDD)

---

### Post by mystmaiden on 2013-09-29
Thank you, sandyd for the reply.
So far, I have not found which key might give me a boot menu, alas. When I look at it with gparted, it shows only the 465 gigs of unallotted space. Does 35 gigs of hard drive space seem like an awful lot to be missing? Is there a way to recover it with gparted?

---

### Post by whitesmith on 2013-09-29
Yup. Since there appears to be nothing useful on your HDD, just use gparted to delete the new partition. You should now have a 500 GB drive on which you can reinstall Ubuntu. Actually, to be completely safe, you could delete **all** partitions and then create a single large (max size) partition. Hope this helps you.

---

### Post by mystmaiden on 2013-09-29
whitesmith, thanks for the reply. Here's where we come to the crux of the problem though. Gparted doesn't show any partitions. It looks like there aren't any but something must be holding that 35 gigs of hard drive captive. I thought maybe there was something hidden

---

### Post by LukeMorrison on 2013-09-29
On any hard drive, there is some space "missing."  A 40 GB hard drive shows up as 37 GB, and if you extrapolate that out, it is close to the same ratio for a 500 GB hard drive, roughly 35 GB.

---

### Post by mystmaiden on 2013-09-29
Thanks Luke. I wonder though why my computer is no longer reading this as a completely blank drive? When I loaded the os (Precise LTS 64 bit) it showed as being 501 gb. Now it acts as if there is something still on the drive and wants to rescue grub. I may have to wait and just pick up a dvd drive this week and load the silly thing that way. Not sure if this is helpful but attached is a screenshot of gparted. (I plugged it into my other ubuntu machine via an external drive)

---

### Post by oldfred on 2013-09-29
Ignore the size issue as that is not your problem.

 Hard Drive size
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)
More confusion?
[http://www.neowin.net/news/ubuntu-implements-units-policy-will-switch-to-base-10-units-in-future-release](http://www.neowin.net/news/ubuntu-implements-units-policy-will-switch-to-base-10-units-in-future-release)
1 Gigabyte (GB) = 1,000,000,000 bytes.
1 Gibibyte (GiB) = 1024x1024x1024 = 1,073,741,824 bytes
160 GB (gigabytes) = 149.01 GiB (gibibytes)
So your 500GB should be about 465GiB.

But gparted will not show partitions for several reasons. It used to not not even show a drive if an NTFS partition was corrupted, but now it usually does. But RAID, gpt, dynamic partitions from Windows, corrupted partition table and several other reasons. 

 Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by mystmaiden on 2013-10-04
I bought a dvd drive today, loaded windows 7 - 64 bit and Ubuntu Precise 64 bit with no trouble. I did discover that there was a bit of a bug where this mb and bootable usbs are concerned so that may have been the problem.

---

