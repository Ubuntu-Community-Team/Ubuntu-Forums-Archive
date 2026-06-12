---
title: "How do I access another partition from the terminal?"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by TheGuyWithTheFace on 2012-04-16
The title's fairly self explanatory, I know how to change the working directory to / of my main partition, but not / on another partition. I know it's possible, I can see it in the file GUI, so it must be possible, right?

---

### Post by Bucky Ball on 2012-04-16
If you had, for instance, a separate /home partition you would simply issue:
```

cd /home
```

If you're mounting a partition somewhere on boot (with fstab say), for instance /home in /media, you would issue:
```

cd /media/home
```

---

### Post by sudodus on 2012-04-16
1. The first step is to mount a partition.

This is done more or less automatically depending on what kind of partition it is. Most partitions are easily mounted with the file browser. You can mount it manually with the ***mount*** command line tool, or you can mount it automatically via an entry in /etc/fstab (which calls mount to do the job).

2. The second step is to go to the partition, to change directory, ***cd***, to it.

First check which partitions are mounted with the command ***df***, yes it is that simple
```
df
``` It will show which partitions (file systems) that are mounted on which directory in the file system. Adding to *Bucky Ball*'s list, I suggest the removable devices (for example partitions on USB drives), that are often auto-mounted on ***/media/some-name***.

In that case use the cd command to go there
```
cd /media/some-name
``` and list the files and subdirectories with ***ls*** (or long format) ```
ls -l
```
or view a text file with ***less*** directly without 'going there' ```
less /media/some-name/file.txt
```

---

### Post by oldos2er on 2012-04-16
> **TheGuyWithTheFace said:**
> The title's fairly self explanatory, I know how to change the working directory to / of my main partition, but not / on another partition. I know it's possible, I can see it in the file GUI, so it must be possible, right?

Gnome 2.x used to have an add-on for Nautilus called nautilus-open-terminal that made this easy. I don't know if it's available for Gnome 3.x and/or Unity, but you could check in the Software Center.

---

### Post by TheGuyWithTheFace on 2012-04-19
Cool, thanks for explaining that! As you can see, I know pretty much nothing about the terminal...

---

### Post by Cheesemill on 2012-04-19
If the partition is one that you have mounted by clicking on it in the file manger then it is mounted in a folder under the hidden .gvfs folder in your home directory.
```
cd ~/.gvfs
```

---

### Post by jerome1232 on 2012-04-19
> **Cheesemill said:**
> If the partition is one that you have mounted by clicking on it in the file manger then it is mounted in a folder under the hidden .gvfs folder in your home directory.
```
cd ~/.gvfs
```
Not to muddy the waters.. but..

Well... erm... kinda, that's largely for things such as network shares, which don't get a traditional mount points when done via nautilus, real partitions, however, get real mount points under /media, unless designated otherwise by fstab.

Something like sftp://me@myserver/home/me (Thats what you would get if you used nautilus' "connect to server" feature using ssh) would be found under .gvfs and nowhere else.

---

