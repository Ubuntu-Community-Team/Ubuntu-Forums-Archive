---
title: "Making Custom Desktop"
date: 2007-10-02
forum: Programming Talk
---

### Post by Emerican_360 on 2007-10-02
I'm new to Linux (just got Ubuntu 7.04 a few days ago) and im really impressed with it! Si i downloaded all the Ubuntu source from [http://cdimage.ubuntu.com/releases/feisty/release/source/ubuntu-7.04-src-1.iso]("http://cdimage.ubuntu.com/releases/feisty/release/source/ubuntu-7.04-src-1.iso")
and i want to customize certain things on my desktop like extended options for themes etc... Where do i start? I can code quite well in c/c++ and i know some python and java. Any help or links to sites with a tutorial on building a custom Ubuntu or something will be welcome

Thanks

---

### Post by 505 on 2007-10-02
Most of the things you see are actually not Ubuntu. Ubuntu consists of all kinds of different software. For example, the desktop environment is called Gnome. Themes are also part of this. So if you want to change anything, you have to change Gnome. It's better to search for information there then here. See [http://developer.gnome.org/](http://developer.gnome.org/)
However, Ubuntu - as a distribution - works together with all the software developers Ubuntu consists of. So if a bug is filed here, or a patch supplied it can end up in the original version.

---

### Post by Emerican_360 on 2007-10-02
Thanks a lot!:)

---

### Post by MicahCarrick on 2007-10-02
Ubuntu is using the GNOME desktop environment which uses the GTK+ toolkit for the GUI. Themes are typically GTK+ themes which in turn have a theme engine (such as Metacity).

So, if you simply want to tweak appearance, icons, cursors, and things of that nature, check out [http://art.gnome.org/](http://art.gnome.org/) for information. If you want to actually start hacking the desktop, and since you know C, start digging into the GNOME sources. 

Many things are independent packages. So if you find a dialog somewhere you want to tweak, try finding out exactly what it is, download it's source, re-compile it and viola!

If you want to actually make changes that are requested by or planned for future releases of GNOME, check out [GnomeLove]("http://live.gnome.org/GnomeLove") where you kind find /submit lists of bugs, feature requests, and discussions on the above. Find a bug, fix it, and submit it.

---

### Post by Nekiruhs on 2007-10-02
> **MicahCarrick said:**
> Ubuntu is using the GNOME desktop environment which uses the GTK+ toolkit for the GUI. Themes are typically GTK+ themes which in turn have a theme engine (such as Metacity).

So, if you simply want to tweak appearance, icons, cursors, and things of that nature, check out [http://art.gnome.org/](http://art.gnome.org/) for information. If you want to actually start hacking the desktop, and since you know C, start digging into the GNOME sources. 

Many things are independent packages. So if you find a dialog somewhere you want to tweak, try finding out exactly what it is, download it's source, re-compile it and viola!

If you want to actually make changes that are requested by or planned for future releases of GNOME, check out [GnomeLove]("http://live.gnome.org/GnomeLove") where you kind find /submit lists of bugs, feature requests, and discussions on the above. Find a bug, fix it, and submit it.
Metacity is the Window Manager not the theme engine.

---

