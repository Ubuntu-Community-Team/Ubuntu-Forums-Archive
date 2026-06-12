---
title: "I need good documenting software recommendations."
date: 2018-12-25
forum: Programming Talk
---

### Post by Blix775 on 2018-12-25
I am currently building an application in .Net Core in MVC and I need some programs that will work in Ubuntu to create the following things:
[LIST]
[*]Entity Relationship Diagram
[*]Data Dictionary
[*]Data Flow Diagram
[*]Unified Modeling Language
[/LIST]
I have googled but I have not found something I like. I was checking out Umbrello and it seems it is no longer under development. So can anyone give me any recommendations?
I am using Ubuntu Budgie 18.04.

---

### Post by spjackson on 2018-12-26
Perhaps dia will be of interest - except for the Data Dictionary.

---

### Post by Blix775 on 2018-12-26
> **spjackson said:**
> Perhaps dia will be of interest - except for the Data Dictionary.

It seems to no longer be supported. 
[http://dia-installer.de/download/linux.html](http://dia-installer.de/download/linux.html)
Ubuntu 12.04?

---

### Post by spjackson on 2018-12-27
> **Blix775 said:**
> It seems to no longer be supported. 
[http://dia-installer.de/download/linux.html](http://dia-installer.de/download/linux.html)
Ubuntu 12.04?
It has now been part of the Gnome project for several years and as such I would regard it as supported: [https://gitlab.gnome.org/GNOME/dia](https://gitlab.gnome.org/GNOME/dia)

In any event, there is a current Ubuntu package for it:
```

$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.10
DISTRIB_CODENAME=cosmic
DISTRIB_DESCRIPTION="Ubuntu 18.10"



$ sudo apt-get install dia
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  dia-common dia-shapes gsfonts-x11 libart-2.0-2 python-cairo
  python-gobject-2 python-gtk2
Suggested packages:
  python-gobject-2-dbg python-gtk2-doc
The following NEW packages will be installed
  dia dia-common dia-shapes gsfonts-x11 libart-2.0-2 python-cairo
  python-gobject-2 python-gtk2
0 to upgrade, 8 to newly install, 0 to remove and 100 not to upgrade.
Need to get 9,292 kB of archives.
After this operation, 35.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

---

