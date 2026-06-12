---
title: "How to create Debain package"
date: 2010-04-06
forum: Packaging and Compiling Programs
---

### Post by surabhi on 2010-04-06
Hello

I have developed an application using GLADE,PYTHON,GTK,Shell script .The main program is a python file in which Glade file and shell script is being called.Right now my application is running successfully by issuing the command filename.py
I want to create debian package for my application and wanted the installed programme to go to the system tools of the application menu.
**How can I create a debian package .Please guide me**.
Thanks and Regards.

---

### Post by lisati on 2010-04-06
Have a look here: [http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)

---

### Post by surabhi on 2010-04-06
I followed the steps given in the above link 
after issuing the command 
**dpkg-deb --build doctorboss-1.0**
only this message comes

dpkg-deb: building package `doctorboss' in `doctorboss-1.0.deb'.

and I am not able to locate the debian package.
Could you please help me .

---

### Post by dominiquec on 2010-04-06
Try this tutorial:

[http://www.ibm.com/developerworks/linux/library/l-debpkg.html](http://www.ibm.com/developerworks/linux/library/l-debpkg.html)

---

### Post by surabhi on 2010-04-06
make[1]: *** No rule to make target `distclean'.  Stop.
make[1]: Leaving directory `/home/surabhi/Documents/diagnostic_tool/package/doctorboss-1.0'
make: [clean] Error 2 (ignored)
 dpkg-source -b doctorboss-1.0
dpkg-source: info: using source format `1.0'
dpkg-source: info: building doctorboss in doctorboss_1.0-1.tar.gz
dpkg-source: info: building doctorboss in doctorboss_1.0-1.dsc
 debian/rules build
./configure --prefix=/usr
make: ./configure: Command not found
make: *** [build] Error 127
dpkg-buildpackage: error: debian/rules build gave error exit status 2
debuild: fatal error at line 1334:
dpkg-buildpackage -rfakeroot -D -us -uc failed



I am getting some error after issuing deb build is that because something is missing from the rules file .
Please help me to fix this error .

---

### Post by surabhi on 2010-04-06
Thanks dominiquec

I created the debain package , but after it get installed I am not able to run it (locate )
Do I need to set any specific path for that ?

---

### Post by Zoot7 on 2010-04-07
Normally the best way to do it is "debianize" the source with **dh_make**. ( Install the package dh-make).
To use it just run it from within the source directory, it'll work if you've a properly named file in the above directory. ie. <package name>_<version>.orig.tar.gz.

What that does is create a sample debian directory containing all the necessary files. The only real ones you have to worry about are the rules file (which specifies all the compile options) and the control file (which specifies all the dependencies). Then you can build it with running **dpkg-buildpackage** from the source directory.

Hate to send you off to read *more stuff*, but it's worth having a read of the following:
[http://www.debian.org/doc/maint-guide/ch-first.en.html](http://www.debian.org/doc/maint-guide/ch-first.en.html)
[http://www.debian.org/doc/maint-guide/ch-dreq.en.html](http://www.debian.org/doc/maint-guide/ch-dreq.en.html)

---

### Post by surabhi on 2010-04-08
Thanks ZOOT7

I followed the same procedure that u suggested but after running 
dpkg-buildpackage I am getting this error 


debian/rules build
./configure --prefix=/usr
make: ./configure: Command not found
make: *** [build] Error 127
dpkg-buildpackage: error: debian/rules build gave error exit status 2

Can you help me to solve this

---

### Post by Zoot7 on 2010-04-08
Try running each one of the following command from the source directory and see which one its complaining about:
```
dh_testdir
dh_auto_configure
dh_auto_build
dh_auto_test
```

---

### Post by surabhi on 2010-04-08
It is showinh no error from the source directory but after going to debian subdirectory it is showing these errors

dh_auto_configure: cannot read debian/control: No such file or directory
dh_auto_test: cannot read debian/control: No such file or directory

---

### Post by Zoot7 on 2010-04-08
> **surabhi said:**
> dpkg-buildpackage: error: debian/rules build gave error exit status 2

"debian/rules build" executes the same commands as I've listed above, so if they're working individually they should work when dpkg-buildpackage calls them.

> **surabhi said:**
> It is showinh no error from the source directory but after going to debian subdirectory it is showing these errors

dh_auto_configure: cannot read debian/control: No such file or directory
dh_auto_test: cannot read debian/control: No such file or directory
You're supposed to run them from within the source directory itself, not the debian sub directory contained within.

---

