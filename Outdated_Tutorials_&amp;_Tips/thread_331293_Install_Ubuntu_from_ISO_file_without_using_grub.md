---
title: "Install Ubuntu from ISO file without using grub"
date: 2007-01-04
forum: Outdated Tutorials &amp; Tips
---

### Post by energiya on 2007-01-04
After some research on this forums, I found this [tutorial]("http://www.ubuntuforums.org/showthread.php?t=316093"), but I never managed to figure out how to write grub to a floppy. So I will try to describe how I did it without grub.

First of all, you have to download the alternate cd from the Ubuntu website (the standard live cd DOESN NOT work from iso). 

- download all files from [here]("http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/") (for dapper).

- if you have a fat partition (I think it works on NTFS or EXT3 to), copy the ISO (don't rename it) and the 3 files downloaded on that partition (don't put them in any folder, let them in root).
 
- download Gujin from [here]("http://sourceforge.net/project/showfiles.php?group_id=15465") (select the standard download)

- download Rawwrite from [here]("http://www.chrysocome.net/rawwrite")

- using Rawwrite, make a floppy with the "full" image from the standard gujin package (I extracted the full.img.gz and wrote to floppy the resulting floppy.144, I think :-k )

- if you have linux installed, follow the quick tutorial on the gujin page or in the install.txt file, becouse linux doesn't need an app like rawwrite

- be sure you have floppy as your first boot device in BIOS an reboot
Gujin should start and you can now select the partition that has the kernel, and the installation.

**ATTENTION!!**
If you are installing X/K/Ubuntu 6.10 this will fail to find the iso, so you have to write
mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0 
to terminal 2 and try again.
I encourage you to read john_spiral's [tutorial]("http://www.ubuntuforums.org/showthread.php?t=316093"). the whole instalation procedure it's presented nicely there.

Hope this helps

---

