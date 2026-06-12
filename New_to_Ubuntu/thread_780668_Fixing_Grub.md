---
title: "Fixing Grub"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by jerden on 2008-05-03
Fixing Grub
I have Windows Vista Xp and Ubuntu Hardy installed on my laptop I had Vista and XP working fine and booting using Vista Boot Pro now Ive always loved using Ubuntu so I installed it over my pre-existing copy of Gutsy but for some reason now the grub shows Vista and Hardy but not XP ive added it through editing the grub menu but i still does not work.

the roots I have in the Grub list show Ubuntu as hda(0,6) Vista as hda(0,0)

but when I open the Vista and XP hard drives within Ubuntu, Vista shows as hda(0,2) and XP as hda(0,2)_ notice the underscore beside the hda(0,2) why is that?

I have my xp disc here would going into command line through the xp disc and doing fixBoot and fixMBR solve the proble or what should i do?

Sorry I posted this in Hardware and laptops with out realizing as well sorry!

---

### Post by kirios on 2008-05-03
What do you see when you choose the Vista option in the grub menu?

---

### Post by jerden on 2008-05-03
> **kirios said:**
> What do you see when you choose the Vista option in the grub menu?

it loads to another boot menu  with just Vista and the HP Recovery disc

---

### Post by kirios on 2008-05-03
Can you post the output of **sudo fdisk -l** and the contents of **/boot/grub/menu.lst**?

---

### Post by jerden on 2008-05-03
sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ffe8ffe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21700   174302343+   7  HPFS/NTFS
/dev/sda2           21700       24887    25601024    7  HPFS/NTFS
/dev/sda3           24888       28711    30716280    5  Extended
/dev/sda4           28712       30401    13574925    7  HPFS/NTFS
/dev/sda5           24888       25269     3068383+  83  Linux
/dev/sda6           25270       25651     3068383+  82  Linux swap / Solaris
/dev/sda7           25652       28711    24579418+  83  Linux

Disk /dev/mmcblk0: 2007 MB, 2007498752 bytes
29 heads, 28 sectors/track, 4828 cylinders
Units = cylinders of 812 * 512 = 415744 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        4829     1960320+   6  FAT16


and grub boot list is 

## ## End Default Options ##

title		Ubuntu 8.04 Hardy Heron
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=544a3a53-81ad-4692-a4b8-3645a317ab8b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

#title		Ubuntu 8.04, memtest86+
#root		(hd0,6)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=544a3a53-81ad-4692-a4b8-3645a317ab8b ro single
initrd		/boot/initrd.img-2.6.24-16-generic


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
#title		Windows Vista/Longhorn (loader)
#root		(hd0,3)
#savedefault
#makeactive
#chainloader	+1

I hope thats all you wanted

---

### Post by kirios on 2008-05-03
Looks alright. XP should be handled by the Vista bootloader (not grub), so try installing EasyBCD on Vista to fix the XP boot option. 
[http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")

---

### Post by jerden on 2008-05-03
Oh wow that worked thanks a lot!!!

---

