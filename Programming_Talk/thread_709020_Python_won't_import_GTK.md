---
title: "Python won't import GTK"
date: 2008-02-27
forum: Programming Talk
---

### Post by soltanis on 2008-02-27
I recently installed a python modification, Stackless python. It replaced the python executable with a modified version, I think (opening up python, the welcome message isn't the same, it says "Stackless python <version> <etc.>"

For some reason, python won't import gtk anymore. I've tried reinstalling python, python-gtk2, and python-glade, etc; all the applications which use python to make GUIs (which are shockingly numerous in ubuntu) don't work anymore. That includes the controls to my printer, which currently can't print since I can't access the printer configuration menu.

How do I fix this and get my python and gtk back?

EDIT:
/usr/lib/python2.5/site-packages/gtk2.0/
is empty. wtf?
I tell synaptic to reinstall and it does nothing. Attempting to install from source fails (I don't know why). What the heck? Can someone lend me their .so files for gtk?

---

### Post by dwblas on 2008-02-27
You also want to check /usr/lib/pygtk.  You may have to uninstall and then install the packages.  The package manager may think that the packages are installed and so doesn't do the re-install.

---

### Post by soltanis on 2008-02-27
I cannot uninstall python or python-gtk2 because there are too many dependencies, and apt-get/synaptic refuse to remove a package without removing all the dependencies. These include, just to demonstrate my point

ubuntu-desktop
openoffice.org
ubuntu-xen-desktop
envy

And a few other things that I'd honestly rather not uninstall.

---

### Post by prensing on 2008-02-27
Maybe try: 
   apt-get --reinstall install python
or similar with other packages.

---

### Post by dwblas on 2008-02-28
Check that you have something in /usr/lib/pygtk/2.0.  That's the only package that I see that you didn't reinstall.  Here is a link to the Ubuntu package if you have to install it by hand, but a synaptic reinstall should do the trick.
[http://packages.ubuntu.com/feisty/source/pygtk](http://packages.ubuntu.com/feisty/source/pygtk)

---

