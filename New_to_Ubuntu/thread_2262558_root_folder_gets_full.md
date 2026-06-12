---
title: "root folder gets full"
date: 2015-01-25
forum: New to Ubuntu
---

### Post by bigmakmotorbreath on 2015-01-25
After so many updates my root folder gets too full to operate. I have logged into the file system as SU and I look around but still cannot find any temporary data to delete. I wonder how a routine cleanup could be executed. many Thanks-

---

### Post by Bashing-om on 2015-01-25
bigmakmotorbreath; Hi Welcome to the forum .

What we often see in this condition:
> 
 my root folder gets too full to operate

is a result of many old kernels still residing in /boot .
Before we get hasty and jump to that conclusion, let's have a look.
```

df -h
df -i
cd /
sudo du -sx * | sort -n
cd
dpkg -l | grep linux-

```
If you need to drill down further, use 'cd' to move to a directory of interest then repeat the 'du' command.
The results are in megabytes.

Once this situation is under control, and you know what is going on, we will discuss the general house cleaning - there just is not much required in a linux operating system.


[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by oldos2er on 2015-01-25
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by SeijiSensei on 2015-01-25
When you say "root folder," do you mean the top of the directory tree, or root's home folder /root?  I'm guessing the former.

If /var is on the same filesystem as /, then I'd take a look in /var/log.  Maybe there's some problem on your machine that's generating error messages and filling the log files.

How big is the partition used as /?

---

