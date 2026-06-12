---
title: "Partition/File Transfer problem"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by django0909 on 2008-05-12
Hi,

Installed 8.04 and ran into a serious problem with it hanging at the kubuntu splash screen. Figured I would run the live CD to get back on line and try to work out what was causing the problem. Eventually decided to reinstall a copy of 6.06 back into another partition in order to try and save some important stuff from the 8.04 partition - which is where I am currently stuck. I can't get the 6.06 partition to see the 8.04 partition. When I can, I want to be able to save the files from the 8.04 partition, drag them over to the 6.06 partition, resize the drive so the whole 80gb is dedicated to the new partition and then perform a live CD install of 8.04, rather than an online upgrade, which seemed to go totally wrong. Regardless, if anyone can help me transfer the files over I would be very grateful. The disk partition information is as follows:

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5466    43905613+  83  Linux
/dev/hda2            9384        9729     2779245    5  Extended
/dev/hda3   *        5467        9383    31463302+  83  Linux
/dev/hda5            9554        9729     1413688+  82  Linux swap / Solaris
/dev/hda6            9384        9553     1365462   82  Linux swap / Solaris

Partition table entries are not in disk order

```

As far as I am sure, hda1 is the 8.04 partition and hda3 is the 6.06 partition.

If anyone can help I would be grateful!

Thanks all.

---

### Post by hermes0710 on 2008-05-12
Can you post the contents of fstab while on 6.06?

---

### Post by django0909 on 2008-05-12
Yup, here you go.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I understand I need to add a new line for hda1, but I'm not 100% sure what to put. Do I then run mount /dev/hda1 from a terminal, and do alt+f2, gksu nautilus to see everything, and transfer over that way?

---

### Post by django0909 on 2008-05-12
Problem solved.

---

### Post by MaxVK on 2008-05-12
If you get a moment post your solution so others can benefit from your experience. ;)

---

### Post by django0909 on 2008-05-12
Sure :)

Please note this might not have been the right thing to do but it worked for me.

I opened fstab in gedit, and added the following:

```
/dev/hda1       /media/old      ext3    defaults
```

I then created a new file from within my 6.06 partition, in /media, and called it 'old'

I then opened a terminal and typed the following:

```
sudo mount /dev/hda1
```

Which enabled me to see the contents of my 8.04 partition in /media/old.

I then physically transferred all the files I wanted to save into the 6.06 partition, and then resized it to fill the rest of my drive :)

If someone can benefit from this then that would be great, I know what a pain it is trawling these forums for an answer to such a specific problem!

---

### Post by MaxVK on 2008-05-13
Nice one thanks. I don't need this information right now, but its good to know that its here if its needed, and I'm sure that others will benefit from this in the not so distant future.

Regards

Max

---

