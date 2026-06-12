---
title: "get free harddisk space in c program"
date: 2009-02-04
forum: Programming Talk
---

### Post by monkeyking on 2009-02-04
If I want system info about my memory I can simply read the 
[PHP]/proc/mem_info[/PHP]
If I want system info about my cpu usage I can simply read the first line in
[PHP]/proc/stat[/PHP]

Are there no simple way to get the information about the harddisk usage.
Similar to the first line in the output of df

thanks in advance

---

### Post by stroyan on 2009-02-04
You can find the mounted file systems by reading /etc/mtab.

You can find the free and used space of each file system by calling statfs() for each mount point.

---

### Post by monkeyking on 2009-02-11
Hey, thanks for your reply, but I ended up doing something like this.

[PHP]
#include <sys/statvfs.h>
...
float perc = (100*(1-(float)diskinfo.f_bavail/diskinfo.f_blocks));
[/PHP]
perc will then be a number between 0-100 with the current percentage of diskusage.

---

