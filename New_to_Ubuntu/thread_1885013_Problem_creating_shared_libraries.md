---
title: "Problem creating shared libraries"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by RobertMajor on 2011-11-22
Hi all,

I am having trouble creating and installing a shared library. I am trying to run some programs from OpenGL Super Bible which requires the shared library GLTools.

I have tried multiple ways of generating this shared library following the instructions from these sites:

[www.gnu.org/software/libtool/manual/libtool.html#Creating-object-files]("http://www.gnu.org/software/libtool/manual/libtool.html#Creating-object-files")
tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html
[www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html]("http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html")

Every time I have managed to generate the shared library and install it with no problems (I do get a few warning when compiling). At the end of the process I end up with the following three files in /usr/local/lib

libGLTools.so
libGLTools.so.0
libGLTools.so.0.0.0

running ldconfig -v I get: libGLTools.so.0 -> libGLTools.so.0.0.0

But then when I try to run my code in Qt I get the following message in Application Output:

>> error while loading shared libraries: libGLTools.so.0: cannot open shared object file: No such file or directory

Furthermore, if I use ldd I get a list of all the libraries used by the program including libGLTools but it says libGLTools.so.0 => not found

/usr/local/lib is definitely on my search path since the program uses other libraries in that folder and it has no problems finding those. I have now spent over week on this and I cannot figure out how to fix it. Any suggestions would be greatly appreciated?

---

