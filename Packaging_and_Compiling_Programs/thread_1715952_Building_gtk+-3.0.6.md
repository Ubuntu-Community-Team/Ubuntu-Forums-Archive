---
title: "Building gtk+-3.0.6"
date: 2011-03-27
forum: Packaging and Compiling Programs
---

### Post by nocturnal1 on 2011-03-27
I can't seam to configure gtk+-3.0.6, when I try to configure gdk-pixbuf-2.22.1 I keep getting the error:
```
configure: error:
*** GLIB 2.25.15 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/pub/gtk/
```This is what I did
1) Created a folder called gtk in /opt like the example at: [http://library.gnome.org/devel/gtk/2.21/gtk-building.html](http://library.gnome.org/devel/gtk/2.21/gtk-building.html)
cd /opt
sudo mkdir gtk

2) Downloaded all newest versions of the packages from the links here to /ect/gtk :
[http://www.gtk.org/download-linux.html](http://www.gtk.org/download-linux.html)

3) Unpacked the packages with:

sudo tar xvf gtk+-3.0.6.tar.gz
sudo tar xvfz glib-2.28.4.tar.gz
sudo tar xvfz gdk-pixbuf-2.22.1.tar.gz
sudo tar xvfz pango-1.28.3.tar.gz

4) Followed the instructions for Glib in the included text file called: INSTALL
cd /opt/gtk/glib-2.28.4
sudo ./configure
sudo make
sudo rm -rf /install-prefix/include/glib.h /install-prefix/include/gmodule.h
sudo make install

5) Repeat for the other packages except without sudo rm. The INSTALL file for gdk-pixbuf-2.22.1 was empty.

6) Added the paths to the txt file called environment in /ect from the instructions here: [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)
cd /etc
gksu gedit environment
added:   /opt/gtk/gtk+-3.0.6:/opt/gtk/glib-2.28.4:/opt/gtk/gdk-pixbuf-2.22.1:/opt/gtk/pango-1.28.3

I've also tried using jhbuild but it's just too complex. Please help I've been messing with this for days now.

---

### Post by mlt2011 on 2011-03-28
What are the values of the environment variables
PKG_CONFIG_PATH and
LD_LIBRARY_PATH?

---

### Post by nocturnal1 on 2011-03-28
```
me@ubuntu:~$ locate pkg-config
/etc/bash_completion.d/pkg-config
/home/me/cvs/jhbuild/patches/talloc-pkg-config-removal.patch
/home/me/cvs/jhbuild/patches/tdb-pkg-config-removal.patch
/home/me/cvs/jhbuild/patches/tevent-pkg-config-removal.patch
**/usr/bin/pkg-config**
/usr/share/doc/pkg-config
/usr/share/doc/pkg-config/AUTHORS
/usr/share/doc/pkg-config/NEWS.gz
/usr/share/doc/pkg-config/README
/usr/share/doc/pkg-config/changelog.Debian.gz
/usr/share/doc/pkg-config/changelog.gz
/usr/share/doc/pkg-config/copyright
/usr/share/man/man1/pkg-config.1.gz
/var/lib/dpkg/info/pkg-config.list
/var/lib/dpkg/info/pkg-config.md5sums
```
I'm using Lucid, how do I open pkg-config to find the values? , how do I find LD_LIBRARY_PATH, the locate command returns nothing?

---

### Post by mlt2011 on 2011-03-28
When you run the configure script for gdk-pixbuf, it tests to see that a  recent version of glib is available, but it is finding an older  version--probably the one installed on your system by default in /lib.  Since you built glib by hand, it should have installed a new version in  /usr/local/lib. You can try adding this directory either as the  LD_LIBRARY_PATH environment variable, or perhaps adding it to the  environment (e.g., add /usr/local/lib in your step #6 above). To see if  this will work, first try:
```
sudo LD_LIBRARY_PATH=/usr/local/lib ./configure
```when trying to configure gdk-pixbuf. If you can get past the error, then  you may want to add this path as in your step #6--but I have not used  this method, so I'm not sure this will work.

---

