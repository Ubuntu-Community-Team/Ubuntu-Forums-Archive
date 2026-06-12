---
title: "Where is Motif?"
date: 2008-09-09
forum: Programming Talk
---

### Post by resander on 2008-09-09
I am an Ubuntu newbie wanting the Motif header files for C/C++ programming. Where/how can I find these and, if there is some form of search facility, what search key to use?

---

### Post by amo-ej1 on 2008-09-09
```

edb@lapedb:~$ apt-cache search motif | grep dev
freeglut3-dev - OpenGL Utility Toolkit development files
libglut3-dev - development libraries and headers for GLUT
libxt-dev - X11 toolkit intrinsics library (development headers)
libzephyr-dev - The original "Instant Message" system development libraries
tk8.4-dev - Tk toolkit for Tcl and X11, v8.4 - development files
lesstif2-dev - development library and header files for LessTif 2.1
libvibrant6-dev - NCBI libraries for graphic biology applications (development files)
libwxgtk2.4-contrib-dev - wxWindows Cross-platform C++ GUI toolkit (development contrib libs)
libwxgtk2.4-dbg - wxWindows Cross-platform C++ GUI toolkit (GTK+ development)
libwxgtk2.4-dev - wxWindows Cross-platform C++ GUI toolkit (GTK+ development)
libxbae-dev - Xbae Matrix Widget development package
tk-dev - The Tk toolkit for Tcl and X11 (default version) - development files
tk8.3-dev - Tk toolkit for Tcl and X11, v8.3 - development files
tk8.5-dev - Tk toolkit for Tcl and X11, v8.5 - development files
xmhtml1-dev - A Motif widget for display HTML 3.2
libmotif-dev - Open Motif - development files

```

So you probably want to install the last one 

```

sudo apt-get install libmotif-dev

```

To see what files are in an installed package

```

dpkg -L libmotif-dev

```

---

### Post by resander on 2008-09-10
I have spent nearly two days getting nowhere trying packages with motif in the name. I never found the header files. Where I really expected them I got odd-looking script-like files archived with gz.

While looking and fumbling I stumbled upon packages lesstif2 and lesstif2-dev. The latter contained the header files and also static libraries. I fed these to the code::blocks IDE and my little test program worked fine.

Why was it so difficult to find this? Is it because Motif has fallen into disuse in the Linux world?

---

### Post by mssever on 2008-09-10
> **resander said:**
> Why was it so difficult to find this? Is it because Motif has fallen into disuse in the Linux world?
Motif is proprietary, so it's not available in the repos. I think that lesstif is a motif clone (which you found). So the reason it's so hard to find is because it isn't there. :)

To be honest, I can't understand why someone would want motif/lesstif in the first place since they're so ugly, but that's just me.

---

### Post by resander on 2008-09-11
> **mssever said:**
> To be honest, I can't understand why someone would want motif/lesstif in the first place since they're so ugly, but that's just me.

I want to port C++ programs to Linux and if all goes well, eventually myself. I need a GUI that is easy to use/learn and free. And small. From reading the manual it would appear Motif satisfies these criteria.  

I did not know Motif was proprietary, indeed I thought no programs in the Unix/Linux world are. The lesstif2 is under LGPL which (I think) means it is free to use and incorporate in my own software. 

I have heard of QT and wxWidgets. Are they small and better/better-looking?

---

### Post by amo-ej1 on 2008-09-11
The 'big three' are Qt, GTK and wxWdidgets, it think it would be rather difficult to be worse looking than motif ;-). The only question remaining is what do you mean by 'small' ?  Memory footprint  ? And even that is relative ... perhaps  to better state the environment or what you plan to do. Because there are also several of those GUI libraries adapted to the use on mobile devices (take a look at [www.openmoko.org](www.openmoko.org) where the focus on a complete solution for smartphones, including the GUI aspects)

---

### Post by jespdj on 2008-09-11
See [FAQ: GUI Toolkits for Linux](http://ubuntuforums.org/showthread.php?t=772507&highlight=GUI+toolkits)

GTK+ is the GUI toolkit used by the GNOME desktop (Ubuntu).
Qt is the GUI toolkit used by the KDE desktop (Kubuntu).

Note that you can also run GTK+ programs on Kubuntu and Qt programs on Ubuntu; your choice of GUI toolkit does not restrict you to a certain desktop environment.

Ofcourse there is proprietary software on Linux and other Unix-like operating systems. Your video driver for example is most likely a piece of proprietary software running on your Ubuntu system. Adobe Flash is another example.

---

### Post by resander on 2008-09-13
Many thanks for the advice.

Having read more about Motif, I no longer think it is simple to use. I have to wash my mouth with soap (or is it the pen). In Windows I can place a control at x,y with one call. Motif seems to require several, including placement managers for this simple task. Motif has callbacks for events, while Windows uses messages that have to be analysed. To me Windows, on balance, is easier to use and learn (that is coming from someone who is fed up using bloatware like Windows). Nor, do I believe Motif can be small sitting on top of X-Windows with its protocols and XT.

So, I will have a look at GTK and QT. Hopefully, these will be easier to find and get up and working.

For a GUI, how small is small? Well, Vista with its GUI is not, GDI+ used in Windows XP and probably used for the XP GUI is not (2.5MB?). So what is? A GUI is not complicated. The operating system already handles the detection of events and 2D graphics packages are available for rendering the widgets. Giving widgets a 3D look is not space consuming (take a screen shot of a GUI, zoom in and have a look). Nor is the technical use of gradients and filters to beutify the GUI (leaving the artistic skills and time out of it). I think a simple and sufficient GUI for a PC should be well within 100KB, including size of code and necessary data support, not pixel buffers.

---

