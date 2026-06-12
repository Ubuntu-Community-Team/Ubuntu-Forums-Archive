---
title: "[Python] Gnome Support for Windows"
date: 2008-09-13
forum: Programming Talk
---

### Post by cleo.mclellan on 2008-09-13
Hi All,

I am trying to get a PyGTK application working on Windows. I have installed
the basic stuff like pygtk, gtk, and pango using an all in one installer.
So a basic application found in the tutorials work perfectly. I made another
application that requires more modules. Here are my import statements:

import pygtk
import gtk
import gtk.glade
import gtkhtml2, gnomevfs
import pango
import string
import datetime
import os
import gobject
import gnome.ui

I think the ones that need to be installed are gnomevfs, gnome, gnome.ui,
and gtkhtml2. All else can be imported successfully.
I found a message on another forum that specified where to obtain Win32
packages for these modules: (it's at an FTP site)

I think my question is: Are these the appropriate packages to get it
installed on Windows, and if so, how can you install them?

I truly appreciate any help.

---

### Post by slavik on 2008-09-13
umm, gnome won't exactly work ... besides, you don't need gnome for gtk

---

### Post by cleo.mclellan on 2008-09-13
I think [http://ftp.gnome.org/pub/gnome/binaries/win32/](http://ftp.gnome.org/pub/gnome/binaries/win32/) might be a  way to get the packages for Windows. I think my question is what to do with them.
BTW, thanks for the reply.

---

### Post by SeanHodges on 2008-09-15
You need to install PyGTK and it's dependencies in Windows:

[http://www.pygtk.org/downloads.html](http://www.pygtk.org/downloads.html)

There are some good instructions here:

[http://faq.pygtk.org/index.py?req=show&file=faq21.001.htp](http://faq.pygtk.org/index.py?req=show&file=faq21.001.htp)

---

