---
title: "[SOLVED] what is the filesystem of linux?"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by mdialogo on 2008-08-09
i am familiar with windows, but not with linux. i just want to learn some basic info about linux like its file system, does linux also have drives like c:, d:, and other fundamental info. any links?

---

### Post by zachtib on 2008-08-09
> **mdialogo said:**
> i am familiar with windows, but not with linux. i just want to learn some basic info about linux like its file system, does linux also have drives like c:, d:, and other fundamental info. any links?

well, there are a lot of filesystems on linux. ext3 is the default on ubuntu, but there's also reiserfs, XFS, etc.

Also, it doesn't use drive letters, but mountpoints.  your main disk is mounted at / and the rest of the drives are mounted beneath it.
For example, I have drives mounted at /home and /media/storage

---

### Post by pi.boy.travis on 2008-08-09
Ubuntu's default is ext3, but it can use just about any file system you can think of.

---

### Post by demiurgicdaemon on 2008-08-09
[http://www.freeos.com/articles/3102/]("http://www.freeos.com/articles/3102/")

still relevant so should be a nice quick overview.

---

### Post by mdialogo on 2008-08-09
how about folders? does linux has folders like windows? can you give some links on fundamentals of linux? thanks...

---

### Post by pi.boy.travis on 2008-08-09
Yes, Linux has folders just like Windows.  As far a working with files, folders, archives, etc., Linux and Windows aren't that different.

---

### Post by Squid Tamer on 2008-08-09
You might hear folders called "directories" though. They are different words for the same thing.

---

### Post by phrostbyte on 2008-08-09
> **mdialogo said:**
> how about folders? does linux has folders like windows? can you give some links on fundamentals of linux? thanks...

Why don't you give Ubuntu a try for yourself? There is a LiveCD you can download that won't affect stuff on your computer.

---

### Post by John.Michael.Kane on 2008-08-09
> **mdialogo said:**
> how about folders? does linux has folders like windows? can you give some links on fundamentals of linux? thanks...

Here are some starting points.
[Filesystem_Hierarchy_Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")
[Home_directory]("http://en.wikipedia.org/wiki/Home_directory")
[Root_directory]("http://en.wikipedia.org/wiki/Root_directory")

---

### Post by SunnyRabbiera on 2008-08-09
> **mdialogo said:**
> how about folders? does linux has folders like windows? can you give some links on fundamentals of linux? thanks...

all operating systems have directories/ folders of some sort.

---

### Post by scorp123 on 2008-08-09
> **SunnyRabbiera said:**
> all operating systems have directories/ folders of some sort. MS-DOS 1.x back in 1981 didn't ;)  .... "UNIX-style" (sub-)directories were introduced as something "completely new" with MS-DOS/PC-DOS 2.x back in 1983 ... :D

---

