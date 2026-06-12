---
title: "gegl ./configure problem"
date: 2012-04-23
forum: Packaging and Compiling Programs
---

### Post by cerke on 2012-04-23
Hi guys!

So, I've been trying to install gimp 2.8 rc1 on my Ubuntu 10.10
and I installed a bunch of libraries. Then I got stuck on gegl 0.2.0.
compiling...
At a point after the ./configure (or ./autogen.sh) command it says:

```
./configure: line 16446: syntax error near unexpected token `$GLIB_REQUIRED_VERSION,'
./configure: line 16446: `AM_PATH_GLIB_2_0($GLIB_REQUIRED_VERSION, :,'

```

What does it mean? I already installed the glib 2.28.2. version (which is btw one of the newest versions) and it still bugs me..

Can somebody help?

---

### Post by oldos2er on 2012-04-23
Moved to Packaging and Compiling Programs.

---

### Post by cerke on 2012-04-24
Sorry, didn't know where to put the topic..

so, anyone...help?

---

### Post by SeijiSensei on 2012-04-24
How about first running "sudo apt-get build-dep gegl"?  Maybe it's missing a dependent library.

---

### Post by bregma on 2012-04-24
> **cerke said:**
> Hi guys!
```
./configure: line 16446: syntax error near unexpected token `$GLIB_REQUIRED_VERSION,'
./configure: line 16446: `AM_PATH_GLIB_2_0($GLIB_REQUIRED_VERSION, :,'

```

This error means the file [FONT="Courier New"]/usr/share/aclocal/glib-2.0.m4[/FONT] is not installed.  It is normally packaged in libglib2.0-dev -- check to see if that package is installed.  If you built glib from source instead, make sure it was built with the right prefix and installed properly.

---

### Post by cerke on 2012-04-25
tried the 'sudo apt-get build-dep gegl' already a bunch of times, and it says:
```
E: Could not open file /var/lib/apt/lists/ppa.launchpad.net_otto-kesselgulasch_gimp_ubuntu_dists_maverick_main_source_Sources - open (2: No such file or directory)

```

then I tried to add that ppa repository that it asks, but with no result..
(I think someone put the whole gimp 2.8 package on that repository but it seams that I can't install from it..)

And after that not working tried to install the 'libglib2.0-dev' library and it works!!
gegl finally has everything it needs to run the 'make' command.
so, I run make && make install and it seams everything is as it should be.

but then I try to run ./configure for the gimp 2.8 rc1 installation and it says:
```
checking for GEGL... no
configure: error: Package requirements (gegl-0.2 >= 0.2.0) were not met:

No package 'gegl-0.2' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GEGL_CFLAGS
and GEGL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

da faq? checked it, gegl 0.2 package is in the usr/local/lib directory (among all).
why does it say it's not there?

---

### Post by bregma on 2012-04-25
> **cerke said:**
> tried the 'sudo apt-get build-dep gegl' already a bunch of times, and it says:
 gegl 0.2 package is in the usr/local/lib directory (among all).
why does it say it's not there?

Perhaps the rules to search for gegl do not look in /usr/local... did you try setting GEGL_CFLAGS and GEGL_LIBS explicitly?

---

### Post by cerke on 2012-04-25
it seams I cannot find those scripts...
where could they be?

---

### Post by bregma on 2012-04-25
> **cerke said:**
> it seams I cannot find those scripts...
where could they be?
They're enviroment variables.

I think the solution is to set PKG_CONFIG_PATH to pick up your installation before running configure.

Try
```
PKG_CONFIG_PATH=/usr/local/lib/pkgconfig ./configure
```
and see if that helps.  Note that there are no spaces around the '=', that's important.

---

### Post by cerke on 2012-04-26
still the same.
where are this variables (GEGL_CFLAGS and GEGL_LIBS) set so I can set them manually? maybe that will do..

---

### Post by bregma on 2012-04-26
The variables are not normally set.  They allow you to customize the behaviour of ./configure.  Try **./configure --help** to find out how to customize the behaviour of ./configure.

---

### Post by cerke on 2012-04-27
thanx, I'll try that. ^^

UPDATE: ok, solved the problem with gegl by using PKG_CONFIG_PATH and giving the right path to it.
then it asked for atk package, then for libffi, then glib, then gtk+...
I'll go crazzyyyyyy!!!

---

### Post by cerke on 2012-04-28
ok, after installing a bunch of packages, I detected a new problem...
now, my system doesn't read usb sticks, cd-s, dvd-s and stuff like that.
I have to manually mount them trough Disk Utility...
and on top of that I can't burn any cd-s cause my system can't recognize a blank cd-r...
also, my old gimp 2.6 lost some of the tools like velvet denoise...

I'm thinking of giving up. :-k

---

### Post by cerke on 2012-05-03
ok, installing new packages means installing 3 more on every new...
on top of that my ubuntu distribution is no longer supported..and gimp 2.8 is programmed for ubuntu 12.04 and it's almost impossible to get it working on 10.10 without messing something up.

conclusion: got to install a fresh distribution of linux (I'm thinking trying bodhi linux) and then all will work fine.

thanx to everyone who tried to help, I appreciate it very much.

---

### Post by geckobr on 2012-07-01
I think that solution can work to solve gegl problem:

```
Building and Installing GEGL From Source

git clone git://git.gnome.org/gegl
cd gegl
./autogen.sh --prefix=/opt/gimp-2.8
make
sudo make install
cd ..
```

source:
[http://www.gregorystrike.com/2012/05/03/how-to-build-gimp-2-8-from-source-in-ubuntu-12-04/](http://www.gregorystrike.com/2012/05/03/how-to-build-gimp-2-8-from-source-in-ubuntu-12-04/)

c'ya

---

