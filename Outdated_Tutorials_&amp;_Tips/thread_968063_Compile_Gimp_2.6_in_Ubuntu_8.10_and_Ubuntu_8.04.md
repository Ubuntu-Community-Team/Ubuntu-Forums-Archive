---
title: "Compile Gimp 2.6 in Ubuntu 8.10 and Ubuntu 8.04"
date: 2008-11-02
forum: Outdated Tutorials &amp; Tips
---

### Post by niccholaspage on 2008-11-02
This tutorial will show you how to compile Gimp 2.6 in Ubuntu 8.10 and Ubuntu 8.04(Please test Ubuntu 8.04. It worked for me, But I have no idea about you.).
Any 2.6 version should work. ex:2.6.1, 2.6.2 etc.
Before we start, I am going to go through a Why Compile Gimp?

First of all, Why go through trouble compiling Gimp when its there in the repositories?
Well, It will get you the latest. For example now that Ubuntu 8.10 is out, getdeb won't update any debs for 8.04, Which means Gimp will be stuck at 2.6.1 at the website. You may find some repository but compiling makes you learn something about the operating system.
And it might not always be good to have the latest and greatest, So there might even be a guide to compiling 2.4 soon. You never know. So now that we got that out of the way, Lets start the tutorial! (I hope you want to.)

1. Install the packages need to compile programs:
```
sudo apt-get install build-essential subversion libtool ruby
```2.Install Gimp's dependencies:
```
sudo apt-get build-dep gimp
```3.Get the latest Gimp version from the website and extract it:
```

wget ftp://ftp.gimp.org/pub/gimp/v2.6/gimp-2.6.2.tar.bz2
tar jxvf gimp-2.6.2.tar.bz2

```4.Get and Compile BABL:
```

svn co http://svn.gnome.org/svn/babl/trunk/ babl
cd babl
./autogen.sh --prefix /home/$USER/gimp-2.6
make (or "make -j 2" for multiple cores.)
make install
cd ..

```5.Get and Compile GEGL
```

svn co http://svn.gnome.org/svn/gegl/trunk/ gegl
cd gegl
./autogen.sh --prefix /home/$USER/gimp-2.6
make (or "make -j 2" for multiple cores.)
make install
cd ..

```6.Compile Gimp:
```

cd gimp-2.6.*
export PKG_CONFIG_PATH=/home/$USER/gimp-2.6/lib/pkgconfig
./configure --prefix /home/$USER/gimp-2.6
make (or "make -j 2" for multiple cores.)
make install

```7. Enjoy your Gimp by running(You will need to be the user who compiled Gimp):
```
/home/$USER/gimp-2.6/bin/gimp
```Now what if you want to uninstall Gimp? Well this is simple. Delete the directories and run the following commands:

1.Remove Gimp's dependencies:
```

sudo apt-get autoremove --purge

```If you don't have a updated computer, than run this command instead of the one above:
```

sudo apt-get purge docbook-xsl docbook-xsl-doc-html libbabl-0.0-0-dev libffi-dev libgegl-0.0-dev python-gobject-dev python-gtk2-dev python-gtk2-doc

```If you are running Hardy you may need to omit some packages above.
2.If you are running **Intrepid**, run the following command:
```

sudo apt-get remove dpkg-dev g++ g++-4.3 libc6-dev libstdc++6-4.3-dev libtimedate-perl linux-libc-dev patch subversion libtool ruby

```If you are running **Hardy**,than run this command instead:
```

sudo apt-get remove dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl linux-libc-dev patch subversion libtool ruby

```3.And Finally run this command:
```

cd /home/$USER/
rm -rf .gimp-2.6 .gegl-0.0

```If you have trouble just post below.

---

### Post by niccholaspage on 2008-11-05
BUMP!

I finally added some uninstall instructions and everything and now the tutorial is finally in the Tutorial Section.

---

### Post by halem on 2008-11-16
Hi, I just followed this guide and it was perfect and all but, it didn't show me how to remove the older versions that lingered and how do I make it so that the start menu link to gimp actually go to 2.6.2 instead of 2.6.1 in Ubuntu 8.10.

How do I also remove the source code files from the computer as well after compiling.

This guide is perfect btw. Thanks

---

### Post by exploder on 2008-11-16
Gimp 2.6.2 is available for Hardy and Intrepid. I made a request at getdeb.net and they kindly built the packages for Hardy.

---

### Post by kevdog on 2008-11-16
Does gimp have a svn version?

---

### Post by halem on 2008-11-16
If you don't mind me asking, how exactly do you use the files from getdeb.net

I don't want to do it wrong so I'm asking ahead of time

---

### Post by polarapfel on 2009-02-07
I can't build gegl as autogen.sh/configure.sh fails to find the already installed babl.

This is the resulting output of configure:

```
checking for BABL... configure: error: Package requirements (babl >= 0.0.23) were not met:

No package 'babl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BABL_CFLAGS
and BABL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Configure failed or did not finish!
```

My prefix is "/opt/backports/gimp-2.6". babl is installed in libs and include.

I tried setting

```
export PKG_CONFIG_PATH=/opt/backports/gimp-2.6/lib/pkgconfig
```

/opt/backports/gimp-2.6/lib/pkgconfig contains babl.pc with this content:

```
prefix=/opt/backports/gimp-2.6
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
includedir=${prefix}/include

Name: babl
Description: Dynamic, any to any, pixel format conversion library
Version: 0.0.23
Cflags: -I${includedir}/babl-0.0
Libs: -L${libdir} -lbabl-0.0 -lm
```

Still, gegl's configure script won't find babl.

I don't know what's wrong here.

Any help is welcome.

I explicitly don't want deb-get's Gimp packages as I want to keep Hardy's Gimp 2.4. Using the pre-made packages, there is a dependency problem with the "ubuntu-desktop" meta-package which really shouldn't be removed.

Thanks for your help!

Tobias

---

### Post by solder4Christ on 2009-02-10
I'm having the same problem as polarapfel.

---

### Post by neota on 2009-02-11
> **polarapfel said:**
> I can't build gegl as autogen.sh/configure.sh fails to find the already installed babl.

This is the resulting output of configure:

```
checking for BABL... configure: error: Package requirements (babl >= 0.0.23) were not met:

No package 'babl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BABL_CFLAGS
and BABL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Configure failed or did not finish!
```

My prefix is "/opt/backports/gimp-2.6". babl is installed in libs and include.
Still, gegl's configure script won't find babl.

I don't know what's wrong here.


Neither do I. However, I fixed it by deleting all installed BABL and GEGL libraries / files, checking out the latest svn versions of BABL and GEGL, and recompiling and reinstalling them.

Kevdog:
[http://developer.gimp.org/svn.html](http://developer.gimp.org/svn.html)

---

### Post by Shawn Reist on 2009-02-12
Hello,

I am still learning how to do things in Linux.  I managed to followed the instructions to upgrade gimp 2.4.5  to 2.6.4 on my EeePC, ran into error about 


```
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BABL_CFLAGS
and BABL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```


I did some searching and used following two lines. I am not sure which *one or both* allowed me to finish compiling **gegl**

```
export PKG_CONFIG_PATH=/home/shawn/gimp-2.6/lib/pkgconfig:$PKG_CONFIG_PATH

export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH
```

this was inserted into step 5.



```
svn co http://svn.gnome.org/svn/gegl/trunk/ gegl
cd gegl
[B]export PKG_CONFIG_PATH=/home/shawn/gimp-2.6/lib/pkgconfig:$PKG_CONFIG_PATH
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH[/B]
./autogen.sh --prefix /home/$USER/gimp-2.6
make (or "make -j 2" for multiple cores.)
make install
cd ..

```

Now...

I am wondering if I can somehow make the compiled program into a **deb** so if and when I redo my system I can just install the deb without having to recompile the complete program.

I would also like to know how I can have the compiled program installed to the /usr/share directory?

---

### Post by horacle on 2009-07-12
I was unable to install babl at all

---

### Post by Adam590 on 2010-03-15
Looks promising, but I also can't install BABL.

I get this at the end of the "make" step:

```
make[2]: *** No rule to make target `CIE-Lab.la.lo', needed by `CIE-Lab.la'.  Stop.
make[2]: Leaving directory `/home/myusername/babl/extensions'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/myusername/babl'
make: *** [all] Error 2

```

FWIW, I've also tried checking at getdeb, but unfortunately they aren't offering this version for anything prior to Ubuntu 9.04 (and their "legacy website" link doesn't work).

---

