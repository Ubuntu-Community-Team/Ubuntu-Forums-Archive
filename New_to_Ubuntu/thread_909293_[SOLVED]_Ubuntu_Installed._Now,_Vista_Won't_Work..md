---
title: "[SOLVED] Ubuntu Installed. Now, Vista Won't Work."
date: 2008-09-03
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2008-09-03
I have successfully installed Ubuntu in my Lenovo laptop. :^D It is awesome! (And thanks again for those that helped with the partition problem I had in installation!_&#915;L° I am grateful.)
However, when I checked to see of my Windows Vista was still okay, it would not run. Lenovo's "Rescue and Recover 4.0" would run in its stead. How do I make Vista work again?

Thanks again for your time.

Take care.

Sincerely,
RedStarYellowSun

---

### Post by billgoldberg on 2008-09-03
Are you sure you didn't remove your vista partition?

Try the "super grub disk" live cd to boot your vista parition and repair the grub.

---

### Post by RedStarYellowSun on 2008-09-03
"Are you sure you didn't remove your vista partition?

Try the "super grub disk" live cd to boot your vista parition and repair the grub."

I am sorry, I do not know too much about computers. Do you mean I should have partitioned Windows first, and then installed Ubuntu?
What is "super grub disk"? You mean the Ubuntu install disc?

Thanks again.

Take care,
RedStarYellowSun

---

### Post by Nepherte on 2008-09-03
It's possible the entry line for your vista in grub points to the wrong location (partition), assuming your lenovo recovery is on a separate partition. Post the output of your menu.lst file:
```
cat /boot/grub/menu.lst
```

---

### Post by Joeb454 on 2008-09-03
Can you open a terminal (Applications &#8594; Accessores &#8594; Terminal)

and then copy-paste the following into it: ```
sudo fdisk -l
```

You will be asked for your password, enter that - even though it doesn't show you entering it, please keep typing ;) - then hit enter, and paste the output here :)

---

### Post by RedStarYellowSun on 2008-09-03
> **Joeb454 said:**
> Can you open a terminal (Applications &#8594; Accessores &#8594; Terminal)

and then copy-paste the following into it: ```
sudo fdisk -l
```

You will be asked for your password, enter that - even though it doesn't show you entering it, please keep typing ;) - then hit enter, and paste the output here :)

Okay, comrade. Here it is:

Border 010101011101010010101010101010101010101101011010100101 Border

"Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x726345d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         820     6580224   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         820        9995    73698242+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            9995       19457    76008240    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5            9995       19066    72863248+  83  Linux
/dev/sda6           19066       19457     3144928+  82  Linux swap / Solaris

Disk /dev/sdb: 1998 MB, 1998585856 bytes
16 heads, 32 sectors/track, 7624 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7624     1951728    e  W95 FAT16 (LBA)"

Border 01001101010101010010101000010101001010100101001111010101Border

Thanks for your time.

Take care.

Sincerely,
RedStaYellowSun

---

