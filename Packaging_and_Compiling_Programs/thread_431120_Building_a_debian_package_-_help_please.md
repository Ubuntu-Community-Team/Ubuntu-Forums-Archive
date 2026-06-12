---
title: "Building a debian package - help please"
date: 2007-05-02
forum: Packaging and Compiling Programs
---

### Post by Kreuger on 2007-05-02
First, sorry if this is the wrong forum. Anyway, I want to build my own deb packages of amsn using the svn code. Can someone please provide me a thorough guide on how to do this? I downloaded the source from their site and extracted it then tried using dh_make but it said I already had a debian folder and Im not sure what else to do. Once I learn how to do this, I plan to create debs of all the programs I use (using svn) to provide to people who have trouble compiling.

---

### Post by Kreuger on 2007-05-03
anyone?

---

### Post by kodoku on 2007-05-03
To make debs from source, you'll need to install 'checkinstall' from the repos

The general steps for compiling from source are

*In a terminal, cd'ed to the source directory*
> ./configure

> make

> sudo checkinstall

The final step should install the created deb for you, and you can find the deb in the source directory.

---

### Post by psychicdragon on 2007-05-04
Please don't use checkinstall to create Debian packages. Especially if you're building a newer version of a package that is in the repositories. checkinstall packages lack dependencies and are versioned incorrectly, which can come back to bite you in the *** when you do a dist-upgrade.

dh-make is fairly simple to use, once you've made a couple of packages and it creates non-busted packages.

If the package you're building already has a debian sub-directory, all you need to do is this:
```
fakeroot debian/rules binary
```

Here's a pretty good introduction to creating packages with dh-make: [http://www.debian-administration.org/articles/337](http://www.debian-administration.org/articles/337)

---

### Post by hod139 on 2007-05-04
If all you want is a deb package for your own system, to make the package register with apt and uninstall easier, then checkinstall is fine.  If you want to build a distributable package, then you should use dh-make.

---

### Post by Kreuger on 2007-05-05
> fakeroot debian/rules binary Since amsn has the debian directory I tried this figuring it'd be the easiest but it came up with an error at the end: (If you need, I'm attaching the full output as well)
> dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-gencontrol: error: syntax error in parsed version of changelog at line 0: empty file
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1

> Here's a pretty good introduction to creating packages with dh-make: [http://www.debian-administration.org/articles/337](http://www.debian-administration.org/articles/337) This seems a bit confusing but I'll read it over a few times. The more I go over it, the more it seems to make sense.

> If all you want is a deb package for your own system, to make the package register with apt and uninstall easier, then checkinstall is fine. If you want to build a distributable package, then you should use dh-make. As I said in my original post, I am planning to make them distributable

---

### Post by Yuske on 2007-09-18
> **psychicdragon said:**
> Please don't use checkinstall to create Debian packages. Especially if you're building a newer version of a package that is in the repositories. checkinstall packages lack dependencies and are versioned incorrectly, which can come back to bite you in the *** when you do a dist-upgrade.

dh-make is fairly simple to use, once you've made a couple of packages and it creates non-busted packages.
Here's a pretty good introduction to creating packages with dh-make: [http://www.debian-administration.org/articles/337](http://www.debian-administration.org/articles/337)

truth. dh-make is pretty easy to use, last week I wanted to install postgresql 8.2.4 here, but without compiling it... it was really easy, even for a newbie on linux like me.

but I think there is a much better guide for creating debian packages right here on this forum: [http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003) - I followed this one to make the postgresql 8.2.4 .deb package =)

---

### Post by shafi on 2007-12-01
Dear all, I have programmed and application using Java and now i want to build a package that could install it on my ubuntu, but when i try the dpkge -b i find the following error:  please help me, 
I have used the following packages in my program:

import java.awt.*;
import java.awt.event.*;
import java.io.*;
import java.net.*;
import java.util.Vector;
import javax.swing.*;

> 
dpkg -b /usr/bin/XDicFa/ XDicFa.deb

dpkg-deb: failed to open package info file `/usr/bin/XDicFa//DEBIAN/control' for reading: No such file or directory


this is the control file:

[HTML]Version: 1.0
Section: Accessories
Priority: optional
Architecture: all
Essential: no
Depends: libgcj7-awt  
Installed-Size: 5MB
Provides: XDicFa
Description: English Persian Dictionary
[/HTML]

---

