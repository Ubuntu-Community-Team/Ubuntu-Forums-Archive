---
title: "Grub How Enable WIndows Operating System"
date: 2014-03-22
forum: New to Ubuntu
---

### Post by MIraan_Baloch on 2014-03-22
HI,
I have insttaled windows 7 than installed ubuntu 13.10 now when i am starting my pc grub loader not appeared and ubuntu is default operating system in my computure, can anyone help me to enable the grub loader and windows operating system i need both operating systems to run on my computer, thanks be quick

---

### Post by david98 on 2014-03-22
Follow the instructions on here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) easy fix.

---

### Post by su:bhatta on 2014-03-22
When you enter a Ubuntu session open a Terminal and run  this command

```
sudo update-grub
```

It should update grub and you should be able to see that Windows partition is recognized.
Just to be safe, you can mount the WIndows partition before you run the command on Terminal.
Reboot and Grub should give you the choice of Ubuntu or Windows at startup.

If that doesn't work, go for Boot repair, as suggested by david98.

---

### Post by gjohnz on 2014-03-22
A solution that almost always works for me in these cases is to mount the Windows partition before updating grub. You would first need to find out what partition Windows resides on. It is usually /dev/sda1, but to be sure you can use sudo in the terminal to find out.
```
 sudo fdisk -l
```
Assuming that Windows is in fact on /dev/sda1 you would then mount that partition under your Ubuntu system. Of course you need to replace /dev/sda1 with whatever partition number fdisk tells you Windows resides on.
```
sudo mkdir /temp
sudo mount -t ntfs-3g /dev/sda1 /temp
```
Then update grub.
```
 sudo update-grub
```
Now unmount the Windows partition and remove the temp folder *if so desired*.
```
sudo umount /temp
sudo rm -rf /temp
```
Reboot and see if you have a Windows entry in your boot menu.

---

### Post by ajgreeny on 2014-03-22
Let's just hope that you didn't overwrite the Windows partition when you installed Ubuntu; it happens more often than you might think, depending on the method you chose for the ubuntu install.

gjohnz's first command will tell us a lot more.

---

### Post by MIraan_Baloch on 2014-03-22
THanks for help me, solved

---

