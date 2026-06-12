---
title: "I can't boot up all the way"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by schmidtbag on 2008-07-31
I don't really consider myself a Linux noob, I just don't really know what to categorize this problem under.

Anyways, I've been running Ubuntu for a little over a month perfectly on this 2.2GHz P4 with 768MB of RAM on a 40GB ATA HDD.  I recently upgraded it to 2.4GHz Athlon 64.  Now, the computer doesn't complete it's boot process.

I told Ubuntu to show some diagnostics as it shows the splash loading screen.  The bar is moving but its stuck when it says "Waiting for root file system..."

About 5 minutes later it clears the screen with a message saying:
```
[ 206.470735] usplash[1241]: segfault at b789d040 eip b7f38ed2 esp bfc57b30 error 6

Busybox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```
The (initramfs) part lets me type, but it seems very restrictive.

I put the CD back in and it works fine, I know this is just because I'm switching from very different parts (even RAM type) but I really really don't want to reinstall everything.

---

### Post by annda on 2008-07-31
you can expect trouble when changing computer parts. this is related to disk changes but might be helpful in saving you from a reinstall:
[https://bugs.launchpad.net/ubuntu/+bug/205990](https://bugs.launchpad.net/ubuntu/+bug/205990)

you can try to boot into recovery mode and follow the advice.

---

### Post by schmidtbag on 2008-07-31
Not even recovery mode starts up, so your solution didn't help.  sudo wasn't even considered a command.  recovery mode boots up the same but it seems to be doing different things than it usually does.

This is weird, it is reading from my HDD but its acting like it doesn't exist.

---

### Post by gjoellee on 2008-07-31
with which kernel does this happen?

Note: Kernel 2.6.24-20 does mostly not work good (if it doesn't work remove it)

---

### Post by annda on 2008-07-31
> **schmidtbag said:**
> Not even recovery mode starts up [...]  recovery mode boots up the same but it seems to be doing different things than it usually does.

so can you get into commandline recovery or not? as to sudo: my fault, i forgot to mention that in recovery aka single-user mode you are already root, so there is no need for sudo.

is there a way you could post the output of blkid and the contents of your /etc/fstab and /boot/grub/menu.lst ? that way we could learn more about your problem.

---

### Post by schmidtbag on 2008-07-31
@gjoellee:
I'm pretty sure I have 2.6.24-19

@annda:
no, I can't get into recovery mode.  Both normal boot and recovery boot hesitate at the same spot and after about 5 minutes of trying to wait for the "root file system", it gives up and just shows the (initramfs), which seems to have a very restricted set of functions
also, I am not root because just typing "blkid" doesn't work at all, it says "/bin/sh: blkid: not found"

---

### Post by annda on 2008-07-31
can you at least check - using the live cd - if your fstab and menu.lst files are ok? does removing "quiet splash" in menu.lst (or on-the-fly in GRUB's boot parameters) and/or UUIDs in fstab help at all?

---

### Post by Maju on 2008-07-31
Hello. I am totally new to Linux, Ubuntu and all this and just installed with Wubi and went fine until after boot, when I got stuck in the same MS-DOS-like screen like the one shown above. 

I was hoping to end in a Windows-like interface (isn't that X11?) but all I got is that silly screen and, sincerely, no idea what to do next.

---

### Post by schmidtbag on 2008-07-31
Hmm well heres something weird, when I start up the live cd, my hdd isn't labeled.  The "Filesystem" labeled is just the live cd account.  But what is supposed to be my HDD is labeled as an inaccessible "SCSI Drive".  Now, I do have an SCSI card in my computer, but nothing is connected to it ATM and Ubuntu never did this before with the other motherboard.

Now what?

As a side note, I do plan to copy my data from the ATA 40GB HDD (That Ubuntu is on now) to a 160GB SATA, so I'd like to know how I could do that as well, or if thats really all I have to do to make this work

---

### Post by schmidtbag on 2008-08-01
Many hours later and many things changed.  I put in my 160GB drive and installed windows on it, then used some programs to copy all my data from my linux 40gb.  For some weird reason, even after formatting the HDD in Windows and Ubunutu's live CD, the 40GB HDD still can't be read by Linux, it is still only recognized as an SCSI drive.  GParted works with it but the file browser that comes with Ubuntu doesn't.  I have the 40gb removed entirely ATM.

So, now my new issue is how do I make this 40GB partition (in my 160gb hdd) ext3?  I have a 512mb swap partition at the very end of the drive, and the rest of the space in between is ext3

---

### Post by rossperk on 2008-08-01
> **schmidtbag said:**
> ...the 40GB HDD still can't be read by Linux, it is still only recognized as an SCSI drive.  GParted works with it but the file browser that comes with Ubuntu doesn't.  I have the 40gb removed entirely ATM.

So, now my new issue is how do I make this 40GB partition (in my 160gb hdd) ext3?  I have a 512mb swap partition at the very end of the drive, and the rest of the space in between is ext3

I have a similar issue. I have an 80GB PATA drive that I partitioned to [10GiB ext3][62.5GiB ext3][2GiB Swap] using GParted from the LiveCD of Ubuntu 8.04.1 i386, on my Asus A8N32-SLI mobo, which has a 64-bit AMD proc.

Though the hard drive's PATA, GParted's mounting the drives as /dev/sda1, 2, and 3, instead of hda. Is this normal?

Anyway, I run the installer and assign the above mount points to "/", "/home", and Swap, respectively. It seems to install fine, but upon first boot, during the Ubuntu logo with that orange thing bouncing back and forth, it drops to the same Busybox / initramfs prompt quoted above. When I boot it to recovery mode, I read the following error right before it drops to Busybox:```
ALERT! /dev/disk/by-uuid/cee392fd-173a-4fbe-9a54-3f21c4aec562 does not exist. Dropping to a shell!
```

I've tried escaping at the GRUB prompt and changing the second line from /dev/disk/by-uuid/... to /dev/sda1 which it also doesn't take, giving the same error except with the same change I made.

Here's the kicker. I go *BACK* to the LiveCD, open up GParted, and now it has yellow bangs next to my two ext3 partitions! If I right-click on one of them and select Information, it gives the following Warning at the bottom of the window:```
e2label: No such file or directory while trying to open /dev/sda1
Couldn't find valid filesystem superblock.

Couldn't find valid filesystem superblock.

dumpe2fs 1.40.8 (13-Mar-2008)
dumpe2fs: No such file or
directory while trying to open /dev/
sda1

Unable to read the contents of this filesystem!
Because of this some operations may be unavailable.
```

I've tried deleting the two partitions and re-creating the two using GParted. The new partitions seem to be created just fine, but after running the installer, it still won't boot, and the errors return upon going back to GParted on the LiveCD.

schmidtbag: are you getting these same errors when you bring up your Ubuntu partition in GParted after trying to install on it?

everyone else: any ideas from these details?

---

### Post by schmidtbag on 2008-08-01
I solved everything I need to for this question.  Every other question I have is not related to this.  Thanks anyway everybody.

---

