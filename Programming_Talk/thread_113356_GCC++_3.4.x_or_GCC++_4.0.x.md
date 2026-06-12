---
title: "GCC/++ 3.4.x or GCC/++ 4.0.x ?"
date: 2006-01-06
forum: Programming Talk
---

### Post by bkv2k on 2006-01-06
I'm very new to Ubuntu/Linux.  I would like to do some programing in C++ using wxWidgets. When I loaded my system I installed gcc/++ 4.0.x. So far, I haven't been able to get gtk+ or wxWidgets to compile. It's occurred to me that the compiler version may account for some of my problems. Would I be better off with the 3.4.x version of the compiler?

---

### Post by Lord Illidan on 2006-01-06
Can you give us the errors given when compiling?

---

### Post by bkv2k on 2006-01-06
[QUOTE=Lord Illidan]Can you give us the errors given when compiling?[/QUOTE]

I'm not sure that I know how to do this. Here are the last messages:

**********************************************
checking for GTK+ version...
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.
****************************************************************

This is from INSTALL.txt:

*******************************
> mkdir buildgtk
> cd buildgtk
> ../configure --with-gtk
> make
> su <type root password>
> make install
> ldconfig
*******************************

When I execute the third line, the messages above result.  It appears that I need to install/compile gtk+-2.0. I suspect that will keep me busy for quite a while.

---

### Post by mo_x on 2006-01-06
You don't need to compile these packages yourself. You can install them with apt-get or synaptic.

---

### Post by bkv2k on 2006-01-06
[QUOTE=mo_x]You don't need to compile these packages yourself. You can install them with apt-get or synaptic.[/QUOTE]

I managed to melt my system down trying to remove gcc 4.0.x, so now I have a fresh ubuntu system to work from. :-)  Given that I have not loaded gcc, which version would you recommend?

Are you saying I can use Synaptic to load gtk+ and wxWidgets?

BTW, thanks to everyone for the help!

---

### Post by mo_x on 2006-01-06
sudo apt-get install build-essential libwxgtk2.6-dev

This will install everything needed to build software (gcc-4.0) and the wxWidgets development library.
Search in Synaptic for other packages, there is also some documentation.

---

### Post by bkv2k on 2006-01-06
Thanks for the help. I got gtk+ loaded and wxWidgets compiled/installed with no problem with gcc 4.0.x.

---

