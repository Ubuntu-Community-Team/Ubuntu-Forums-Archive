---
title: "Partitions doesn't appear right way during installation"
date: 2014-12-04
forum: New to Ubuntu
---

### Post by Ahmed_Sabry on 2014-12-04
Previously I tried to install Ubuntu on my Laptop And selected install it alongside Windows 7 and click install, then I shocked when I saw that all data of HDD has been deleted and become one partition :(.

 I found a way to recover my data and finally recovered my data addition to Windows 7 data and booting.
This isn't my first try to install Ubuntu I have installed it on my Desktop without any problems
My current problem during install Ubuntu via advanced way of partitioning:

I have HDD of 5 partitions [FONT=century gothic][SIZE=4][COLOR=#333333]
[IMG]http://i.stack.imgur.com/3uvWr.jpg[/IMG][/COLOR]
[/SIZE][/FONT]The second partition is unallocated ( I delete it to install Ubuntu "swap","system","user" )
but when I tried to partition it from Ubuntu I found a different strange partitions table of HDD[FONT=century gothic][SIZE=4][COLOR=#333333]

[IMG]http://i.stack.imgur.com/TXqSf.jpg[/IMG][/COLOR][/SIZE][/FONT]

---

### Post by fantab on 2014-12-04
Post the output of the following from "Try ubuntu":
```
sudo parted -l
```

---

