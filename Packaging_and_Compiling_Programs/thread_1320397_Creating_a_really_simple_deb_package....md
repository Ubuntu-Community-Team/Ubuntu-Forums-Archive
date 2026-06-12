---
title: "Creating a really simple deb package..."
date: 2009-11-09
forum: Packaging and Compiling Programs
---

### Post by Kazade on 2009-11-09
I'd like to create a Debian package that does the following:

1. Installs some files to different locations
2. Sets up some permissions
3. Restarts Apache

But all the packaging tutorials I find involve packaging applications that must be compiled. Is there just a simple way to create a Deb package that does the above?

---

### Post by realzippy on 2009-11-09
Well,compiling is not so hard...

but,this could help:

[http://users.telenet.be/mydotcom/howto/linux/package.htm](http://users.telenet.be/mydotcom/howto/linux/package.htm)

---

### Post by Fatman_UK on 2009-11-09
This is a basic tutorial on getting files into the right places:

[http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)

You do need to know the absolute paths they will be in. I guess you also need to find out how to run a script from the package. Then, in the script you would have something like:

```

chmod 400 index.html
/etc/init.d/apache2 restart

```

HtH,
Fatman

---

### Post by SevenMachines on 2009-11-09
There are a number of ways to do this using debhelper. If you create a file debian/<mypackage>.install
then you can specify which files install where. ie,
path/in/my/source/dir/* /path/to/install/to

to have apache restart you will most likely want to have a file
debian/<mypackage>.postinst
which contains the script to be run after install

you could actually have a debian/rules file with only two lines! 
#!/usr/bin/make -f
include /usr/share/cdbs/1/rules/debhelper.mk

but most likely you'll want some finer control, see /usr/share/doc/debhelper/examples/ for some you may want to look at

also, there may be a package that does similar to what your trying to, try
$apt-get source screensaver-default-images
and have a look at that, there are probably better examples but it was the first i could find at half-time :)

---

### Post by Kazade on 2009-11-10
Thanks for your help guys. In the end I wrote a little Python script that builds the deb package and it's working great :D

I do have another question but that's for another thread ;)

---

