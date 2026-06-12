---
title: "Searcing for Files by File Size"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by cforput on 2008-06-08
Newbie here. My hard drive is full and I can't figure out why. In windows, you could use explorer (file manager) to search for files based on size. How do you do that in Nautilus?

---

### Post by SunnyRabbiera on 2008-06-08
In nautilus you can go to "view" then to "arrange items" then "by size"

What is your hard drive size? your partition size?

---

### Post by cforput on 2008-06-10
HDD size is 160 GB but I am using dual boot still. I have a few more apps to get converted (if I can) and then run for a while solely on Ubuntu. If successful, I will put all 160GB toward Ubuntu.

I have 3 partitions. 1 for XP, 1 for Ubuntu and 1 for both were I store data. 

I don't think I was clear last time in what I am looking for. I have been doing some work on some DVDs I have and a bunch of times I had to force quit. I wanted to search my HDD for all files over 100MB (as an example). In Explorer, there was an option to search for files with file size parameters. This way, I could find all large files and determine if I needed them or not. If I had to force quit, it is possible that the app left some incomplete DVD images that could be substantial in size.

Is there a way to search your entire HDD (or at least the part you have access to) and look for files greater than 100MB?

---

### Post by bluepowder7 on 2008-06-10
places - search for files
name contains = <blank> or *
look in folder = filesystem
select more options
-> follow symbolic links, click ADD
-> size at least ...., click ADD
enter size, hit find

---

### Post by iaculallad on 2008-06-10
Or you could do it using the ever-powerful terminal:

```
find . -type f -size +1024k -exec ls -lh {} \;
```

+/-1024k represents the size of the file you want to search.

---

### Post by cforput on 2008-06-10
> **bluepowder7 said:**
> places - search for files
name contains = <blank> or *
look in folder = filesystem
select more options
-> follow symbolic links, click ADD
-> size at least ...., click ADD
enter size, hit find

Bluepowder7, this is exactly what I needed. Thanks. Case solved!

---

### Post by unutbu on 2008-06-10
Click Applications>Accessories>Disk Usage Analyzer
Click Scan Filesystem

This gives a pie-shaped graphical representation of the relative size of folders on your hard drive. It is an amazingly useful tool for visualizing where all your HD space has gone.

---

