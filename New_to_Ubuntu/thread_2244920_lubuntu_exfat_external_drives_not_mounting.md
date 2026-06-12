---
title: "lubuntu exfat external drives not mounting"
date: 2014-09-19
forum: New to Ubuntu
---

### Post by ollie3 on 2014-09-19
I have my two old hard drives, taken out of old laptops and one has data on, and one is freshly formatted.  When I try to mount them it says this, they are in a usb portable hard drive enclosure

Error mounting /dev/sdc1 at /media/ollie/F6AA-CC33: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdc1" "/media/ollie/F6AA-CC33"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'

can anyone help me with this please?

---

### Post by yancek on 2014-09-19
How did you try to mount them?  Did you try to access them through the File Manager under the /media directory.  You could try running this command to verify the filesystem type:

parted -l(Lower Case Letter L in the command)

---

### Post by ollie3 on 2014-09-19
they show up as ex-fat hard drives, in the file directory, so it shows a 160gb hard drive but when I click on it it, i get the above eror messege, i'm not sure how to run the cmd you suggest, do |I need to put something in front of parted-l? as when I put that into terminal it ignored it

---

### Post by steeldriver on 2014-09-19
AFAIK exfat is not supported out of the box - you will need to install at least the exfat-fuse package

---

### Post by yancek on 2014-09-19
Sorry, you need:  sudo parted -l

---

### Post by ollie3 on 2014-09-20
ignore that last post just added and then deleted, I forgot to put sudo in front of the utilities cmd, all good now thanks for you time :)

---

