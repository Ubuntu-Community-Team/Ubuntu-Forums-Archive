---
title: "Help with a simple bash script"
date: 2012-01-18
forum: Programming Talk
---

### Post by cortman on 2012-01-18
I'm still getting my feet wet in bash scripting, and was working, just for fun, on a simple backup script the other evening.
As a test, I'm trying to copy a file called "doug" in my home to the /data/backup folder.
/data is a separate NTFS partition on my HD that I use for storage.
My goal is to have the script look in /data, and if there is a folder called "backup" in it already, rename it "backup.old", create a new "backup" folder, and copy /home/cortman/doug into it.
If there is no folder on /data called backup, I want it to create one and copy /home/cortman/doug into it.


```
if [ -d /home/cortman/data/backup ] ; 
then
mv /home/cortman/data/backup backup.old ;
mkdir /home/cortman/data/backup ;
cp /home/cortman/doug /home/cortman/data/backup ; 
else
mkdir /home/cortman/data/backup ; 
cp /home/cortman/doug /home/cortman/data/backup ; fi
```

The problem:

I run it once, with no existing backup folder. It works great.
I run it a second time. It copies the old ~/data/backup folder into my main ~/ folder and renames it backup.old, and makes a new backup folder in ~/data.
I run it a third time. Now it moves the old ~/data/backup folder into ~/backup.old, and makes a new backup folder in ~/data.
I run it a fourth time, and get an error- 

> mv: cannot move `/home/cortman/data/backup' to `backup.old/backup': Directory not empty
mkdir: cannot create directory `/home/cortman/data/backup': File exists

Sorry if tl;dr, or if I'm doing it all wrong or missing something totally obvious. Any input would be greatly appreciated!

---

### Post by sudodus on 2012-01-18
> **cortman said:**
> ...
```
if [ -d /home/cortman/data/backup ] ; 
then
mv /home/cortman/data/backup backup.old ;
mkdir /home/cortman/data/backup ;
cp /home/cortman/doug /home/cortman/data/backup ; 
else
mkdir /home/cortman/data/backup ; 
cp /home/cortman/doug /home/cortman/data/backup ; fi
```

The problem:
...
I run it a fourth time, and get an error
```
mv: cannot move `/home/cortman/data/backup' to `backup.old/backup': Directory not empty
mkdir: cannot create directory `/home/cortman/data/backup': File exists
```

One thing that might create an error is that you have a relative path in the move-target. This would be better:
```
mv /home/cortman/data/backup /home/cortman/backup.old
``` but maybe your main problem is that you should delete the old directory before the move command. So maybe this script would work
```

#! /bin/bash

if [ -d /home/cortman/data/backup ]
then
 rm /home/cortman/backup.old
 mv /home/cortman/data/backup /home/cortman/backup.old
 mkdir /home/cortman/data/backup
 cp /home/cortman/doug /home/cortman/data/backup
else
 mkdir /home/cortman/data/backup
 cp /home/cortman/doug /home/cortman/data/backup
fi

```

By the way, [FONT="Courier New"][SIZE="3"]rsync[/SIZE][/FONT] is a more powerful alternative than [FONT="Courier New"][SIZE="3"]cp[/SIZE][/FONT] for this kind of task. Read
```
man rsync
```

---

### Post by cortman on 2012-01-18
Thanks! I added rm, then added the -r flag and it seems to be working. I get an error message initially when there's no backup.old to remove, but the rest of the script still operates.
I'm planning to look into rsync probably too, but this was just kind of an exercise, as I'm trying to learn bash scripting better.

---

### Post by sudodus on 2012-01-18
> **cortman said:**
> Thanks! I added rm, then added the -r flag and it seems to be working. I get an error message initially when there's no backup.old to remove, but the rest of the script still operates.
I'm planning to look into rsync probably too, but this was just kind of an exercise, as I'm trying to learn bash scripting better.
That's right, I forgot about -r to remove also the subdirectories. I'm glad you found it yourself.
Furthermore, you might add
```
-f, --force
       ignore nonexistent files, never prompt

``` making it ```
rm -rf /home/cortman/backup.old
``` to make it not complain.

Good luck with rsync :-)

---

