---
title: "cli - tech difficulties.  making bootable dvd"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-19
ok so I am  following the steps in this link :[http://ubuntuforums.org/showthread.php?t=688872&page=12](http://ubuntuforums.org/showthread.php?t=688872&page=12)   I was converting the directory tree into a squashfs and it just ceased:

adamogardner@CRONUS:~$ sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT}
sudo: unable to resolve host CRONUS
Parallel mksquashfs: Using 2 processors
Creating little endian 3.1 filesystem on //filesystem., block size 131072.
[============================                              ]  73842/149545  49%

so I opened a new tab and tried it again but to no avail:

adamogardner@CRONUS:~$  sudo mksquashfs ${WORK}/rootfs ${CD}/${FS_DIR}/filesystem.${FORMAT}
sudo: unable to resolve host CRONUS
Can't find a SQUASHFS superblock on //filesystem.
Failed to read existing filesystem - will not overwrite - ABORTING!
To force Mksquashfs to write to this block device or file use -noappend
adamogardner@CRONUS:~$ 

Is my disk too small?  how can I tell?  What can I do?

---

### Post by hyper_ch on 2008-07-19
why don't you post in that thread?

---

### Post by adamogardner on 2008-07-19
what thread?

---

### Post by hyper_ch on 2008-07-19
the one you mentioned

---

### Post by adamogardner on 2008-07-19
oh I never thought of that.

---

