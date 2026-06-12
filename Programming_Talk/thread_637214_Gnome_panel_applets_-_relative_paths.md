---
title: "Gnome panel applets - relative paths"
date: 2007-12-10
forum: Programming Talk
---

### Post by kevykev on 2007-12-10
Hi All,

I'm currently writing a panel applet for gnome and I was wondering if it is possible to use relative paths to files (relative to the root directory of the applet, for instance) within the applet.

For example, can i load icons, or glade UI files, without specifying their absolute paths? Alternatively, Is it possible somehow to determine the directory containing the applet?

If the paths must be absolute, is the correct procedure to install icons, resources, etc, in some known location like '/usr/share/appname'?

I'm writing the applet in python by the way.

Thanks,
Kevin

---

### Post by MicahCarrick on 2007-12-10
I'm afraid I'm not sure how this is done in python, however, in C we use the GNU build tools (configure, make, make install) to build the app which also defines the paths during the ./configure step.

I suggest you find another Gnome panel or gnome application written in Python and look at how it's installation script is working.

---

### Post by kevykev on 2007-12-14
Thanks for the response. It looks like I can use the GNU autotools for python projects too, but it's a bit messier.

---

