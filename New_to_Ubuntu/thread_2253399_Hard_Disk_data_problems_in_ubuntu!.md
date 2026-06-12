---
title: "Hard Disk data problems in ubuntu!"
date: 2014-11-19
forum: New to Ubuntu
---

### Post by aminurizam on 2014-11-19
Hi guys. I need help about my hard disk in ubuntu, they didnt read the data from windows which means the hard disk in ubuntu didnt have the file in windows. So im always need to open windows when i need to use file in windows. 
Hope u can help me guys, thanks in advance!

---

### Post by Mark Phelps on 2014-11-19
>  they didnt read the data from windows 

Specifically, which "data" are you talking about? Ubuntu doesn't import ALL the "data" from Windows as part of its setup.

---

### Post by Impavidus on 2014-11-19
It's not exactly clear what you mean. Windows and Ubuntu are on their own separate partition on the hard drive, each having their own file system. Windows cannot read the files on the Ubuntu system, but Ubuntu can read and even write files on the Windows system – provided Windows was properly shut down and is not in hibernation or using fast boot. In your file manager in Ubuntu you should see a list of the available partitions, including the Windows partition. Click them to mount and the file manager should show the files (or give an error message).

---

