---
title: "install Ubuntu from USB"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by noemik on 2012-09-26
Dear All,
I'm trying to install Ubuntu instead of Linpus Linux on my new Acer Aspire One. I'm following this blog post: [http://deltamonk.hubpages.com/hub/Replacing-Linpus-Linux-on-an-Acer-Aspire-One](http://deltamonk.hubpages.com/hub/Replacing-Linpus-Linux-on-an-Acer-Aspire-One)
I downloaded the ISO file, then UNetbootin, and did with it what was written. Te problem is that UNetbootin was strange; now there is something on my USB but I'm not sure it's enough. There are maps with no size: boot, casper, dists, install, isolinux, pics, pool; and two files: ubninit and ubnkern. Is it good, can I start installing?
Thanks in advance!

---

### Post by snowpine on 2012-09-26
Welcome to the forums! 

Who is "deltamonk"? Do you trust this person more than Ubuntu developers? Would you rather follow a how-to from some random guy's blog, or the official easy instructions with screenshots from ubuntu.com?

[http://www.ubuntu.com/download/help/try-ubuntu-before-you-install](http://www.ubuntu.com/download/help/try-ubuntu-before-you-install)

To answer your specific question: Unetbootin sometimes works, sometimes it doesn't--it isn't part of, or recommended by, Ubuntu. To know whether or not it worked, you need to reboot your computer and select the USB from your boot options. Then I recommend trying Ubuntu in "live" mode for a few days before you commit to an install.

Good luck! :)

---

### Post by noemik on 2012-09-26
Thank you Snowpine!

I decided to follow deltamonk because Ubuntu required a 2GB USB and I have only 1, and deltamonk said this has to be enough for UNetbootin. And this blog was more or less undrstandable even for me...

Now it turned out that I've forgotten to format my USB, now I think I have the things on it.

Thank you again!

---

### Post by HiImTye on 2012-09-27
the USB stick doesn't need to be any more than 1GB unless you want persistence (saving installs of new programs, etc). just the liveUSB is less than 1GB

---

### Post by krishna.ub on 2012-09-27
Try Live USB Creator for Ubuntu.

---

### Post by shreepads on 2012-09-27
> **noemik said:**
> Thank you Snowpine!

I decided to follow deltamonk because Ubuntu required a 2GB USB and I have only 1, and deltamonk said this has to be enough for UNetbootin. And this blog was more or less undrstandable even for me...

Now it turned out that I've forgotten to format my USB, now I think I have the things on it.

Thank you again!

Use the standard CD image, not the DVD image. That will easily fit on a 1GB stick..

---

### Post by geronl on 2012-09-27
> **shreepads said:**
> Use the standard CD image, not the DVD image. That will easily fit on a 1GB stick..

I have a question!!

If I have a 4GB flashdrive and use it as a backup bootdisc can I still save files on it?

---

### Post by HiImTye on 2012-09-28
> **geronl said:**
> If I have a 4GB flashdrive and use it as a backup bootdisc can I still save files on it?
if you want to use it as a generic storage drive, you can resize the partition after install in GParted, just make sure to 'unmount' it in GParted first. if you don't want to save new installs of files, and want to maximize your space on the drive, choose 'discarded on shut down' at the bottom of the Startup Disk Creator. that will skip creating a persistence file and let you have more space for your storage partition.

so to recap, here is the procedure:

[LIST=1]
[*]insert the USB drive
[*]backup any data you want on the USB drive
[*]open Startup Disk Creator
[*]select the ISO image and the USB stick
[*]optionally: erase the USB drive by clicking on 'Erase Disk'
[*]optionally: either drag the slider to the right to increase the size of the persistence file, or, choose 'discarded at shut down' to disable persistence and maximize your storage partition
[*]close the Startup Disk Creator and open GParted
[*]select your USB drive in the top right menu
[*]unmount the drive by selecting it in the list and then right clicking on it and choosing 'Unmount'
[*]right click on it and choose 'resize'
[*]on the top bar in the window that pops up, drag the slider on the right all the way to the left until it stops
[*]click apply. if it fails, repeat, but increase the size by 1. if it succeeds, proceed.
[*]right click on what is now 'Unallocated Space'
[*]choose the file system (ext4 if you are only using it on *nix boxes, FAT32 if you are using it between devices), and optionally type a label.
[*]apply the changes.
[/LIST]
viola!

---

