---
title: "Resizing partitions help!"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by oscillator on 2012-08-17
I bought a laptop with windows 7 preinstalled. I installed 12.04 on it, now I've deleted the windows partitions and have lots of unallocated space. 
I used gparted liveCD to try and resize my ubuntu partition (which in my mind means make that space available for ubuntu to use) and followed the instructions here - [https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows) - on resizing, did this, it took 00:00:01 seconds to move /dev/sda4/ to the left and resize to X GiB' which i thought was odd.

Then, well see the screenshot i attached for that, basically nothing has happened, so pretty please someone how do i do this properly?

---

### Post by Double.J on 2012-08-17
> **oscillator said:**
> 

Then, well see the screenshot i attached for that, basically nothing has happened, so pretty please someone how do i do this properly?

Hi there,

Before going any further is everything backed up? 

You want to move data towards the start of the drive, not resize it, this is going to take a long time as every single sector will be copied. This is just how hard drives use data. so long as you have deleted the windows partition, you just need to move not resize the partition to the left, apply, let it complete, then resize it to the right and apply.

Never let gparted rack up a load of pending actions - apply each one when ready... it reduces the chance of errors, but as I say, the most important thing is to make sure it's all backed up as you are going to be copying the partition and deleting the old one essentially so you want to make sure the data is safe :)

Best of luck!

Edit:
I missed the obvious here, so far you have just resized the extended partition /dev/sda4 to fill up the drive.. now you need to move the logical partition /dev/sda5 to the left (so it's at the start of the drive) and then resize it to the right (so it fills it up) :)
Also I noticed there's no space allocated for a swap partition? is this the "unknown partition", or were you using a swap file?

---

### Post by oscillator on 2012-08-17
OK so I just now need to move it to the right, how do I do that when it's already to the right of the unallocated space (in gparted) ? Everythings backed up btw.

---

### Post by oscillator on 2012-08-17
ah I guess i just move the unallocated space to the right to do that?

---

### Post by Double.J on 2012-08-17
> **oscillator said:**
> OK so I just now need to move it to the right, how do I do that when it's already to the right of the unallocated space (in gparted).

The light blue border all around the partition table is actually /dev/sda4, your extended partition that contains the logical partitions /dev/sda5 and /dev/sda6... these are where your data lies.

unfortunately you cant move free space, think of this as an absence of something - you can't easily move the room around a chair, but you can move the chair around the room?

/dev/sda5 is where your linux partition (ubuntu most likely) is, so you just need to click on it, select move/resize and in the box that appears drag it all the way to the left and then click apply.

It should now (after some time) be on the left with the free space on the right, so now you click on it again and select move/resize, but this time change free space following to equal 0 and again apply - it should now occupy the free space and you're done :)

---

### Post by oscillator on 2012-08-17
OK so ive moved it to the right, although it said free space following or something (the top selection box) was 1 MiB, so I assumed that meant it wasn't moved completely to the right so changed that to 0.
Clicked OK and there was a message saying moving sda5 ( i cant move 4) would likely result in failure to boot, but I've done it anyway.

If that means it's sure to bust linux, I'm just giving up completely and reinstalling linux.

Thanks anyway :)

---

### Post by oldfred on 2012-08-17
I do not like moving partitions left, but also like smaller / (root) partitions. Then I use the remain space for /home or just data partition(s). I create 25GB / partition and have all my data in other partitions. I use about 7 to 9GB in /, but am aggressive in moving data folder and some hidden folders like Firefox & Thunderbird profiles.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

---

### Post by oscillator on 2012-08-17
Just noticed your edit, good thing too, I'm just growing sda5 after moving it to the right, I asked what the unknown partition was on IRC, apparently it is the swap partition, I', just going to leave it alone and hope I don't need to do anything to it?

---

### Post by oldfred on 2012-08-17
If you encrypted your /home, then swap is automatically encrypted also. Then gparted cannot see that as it is not a normal swap but encrypted.

---

