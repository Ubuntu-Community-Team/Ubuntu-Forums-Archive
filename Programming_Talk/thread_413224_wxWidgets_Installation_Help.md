---
title: "wxWidgets Installation Help"
date: 2007-04-18
forum: Programming Talk
---

### Post by grantus on 2007-04-18
I am having trouble installing the wxWidgets X11 and GTK libraries.
I run the configure tool and get errors right at the end regarding missing X11 or GTK libraries. 
The Package Manager tool shows that the X11 lib and GTK libs are installed.
The .so files exist in the /usr/libs folder.
The path variable is set to contain that directory among many others.

Is there an obvious step i am missing?

Running Ubuntu 6.10
HP Compaq nw8440 laptop
Fresh install (just over an hour ago)
No internet access to the Linux machine due to a restricted corporate LAN allowing only corporate PCs.
Can download binaries and copy to Linux box via USB stick.

---

### Post by dsl on 2007-04-19
If you are installling from sources, you need libgtk2.0-dev for wxGTK.
Never used wxX11 but I think the problem is similar.

---

### Post by grantus on 2007-04-19
Okay.

I have acquired and installed many packages now:

wx -- libwxbase, libwxbase-dev, libwxgtk, wxHeaders, wxCommon.
gtk -- libgtk, libgtkbin, libgtkcommon, libgtkdev

The .so files for libwx exist in /usr/lib. The .h files in the /usr/indclude/wx folder exist. The package files exist is /usr/lib/wx/package.
The PATH variable has th include files directory in it. The LD_LIBRARY_PATH variable has the library files directory in it.

wx-config exists in /usr/bin.

i go to compile my code, with 

g++ code.cpp `wx-config --libs` `wx-config --cppflags` -o code

Doesn't work. It goes through every .h file in the wx include folder and states that it is not declared in this scope or not declared at all.
Why?

---

### Post by dsl on 2007-04-21
> **grantus said:**
> Okay.

I have acquired and installed many packages now:

wx -- libwxbase, libwxbase-dev, libwxgtk, wxHeaders, wxCommon.
gtk -- libgtk, libgtkbin, libgtkcommon, libgtkdev

The .so files for libwx exist in /usr/lib. The .h files in the /usr/indclude/wx folder exist. The package files exist is /usr/lib/wx/package.
The PATH variable has th include files directory in it. The LD_LIBRARY_PATH variable has the library files directory in it.

wx-config exists in /usr/bin.

i go to compile my code, with 

g++ code.cpp `wx-config --libs` `wx-config --cppflags` -o code

Doesn't work. It goes through every .h file in the wx include folder and states that it is not declared in this scope or not declared at all.
Why?

"not declared in this scope" usually refers to variables, not to include files.

If you post the whole bunch of messages (or a significant selection if it is too long) maybe I could understand more.

Also, you could post the outputs of the single commands

```

wx-config --cppflags
wx-config --libs

```

---

