---
title: "Qt configure error: Basic XLib functionality test failed"
date: 2009-06-10
forum: Programming Talk
---

### Post by remy06 on 2009-06-10
Hi,

I am trying to install Qt from source on ubuntu 8.04 hardy.I've downloaded "qt-x11-opensource-src-4.5.1.tar.gz" from their website.

I am following this tutorial on building static Qt applications:
[http://wiki.qtcentre.org/index.php?title=Building_static_Qt_on_Linux]("http://wiki.qtcentre.org/index.php?title=Building_static_Qt_on_Linux")

These are the commands I used so far:
```

./configure -static -release


```

but I am unable to get pass this step due to the following error while configuring halfway:

```

...
...
Basic XLib functionality test failed!
 You might need to modify the include and library search paths by editing
 QMAKE_INCDIR_X11 and QMAKE_LIBDIR_X11 in /tmp/qt-x11-opensource-src-4.5.1/mkspecs/linux-g++.

```

I have tried installing libx11-dev and xlibs-static-dev but the error persist...

Can someone please advice on how to solve this or how to specify the path mentioned??

Thanks in advanced..

---

### Post by gnuchanux on 2009-06-10
I too having the same problem.

The Google results gave me this link.
[http://www.qtforum.org/article/27401/debian-xlib-test-failed-after-configure.html](http://www.qtforum.org/article/27401/debian-xlib-test-failed-after-configure.html)

Anyway the answer there doesn't work for me.

---

### Post by remy06 on 2009-06-10
ya i've tried that too and it seems that the mentioned package in the google link, qt4-qmake does not exist..thus am trying to modify the include and library paths as mentioned in the error but not sure how to do it right..

Does anyone have a solution?

---

### Post by famaster on 2009-06-10
I had the same problem when I tried to install it, but when I tried to install QT4.5.1 for Embedded Linux, it worked fine.  Link: [http://www.qtsoftware.com/downloads/embedded-linux-cpp](http://www.qtsoftware.com/downloads/embedded-linux-cpp)

After downloading, the only difference is instead of "./configure", use "./configure -embedded".  Hope that helps.

---

### Post by famaster on 2009-06-10
Actually I'm having problems after that.  I got the "make" to work and everything, but after that, it's as if I never installed it.  How do I check the version of QT?  I don't think there were any errors, and I know it had to at least be partially successful because there's the QTEmbedded-4.5.1 folder in my /usr/local/Trolltech folder.

---

### Post by remy06 on 2009-06-11
Hi,

I've managed to install already.However, my application is missing functionality....Please refer to here:
[http://ubuntuforums.org/showthread.php?p=7438479#post7438479]("http://ubuntuforums.org/showthread.php?p=7438479#post7438479")

---

### Post by MattPhillips on 2009-07-18
Just to say thank you--I had the same problem and the solution gnuchaux linked to worked for me.  (Sorry it didn't work for him/her!)

Matt

---

### Post by martinreddy on 2009-10-08
I had the same problem. I found the config.tests/x11/xlib/ directory and did a 'make' there. That way I got an actual compile error: cannot find -lXext.

Installing the package 'libxext-dev' solved the problem for me.

---

### Post by stiebrs on 2009-10-18
thanks martinreddy. used your solution under debian lenny and now it's compiling. at least configuring ;)

---

### Post by ranskalex on 2009-11-12
worked for me too. Thanks martinreddy

---

### Post by toddunknown on 2009-11-12
Martinreddy's solution worked also for me on Red Hat Linux 5.3 after:

yum install libXext-devel

:KS

---

### Post by berte on 2010-05-18
Installed libxext-dev and configure worked on Ubuntu 10.04 (Lucid) using Qt 4.7 beta.

---

### Post by mark@qtrac.eu on 2010-06-11
I had the same problem. I installed zillions of -dev X libraries to no avail. But as soon as I installed libxext-dev as suggested here, the error went away and Qt is now building...
Thanks!

---

### Post by juhvu on 2010-06-26
Hi guys,

installing the libxext-lib was probably a prerequisite for me too, but that wasn't enough on my x64 10.04 Ubuntu.

I actually checked the qt/mkspecs/linux-g++-64/qmake.conf
The two suggested variables in the error output were pointing out to a
/usr/X11R6/lib64
but on my setup, there was no folder X11R6, but instead the needed stuff was directly under /usr/lib64

So I ripped the X11R6 from both paths and now it configures.

---

### Post by cbmnementh on 2010-06-30
Thanks martinreddy! Much appreciated.

---

### Post by Abir Valg on 2010-10-29
Thanks for the hint
On Ubuntu 10.10 here 
I downloaded libX11dev and libXext-dev,
besides I modified the spec file to point to /usr/include/X11 and /usr/lib/X11 instead of usr/X11R6/include & lib. (I donno if the last step played any role, though)

---

### Post by Wolfgang Griech on 2010-11-27
hi guys, you ever read the appropriate Qt page:
**[SIZE=4]"Qt for X11 Requirements" ???[/SIZE]**

[http://doc.qt.nokia.com/4.7/requirements-x11.html](http://doc.qt.nokia.com/4.7/requirements-x11.html)

got the same error messages as you described above, but perfectly worked after following that Qt page ;-)

---

### Post by thiago.project on 2012-07-18
Still get this error on Linux Mint 13 and Martinreddy's solution worked also for me. As Wolfgang mentioned, now I should give some credit to the requirements page next time. \o/ :D

---

### Post by ihussain on 2012-10-16
Thanks martinreddy. It worked for me in one go.

---

