---
title: "[SOLVED] CMake"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Niniel on 2008-07-16
I'm trying to compile kgrubeditor 0.7 since the last version in the repositories is 0.5, and there aren't any deb files of this version. Soo... I got myself the source and it says cmake is needed. Got that too but now cmake can't find the compiler:
> -- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- broken

GCC is installed in /usr/bin/gcc-4.1...
I can't figure out how to tell cmake to look in the correct directory... any ideas?
Thanks.

---

### Post by sdennie on 2008-07-16
To get all the deps you need to build a newer version of a package that already exists in the repos, you can try this:

```

sudo apt-get build-dep kgrubeditor

```

---

### Post by Niniel on 2008-07-17
Hm, that helped some... but of course now I get a different error message:

> -- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
CMake Error: ERROR: Could not find KDE4 kde4-config
-- Configuring done

---

### Post by Bachstelze on 2008-07-17
```
sudo apt-get install kdelibs5-dev
```

---

### Post by Niniel on 2008-07-17
Looks like I had that already:

> x@y:~$ sudo apt-get install kdelibs5-dev
[sudo] password for x: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kdelibs5-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libiptables-ipv4-ipqueue-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Still get the same error.
Maybe I need to install KDE...

---

### Post by Niniel on 2008-07-21
And that's what I did. After that, it worked.
Thanks for trying to help, Vor and Hymn.

(KDE4 looks pretty slick... kind of like a "love" child of Mac OS and Vista though... and it's a bit on the slow side).

Incidentally, the download page for this program over at kde-apps.org claims there's a Ubuntu build... it must be very well hidden though because I was unable to find it.

---

### Post by Artemis_Fowl on 2008-07-23
Well, you needn't have installed the whole KDE4.0 for just an application. :)

All you should have done is:
```
export PATH=/usr/lib/kde4/bin/:$PATH
```

Unfortunately, there is no (public) *Ubuntu package for KGRUBEditor 0.7. There will be though, once KGRUBEditor 0.8 is released (I hope soon).

Btw it is planned to include KGRUBEditor in the next release of Kubuntu in the form of a System Settings module.

---

### Post by Niniel on 2008-07-27
That's good to hear. 
One thing though - background preview, the reason why I upgraded, wasn't working for me, not under Gnome, and not under KDE. At least now it says "Can't create preview" instead of just not doing it. :)

As for KDE, I don't mind, I wanted to take a peek at it anyway.

---

### Post by Artemis_Fowl on 2008-07-29
Sounds like a bug. Would you mind reporting it under Launchpad( [https://launchpad.net/kgrubeditor](https://launchpad.net/kgrubeditor) ) or SourceForge( [http://sourceforge.net/projects/kgrubeditor/](http://sourceforge.net/projects/kgrubeditor/) )? In the worst case PM me so as to keep the topic as clean as possible.

I'll personally take care of it.

---

