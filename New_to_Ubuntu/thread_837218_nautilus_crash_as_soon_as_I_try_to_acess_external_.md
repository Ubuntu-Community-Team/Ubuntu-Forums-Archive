---
title: "nautilus crash as soon as I try to acess external hd"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by borgrodrick on 2008-06-22
Nautilus is crashing when I try to open the directory of an external hard disk. It shows the data of the hard disk (files & folders) then it becomes unresponsive... The CPU usage spikes up and after waiting some time it asks me whether to Force Quit and Cancel...

Does anyone knows what`s wrong??

---

### Post by Troll_the_Great on 2008-06-22
What format is the disk?NTFS?If yes you should install ntfs-config.Have a look here:[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
Hope this helps.
Cheers!

---

### Post by borgrodrick on 2008-06-22
The drive is formatted in fat32 format

---

### Post by sayakb on 2008-06-22
Open nautilus via terminal, and then open the USB Harddrive. Post any error messages you get there.

---

### Post by NilsE on 2008-06-22
This may be related to an existing nautilus and gvfs file system problem.  If so opening nautilus like this may help.

dbus-launch nautilus

---

### Post by borgrodrick on 2008-06-24
I didn`t get any errors when I tried to open nautilus in command line. Also when I used dbus-launch nautilus it also didn`t work out. 

I noticed that the problem is present only with a specific external hd. If I try another external hd it works perfectly... 

Also this external hd (that is giving me errors in ubuntu) works oki in any other OS (Windows and Linux)

---

