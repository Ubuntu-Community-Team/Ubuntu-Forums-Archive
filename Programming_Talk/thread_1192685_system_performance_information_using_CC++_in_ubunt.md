---
title: "system performance information using C/C++ in ubuntu"
date: 2009-06-20
forum: Programming Talk
---

### Post by polarbear12345 on 2009-06-20
well guys i am writing a C program which needs to maintain a log of system uses periodically for ubuntu 8.10
CPU uses
RAM uses etc

however i have got no idea how to implement it  so any help will be useful.........

will i have to code the whole thing , better if i get some software from which i can extract the information???

---

### Post by dwhitney67 on 2009-06-20
That information is tucked away in one of the files in the /proc directory, but I do not have any experience dealing with such.  I know for the memory utilization, the file is /proc/meminfo.  Perhaps the /proc/stat file can offer additional information.

In the distant past, when I was developing something similar for a Solaris workstation, I downloaded the source code for the 'top' application, and used the relevant portions to get the CPU utilization.  I remember this being difficult, so it is probably not the first thing I would try today.

---

### Post by froggyswamp on 2009-06-20
**Discover the possibilities of the /proc directory**

[http://www.linux.com/archive/feature/126718](http://www.linux.com/archive/feature/126718)

---

### Post by monkeyking on 2009-06-20
yeah just read the proc directory,
you can get swap info, mem info , cpu info from this.

But if you need harddrive usage I think you need to use stat/statvfs.h

I once did this systemmonitor program like this,
use the following
```

/proc/stat //cpu
/proc/meminfo //memory

//and the statvfs was something like

float hd_use;
char *filename;
struct statvfs diskinfo
if (!statvfs(filename, &diskinfo)) 
  hd_use = (100*(1-(float)diskinfo.f_bavail/diskinfo.f_blocks));


```

good luck

---

### Post by slavik on 2009-06-20
perl wrappers around other commands, easy and cross-platform.

---

### Post by polarbear12345 on 2009-06-22
well i think it can be done using command htop also..
htop is actually a command line system monitor...
its output can be written in a file for eg:
htop|cat>hello.txt
now one just needs to extract the required value from the file hello.txt

---

