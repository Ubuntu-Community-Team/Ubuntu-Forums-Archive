---
title: "Preserve an existing installation with dd?"
date: 2008-11-06
forum: Other OS Talk
---

### Post by K.Mandla on 2008-11-06
This feels like a strange question, so I was wondering if anyone would offer suggestions or advice.

I was bequeathed a [100Mhz Pentium laptop]("http://kmandla.wordpress.com/2008/11/06/jackpot/") with a working Windows 95 installation in place; I'd like to keep the installation intact on another machine and wipe the physical drive to install Linux.

I can transplant the drive into another machine and use dd to write the entire (only 800Mb) drive to a file, then write it back if I run into problems, right? I usually do this with USB drives and emulated systems, for my OLPC.

I figured I should ask if this will work, before relying on it to work. :shock:

---

### Post by tea for one on 2008-11-06
Good morning

I was exploring the dd command last weekend and I found it to work very well but it is fairly slow.

I copied a Linux Puppy OS from a USB stick to an external hard drive and then copied it again to a different USB stick. All settings and data were intact. The size was about 220MB and it took approx 5 minutes. The copy booted perfectly via Grub in my main Ubuntu installation.

When copying, both the source and the destination have to be mounted.

I have not yet copied a Windows installation, I would be interested in hearing the outcome. 

By the way, I found this helpful for the command line instructions.

[http://ubuntuforums.org/showthread.php?t=599599](http://ubuntuforums.org/showthread.php?t=599599)

---

### Post by caljohnsmith on 2008-11-06
Yes, you can use "dd" to make an exact clone of your HDD. But as "tea for one" pointed out, dd can be slow, but that's only true if you use dd's default 512 byte block size for copying; instead you can specify a larger block size for copying and speed things up considerably, and the only trick is using the "conv=notrunc" option so that every byte on the HDD is copied the way it should, even if the HDD size is not an exact multiple of the block size used for copying. So bottom line, try something like:
```
sudo dd if=/dev/[COLOR="Blue"]<source drive>[/COLOR] of=[COLOR="Blue"]source_drive_image.bin[/COLOR] bs=[COLOR="Red"]10M[/COLOR] conv=notrunc
```
Using a 10 MB block size for copying like above, as opposed to the default 512 byte block size, will really speed the copying process with dd. Also, if you want to save space, you can clone and compress the HDD image file in one step:
```
sudo dd if=/dev/[COLOR="Blue"]<source drive>[/COLOR] bs=10M conv=notrunc | gzip -c > ~/Desktop/[COLOR="Blue"]source_drive_image.bin.gz[/COLOR]
```
That will save the gzipped image file to your desktop. Anyway, let me know how it goes. :)

---

### Post by tea for one on 2008-11-06
Following on from the suggestion by "caljohnsmith", you may also want to investigate Partimage. 

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page).

I have used this for copying disc images, but I did have a little local difficulty because you have to use the space bar (as opposed to enter)to select an option. The manual is a little incomplete for first time users.

Partimage gives you compression choices but, I stress, that it is not simple software to pick up and use effortlessly.

If you want to try Partimage, my suggestion would be to burn a copy of SystemRescue Live CD because it comes bundled with GParted and a terminal.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Kind regards

---

### Post by C.S.Cameron on 2008-11-06
I'm trying to recall if you can even swap Windows 95 hard disks between machines, I don't think you could with 98.

---

### Post by K.Mandla on 2008-11-07
Thanks everybody. I'm going to give this a run as soon as I can come up with an hour's free time. Cheers. :D

---

