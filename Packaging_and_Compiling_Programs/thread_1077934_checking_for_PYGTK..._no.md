---
title: "checking for PYGTK... no"
date: 2009-02-22
forum: Packaging and Compiling Programs
---

### Post by dodle on 2009-02-22
**Edit:** Never mind.  Argh, I often seem to find the answer right after I've posted my problem.  I didn't look carefully enough.  The missing package was python-gnome2-desktop-dev

[COLOR="Red"][SOLVED][/COLOR]
I'm trying to compile gnome-games-2.22.3 from source (for practice).  But my compiler can't seem to find pygtk.  I have python-gtk2-dev already installed, and every other package I could think of that might have something to do with it.  Here is part of the output of ./configure:```
...
...
...
...
checking what language compliance flags to pass to the C++ compiler... 
checking for C99 variadic macros... yes
checking for C99 variable arrays... (cached) yes
checking for C99 initializers... yes
checking for stdint.h... (cached) yes
checking for C99 stdint.h... yes
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for which platform to build... gnome
checking whether to enable sound support... yes
checking for which sound library to use... sdl_mixer
checking whether to enable scalable graphics... yes
checking for GTHREAD... yes
checking for GTK... yes
checking for GCONF... yes
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for gconftool-2... /usr/bin/gconftool-2
checking for GNOME... yes
checking for RSVG... yes
checking whether librsvg supports gnome-vfs... yes
checking for PYGTK... no
configure: error: Some games need python, but python, pygtk or gnome-python-desktop packages were not found.

```Am I missing an important package?  I can't figure it out.

---

