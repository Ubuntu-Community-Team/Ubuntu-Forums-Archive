---
title: "Attempted install u14.04.1 on hpCompaq; quit half way ; attemped to boot got boot err"
date: 2014-10-15
forum: New to Ubuntu
---

### Post by nu2u904 on 2014-10-15
Thought I had my thread solved however attempting to install u14.04.1 on hpcompaq; install quit half way through; attemped a reboot got boot error 15.When rebooting with live dvd system now runs extremely slowly. Tried to download Grub repair without success. What is grub error 15? Any suggestions?

---

### Post by yancek on 2014-10-15
Grub Error 15 is file not found, usually because it cannot find the kernel or initrd file on the partition.  As far as I know, Grub2 doesn't use it and it is Grub Legacy.  What did you have for an operating system prior to trying the install?  Did you install over it, to the same partition?  Do you have any OS on the computer?  If the install quit half way thorugh, I don't see any alternative to reinstalling, something.

---

### Post by nu2u904 on 2014-10-15
> **yancek said:**
> Grub Error 15 is file not found, usually because it cannot find the kernel or initrd file on the partition.  As far as I know, Grub2 doesn't use it and it is Grub Legacy.  What did you have for an operating system prior to trying the install?  Did you install over it, to the same partition?  Do you have any OS on the computer?  If the install quit half way thorugh, I don't see any alternative to reinstalling, something.

Thank you. I had a working xps before ubiquity destroyed grub. I used gparted to overwrite u10.04 and used a 21GB ext4 partition to be root and the old root partition to be /home when the ubuquity installer would create the mount points. What do I do to recreate grub2?

I just now used gparted in a live session and partitions and file systems are correct.I am attempting to run ubiquity from the live session, It won't let me put checkmarks for down load software and download 3rd party software. I clicked on continue and its been showing the spinning wheel for the last half hour. What do I do now? How do I repair the boot loader so I can run xp?

---

### Post by nu2u904 on 2014-10-15
> **nu2u904 said:**
> Thank you. I had a working xps before ubiquity destroyed grub. I used gparted to overwrite u10.04 and used a 21GB ext4 partition to be root and the old root partition to be /home when the ubuquity installer would create the mount points. What do I do to recreate grub2?

I just now used gparted in a live session and partitions and file systems are correct.I am attempting to run ubiquity from the live session, It won't let me put checkmarks for down load software and download 3rd party software. I clicked on continue and its been showing the spinning wheel for the last half hour. What do I do now? How do I repair the boot loader so I can run xp?

After an hour I clicked on quit and got back to my live dvd screen. I was unable to open firefox and when I entered term in the dash search box, the whole system froze. Launch faded and could not shutdown, reisub didn't work. So how I going to be able to install u14.04.1? wHAT WOULD CAUSE A LIVE SESSION TO BEHAVE THIS WAY?

---

