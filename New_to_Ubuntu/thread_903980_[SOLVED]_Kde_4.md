---
title: "[SOLVED] Kde 4"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by bgast1 on 2008-08-28
To install the latest KDE 4 in Ubuntu Hardy Heron Gnome, do I have to update my sources list?

---

### Post by tuxxy on 2008-08-28
Heres a [guide]("http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml")

---

### Post by SuperSonic4 on 2008-08-28
I think you can just type ```
sudo aptitude install kubuntu-kde4-desktop
``` although you can replace desktop with core if you don't want KDE4's apps.

I think it is because the sources are included by default in hardy

---

### Post by Crafty Kisses on 2008-08-28
First you need to edit the **/etc/apt/sources.list **file

```
sudo gedit /etc/apt/sources.list
```

add the following line

```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
```

Save and exit the file

Update the source list using the following command

```
sudo aptitude update
```

Install KDE 4.0 in Ubuntu

First you need to remove any exiting kde4 using the following command

```
sudo aptitude remove kdelibs5 kde4base-data kde4libs-data
```

Now install kde4.0

```
sudo aptitude install kde4-core
```

This will complete the kde4.0 installation.

---

### Post by tuxxy on 2008-08-28
If you plan to install it with that command, you may want to remove KDE 3 first

```
sudo apt-get remove --purge kdebase-bin-kde3
```

---

