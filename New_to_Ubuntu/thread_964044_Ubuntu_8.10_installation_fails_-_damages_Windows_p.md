---
title: "Ubuntu 8.10 installation fails - damages Windows partition"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by scarolan on 2008-10-30
I attempted a default Ubuntu 8.10 installation on my Dell XPS system that came with Windows Vista, and the disk partition tool failed and damaged the boot partition.

Fortunately the Windows system rescue tool was able to fix it so I'm back up and running, but probably won't be installing Ubuntu again until I can get a second hard drive.

Just thought I'd post this here as a warning to others who are considering using the installer to make a dual-boot system.  Proceed with caution, and make sure you have backups!

---

### Post by ibuclaw on 2008-10-30
Try using Hardy... It is by far the safest route in my opinion.

And as for partitioning... It would also be my recommendation that you use the **Partition Manager** that comes with the LiveCD to partition your hard drive first. Shrink the size of the NTFS partition to a reasonable level and create a new filesystem with the **ext3** format in the empty space.

Then try installing Ubuntu in the created filesystem by using the option "**Custom Partitioning**" when it asks you what to do.

Regards
Iain

---

