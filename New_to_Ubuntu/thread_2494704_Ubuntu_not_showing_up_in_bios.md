---
title: "Ubuntu not showing up in bios"
date: 2024-01-24
forum: New to Ubuntu
---

### Post by oyin-k7 on 2024-01-24
Hi all, 
I'm a new user and I'm trying to dual boot windows with Ubuntu but the Ubuntu grub menu isn't show up after installation and Ubuntu isn't on my bios but when I try to delete the partition for Ubuntu on my windows it says "the selected partition was not created by windows and might contain data recognised by other operating systems" , I tried using boot repair but that didn't work so I don't know what to do. The link to the boot repair is [https://paste.ubuntu.com/p/6wd7PynhPC/](https://paste.ubuntu.com/p/6wd7PynhPC/)

---

### Post by tea for one on 2024-01-24
Line 57 - Warning: NVram is locked (Ubuntu not found in efibootmgr)

Can you access your UEFI settings and disable these options (if they are present):-
TPM (Trusted Platform Module)
PTT (Platform Trust Technology)
FTPM (Firmware Trusted Platform Module)
TPT (Trust Platform Technology)
Device Guard (some Lenovo devices)
OS Optimised Defaults (some Lenovo devices)
Lock UEFI BIOS Settings
Boot Order Lock

---

### Post by oldfred on 2024-01-24
Lenovo seem to have Boot Order Lock.
Lenovo Locked UEFI/BIOS setting, check your UEFI settings:
[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)
The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.
Lenovo Thinkpad T495 Boot Order Lock
[https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots](https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots)

Windows updates may also update UEFI firmware, and that resets many settings back to defaults. best to keep a list of what you change, so you can redo it on updates.
Also Windows updates may turn fast startup back on. That sets hibernation flag which can prevent grub from booting Windows.

---

### Post by oyin-k7 on 2024-01-24
Hi , I've tried what you both recommended with disabling secure boot and device guard and things , but none of the tips are working and my Lenovo laptop doesn't have a boot order lock , Ubuntu isn't showing up at all.

---

### Post by oldfred on 2024-01-24
Can you directly install an UEFI entry using live installer or do you get same locked error?

man efibootmgr
Generic entry
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0nX -p Y

Probably your entry should be:
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

---

### Post by MAFoElffen on 2024-01-25
There are a few things to look for yet.

**Always** check to see if /sys/firmware/efi exists to ensure your are booted as UEFI mode...
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"

```
List the output of efibootmgr -v to ensure what Linux see's there. Look for the Ubuntu .efi files that oldfred listed in his post. If they are not there. Then temp mount the EFI partition, then look what is there using the tree command.
```

sudo efibootmgr -v

```
Check the partitions of all drives to look for  multiple instances of EFI partitions. If there are multiple instances, some UEFI BIOS will only recognize the first one it finds.
```

for n in $(sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq | grep -E '^Disk /dev/' | grep -v /mapper | awk '{print $2}' | sed 's/://g'); do sudo sgdisk -p $n; done

```

---

### Post by oyin-k7 on 2024-01-26
Hi all , it's been solved now , after hours of trying everything recommended and hours of tears it turns out that when I turned off fast boot I forgot to save the changes so that was the problem all along.

Thank you for your time teaforone, Oldfred and MAFoElffen

---

### Post by MAFoElffen on 2024-01-26
LOL. Glad to hear that.

Please use the "Thread Tools" link in the upper right of the page to mark your thread as "Solved".

---

