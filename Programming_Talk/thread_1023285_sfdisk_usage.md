---
title: "sfdisk usage"
date: 2008-12-27
forum: Programming Talk
---

### Post by Nonno Bassotto on 2008-12-27
I'm using sfdisk in a bash script to partition a usb pendrive. I want to create two primary partitions: the first should be FAT16, 750MB and bootable, the second should be EXT2 and can take the rest of the space. The pendrive is already formatted, but if I understand well, I don't need to delete the existing partitions before declaring a new table. Assume the device name of the pendrive is stored under the variable $device, (so $device might be "sdb" or something like that). Will this script work?

```

sfdisk /dev/"$device" -uM << EOF
,750,6
;
EOF

sfdisk /dev/"$device" -N1 << EOF
,,,*
EOF

mkfs.vfat -F 16 -n readylatex /dev/"$device"1
mkfs.ext2 -b 4096 -L casper-rw /dev/"$device"2

```

Can I save one step by doing
```

sfdisk /dev/"$device" -uM << EOF
,750,6,*
;
EOF

mkfs.vfat -F 16 -n readylatex /dev/"$device"1
mkfs.ext2 -b 4096 -L casper-rw /dev/"$device"2

```

---

