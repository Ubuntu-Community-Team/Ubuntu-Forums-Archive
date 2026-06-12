---
title: "OpenGL on Eclipse"
date: 2009-03-10
forum: Programming Talk
---

### Post by Ibrahim mufeed on 2009-03-10
Hi,

I am trying to do some OpenGL programing on my Ubuntu, using Eclipse, I never write any code on linux before, but I do A LOT on Windows XP.

I have installed Eclipse suing the Add Remove programs but after the installation I found out that it is only for Java programing, and I need to write C, C++ programs.

Also, I do not know how to install or configure OpenGL, I did it on Visual Studio on XP, but I want to try it on Ubuntu.

I need some basic detailed instructions, (if any).

Thanks,

---

### Post by diafanos on 2009-03-10
> **Ibrahim mufeed said:**
> Hi,
I have installed Eclipse suing the Add Remove programs but after the installation I found out that it is only for Java programing, and I need to write C, C++ programs.




You can install netbeans with c/c++ support ([http://www.netbeans.org/downloads/index.html]("http://www.netbeans.org/downloads/index.html"))

---

### Post by vandorjw on 2009-03-10
I don't know about OpenGL but I do know if you want to program you need.

sudo apt-get install build-essential

I do not like net-beans and prefer geany.

Geany supports all languages I have come across.
(although it is not as powerful as netbeans, it is ALOT faster)

Cheers - CC7

---

### Post by JPtux on 2009-03-10
You have to install a plugin to use eclipse with C/C++.
Regards

---

### Post by Shin_Gouki2501 on 2009-03-10
netbeans, java + netbeans jogl pack , works fine here.

---

### Post by k2t0f12d on 2009-03-10
I might recommend [Code::Blocks]("http://www.codeblocks.org/").  It's a fully functional C/C++ IDE based on wxWidgets.  Very familiar working environment if you are coming from MSVS.

I'm not sure if there is a Debian package release, so, here are some useful directions for getting a working copy put up on your machine.

[http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_from_source_on_Linux](http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_from_source_on_Linux)

---

### Post by Can+~ on 2009-03-11
> **Ibrahim mufeed said:**
> Hi,

I am trying to do some OpenGL programing on my Ubuntu, using Eclipse, I never write any code on linux before, but I do A LOT on Windows XP.

I have installed Eclipse suing the Add Remove programs but after the installation I found out that it is only for Java programing, and I need to write C, C++ programs.

Adding support for C/C++ in eclipse:

```
sudo apt-get install eclipse-cdt
```

And for opengl, I guess you only need to set up the project with the corresponding flags.
(and for pytholians, eclipse-pydev is recommended)

---

### Post by Ibrahim mufeed on 2009-03-12
Thank you so much, It works now.

I will start having fun on Eclipse. ;)

---

