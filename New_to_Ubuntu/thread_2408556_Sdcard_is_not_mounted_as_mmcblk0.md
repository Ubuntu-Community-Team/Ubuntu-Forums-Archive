---
title: "Sdcard is not mounted as mmcblk0"
date: 2018-12-19
forum: New to Ubuntu
---

### Post by bigdrago on 2018-12-19
Hi.
I need to know the CID of my simcard.
I insert the sdcard and type df.

The sdcard shows as /media/ubuntu/1F01-1972

But I need to make it show like mmcblk0 to read CID.
This is the command to type to read CID:

"cat /sys/block/mmcblk0/device/cid"

I have tried to insert the card into macbook air and asus laptop.

Any ideas? Using ubuntu 18.04.1 LTS from usb memory pen.

---

### Post by jazzrock71 on 2019-02-05
HI,
I have the same problem. Any idea?

Thanks

---

### Post by Holger_Gehrke on 2019-02-05
You don't mount the device, you mount the filesystem(s) on the device. The directory into which a file system is mounted is named either for the volume label or (if no label exists) for the UUID of the file system. This is done because one device can contain multiple file systems (think partitions ...). So the only situation where a card will be mounted as 'mmcblk0' would be if you gave a file system the label 'mmcblk0'. 

To find out the device name for a mounted file system, you can run 'mount|grep "1F01-1872"' (search the output of mount for the name of the directory). This will output a line that looks like 
```
/dev/something on /media/ubuntu/1F01-1872 type somethingElse (lotsOfOptions)
```
For a card reader connected through PCI the "something" will be mmcblkXpY (with X the number of the card reader and Y the number of the partition). You can then look at the pseudo-file containing the CID with the command quoted in the original post, perhaps substituting the value of X for the 0 in "mmcblk0". If "something" looks like "sdXY" (with X a letter and Y a digit), then your card reader is connected through USB and you can't access the CID because USB card readers don't make that information available.

Holger

---

