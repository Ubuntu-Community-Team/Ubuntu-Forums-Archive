---
title: "Dependancy tracker"
date: 2006-05-14
forum: Repositories &amp; Backports
---

### Post by Tortanick on 2006-05-14
I'm considering the feasibility of useing an xbuntu-nautilus combination, and I'm having trouble tracking nautilus's dependancies.

Is there a something that will take a single package, and list its dependancies, and its dependancies' dependancies etc.

---

### Post by Sutekh on 2006-05-15
There is a better way that escapes me, but you could use the simulate function of [B]apt-get

[/B]```
sudo apt-get install -s nautilus
```
Which will list the packages that will be installed to get nautilus working.
```
user@ubuntu:~$ sudo apt-get install -s nautilus
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libbeagle0 libeel2-2 libeel2-data nautilus-data
Suggested packages:
  eog evince pdf-viewer totem mp3-decoder
Recommended packages:
  desktop-base nautilus-cd-burner
The following NEW packages will be installed
**  libbeagle0 libeel2-2 libeel2-data nautilus nautilus-data**
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Inst libbeagle0 (0.2.6-1ubuntu4 Ubuntu:6.06/dapper)
Inst libeel2-data (2.14.1-0ubuntu2 Ubuntu:6.06/dapper)
Inst libeel2-2 (2.14.1-0ubuntu2 Ubuntu:6.06/dapper)
Inst nautilus-data (2.14.1-0ubuntu7 Ubuntu:6.06/dapper)
Inst nautilus (2.14.1-0ubuntu7 Ubuntu:6.06/dapper)
Conf libbeagle0 (0.2.6-1ubuntu4 Ubuntu:6.06/dapper)
Conf libeel2-data (2.14.1-0ubuntu2 Ubuntu:6.06/dapper)
Conf libeel2-2 (2.14.1-0ubuntu2 Ubuntu:6.06/dapper)
Conf nautilus-data (2.14.1-0ubuntu7 Ubuntu:6.06/dapper)
Conf nautilus (2.14.1-0ubuntu7 Ubuntu:6.06/dapper)
user@ubuntu:~$

```

If you want to do things manually, check out [Ubuntu Packages - Nautilus](http://packages.ubuntu.com/breezy/gnome/nautilus)

---

