---
title: "Installing on UEFI NB doesn't work"
date: 2015-12-21
forum: New to Ubuntu
---

### Post by grador on 2015-12-21
Hi, I have problem to install Kubuntu on my Ultrabook Asus UX51V. Any help appreciated.
My steps so far:
[LIST=1]
[*]Turned off secure boot and Fast boot in Bios 
[*]Installed 64-bit 15.10 Kubuntu. Installed in on hidden (?) partition (17GB), first on the list (second was my standard 500 GB SSD). 
[*]Restarted and entered BIOS (USB removed first). Only entry is Windows Boot Manager - it still works, I can boot to windows 10 
[*]Boot from USB again. Install and run boot-repair in automatic mode. It said boot mngr is repaired. Here is the result - [http://paste2.org/9htFx3Lw](http://paste2.org/9htFx3Lw) 
[*]Restart and enter BIOS - two new boot entries - both says "ubuntu". Booth booted into text based GNU GRUB (Minimal BASH-Like line editing...) 
[*]Boot back into windows 10. Run "bcedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi". (found on some topic on the net) 
[*]Restart, enter bios. One of the "ubuntu" entries changed to "Windows Boot Manager", but boot into the same GNU GRUB... 
[/LIST]

Don't know what to do next. I read somewhere that I need to reinstall kubuntu, but I am worried I will get to step 3 again.

Can anyone help me pls?

PS: I don't need windows there.

---

### Post by oldfred on 2015-12-22
Is this one of the UltraBooks with dual drives in RAID?
It looks like you have sda & sdb as RAID and/or LVM. I do not really know either, both use /mapper to identify drives.

But standard desktop installer does not install grub correctly with RAID. Last desktop version with LVM & RAID was 12.04 with alternative installer. Ubuntu discontinued alternative installer with 12.10. Now new versions do support LVM, but only seem to see & install to RAID, but grub does not seem to install correctly?
Boot-Repair seemed to have issues mounting RAID partitions. Not exactly sure what issue is, but it need to mount partitions to correctly reinstall grub to RAID.

Do you want to keep the RAID? Some prefer to have the larger space that two drives give. RAID 0 is just for speed and if either drive fails you lose all data. While backups normally are important, with RAID 0 you must have good backups or no data you care about.

---

