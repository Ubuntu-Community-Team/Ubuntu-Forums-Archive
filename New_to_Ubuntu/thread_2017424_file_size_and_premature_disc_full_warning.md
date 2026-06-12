---
title: "file size and premature disc full warning"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by Puzzleman on 2012-07-05
Why does my file
"Ubuntu/file system/proc/kcore"
read as having a file size of 140.7 TB or (140,737,486,266,368 bytes)  ?

This is obviously far larger than my hard drive. Could it be related to a message that I am running out of space and cannot load anymore files?  I deleted a few things and the computer is running normally again but I seem to be limited to about 100 Gigabytes even though I am partitioned for 375 Gigabytes more or less?

Any help with either question would be appreciated.

Puzzleman

---

### Post by matt_symes on 2012-07-05
Hi

> **Puzzleman said:**
> Why does my file
"Ubuntu/file system/proc/kcore"
read as having a file size of 140.7 TB or (140,737,486,266,368 bytes)  ?

Mine is big as well. This is not a problem.

```
[matthew@matthew-aspire7450 ~]$ ls -lh /proc/kcore 
-r--------. 1 root root 128T Jul  5 14:12 /proc/kcore
[matthew@matthew-aspire7450 ~]$
```kcore is not connected with on disk storage but is the kernel memory  space. I have to say, i'm not sure why it's reporting the size it is but it's not consuming disk space.

The /proc filesystem is a virtual file system and the file only  gets "created" when you read from it.

It should have  nothing to with with your hard drive space.

> This is obviously far larger than my hard drive. Could it be related to a message that I am running out of space and cannot load anymore files?  I deleted a few things and the computer is running normally again but I seem to be limited to about 100 Gigabytes even though I am partitioned for 375 Gigabytes more or less?

Any help with either question would be appreciated.

PuzzlemanOpen a terminal and type

```
df -h
```Post the output back here between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```Kind regards

---

### Post by Puzzleman on 2012-07-05
Thank you for the info and answer to the question re "kcore" file size.

re: terminal df -h
Here is what posted.
                                  

Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       18G   10G  6.5G  61% /
udev                   1.8G  4.0K  1.8G   1% /dev
tmpfs              741M  824K  740M   1% /run
none                 5.0M       0     5.0M   0% /run/lock
none                 1.9G  224K  1.9G   1% /run/shm
/dev/sda5       350G   52G  299G  15% /host
/dev/sda2       350G   19G  331G   6% /media/Ubuntu


I then went back and tried to load the files which caused the "premature" disc full message and the file loaded without any problem.


I think the problem is fixed so thanks again.


Puzzleman

---

### Post by matt_symes on 2012-07-06
Hi
> 
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       18G   10G  6.5G  61% /
udev                   1.8G  4.0K  1.8G   1% /dev
tmpfs              741M  824K  740M   1% /run
none                 5.0M       0     5.0M   0% /run/lock
none                 1.9G  224K  1.9G   1% /run/shm
/dev/sda5       350G   52G  299G  15% /host
/dev/sda2       350G   19G  331G   6% /media/Ubuntu

This is a WUBI install ? 

You still have 6.5G on the loop file. That should be plenty.

Maybe just a glitch there.

Kind regards

---

### Post by ischliky on 2012-07-13
I am having a similar issue.  I am going using it through Virtualbox but I am unsure how that would cause such a huge file to exist. also 140.7 TB.

here is the result of running: df -h

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       4.0G  3.8G  4.0K 100% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           792M  896K  791M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   92K  2.0G   1% /run/shm
```

I have had this install up and running for approx 20 mins before this occurred.  Really the only setup that was done from the initial defaults was that I mounted a NAS folder as obviously I do not have a lot of space on this install and all my files are kept remotely.

---

### Post by Cheesemill on 2012-07-13
Seeing as Ubuntu requires at least 5GB of HD space for an installation it's no wonder you're short of space with only a 4GB root partition.

---

