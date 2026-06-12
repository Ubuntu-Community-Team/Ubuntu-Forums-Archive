---
title: "Compiling for windows"
date: 2009-11-10
forum: Programming Talk
---

### Post by Ankhwatcher on 2009-11-10
Hi, I'm working on creating a pre-configured windows version of [Qutecom]("http://www.qutecom.org/") for a voip company I work with.

I would prefer to do the work of configuring and compiling on my Ubuntu x64 home server.
I have set up the server and successfully compiled a Linux version of the program from source, but I don't know how/if I can set up the compiler to create a windows installable.

If this is possible I'm sure there is already a guide, so if anyone knows its whereabouts please link me.

Thanks,
-ANkh

---

### Post by kavon89 on 2009-11-10
Hrm, assuming you compiled C/C++ code on Linux with the gnu tools, you may want to look into [Cygwin]("http://www.cygwin.com/") or [MinGW]("http://www.mingw.org/"). MinGW is better in my opinion. If using another compiler doesn't matter, use Visual Studio.

---

### Post by Ankhwatcher on 2009-11-10
I followed the GNU/Linux Instructions on [this page]("http://trac.qutecom.org/wiki/HowToBuildFromSource").
So I used Cmake, G++, QT, Boost and Glib along with a host of other dependancies.

---

### Post by Ankhwatcher on 2009-11-10
> **rojerfredrar said:**
> [COLOR=Black]Hi, Ankhwatcher
I am Rojerfredrar I read your post really you are doing good experiments, well I'm a computer science student so want to do some help but the problem is that I use the gnu so it is limited area for me and the other matter is that I have got admission so I have only basic knowledge I will try to solve your problem.
[/COLOR]

Thanks

---

### Post by Ankhwatcher on 2009-11-16
So does anyone have any ideas? I'm sure this has been done before.

In lue of the lack of response here I have set up windows to compile it, but the dependancy management is very rough compared to Ubuntu.

thanks, ANkh

---

### Post by phrostbyte on 2009-11-16
Try installing [mingw]("apt:mingw"), it's GCC except it makes Windows binaries.

---

### Post by Ankhwatcher on 2009-11-16
> **phrostbyte said:**
> Try installing [mingw]("apt:mingw"), it's GCC except it makes Windows binaries.

You mean install it in windows? In that case I have, it came with Qt.
Apt couldn't find it on Ubuntu, but I'll have a look with synaptics.

---

