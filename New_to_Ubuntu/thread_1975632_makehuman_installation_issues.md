---
title: "makehuman installation issues"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-05-07
I'v been wanting to install a program called makehuman which creates accurate human figures for graphics. Unfortunatly the alpha and nightly .deb files won't run, as they say they need Python 2.6 in order to run. I have no knowledge of installing programs built from source, and I would like someone to read through the answers given, especially the last one when it comes to building from source. The Topic name is:

Re: .debian install python back compatibility issues

and can be found at:

[http://www.makehuman.org/forum/viewtopic.php?t=2486](http://www.makehuman.org/forum/viewtopic.php?t=2486)

> 
Unfortunately, the nightly build is standardized on debian squeeze, which doesn't have python 2.7. Until we move to python 3.x (which will be some time in the future), the only two suggestions I have is to either find a compatibility package to get python 2.6 on your machine, or build from source. I'd suggest the latter, since it really is pretty easy on ubuntu. Basically:
```

sudo apt-get install python2.7 libsdl1.2debian libsdl-image1.2 libglew1.5 wget subversion libpython2.7 libsdl1.2-dev libsdl-image1.2-dev build-essential glew-utils libglew1.5-dev python2.7-dev scons
svn checkout http://makehuman.googlecode.com/svn/trunk/makehuman
cd makehuman
scons

```> 
That will get you an up to date makehuman in a "makehuman" directory.

To update it at a later time, do
```

cd makehuman
svn update
scons

```Is the code accurate? Do you think it will work?

---

### Post by Senior_Buckethead on 2012-05-08
Bump.

---

### Post by Queequeg on 2012-05-27
Just link the /usr/lib/libpython2.7.so.1.0 like so:

```
sudo ln -s /usr/lib/libpython2.7.so.1.0 /usr/lib/libpython2.6.so.1.0
```

and it will work.

---

### Post by Senior_Buckethead on 2012-05-28
```

glenn@acer:/media/Seagate/Software/Linux/Software$ sudo dpkg -i makehuman-nightly-linux-i386.deb
Selecting previously unselected package makehuman-nightly.
(Reading database ... 247486 files and directories currently installed.)
Unpacking makehuman-nightly (from makehuman-nightly-linux-i386.deb) ...
dpkg: dependency problems prevent configuration of makehuman-nightly:
 makehuman-nightly depends on python2.6; however:
  Package python2.6 is not installed.
 makehuman-nightly depends on libpython2.6; however:
  Package libpython2.6 is not installed.
dpkg: error processing makehuman-nightly (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 makehuman-nightly
glenn@acer:/media/Seagate/Software/Linux/Software$ 

```Still telling me that python2.6 is not installed. Is this what they call a 'fatal error'....

They should have up in thread tools a category called 'hopelessly incurable'

---

### Post by damvcoool on 2012-10-02
Makehuman i now in Quantal Repository you may want to try the Beta2 and install makehuman from the repository.

---

