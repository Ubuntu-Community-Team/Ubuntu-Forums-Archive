---
title: "REQUEST: libfreetype 2.2.10"
date: 2006-05-05
forum: Repositories &amp; Backports
---

### Post by bernardfrancois on 2006-05-05
I noticed the latest version of the gimp is not available in the ubuntu 5.10 amd64 repositories (see [http://ubuntuforums.org/showthread.php?t=170810)](http://ubuntuforums.org/showthread.php?t=170810)), so I decided to build it from source myself.

In the INSTALL file that came with the source tarball of the gimp you can read this:
> 
 GIMP 2.2 depends on
     freetype2 being newer than version 2.1.7. Older versions are
     known to have bugs that seriously affect stability of The GIMP.


The version in the repositories seems to be 2.1.7 (so it's not newer than 2.1.7).
The current latest stable version is 2.1.10 (dating back from june 2005), which can be downloaded at the following location:
[http://download.savannah.gnu.org/releases/freetype/freetype-2.1.10.tar.bz2](http://download.savannah.gnu.org/releases/freetype/freetype-2.1.10.tar.bz2)

I would like to see it in the repositories...

---

### Post by bernardfrancois on 2006-05-05
I just tried to install it myself, and I intended to use checkinstall in order to create a .deb package which I could upload to post a link here.

This is what I got when I tried to install the created .deb package:
```

dpkg: error processing freetype-2.1.10_2.1.10-1_amd64.deb (--install):
 trying to overwrite `/usr/bin/freetype-config', which is also in package libfreetype6-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 freetype-2.1.10_2.1.10-1_amd64.deb

```

Removing the currently installed version of libfreetype is not an option, since this will uninstall a lot of other things.

I wonder how someone can upgrade a package on which other packages depend manually...

---

