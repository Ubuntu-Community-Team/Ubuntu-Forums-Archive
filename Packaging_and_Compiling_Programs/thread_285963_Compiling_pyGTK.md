---
title: "Compiling pyGTK"
date: 2006-10-27
forum: Packaging and Compiling Programs
---

### Post by YourFriendlyGopher on 2006-10-27
Hi, this problem has been driving me crazy. I'm trying to get started with GUI programming but I can't compile pyGTK. Using ./configure on pyGTK yields: 

checking for GLIB - version >= 2.8.0...
*** 'pkg-config --modversion glib-2.0' returned 2.12.3, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: gobject is required to build pygtk?

I'm fairly new to Linux and don't really understand how to configure libraries for compiling things. I tried to uninstall glib 2.10.3 from synaptic but it says that I'd have to remove a huge list of programs that I know shouldn't be removed. I don't know, messing around with libraries is confusing :confused:. If anyone has any ideas on what to do that'd be great, thanks.

---

### Post by po0f on 2006-10-27
Is there any reason you are compiling it?  It's available in the [repos](http://packages.ubuntu.com/dapper/python/python-gtk2).  Also, it's weird that you have glib 2.10.3 installed, but pkg-config said you have 2.12.3.  Did you also compile glib from source as well?

---

### Post by YourFriendlyGopher on 2006-10-28
Oh, I wasn't aware it was in the repositories.. I was looking for 'pygtk' with apt-get. To be honest I can't remember if I compiled glib from source or if I got it through an update. Eh, well at least I sort of know what I'm doing with this now, thanks for the info.

---

### Post by ssam on 2006-11-01
it takes a while to get used to the package naming scheme. all the python libraries are called

python-* or python2.4-*

pygtk is called python-gtk2

a search with synaptic will usually find stuff. you can also use
```
sudo apt-get build-dep packagename
```
to get all the bits you would need for compiling it.

---

### Post by americux on 2006-11-02
Hi, 
I think you have installed glib 2.12.3 from sources (placed in /usr/src) in /usr/local. Supposing this, have you tried to
$export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig &
$export LD_LIBRARY_PATH=/usr/local/lib &
$GLIB=/usr/src/glib-2.12.3/glib sudo ./configure  ??

If this last doesn´t work, you could try to fix the question editting /etc/ld.so.conf, adding the line /usr/local/lib, running sudo ldconfing, moving files form /usr/local/lib/pkgconfig to /usr/lib/pkgconfig and creating the soft link to /usr/lib/pkgconfig in /usr/local/lib/pkgconfig.

Good luck, a.

---

### Post by kellogs on 2006-11-23
> I think you have installed glib 2.12.3 from sources (placed in /usr/src) in /usr/local. Supposing this, have you tried to $export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig & $export LD_LIBRARY_PATH=/usr/local/lib & $GLIB=/usr/src/glib-2.12.3/glib sudo ./configure ??

You can always add "/usr/local/lib" to your environment variables PKG_CONFIG_PATH and LD_LIBRARY_PATH that are in /etc/environment (plain name, "environment"),if they don't exist add those two lines so it seems like:

PKG_CONFIG_PATH=/usr/lib/pkgconfig:/usr/local/lib/pkgconfig
LD_LIBRARY_PATH=/usr/lib:/usr/local/lib

without removing the old paths that could be there already.

environment file is like export, but export only lives on the active session, you can do that and they will be on the session on every boot, yo can change this if needed opening again '/etc/environment' and changing those lines.

(I think pkgconfig automatically looks on /usr/local by default but its better to make sure).

Also, you might add /usr/local/lib line to /etc/ld.so.conf and 'sudo ldconfig' after, ld.so.conf file is there to tell the system were to look to possible new library paths and you update the changes with sudo ldconfig.

And a last advice, ubuntu seems to mess with new packages compiled by your self , I recommend that if you cant remove a package because of dependencies, just compile it with "configure --prefix=/usr" option and it will overwrite the libs you installed with synaptic like for example the default glib version that configure insist, in case you want it back remove the just compiled and install from synaptic, easy!
these also removes the problem of when you have two libraries in the system, one old and one newer(compiled i.e.) doing this it overwrites old libraries and works well.

hope this helps. cheers.

---

### Post by YourFriendlyGopher on 2006-12-03
Oops, I forgot I started this thread, sorry. :oops: 

Anyway, I tried what you've all said and it works! Thanks very much guys!

---

