---
title: "Can't boot from pen drive"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by ankitSurfzen on 2013-03-07
Hello,
i am unable to boot from my pen drive since the last few months. Previously,it worked fine but all of a sudden it stopped working. I have read other posts and tried the steps shown but they didn't help. I am in urgent need, please help.

---

### Post by grahammechanical on 2013-03-07
> I am in urgent need, please help.

How can anyone give you urgent help with so little information?  From the information that you do give I guess that the pen drive is broken and you need to replace it. Help us to help you.

---

### Post by vamp774 on 2013-03-07
Check your boot priority in your BIOS.  If your hard drive is first over your thumb drive it will just boot the OS on the disk

---

### Post by black veils on 2013-03-07
another possibility is a corrupted mbr. but this still may not be the problem.

1. my way to deal with that (possibly inefficently) would be to open a file manager, show hidden files, copy all the files on the disk to your hard drive.

2. after that is completely finished, open gparted and locate the usb stick from the top-right selector.

3. right-click and unmount, then delete, and apply.

4. menu >> device >> create partition table

5. create new partition of FAT32 and let it use the entire usb stick, apply.

6. after all is done, you may want to give it a name (label), apply.

7. use the same application as before to remake the bootable disk with the same .iso file you used.

8. after it is done, open file manager, show hidden files, delete all files from the usb stick and replace with the files you copied to hard drive earlier.

---

