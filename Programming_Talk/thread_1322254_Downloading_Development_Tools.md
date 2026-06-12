---
title: "Downloading Development Tools"
date: 2009-11-10
forum: Programming Talk
---

### Post by theunixgeek on 2009-11-10
My Ubuntu computer doesn't have access to the internet, but I do through my Mac. I want to install some development tools on my fresh Ubuntu installation (gcc, quickly, the GTK+/PyGTK libraries, etc). Is there a way to download these development tools packages in the main repository as a disk image? Or is there another way for me to get all the packages I want without access to the internet on Ubuntu?

---

### Post by froggyswamp on 2009-11-10
I've been wondering myself, but I suppose that if you used a DVD image to install Ubuntu there could/should also be the (main) devel packages and if so, you could add that DVD to your Software Sources so that Ubuntu installs the devel packages from the DVD. At least the Mandriva DVD contains the devel files and I did so and it worked on Mandriva 2010 PowerPack.

---

### Post by Flimm on 2009-11-10
You can use Synaptic to create download scripts. Just mark the packages you want to install and then click File, Generate package download script. I don't use Mac OS X myself but I think you can install wget on it, making the script runnable on a Mac.

---

### Post by jespdj on 2009-11-12
You can download the *.deb packages from [http://packages.ubuntu.com](http://packages.ubuntu.com)

Install a *.deb package by double-clicking on it, or running this in a terminal:
```
dpkg -i filename.deb
```
If the package you want to install depends on other packages, you'll need to install those first.

---

