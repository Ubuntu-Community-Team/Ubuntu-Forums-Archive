---
title: "Triple-boot Fedora/Ubuntu/Vista"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by MasterSander on 2008-06-15
I just installed fedora after using my dualboot for a while, but I can't access it through Vista, even after installing the IFS ext2/ext3 support. 

Why do I want to do this? I'd like to rename the partition (rename the label) 'cause now it shows up as /1 and I'd like to rename it to fedora. It's also handy to copy files from my /home dir.

Anyone got an idea about how to fix this or how to rename in ubuntu?

---

### Post by adamogardner on 2008-06-15
I'm sorry I can't advise you in you in your situation, but you brong up a serious question of my own.
I didn't know you could access one partition from another.  So when I'm in either Ubuntu or Vista how do I get to and from the other?  I am only familiar with the GRUB, but you seem to suggest there is another way without restarting.

---

### Post by MasterSander on 2008-06-15
Yes there is! In vista you can install IFS drives support to access ext3 file systems and in ubuntu with ntfs-3g you can access any ntfs drive partition, of course you have to mount it, edit /etc/fstab to do this.

First make the dir wherre to mount: sudo mkdir /media/ntfs

Edit /etc/fstab by adding this line : /dev/hda1  /media/ntfs  ntfs  defaults  0 0

If vista is on partition 1

---

### Post by MasterSander on 2008-06-15
Anyone got an idea?

---

### Post by meierfra. on 2008-06-16
```
sudo e2label /dev/sda3 fedora
```

where /dev/sda3 has to replaced by your fedora partition

---

### Post by Jammy4041 on 2008-12-01
To rename your /fedora partion's label, open gparted from a live cd. There will be an option to change the label.

---

