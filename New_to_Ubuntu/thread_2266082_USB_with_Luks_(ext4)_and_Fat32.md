---
title: "USB with Luks (ext4) and Fat32"
date: 2015-02-19
forum: New to Ubuntu
---

### Post by danne33 on 2015-02-19
Is it possible to divide a USB into two partitions. One that contains Luks + EXT4 and the other partition is plain Fat32. 
The reason is that I want to have one highly encrypted partition with sensitive files that I can only open at home.
The other partition (Fat32) is used for work and friends computer. It should be easily add and extract files on Windows computer at work without using programs.

---

### Post by newb85 on 2015-02-19
I've never tried it, but I'd imagine it's possible.  I would put the Fat32 partition first, in case Windows doesn't want to read past the ext4 partition, which it won't recognize.

---

### Post by danne33 on 2015-02-20
Will it damage the security on Luks partition by having a seperate Fat32 partition?
How could the installation be made? So far I only succeded to install Luks by erasing the whole USB-stick.

---

### Post by newb85 on 2015-02-20
Have you tried using gParted?  Or just the options available from the context menus in your file browser?

(Warning: if you use gParted, make sure you're formatting the right drive.)

---

### Post by danne33 on 2015-02-20
Success!!! The following steps had to be made:
Delete the complete partition on gparted. Make a new partition table (MBR) to make several logical volumes. Make one Fat32 logical volume and one Luks volume in program gnome-disks.

---

### Post by newb85 on 2015-02-22
Great! Please mark as solved.

---

