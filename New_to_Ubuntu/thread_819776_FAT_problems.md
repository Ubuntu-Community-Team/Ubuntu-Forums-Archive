---
title: "FAT problems"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by takuhii on 2008-06-05
it would seem ubuntu is refusing to mount ANY memory pens that are fat (16/32) formatted. This used to work, but now it doesn't.

When I plug the memory pen/stick in, I get this popup

CANNOT MOUNT VOLUME.
Invalid mount option when attempting to mount the volume.

Any ideas?

---

### Post by tamoneya on 2008-06-05
try being explicit about it:```
sudo mount -t vfat /dev/sdb1 /media/USB
```

---

### Post by phidia on 2008-06-05
With the drive still plugged in does dmesg | tail or sudo fdisk -l (typed at a terminal) provide any useful error messaging about the drive?

---

### Post by takuhii on 2008-06-06
sudo fdisk -l produces this...

Disk /dev/sde: 1997 MB, 1997799424 bytes
62 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot Start End Blocks Id System
/dev/sde1 ? 202429 499388 570754815+ 72 Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
phys=(357, 116, 40) logical=(202428, 43, 11)
Partition 1 has different physical/logical endings:
phys=(357, 32, 45) logical=(499387, 30, 51)
Partition 1 does not end on cylinder boundary.
/dev/sde2 ? 43884 547534 968014120 65 Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
phys=(288, 115, 43) logical=(43883, 52, 47)
Partition 2 has different physical/logical endings:
phys=(367, 114, 50) logical=(547533, 14, 42)
Partition 2 does not end on cylinder boundary.
/dev/sde3 ? 486442 990091 968014096 79 Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
phys=(366, 32, 33) logical=(486441, 36, 30)
Partition 3 has different physical/logical endings:
phys=(357, 32, 43) logical=(990090, 59, 39)
Partition 3 does not end on cylinder boundary.
/dev/sde4 ? 750698 750712 27749+ d Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
phys=(372, 97, 50) logical=(750697, 30, 25)
Partition 4 has different physical/logical endings:
phys=(0, 10, 0) logical=(750711, 57, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order.

I have even re-formatted the drive in Ubuntu, and no luck, ANYTHING related to FAT is just causes an error (FAT16/32). The pen will work fine in EXT3 and everything else (even REISERFS), and automount perfectly. It's almost as though the FAT support has broken...

---

### Post by Duck2006 on 2008-06-06
> **takuhii said:**
> it would seem ubuntu is refusing to mount ANY memory pens that are fat (16/32) formatted. This used to work, but now it doesn't.

When I plug the memory pen/stick in, I get this popup

CANNOT MOUNT VOLUME.
Invalid mount option when attempting to mount the volume.

Any ideas?

Did you last use it in windoze and not do a safe removal?

---

### Post by The Cog on 2008-06-06
That doesn't look like a proper partition table. When you reformatted it, did you **mkfs /dev/sde1** or did you **mkfs /dev/sde** ? I wonder if you formatted the drive as a filesystem rather than formatting a partition. If so, you should still be able to mount it with:
**sudo mount -t vfat /dev/sde /media/USB**, and probably don't even need the "-t vfat". 

If that doesn't recognise it, then I suggest you repartition it with something like gparted.

---

### Post by takuhii on 2008-06-06
yeah, when I partitioned it with GParted, anything FAT related errors out.

---

