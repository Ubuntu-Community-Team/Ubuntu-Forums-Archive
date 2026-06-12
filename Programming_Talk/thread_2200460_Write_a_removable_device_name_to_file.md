---
title: "Write a removable device name to file"
date: 2014-01-19
forum: Programming Talk
---

### Post by jimmyh1972 on 2014-01-19
Hi

I have a bash script witch saves files to diffrent flash removables (every time the machines reboot &/or the removable changes its get a diffrent name)
I need some script to write the removable name (witch is mounted in a static path /media/user/SOME DEVICE NAME)
to a file 
the script has to recognize the removable name and echo it to a file (let's say in /home/user/Documents/my_removable.txt)

thanks' to helpers

Jimmi

---

### Post by ajgreeny on 2014-01-19
Much easier to simply label the partition on the removable disk; it will then always mount to the same folder in /media/labelname or /media/user/labelname, depending on which version of ubuntu you are using.

You can label partitions with gparted or terminal, but terminal commands will depend on the filesystem on the removable disk, so I recommend gparted.

---

