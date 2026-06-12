---
title: "Permanently mount hard disks and partitions"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by wordmagic on 2008-11-17
I have some disks and partitions with Disk Mounter but when i reboot they are unmounted; is there anyway that they remain mounted?

---

### Post by nickcannard on 2008-11-17
if they are NTFS partitions, you can use a utility called "ntfs configuration tool"
install it from the add/remove programs

it basically edits your fstab for you. 
If you are not trying to mount an NTFS drive, then you will have to edit your fstab file manualy, located in /etc/fstab.
there are many tutorials available, just pick one from google :)

FYI: open terminal and type:
sudo gedit

this will allow you to modify system files in the text editor

---

### Post by wordmagic on 2008-11-17
Thanks, it worked!

---

