---
title: "Creating a dll with MinGW in Linux"
date: 2015-01-14
forum: Programming Talk
---

### Post by efonde on 2015-01-14
Hello,
Firstly I'm a beginner with programming language. I was searching for Pidgin plugin that enable file sharing like and found this gem on [https://sourceforge.net/projects/fserv4pidgin/](https://sourceforge.net/projects/fserv4pidgin/). I was able to compile the source file (fserv.c) into fserv.so by editing the makefile and adding:

```
LINUX_CFLAGS = -I/usr/include/libpurple -I/usr/include/pidgin -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/x86_64-linux-gnu/glib-2.0/include \
                             -I/usr/lib64/glib-2.0/include -I/usr/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0 \
                             -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -DPURPLE_PLUGINS -DENABLE_NLS 
```

I want to use this plugin in pidgin windows but I'm not sure how to do this since windows use dll file. After some search, I found that we could use MinGW to create dll. 
So I installed MinGW in Linux hoping that I could compile the source file (fserv.c) in Linux. So far the only thing I know was from: [http://www.adp-gmbh.ch/win/misc/mingw/dll.html](http://www.adp-gmbh.ch/win/misc/mingw/dll.html).  

With the command: 
```
gcc -Wall -shared fserv.c -o fserv-dll.dll
```

But I got a fatal error:
```
fserv.c:36:23: fatal error: gtkplugin.h: No such file or directory #include <gtkplugin.h>
```

I hope someone could help me with how (if possible) to compile the source file (fserv.c) into a dll one. 
If I can't do it in Linux, could you let me know how to compile that source file in Wndows? What aplication I need and the steps required, etc.

Thank you.

---

### Post by Holger_Gehrke on 2015-01-14
> **efonde said:**
> I was searching for Pidgin plugin that enable file sharing like and found this gem on [https://sourceforge.net/projects/fserv4pidgin/](https://sourceforge.net/projects/fserv4pidgin/). I was able to compile the source file (fserv.c) into fserv.so by editing the makefile and adding:

```
LINUX_CFLAGS = -I/usr/include/libpurple -I/usr/include/pidgin -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/x86_64-linux-gnu/glib-2.0/include \
                             -I/usr/lib64/glib-2.0/include -I/usr/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0 \
                             -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -DPURPLE_PLUGINS -DENABLE_NLS 
```

I want to use this plugin in pidgin windows but I'm not sure how to do this since windows use dll file. After some search, I found that we could use MinGW to create dll. 
So I installed MinGW in Linux hoping that I could compile the source file (fserv.c) in Linux. So far the only thing I know was from: [http://www.adp-gmbh.ch/win/misc/mingw/dll.html](http://www.adp-gmbh.ch/win/misc/mingw/dll.html).  

That post is talking about using MinGW on Windows. What you're trying to do is a cross-compile. gcc is the name of the normal GNU C compiler. I'm not quite certain, but I think MinGW on Linux  installs another executable to produce Windows executables and dlls. The page at [http://arrayfire.com/cross-compile-to-windows-from-linux/](http://arrayfire.com/cross-compile-to-windows-from-linux/) has some information.
> **efonde said:**
> 
With the command: 
```
gcc -Wall -shared fserv.c -o fserv-dll.dll
```

But I got a fatal error:
```
fserv.c:36:23: fatal error: gtkplugin.h: No such file or directory #include <gtkplugin.h>
```

I hope someone could help me with how (if possible) to compile the source file (fserv.c) into a dll one. 
If I can't do it in Linux, could you let me know how to compile that source file in Windows? What aplication I need and the steps required, etc.

Thank you.

It's missing all the includes from the LINUX_CFLAGS line in the Makefile. You should read up on the options for using MinGW and change the Makefile so as to do the cross-compile. Obviously this plugin depends heavily on GTK and GDK. Does the Windows-version of pidgin come with these ? Otherwise you'll have to get them and put those DLLs somewhere where the plugin will find them ...

---

### Post by efonde on 2015-01-14
Here is the full makefile content: 

```
#Customisable stuff here
LINUX_COMPILER = gcc
WIN32_COMPILER = /usr/bin/gcc.exe


LINUX_CFLAGS = -I/usr/include/libpurple -I/usr/include/pidgin -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/x86_64-linux-gnu/glib-2.0/include \
                             -I/usr/lib64/glib-2.0/include -I/usr/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gdk-pixbuf-2.0 \
                             -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -DPURPLE_PLUGINS -DENABLE_NLS
WIN32_DEV_DIR = /root/pidgin/win32-dev
WIN32_PIDGIN_DIR = /root/pidgin/pidgin-2.1.1_win32
WIN32_CFLAGS = -I${WIN32_DEV_DIR}/gtk_2_0/include/glib-2.0 -I${WIN32_PIDGIN_DIR}/libpurple/win32 -I${WIN32_DEV_DIR}/gtk_2_0/include -I${WIN32_DEV_DIR}/gtk_2_0/include/glib-2.0 -I${WIN32_DEV_DIR}/gtk_2_0/lib/glib-2.0/include
WIN32_LIBS = -L${WIN32_DEV_DIR}/gtk_2_0/lib -L${WIN32_PIDGIN_DIR}/libpurple -lglib-2.0 -lgobject-2.0 -lgthread-2.0 -lintl -lpurple


#Standard stuff here
.PHONY:    all clean install uninstall


.DEPENDS: fserv.c 


all: .DEPENDS 
    gcc ${LINUX_CFLAGS} -Wall -pthread -I. -g -O2 -pipe fserv.c -o fserv.so -shared -fPIC -DPIC


install:
    mkdir -p $(DESTDIR)/usr/lib/purple-2
    install -m 664 fserv.so $(DESTDIR)/usr/lib/purple-2/


uninstall:
    rm -rf $(DESTDIR)/usr/lib/purple-2/fserv.so


clean:
    rm -f fserv.so fserv64.so fserv.dll fserv.lo fserv.la




fserv.so: .DEPENDS
    ${LINUX_COMPILER} -Wall -pthread -I. -g -march=athlon-xp -O2 -pipe fserv.c -o fserv.so -shared -fPIC -DPIC ${LINUX_CFLAGS} 


fserv64.so: .DEPENDS
    ${LINUX_COMPILER} -Wall -pthread -I. -g -m32 -m64 -O2 -pipe fserv.c -o fserv64.so -shared -fPIC -DPIC ${LINUX_CFLAGS}


fserv.dll: .DEPENDS
    ${WIN32_COMPILER} -Wall -I. -g -O2 -pipe fserv.c -o fserv.dll -shared -mno-cygwin ${WIN32_CFLAGS} ${WIN32_LIBS} -Wl,--strip-all
    upx fserv.dll

```

Is the last one code was how to compile the fserv.c into fserv.dll ? I read that -mno-cygwin is deprecated and not supported in MinGW. Would it be okay to remove that piece?

I checked and the pidgin windows does comes with all the required DLLs. What to do so the compiler would know where to locate the files? I'm using wine to install the pidgin windows.
Perhaps I should change the location WIN32_DEV_DIR and WIN32_PIDGIN_DIR to my pidgin wine location ( ~/.wine/drive_c/Program Files (x86)/Pidgin) ?

---

### Post by Holger_Gehrke on 2015-01-14
First, check what the MinGW-compiler is actually called. Set that as WIN32_COMPILER in the Makefile. Then check whether the header files for the Windows and Linux versions of the libraries are identical. If they are, you should change the WIN32_CFLAGS to use those, otherwise get the header files, put them somewhere and change the WIN32_DEV_DIR to that and change the option in WIN32_CFLAGS accordingly. And yes, pointing WIN32_PIDGIN_DIR to your copy of pidgin in wine is a good idea, too. I don't know about the -mno-cygwin option, my experience with cross compiling goes more towards pic, avr and arm stuff ...

---

### Post by efonde on 2015-01-14
>First, check what the MinGW-compiler is actually called. Set that as WIN32_COMPILER in the Makefile
Ok, done that. I changed "WIN32_COMPILER = gcc" since the linux use that.

>Check whether the header files for the Windows and Linux versions of the libraries are identical. 
Ok. So I have found out that gtk header files for Windows and Linux are the same.

---

### Post by Holger_Gehrke on 2015-01-15
> **efonde said:**
> >First, check what the MinGW-compiler is actually called. Set that as WIN32_COMPILER in the Makefile
Ok, done that. I changed "WIN32_COMPILER = gcc" since the linux use that.


I think that's wrong. I don't have it installed, but according to packages.ubuntu.com (and to the arrayfire page I linked to earlier) the cross compiler should be called something like i686-w64-mingw32-gcc, with variations depending on whether you're running a 32 or 64 bit Linux and whether you're targeting 32 or 64 bit Windows.

---

### Post by steeldriver on 2015-01-15
While this sounds like a noble exercise, if you have access to a Windows machine the pragmatist in me thinks it would almost certainly be easier to install MinGW/msys on **that** - or use whatever the current "free" version of MS Visual C/C++ or Visual Studio directly on Windows

---

### Post by efonde on 2015-01-15
i tried to install MinGW on windows in another laptop but I don't know why the windows suddenly became heavy loading after that. Almost to the point of freeze. Perhaps because it's a low spec Laptop (AMD C60) and 2GB ram.

And this one laptop that doesn't have windows at all.

---

### Post by efonde on 2015-01-16
anyway, thank you Holger. I'm able to create the DLL. I didn't think I would need to be specific with Pidgin version, Gcc version and MinGW version.

---

