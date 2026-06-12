---
title: "Simple packaging - help required!"
date: 2010-01-09
forum: Packaging and Compiling Programs
---

### Post by inthevidual on 2010-01-09
I am curious if someone could assist me with some very basic packaging for my Ubuntu remaster. I want to package architecture-independent files like themes, icons and other artwork, but I have so far only found tutorials for "debianizing" source code that has a Makefile.

Please help me with this or at least point me in the right direction.

Thanks in advance! :D

---

### Post by SevenMachines on 2010-01-10
a simple general example debian/ setup for this might involve
debian/rules: only 2 lines!
```
#!/usr/bin/make -f
include /usr/share/cdbs/1/rules/debhelper.mk
```(note: you'll need to add build depends on cdbs, debhelper in debian/control if there not already there)

then you can install files that need no building by creating a debian/install or debian/<packagename>.install file with the format 
debian/install:
```
file/in/source/directory   /usr/share/some/place
```

---

### Post by Brandon Williams on 2010-01-10
If you 'sudo apt-get install build-essential', you can then pull down source packages and look at how they are structured. For example, 'apt-get source gnome-humility-icon-theme' will give you the source for one icon theme that uses a fairly simple method for installing an icon theme. You could easily use that method as a template for your package source. humanity-icon-theme is another good example that is fairly simple and easy to use as a template.

---

### Post by BalleClorin on 2010-01-17
This thread helped me too, but I have one remaining issue: How can I chmod +x a file installed with debian/install? Making the original +x does not seem to help...

---

### Post by SevenMachines on 2010-01-17
by default debhelper uses dh_fixperms, which sets file permissions to the debian policy default for those installation directories. to exclude a file from this processing and to leave the permissions as you have them you should add
DEB_FIXPERMS_EXCLUDE = /usr/bin/somefile
to debian/rules, where /usr/bin/somefile is the full installation path of the file

---

### Post by SevenMachines on 2010-01-17
just a quick thing if you need to alter the permissions in your debian/rules file. heres a little example for a package called 'simple' and a file installed to /usr/share/somefile, which i've decided should be world executable!! (oh no!)

#exclude this file from file permission fixing
DEB_FIXPERMS_EXCLUDE = /usr/share/somefile

#now do some very wrong file permissions!
binary-install/simple::
        chmod 777 debian/simple/usr/share/somefile

---

### Post by BalleClorin on 2010-01-17
I'm packaging a java application which is loaded with a shellscript. The java application expects everything to be in the same directory; the shellscript, the main .jar, some configuration files and a 3rd party binary only tool in a subdir. So I figured the easiest thing to do would be to put everything in a subdir of /opt. Maybe I should move the shellscript to /usr/bin and leave everything else in /opt?

---

### Post by SevenMachines on 2010-01-17
i really don't know what the policy would be for that kind of mix. the application requiring everything in the same directory is messy and means files can't be put in the 'right' place. add to that the binary only tool in a subdir....
maybe /opt is the place for it but i really dont know

---

### Post by BalleClorin on 2010-01-18
Every time I try to put chmod in the rules-file I get the following error from debuild: 
debian/rules:4: *** missing separator.  Stop.
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2

Any ideas?

---

### Post by SevenMachines on 2010-01-18
you'd need to post the full debian/rules if not the full debian directory, below is an (silly :) ) example

debian/rules
```

include /usr/share/cdbs/1/rules/debhelper.mk

# Add here any variable or target overrides you need.
DEB_FIXPERMS_EXCLUDE = /usr/share/somefile

binary-install/simple::
    chmod 777 debian/simple/usr/share/somefile
```debian/simple.install
```
somefile /usr/share/
```

---

### Post by BalleClorin on 2010-01-22
Ended up tweaking the bash script so it could be placed in /usr/bin instead. Thanks for your help..

---

### Post by BalleClorin on 2010-01-24
Would it be possible to add the 3rd party binary only app to /usr/bin or something, and then add a symlink to /opt/appname/subdir/linkname?
If yes, how do I add a symlink?

---

### Post by SevenMachines on 2010-01-25
you could try using dh_link in debian/rules along with a debian/<nameofpackage>.links file

---

### Post by BalleClorin on 2010-01-31
> **SevenMachines said:**
> a simple general example debian/ setup for this might involve
debian/rules: only 2 lines!
```
#!/usr/bin/make -f
include /usr/share/cdbs/1/rules/debhelper.mk
```(note: you'll need to add build depends on cdbs, debhelper in debian/control if there not already there)

then you can install files that need no building by creating a debian/install or debian/<packagename>.install file with the format 
debian/install:
```
file/in/source/directory   /usr/share/some/place
```

This works perfectly when making packages for Karmic, but for Lucid I get the following builderror:
```
cp: cannot stat `debian/tmp/pms': No such file or directory
dh_install: cp -a debian/tmp/pms debian/pms//usr/bin/ returned exit code 1
make: *** [binary-install/pms] Error 2
dpkg-buildpackage: error: /usr/bin/fakeroot debian/rules binary-arch gave error exit status 2
```

Any idea why?

---

### Post by BalleClorin on 2010-01-31
Newer mind. got the same error in karmic, must be a change in the source, will look into it later.

---

