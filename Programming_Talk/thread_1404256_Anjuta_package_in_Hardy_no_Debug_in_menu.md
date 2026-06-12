---
title: "Anjuta package in Hardy no Debug in menu"
date: 2010-02-11
forum: Programming Talk
---

### Post by amsterdamharu on 2010-02-11
Installed the following packages:
anjuta
anjuta-common
anjuta-dbg
anjuta-dev

That's all the anjuta I could find in synaptic but still the IDE has no Debug in it's menu. The help file says:
> Choose the menu item  Debug &#9656; Run TargetBut there is no menu item Debug here.

Followed this tutorial:
[http://library.gnome.org/users/anjuta-build-tutorial/2.26/library-anjuta.html.en](http://library.gnome.org/users/anjuta-build-tutorial/2.26/library-anjuta.html.en)
But the window in step 8 looks completely different.
My window:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=146750&stc=1&d=1265894790[/IMG]

And when I try to Build Build or Build Build Project I get the following:
(The main thing being "libxml/parser.h: No such file or directory" meaning that the XML module is not added)
```
make
make  all-am
make[1]: Entering directory `/home/amsterdamharu/Projects/tutprog'
gcc -DHAVE_CONFIG_H -I.  -DPACKAGE_DATA_DIR=\""/usr/local/share"\"   -Wall -g -g -O2 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
/home/amsterdamharu/Projects/tutprog/main.c:20:27: error: libxml/parser.h: No such file or directory
main.c: In function &#8216;main&#8217;:
/home/amsterdamharu/Projects/tutprog/main.c:25: error: &#8216;xmlDocPtr&#8217; undeclared (first use in this function)
/home/amsterdamharu/Projects/tutprog/main.c:25: error: (Each undeclared identifier is reported only once
/home/amsterdamharu/Projects/tutprog/main.c:25: error: for each function it appears in.)
/home/amsterdamharu/Projects/tutprog/main.c:25: error: expected &#8216;;&#8217; before &#8216;doc&#8217;
/home/amsterdamharu/Projects/tutprog/main.c:26: error: &#8216;doc&#8217; undeclared (first use in this function)
/home/amsterdamharu/Projects/tutprog/main.c:26: warning: implicit declaration of function &#8216;xmlParseFile&#8217;
/home/amsterdamharu/Projects/tutprog/main.c:34: warning: implicit declaration of function &#8216;xmlFreeDoc&#8217;
make[1]: *** [main.o] Error 1
make: *** [all] Error 2
make[1]: Leaving directory `/home/amsterdamharu/Projects/tutprog'
Completed unsuccessful
Total time taken: 0 secs

```I think there is something wrong with the deb package or I am missing some packages that should have been installed with it because it is not behaving the way it's own help documentation describes.

---

### Post by Zugzwang on 2010-02-11
> **amsterdamharu said:**
> 
I think there is something wrong with the deb package or I am missing some packages that should have been installed with it because it is not behaving the way it's own help documentation describes.

Documentation becomes outdated very quickly in Linux. If the Anjuta designers choosed to change the GUI a little bit, then the debugging stuff will be somewhere else.

Also note that it is possible that Anjuta isn't showing the debug menu since you didn't manage to build your program yet; thus, there's noting to debug.

As far as the XML-stuff is concerned: That's a build error of your project. The error says that some "libxml" file could not be found. So go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and find out in which package the missing file is, then install it and try again.

---

### Post by amsterdamharu on 2010-02-11
Hi zugwan, thank you for your reply.

Package is installed or I could not add it in step 5
[http://packages.ubuntu.com/search?suite=hardy&arch=i386&searchon=contents&keywords=libxml%2Fparser.h]("http://packages.ubuntu.com/search?suite=hardy&arch=i386&searchon=contents&keywords=libxml%2Fparser.h")

I think it cannot find it because some make/automake config files are incomplete because step 8 fails.

Will try to install Anjuta from tarball and see what dependencies aren't satisfied.
[update]
Tried it and got what I allways get trying to install a tarball, cannot even get through the ./configure.
> checking for GLIB... configure: error: Package requirements (glib-2.0 >= 2.16.0 gobject-2.0 >= 2.16.0 gmodule-2.0 >= 2.16.0 gthread-2.0 >= 2.16.0 gio-2.0 >= 2.16.0 unique-1.0 >= 1.0.0) were not met:

Got the glib [http://laotzu.acc.umu.se/pub/gnome/sources/glib/2.22/glib-2.22.0.tar.gz](http://laotzu.acc.umu.se/pub/gnome/sources/glib/2.22/glib-2.22.0.tar.gz) installed it without errors ./configure make and sudo make install but still get the same error when I run ./configure for anjuta. Giving up for today.

---

### Post by amsterdamharu on 2010-02-11
Ok, completely messed up my system. Anjuta would not install because of GTK+ being to old and GTK+ won't install because glib (called libglib in synaptic) being too old.

Installed glib without a problem but gtk+ complained about the older version still being there and I tried to remove it using synaptic. It was removing a lot of stuff untill I reset it. Should have downloaded the old bins and run make uninstall.

First I need to tar back my system because it's all messed up now. Then install Anjuta again through synaptic. Installing the latest version is just not possible.

---

### Post by amsterdamharu on 2010-02-12
Got anjuta again through synaptic and the version is 2.4.1, the current version for anjuta is 2.28.2 so it's clearly far behind, the deb makers for anjuta must be in a coma or something.

Can't do a manual install because gtk+ needs newer libglib2 and that one can't be removed from synaptic without completely removing your Ubuntu desktop.

[http://linuxappfinder.com/package/anjuta](http://linuxappfinder.com/package/anjuta)
Unless I upgrade to intrepid there is nothing to do.

The debug in this anique version of anjuta is under edit - > preferences -> installed plugins -> debugger.

Strange that anjuta needs automake to build anything but it's not installed as a dependency so it results in nothing compiling/building.

Was hoping for a place where there is more documentation to be found because the tutorials that are there are pretty basic.

---

