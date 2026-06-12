---
title: "Ubuntu Boot Failing - Goes to BusyBox"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Kaspersky_ on 2008-08-03
My Ubuntu boot keeps failing to BusyBox. I installed 8.04 hardy heron using a live cd I made. I checked the disk for errors and it was clean. I used a full guided install on my hard drive. I have a screenshot of how my drives are partitioned.

[img]http://img170.imageshack.us/img170/4465/screenshotqa5.png[/img]

I think it's that both drives are set as slaves or something.

Please help me.

---

### Post by blue_shift on 2008-08-03
What errors are you getting when boot fails?

---

### Post by Kaspersky_ on 2008-08-03
I'm not sure. It just says GRUB loading, please wait. Then the loader takes a really long time to do its job and then sends me to busybox.

---

### Post by blue_shift on 2008-08-03
I don't like the sound of it. If GRUB is failing itself, maybe the problem is the GRUB install. I'm guessing it's on the MBR?

If GRUB is starting then it shouldn't be a problem with both drives acting as slaves.

It's perhaps worth trying to re-install GRUB and seeing what happens there. You can use a liveCD to check your disks / execute commands.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ConMan318 on 2008-08-03
What kind of video card is in this computer?

---

### Post by Kaspersky_ on 2008-08-03
I am now shatting brix.

```
setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... failed

Error 22: No such partition
```

Trying it with a slightly different approach (still from the same thread that blue_shift gave me) Ubuntu successfully embedded one of the GRUB files. The other is still failing miserably:

```
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition
``` 

I'm sure it has to do with it not being able to correctly install the GRUB files.

@ConMan318: I'm not even sure. Whilst I was running on Windows my video card was never installed correctly. I would be using the default vga.dll.

---

### Post by ConMan318 on 2008-08-03
Well I had the same problem (of booting into busybox) when I installed recently.  It might have been for different reasons, though.  You can try what I did to fix it and see if it works, though it quite possibly won't.

At the boot screen, hit 'e' over the Ubuntu selection to edit it.  After that, go down one to the kernel and hit 'e' again to edit that.  After the quiet splash' part, add this:
```

all_generic_ide floppy=off irqpoll

```

The end of the line should look like 'quiet splash all_generic_ide floppy=off irqpoll'.

Then hit 'b' to boot into that selection.  That worked for me because I think I had video card issues and Ubuntu thought I had a floppy drive when I didn't.  If your problems are for a different reason then this fix probably won't do anything.

If it works, post back here because there is some other stuff you need to do to add those options permanently.

Good luck.

---

### Post by blue_shift on 2008-08-03
@ConMan318 -- I don't think that is going to be possible if GRUB isn't loading. Booting into busybox is a symptom of a grave error. Maybe, though.[quote="Kaspersky_"]I'm sure it has to do with it not being able to correctly install the GRUB files.[/quote] Agreed. Perhaps check your partitions are what you think they are using a liveCD / busybox. 
```
sudo fdisk -l
```
(this will list your current partition table, both on local and removable media.)
Have you tried something as simple as ```
grub-install /dev/hda
``` (DISCLAIMER: See in context [http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html](http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html)

---

### Post by Kaspersky_ on 2008-08-03
When I use the command you gave me to check my partitions I get this:

```
Disk /dev/sda: 61.4 GB, 61475807232 bytes
255 heads, 63 sectors/track, 7474 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55054103

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7203    57858066   83  Linux
/dev/sda2            7204        7474     2176807+   5  Extended
/dev/sda5            7204        7474     2176776   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```

What I'm thinking is that it's booting from the wrong drive. It's only a guess.

And when I try to use that other command to install the grub I get this:

```
mkdir: cannot create directory `/boot/grub': Permission denied
```

---

### Post by blue_shift on 2008-08-03
Sorry, probably should be ```
sudo grub-install /dev/hda
```
If that doesn't work, and if it's convenient, how about you remove one of the hard disks to isolate the problem? 

Since "Disk /dev/sdb doesn't contain a valid partition table", chances are if you are booting from it things will go very wrong. Perhaps try both disks if you don't know which is which?

---

### Post by Kaspersky_ on 2008-08-03
The one I try booting from shows the Ubuntu loader. So that should be the right one.

Couldn't I just delete all the partitions and partition tables and let Ubuntu do it from scratch?

---

### Post by Kaspersky_ on 2008-08-03
Bump.

---

### Post by spiderbatdad on 2008-08-03
it looks to me from your screenshot, that you have not set a mount point for sda1; that is, mount point should show a "/"

```
/dev/sda1 ext3 / 59246MB
```also if they should be marked for formatting. swap does not need a mount point.

---

### Post by Kaspersky_ on 2008-08-03
How would I go on mounting the partition(s)?

---

### Post by spiderbatdad on 2008-08-03
> **Kaspersky_ said:**
> How would I go on mounting the partition(s)?

the mount point is set from within the partition editor during the installation process. If you are gettin busybox, it looks like grub is not finding any filesystem, in this case. I would suggest reinstalling, and if you want to manually partition, watch this great screencast. It includes creating a separate /home...very useful.
[http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1](http://screencasts.ubuntu.com/MoS2007/09_Installing_Ubuntu_Part_1)

---

### Post by Kaspersky_ on 2008-08-04
I watched the screen cast, scrutinizing over what I did. I did all that the screen cast told me to do which was to set up 3 different partitions, two ext3's, mounted on / and /home, respectively, and a swap partition. Ubuntu still fails to boot. I'm not sure what's wrong.

---

