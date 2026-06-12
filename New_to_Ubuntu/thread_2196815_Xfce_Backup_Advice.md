---
title: "Xfce Backup Advice"
date: 2013-12-31
forum: New to Ubuntu
---

### Post by mlnease on 2013-12-31
Hello,

After eight years, I'm abandoning the Ubuntu ship and defecting (*very* happily) to Xubuntu/Xfce4.  I love it.  But I need to back up my new install.  In all those years, I've always used sbackup which, if not perfect, I've always found reliable and easy to use.

When I go to install it though, I find I must also install five GNOME packages (among others, as below).  I don't know much about such things, but I've read in the past that I should avoid mixing DEs.  Will this installation cause any conflicts with my shiny, new Xubuntu/Xfce setup?

If so, can anyone recommend a better, simple, GUI backup utility for my system?

```
The following NEW packages will be installed:
  libbonobo2-0{a} libbonobo2-common{a} libbonoboui2-0{a} 
  libbonoboui2-common{a} libgnome2-0{a} libgnome2-bin{a} 
  libgnome2-common{a} libgnomecanvas2-0{a} libgnomecanvas2-common{a} 
  libgnomeui-0{a} libgnomeui-common{a} libidl-common{a} libidl0{a} 
  liborbit2{a} python-gnome2{a} python-pyorbit{a} sbackup sbackup-gtk{a} 
0 packages upgraded, 18 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,956 kB of archives. After unpacking 9,617 kB will be used.
```

Thanks in advance and

Happy Gnu Year,

mn

---

### Post by Tristan_Williams on 2013-12-31
This should be fine, because xfce is GTK based, as is Gnome. I have never encountered a problem between Gnome and xfce packages.
In fact, xfce utilizes quite a few Gnome packages (because of gtk)

Just remember, xfce can handle having gnome packages, and vice versa.
You run into problems when you mix xfce with unity, kde, or lxde, because they done use hardly any of the same anything.

---

### Post by mlnease on 2013-12-31
Thanks, Tristan, this is just the sort of thing I needed to know--really appreciate it.  Backup *en route!*  Happy Gnu Year!

---

### Post by Tristan_Williams on 2013-12-31
You are welcome.

---

### Post by vasa1 on 2013-12-31
> **Tristan_Williams said:**
> ...
You run into problems when you mix xfce with unity, kde, or lxde, because they done use hardly any of the same anything.
Lubuntu and Xubuntu have a lot in common.

---

