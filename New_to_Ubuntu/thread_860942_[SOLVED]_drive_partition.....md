---
title: "[SOLVED] drive partition...."
date: 2008-07-16
forum: New to Ubuntu
---

### Post by surendar164 on 2008-07-16
i installed Ubuntu 7.0 from digit Dvd...

i had 80 GB HD(with 30 gb raw: remaining for Win 2000)....

i selected the option "Take max contiguous space" n successfully installed...

may i know where exactly Ubuntu s now installed?(i am able to see my windows partition in Ubuntu).i also want to know about file system of Ubuntu and how it can read my NTFS partition??

---

### Post by WRDN on 2008-07-16
Open the Terminal and type:

```
sudo fdisk -l
```

Enter your password and the partitions will be listed, allowing you to see where Ubuntu is located.
With regards to accessing a Windows partition, Ubuntu includes the ntfs-3g driver which allows it to read and write to an NTFS Partition.

---

### Post by cariboo on 2008-07-16
Ubuntu is installed on the 30gb of empty space you had on your hard drive. The installer created two partitions in the empty space. "/" is the root partiton where all  the Ubuntu files are located and swap which is similar to the windows page file. The reason you can see your win 2k files is that they are on a differet partition from Ubuntu. Linux does not use drive letters the way windows does. To see the different partions open a Applications-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

This will give you a listing of the partitons and how they are formatted and their sizes.

Jim

---

### Post by Ryadt on 2008-07-16
I just want to add that the file system Ubuntu uses is ext3.

---

### Post by Canis familiaris on 2008-07-16
The Ubuntu partition is mounted at /.

Press Alt + F2:
type /

Also if you want those Computer, Trash, etc.icons on the desktop:
Alt+F2
```
gconf-editor
```
Go to Apps->Nautlius->Desktop.
In the right pane select the icons you wish to view.

---

### Post by surendar164 on 2008-07-17
thank u fellas...

i know open source forums always rocks......instant as well as correct replies....

c u soon:):)

---

### Post by meindian523 on 2008-07-17
Also check out this graphic,explains the Linux filesystem.

---

