---
title: "Grub"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Cheese Roller on 2008-05-03
Hello Ubuntu forums. I haven't been here in a while but let me ask you a general question about GRUB.

I have a dual booting machine, running Debian and Vista on two seperate Hard Disks.

Vista screwed up on me and I had to format it.

As a precaution, I unhooked my Debian drive completely and installed and booted Vista.

When that was done, I hooked my Debian drive back up and tried to boot. GRUB went crazy.

Tell me some things about GRUB so this never happens again, I've given up and I'm going to reinstall Debian.
-
What is the "Master Boot Record"? Where is it stored?
How can I format Vista without Linux going crazy again if I have grub installed?

---

### Post by Aearenda on 2008-05-03
First up, you don't need to reinstall Debian just for this.

You may need to reinstall Grub, but that depends on which drive is your master drive, which drive you are booting from, and so on. The master boot record is what the BIOS causes the PC to load as its first bit of code from the hard disk as it starts up. It tells the processor how to get to the next bit - Vista has probably overwritten it.

I have to go out, so I can't step you through the process until later, but a good beginning would be for you to tell us what drives you have, what partitions you have, and which drive you are booting from.

---

### Post by kirios on 2008-05-03
The MBR is the first sector of a disk where the bootloader and partition table live.

---

### Post by Cheese Roller on 2008-05-03
> **kirios said:**
> The MBR is the first sector of a disk where the bootloader and partition table live.
That means it's only on the Debian HDD right?

Then why did the guy above say Vista would have gotten rid of it?

> **Aearenda said:**
> First up, you don't need to reinstall Debian just for this.

I think I do. When I boot into Debian a GRUB command line comes up and booting sends me to kernel panick.

---

### Post by kirios on 2008-05-03
Unless you had specified that Debian should install grub on the second disk, it would have overwritten the Vista bootloader. 

You can fix the current problem by reinstalling grub.

---

### Post by louieb on 2008-05-03
Did you change the boot order of your hard drives? (May have happened after you unplugged the drive with Linux on it). Changing the order hard drives boot in will drive GRUB nuts.  

One note about the MBR -  each hard drive has its own MBR. So in your case 2 hard drives, 2 MBRs  on on each drive.  

Since I don't know which drive Debian installed its grub MBR code to or which driver was 1st in the boot order when you installed Debian . 

Try booting one drive then the other 1st and see what happens.

---

