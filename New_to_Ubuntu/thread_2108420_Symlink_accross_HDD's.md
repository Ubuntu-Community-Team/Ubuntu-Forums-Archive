---
title: "Symlink accross HDD's?"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by Elitenoname on 2013-01-24
So i am dual booting Ubuntu and Windows 7, I know that in ubuntu you browse the Windows 7 partition and it comes up as a removable device. i was wondering if there was a way you can create a symlink from say the Downloads folder in the windows 7 partition to the /home/user/Downloads folder in ubuntu? and would the data be doubled or would it all be on side of that symlink?

---

### Post by sudodus on 2013-01-24
> **Elitenoname said:**
> So i am dual booting Ubuntu and Windows 7, I know that in ubuntu you browse the Windows 7 partition and it comes up as a removable device. i was wondering if there was a way you can create a symlink from say the Downloads folder in the windows 7 partition to the /home/user/Downloads folder in ubuntu? and would the data be doubled or would it all be on side of that symlink?
Yes, you can use symlinks between different partitions, even if they are on different drives. (But you cannot use hard links.)

See ```
info ln
```

When you create a link in a file browser (Nautilus, Thunar, PCmanFM ...) it will be a symbolic link.

The data will *not* be doubled.

---

### Post by Elitenoname on 2013-01-24
Alright how would the data be stored on that? if i save a file onto the drive in windows 7 would it physicaly be in the ubuntu folder as well or would just be a link point to that file and would be opened with the path of the windows partition?

---

### Post by sudodus on 2013-01-24
The symbolic link is a small file containing only the information how to link the request to where the data is residing. So the file data resides only at the target of the link.

For example:

You have Windows on /dev/sda mounted on /media/win7
and you have a file

/media/win7/Users/elitenoname/Documents/file.txt

Then you link to it with
```
ln -s /media/win7/Users/elitenoname/Documents/file.txt /home/elitenoname/Documents/winfile.txt
```

or you link to the whole directory with
```
ln -s /media/win7/Users/elitenoname/Documents /home/elitenoname
```

---

### Post by sudodus on 2013-01-24
But if you want to share a partition between Windows and Ubuntu it is better to have a separate data partition. It can be an NTFS partition.

It is safer with a separate data partition. It is possible to write from linux into the windows system partition but not quite safe. Reading is OK.

---

