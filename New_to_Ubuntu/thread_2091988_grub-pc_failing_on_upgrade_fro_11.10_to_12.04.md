---
title: "grub-pc failing on upgrade fro 11.10 to 12.04"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by Wednesday on 2012-12-06
during the upgrade I get this message:

Setting up grub-pc (1.99-21ubuntu3.4) ..
/usr/sbin/grub-setup: warn: This GPT Partition label has no BIOS Boot Partition;
 embedding won't be possible!.
/usr/sbin/grub-setup: warn Embedding is not possible.  GRUB can only be installed
in this setup ny using blocklists. However, blocklists aew UNRELIABLE and their
use is discouraged..
/usr/sbin/grub-setup: error: cannot read '/grub/core.img' correctly.


GRUP failed to install the following devices:
/dev/sda


This is the output of parted --list:
Model: ATA WDC WD20EARX-00P (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      17.4kB  300MB   300MB   ext4
 2      302MB   8301MB  7999MB  linux-swap(v1)
 3      8302MB  28.3GB  20.0GB  ext4
 4      28.3GB  128GB   100GB   ext4
 5      128GB   228GB   100GB   ext4
 6      228GB   2000GB  1772GB  ext4

1 is /boot, 2 is swap, 3 is /, 4 is /home, 

This is the output of: debconf-show grub-pc
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD20EARX-00PASB0_WD-WMAZA5675695
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10
 
This is the output of: grub-probe -t device /boot/grub
/dev/sda1

I am still in the middle of the upgrade and when I try to continue (ignoring this) then I am given the option of deciding which device I would like grub-install to be automatically run for. If I select /dev/sda then I come back to the same problem. If I select /dev/sda1 then I get a warning about installing in a partition and it fails and again comes back to the same problem/error. 

I do not know what to do - do I break out of the upgrade? What else? The what ?I had a perfectly working 11:10 system. Please help.

---

### Post by acimi66 on 2012-12-06
I am sorry your having trouble with this.

Read these posts, they are older but it may help you get a handle on finding a solution.

[http://ubuntuforums.org/showthread.php?t=1674891](http://ubuntuforums.org/showthread.php?t=1674891)

[http://ubuntuforums.org/showthread.php?t=1736409](http://ubuntuforums.org/showthread.php?t=1736409)

both ask for the  "boot_info_script" as txt try adding that in your next post.

Good Luck

---

### Post by levlaz on 2012-12-06
Are you able to continue without installing grub, then you can go back and do a boot repair?

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2012-12-07
Boot-Repair is a good choice.

But you need one more partition. I use gpt with BIOS and have to have a tiny 1MB bios_grub partition for grub to install correctly, it has no format and can be anywhere on drive but must have bios_grub flag set.

       However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.

   In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

   You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot on

   Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

---

### Post by YannBuntu on 2012-12-07
(i wonder how 11.10 could boot on GPT without BIOS-boot partition...)

---

### Post by Wednesday on 2012-12-07
Thanks for the very helpful post acimi66. This identified to me that there was a serious bug in the upgrade. Before your post I was perplexed how a standard single OS install of 11:10 could fail in a simple upgrade to the next release. I now understand that there is a fundamental bug in the upgrade (which I suspect is affecting more than me!). 

Having read the posts (some which were related to having a RAID - I do not have a RAID but they gave a hint to the problem) you pointed to I then decided to capture the bootinfoscript data ([http://sourceforge.net/projects/bootinfoscript/?source=dlp](http://sourceforge.net/projects/bootinfoscript/?source=dlp)).  I found that I had a 1.88Mib gap between my /dev/sda1 (/boot) and /dev/sda2 (swap). I then used the GUI version of Gparted to create an extra partition of 1MiB size in the gap. I labelled/flaged this as a BIOS Boot partition (bios_grub) and then carried on with the upgrade. To my surprise the upgrade continued , succeeded and rebooted OK! 


I have attached a summary of the output from bootinfoscript before and after the new partition (/dev/sda7) was created.

If I have a recommendation to the developers (or anyone considering upgrading) it would be to a) check for the BIOS Boot partition BEFORE starting the upgrade and abort, or b) create this new partition at the beginning of the upgrade. 

Thank you for helping.

---

### Post by Wednesday on 2012-12-07
In reply to YannBuntu: I have no idea. I am not very experienced. Maybe it is something to do with the fact that during the original installation I set up the partitions (manually) to have a small boot partition followed by SWAP then filesystem then homes. This is only guess. Maybe you can confirm this as a reason.

---

### Post by oldfred on 2012-12-07
I started using gpt with Maverick or 10.10. I had to manually create the bios_grub as that was recommended.

But it would install with blocklists like it does when you force it into a partition. But I do not know if it would do that without the usual warnings about not using blocklists during an install or not. 

Back then the new install messages were often different or missing where a grub only install had more & different messages.

---

