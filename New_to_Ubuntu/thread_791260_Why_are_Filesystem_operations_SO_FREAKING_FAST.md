---
title: "Why are Filesystem operations SO FREAKING FAST?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by zigx on 2008-05-12
I might be smoking crack (though im pretty sure im not) BUT it seems like any kind of IO operations on ubuntu are lightening fast compared to Windows.

Using the exact same hardware i might add (partition).

Thinks like extracting zips, moving files around, even moving files to my MP3 player seem much much faster.

Can anyone help me understand why this is?  

In the past i started a similar thread but i would like to revive this discussion with current information as i know things like the gnome FS are new in hardy, etc.

---

### Post by Alien.col on 2008-05-12
Yes i've noticed that too the speeds at which Ubuntu unpacks, packs and moves files around is incredibly superior to Windows.

---

### Post by tjwoosta on 2008-05-12
ubuntu is much faster than windows because it uses much less ram and cpu 

(meaning there are more resources available to perform the tasks that you are doing)

---

### Post by Seti on 2008-05-12
Also, have a look at file-system your discs are,
```
sudo cfdisk
```
I'm pretty sure that ext3, reiserfs and the like are a lot more efficient than NTFS.

---

### Post by zigx on 2008-05-13
are there any cold hard facts or is this speculation?

---

### Post by scorp123 on 2008-05-13
> **zigx said:**
> are there any cold hard facts or is this speculation? There is a similar thread here, e.g. Linux file structure vs. Windows file structure and why Windows sucks and UNIX FHS is superior:
[http://ubuntuforums.org/showthread.php?p=4897193#post4897193](http://ubuntuforums.org/showthread.php?p=4897193#post4897193)

And then you might want to read this:

"Why doesn't Linux need defragmenting?"
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

To answer your question: Linux filesystems are faster because they try very hard to avoid fragmentation from happening in the first place whereas Windows makes no such attempts at all.

---

### Post by zigx on 2008-05-17
ill def check those out, thanks a lot scorp

---

