---
title: "VR Juggler, Opengl, OpenSG, and GMTL"
date: 2007-01-21
forum: Programming Talk
---

### Post by smagee12 on 2007-01-21
Hello, I really need VR juggler and GMTL especially for some VR application developemnt,
I do not know how to install thesep ackages to get them working with g++ and ubuntu, if anyoen could help me install any of these packages let me know.  Ill link the sites 

[http://www.vrjuggler.org/]("http://www.vrjuggler.org/")
[http://sourceforge.net/projects/ggt]("http://sourceforge.net/projects/ggt")

I laso need to program opengl, but i think i can figure that out, i dunno.  Any help would eb greatly appreciated, thanks!

---

### Post by hod139 on 2007-01-22
Make sure you have the package build-essential installed.  Then you will have to download the source code of the respective projects.  Then, hopefully, there will be a configure script, and you can run
```

./configure
make 
sudo make install (or sudo checkinstall)

```


The configure script will produce the Makefile, unless there are any errors, and then you type make to build and make install to install.  checkinstall will produce a .deb package for you, which can make uninstalling easier.  Any errors will probable be from missing headers and libraries, which you can search packages.ubuntu.com for the correct package to install.  Usually they are *-dev packages.

If there is no configure script, then there might just be a makefile.

If you have any specific difficulties, just post your problems here.

---

### Post by smagee12 on 2007-01-23
Thanks

---

