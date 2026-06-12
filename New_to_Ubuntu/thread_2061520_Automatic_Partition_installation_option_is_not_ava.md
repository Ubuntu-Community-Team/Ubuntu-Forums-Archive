---
title: "Automatic Partition installation option is not available"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by MarcellusCrow on 2012-09-22
When installing Ubuntu, I do not get the option to automatically partition my hard drive. When I try to do it manually, it does not allow me to resize /dev/sda2, which is my hard drive.

---

### Post by oldfred on 2012-09-22
Welcome to the forums.

If you have Windows installed, you should shrink Windows using the Windows tools. 

But the issue of auto partitioning not working is usually the 4 primary partition limit that MBR partitioning has.

Post this from liveCD terminal. Or screenshot from gparted.

sudo fdisk -lu

---

### Post by Bashing-om on 2012-09-22
MarcellusCrow; Hi ! welcome to the forum .

Firstly, be advised the nomenclature "sda2" says the second partition on the first hard drive => leading to misdirection for help.
 A bit more information would be helpful to allow us to help you.
What version/release are you attempting to install ?
what method are you employing to install ?
Are you dual booting ?


Manual partitioning: What does GParted see as the disk layout ?
Partitioning: Windows tools for window's problems, Linux tools for ubuntu situations.
[INDENT]Help us to help you ---warm regards <==BDQ

[/INDENT]

---

### Post by Mark Phelps on 2012-09-23
"sda2" is NOT your hard drive -- that is "sda".

The numbers following the "sda" indicate the number of the partition on the driv3e ... and in this case "2" is likely to be the OS Partition -- and if you DO use the installer to shrink it, you risk corrupting it and rendering Windows unbootable as a result.

Also, in "sdisk -lu", "l" is a lowercase L, not a one.

We need the result of that command to give you detailed instructions.

---

