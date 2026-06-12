---
title: "HOWTO: gtkpod 0.99.8 (with Album Art and Movie support) on Ubuntu Dapper 6.06"
date: 2006-12-22
forum: Outdated Tutorials &amp; Tips
---

### Post by jak on 2006-12-22
[B]Just wanna use it?
[/B]
Download the attached debs, and do the following..

1. sudo apt-get remove gtkpod-aac gtkpod
*removes the old gtkpod version*
2. sudo dpkg -i libgpod-0.4.0-1_i386.deb
*install our own libgpod alongside the ubuntu one (called libgpod0)*
3. sudo dpkg -i gtkpod-0.99.8-1_i386.deb
*install our new gtkpod*
4. sudo rm /usr/lib/libgpod.so.0
*remove the link to the old 302 library*
5. sudo ln -s /usr/local/lib/libgpod.so.0.400.0 /usr/lib/libgpod.so.0
*make a link to the new 400 library.. all gpod apps (rhythmbox, amarok, gtkpod) will use the shiny new one*

**Wanna do it from scratch?**

I've built the two packages you need using checkinstall, but if you want to build them yourself it was simple...

First, run apt-get install libid3tag0-dev libglade2-dev

Download the source tarballs from sourceforge, extract, run ./configure, then make, then checkinstall

Oh, that was it. Done!



Except we lost gtkpod in the menu, but thats easy to put back! :)

**Note: **There's no need to remove libgpod0 at any point, doing so would remove rhythmbox/amarok etc.. we can keep the Ubuntu library and install the new one (they have slightly different names), just updating the link to the new one!

---

### Post by melvix on 2007-02-03
Hi jak,
i hoped it would be o.k. after following precisely your guide, but trying to load the mounted ipod after starting gtkpod at last i always get the error:

/usr/bin/gtkpod: symbol lookup error: /usr/bin/gtkpod: undefined symbol: itdb_device_set_mountpoint

(Edgy, freshly installed)
 
Is there any way else than building from scratch?

Thanks for your help

melvix

---

### Post by gschoper on 2007-02-03
> **melvix said:**
> Hi jak,
i hoped it would be o.k. after following precisely your guide, but trying to load the mounted ipod after starting gtkpod at last i always get the error:

/usr/bin/gtkpod: symbol lookup error: /usr/bin/gtkpod: undefined symbol: itdb_device_set_mountpoint

(Edgy, freshly installed)
 
Is there any way else than building from scratch?

Thanks for your help

melvix

I built it from scratch this morning. It's not that complicated.

Install dependencies:
```
sudo apt-get install build-essential autoconf flex glib gtk+ libglade libid3tag pkgconfig python python-eye3D libgpod0 python-id3 libgpod-dev python-dev swig
```
Download sources:
```
wget http://downloads.sourceforge.net/gtkpod/gtkpod-0.99.8.tar.gz?modtime=1159139788

wget http://downloads.sourceforge.net/gtkpod/libgpod-0.4.2.tar.gz?modtime=1168909009
```
Uncompress sources:
```
tar -xvvzf gtkpod-0.99.8.tar.gz
tar -xvvzf libgpod-0.4.2.tar.gz
```

Build and install libgpod:
```
cd libgpod-0.4.2
./configure --prefix=/usr
make
sudo make install
```

Build and install gtkpod:
```
cd gtkpod-0.99.8
./autogen.sh --prefix=/usr
make
sudo make install
```

I made these instructions from memory (and bash history), so they may not be perfect, but I don't see why they shouldn't work.

gschoper

---

### Post by oomisilekootsi on 2007-03-24
where can I get these files:
      gtkpod-0.99.8-1_i386.deb
      libgpod-0.4.0-1_i386.deb

even google could not find them...:(

---

### Post by Wargazm on 2007-03-28
> **gschoper said:**
> Install dependencies:
```
sudo apt-get install build-essential autoconf flex glib gtk+ libglade libid3tag pkgconfig python python-eye3D libgpod0 python-id3 libgpod-dev python-dev swig
```

When I do this step, it gives me an error:

```
E: Couldn't find package glib
```

How do I get this package?

---

### Post by rjh78 on 2007-03-29
> **Wargazm said:**
> When I do this step, it gives me an error:

```
E: Couldn't find package glib
```

How do I get this package?

I've got the same problem.  In fact I get this message for 
glib
gtk+
libglade
libid3tag
pkgconfig
python-eye3d

---

### Post by ba0bab on 2009-01-31
me too, it can't find python-eye3d. Anybody?

---

### Post by ba0bab on 2009-01-31
I found the answer. It's because the package is called python-eyed3 and NOT python-eye3d. A bit misleading me thinks!

---

