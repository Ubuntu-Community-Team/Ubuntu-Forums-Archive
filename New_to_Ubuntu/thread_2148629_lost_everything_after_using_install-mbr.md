---
title: "lost everything after using install-mbr"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by srichakradhar on 2013-05-26
[COLOR=#000000]I was dual booting Windows 8 and BackTrack5 but I erased the mbr while using easyBCD. So I tried this..[/COLOR]

[COLOR=#000000]sudo install-mbr -i n -p D -t 0 /dev/[/COLOR][COLOR=Red]sda1
[/COLOR]
[COLOR=#000000]/dev/sda1 was the primary partition in my system which is "System Reserved" for Windows.
When I rebooted my system, it got stuck at the boot logo "HP" and BIOS won't show up even when I pressed the "ESC" to pause start up..
I tried to boot BackTrack5 linux from flash drive, but the flash drive won't get detected, since BIOS itself is not showing up!
 My BIOS version is "Insyde F.66A" and I am using HP pavilion dv4t-1300 CTO notebook PC.
What could be the reason for BIOS not showing up? Can it be fixed??[/COLOR]

---

### Post by lethall1 on 2013-05-26
boot from ubuntu liveCD and reinstall grub2
```
$sudo mount /dev/sdXX /mnt (partition with backTrack)
$sudo mount --bind /dev /mnt/dev
$sudo mount --bind /proc /mnt/proc
$sudo chroot /mnt
#grub-install /dev/sdX (DISK not partition!!!)

```

---

