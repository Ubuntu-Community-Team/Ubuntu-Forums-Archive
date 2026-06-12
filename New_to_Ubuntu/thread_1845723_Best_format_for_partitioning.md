---
title: "Best format for partitioning?"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by diapaman on 2011-09-17
What is the best format (Master boot, GUID, no partition) to partition a 320 gb secondary hdd? It will be used primarily for storage, but I may want to do a dual boot with windows in the future. Currently running natty.

---

### Post by Chiel92 on 2011-09-17
> **diapaman said:**
> What is the best format (Master boot, GUID, no partition) to partition a 320 gb secondary hdd? It will be used primarily for storage, but I may want to do a dual boot with windows in the future. Currently running natty.

I use ntfs for data storage, since Windows and linux can handle it. If you want to go to the edge with comparing, check out this overview:
[http://en.wikipedia.org/wiki/Comparison_of_file_systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems")

---

### Post by garvinrick4 on 2011-09-17
Basic drive, NTFS.

---

### Post by diapaman on 2011-09-17
I guess I'm really asking if I should partition the hdd. If I do not will it affect using it for a dual-boot later?

---

### Post by oldfred on 2011-09-17
If you are never going to install Windows on the drive you can use gpt (GUID). But unless you can boot with UEFI Windows will not install on a gpt disk. Ubuntu works fine with BIOS and gpt (I am booting Maverick with BIOS & gpt drive.) Windows will also read NTFS partitions in gpt.

Otherwise you need to use MBR(msdos) partitioning.

If sharing data with Windows you need NTFS. But if backing up Linux data NTFS does not support permissions & ownership, so you may have to reset that if you copy back to a Linux formated partition.

---

### Post by garvinrick4 on 2011-09-17
Should have one partition?
Is it a USB drive.
Plug it in and:
sudo fdisk -l (lower case L)
What does it show?

---

### Post by srs5694 on 2011-09-17
For an external data-only drive, the choice of MBR vs. GPT makes relatively little difference *if* you're using reasonably modern OSes. Linux has supported GPT for about ten years; Windows has supported GPT since Vista (with spotty support on specific platforms in XP); and OS X has supported GPT since Apple switched to Intel CPUs. All of these have supported MBR since their creation.

If you expect to ever boot from the disk, things get trickier, at least on the Windows side, as oldfred has noted.

You should almost always partition hard disks, whether they're internal or external. AFAIK, the only advantage to not partitioning is that you can use the tiny bit of extra space that the partition table consumes. If you don't partition a disk, though, you reduce flexibility -- it becomes much harder to partition it in the future if you decide you want to do so. There's also the chance that a disk utility will assume the disk contains a partition table and behave inappropriately when it doesn't find one. (This is largely theoretical; I don't know of an OS or utility that writes to the disk without asking you -- but on the other hand, even if it asks, you might slip up and accidentally click the wrong button!)

Overall, then, MBR is the safest choice for greatest compatibility; but GPT will work with modern OSes. GPT also offers some modest advantages, such as backups of its main partition data and CRCs to help OSes and utilities detect damage.

---

