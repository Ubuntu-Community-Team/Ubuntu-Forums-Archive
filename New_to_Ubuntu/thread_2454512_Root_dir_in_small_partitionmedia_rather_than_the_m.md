---
title: "Root dir in small partition/media rather than the main one"
date: 2020-12-01
forum: New to Ubuntu
---

### Post by endfrostx on 2020-12-01
So, Ubuntu places everything in this small 13GB partition while leaving the main one 290GB-ish completely empty, the default directory, and everything is in the small one. Is there any way to change the default dir to the big one instead? If so, are there any consequences for doing this?

Just install it about 3 days ago btw.

---

### Post by Impavidus on 2020-12-01
There are ways to change this, the easiest being a fresh install (and this time doing it right).

Two things I notice: you've got an extended partition, which is a container for other partitions, meaning you use MBR partitioning. This is somewhat old-fashioned, but it works. It's not recommended for freshly formatted drives. Second, the drive is called sdc, which suggests you have at least 2 other drives (sda and sdb).

There's also an efi partition, but it appears to be unused. There might be one on a different drive.

If you have multiple harddrives, it's recommended to partition manually using gparted. Use gparted during a live session, as you cannot edit partitions while running from the system installed on them.

There's not a single correct way to partition, but you should make sure that your root partition is at least 25GB. A few other partitions may be mandatory:
-- If you install in UEFI mode, you need an EFI partition. It doesn't look like you use UEFI mode now, but I can't tell for sure. It is recommended on more recent hardware, but if you're dual booting with Windows, you can't change it. If you are dual booting with Windows in UEFI mode, there already is an EFI partition on one of your other drives.
-- If you use an encrypted system (you don't), you need a /boot partition.
-- If you use GPT (not MBR) partitioning on a legacy (non-UEFI) system, you need a bios-grub partition.
All other partitions are optional. A large /data or /home partition is often recommended to keep your documents separate from your OS, some people like a swap partition and everything else only complicates matters, unless you really know what you're doing.

In the installer, choose the "something else" option, then configure how you want to use each partition. If the mountpoint you want to use isn't in the dropdown list, skip that partition. You can configure it later, after installation.

---

### Post by ActionParsnip on 2020-12-01
Ubuntu doesn't partition like this by default. This has been manually partitioned with a 4Gb swap, 15Gb root then the rest for whatever mount path is truncated in your image. The default is to have one large partition only.

Not Ubuntu's fault.

Yes everything goes into the root partition because the files in Linux go where they go. You can't change the install location like you can in Windows, without a bit of effort and repackaging the application so it installs to another location then dealing with making it work.

---

### Post by The Cog on 2020-12-01
I see the two large partitions are mounted as /media/endfrox, as tough they were mounted manually after boot - not listed in fstab. It makes me wonder if they were a pre-existing Linux installation, the 13G partition was unused, and then Ubuntu was installed "alongside" the existing one.
Just a thought.

---

### Post by ActionParsnip on 2020-12-01
Could you not rsync to a root folder in the larger partition then just set the current /root partition to not mount? One possibility I guess

---

### Post by skipbarker on 2020-12-07
When you install with the default use entire disk option, everything goes in one partition (well mostly, efi and swap will be in their own partitions). If you reinstall, make sure you have a backup of anything you don't want to lose.

---

### Post by grahammechanical on 2020-12-07
You can use sdc6 as a Data partition. I use the rest of my hard disc to store files and documents. You can create folders in that sdc6 partition. The advantage of keeping your data out of the main Ubuntu system folder becomes apparent if you have to re-install Ubuntu. You re-install into sdc7 and avoid formatting sdc6 and you will not lose any of your documents.

If you think the Ubuntu partition (sdc7) is too small (13 GB) and in my opinion it is near the minimum size, then you can use GParted to shrink sdc6 and create space to the left of sdc6. Then you move the swap partition (sdc5) to the right to create unallocated space in front of sdc5. Then you expand sdc6 into the unallocated space to have a larger Ubuntu partition.

Regards

---

