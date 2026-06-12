---
title: "libgtk2.0-dev issues in Hardy"
date: 2008-04-04
forum: Programming Talk
---

### Post by gatlin on 2008-04-04
I am interested in doing some GTK development (a Pidgin plugin FWIW), and so I installed libgtk2.0-dev and other requisite libraries.  As part of the plugin creation process, I downloaded the Pidgin source and compiled (you have to compile Pidgin and then develop plugins in a specific folder to use their makefile).  

Anyway, Pidgin compiled.  That was good.  What is not good is that it appears to be the only GTK app that does so.  When compiling Pidgin plugins, or even the simple Hello World program which GTK provides, I get the compile error that gtk/gtk.h does not exist.  I'm looking at it right now, but this does not seem to matter to the linker.  

Any thoughts?  The GTK libraries were installed to /usr/include.

---

### Post by WW on 2008-04-04
> **gatlin said:**
> ... or even the simple Hello World program which GTK provides, I get the compile error that gtk/gtk.h does not exist.
What command did you use to compile the HelloWorld program?  Did you include `pkg-config --cflags gtk+-2.0` in the gcc command?

---

### Post by gatlin on 2008-04-04
Yes, I did.  Actually it was the command in the tutorial, copied and pasted into the terminal.  

I've once before done a little GTK programming on a machine with the libraries already installed, so I do have a vague idea of what should be going on.  

I will try recompiling pidgin to see if maybe something broke between compiling pidgin and my current endeavors.  This is unlikely, but then again aren't so many bugs unlikely?

---

### Post by WW on 2008-04-04
Do you mean [this tutorial](http://library.gnome.org/devel/gtk-tutorial/stable/x111.html)?  I hope you didn't cut and paste that entire command; that backslash will probably confuse bash (there is another thread about this same issue). A simpler version of that command is
> 
gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags --libs gtk+-2.0`


---

### Post by gatlin on 2008-04-04
What you sent me is exactly what I typed.  I made sure to combine the two calls to pkg-config.  I am certain I followed the compile steps correctly.  The trouble is, I have used apt-get to install libgtk2.0-dev and yet for some reason, while the header files and libraries exist, they are not being discovered by the linker.  

I have a feeling it has something to do with my having upgraded to Hardy (I never tried on Gutsy).

---

### Post by WW on 2008-04-04
Show the output of this command
> 
pkg-config --cflags --libs gtk+-2.0


---

### Post by gatlin on 2008-04-04
-I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0

---

### Post by WW on 2008-04-04
Hmmm... According to [this list](http://packages.ubuntu.com/hardy/i386/libgtk2.0-dev/filelist), gtk/gtk.h is in /usr/include/gtk-2.0, and you say you installed libgtk2.0-dev, so the header file should be there.  The pkg-config command gives the correct -I option to find gtk/gtk.h.  So... I'm stumped.  Sorry.


(You really used back-quotes, and not regular single quotes, around the pkg-config command in your gcc command?  Sorry, just have to check.  Nah, you would probably have gotten some other error if you had done that.)

---

### Post by gatlin on 2008-04-04
Has anyone had this problem in Gutsy?  Also, if someone has gotten this to work, could you please tell me what commands you issued and in what order? 

I'll keep working on it, thanks though!

---

### Post by WW on 2008-04-04
On my gutsy computer, helloworld.c compiles fine with the command I gave above.

---

### Post by WW on 2008-04-04
Take a look at [this bug report](https://bugs.launchpad.net/ubuntu/+source/anjuta/+bug/206868).  There aren't enough details in the report to be sure this is related to your problem, but it sounds familiar.  Too bad the bug reporter didn't also try to build something from the command line.

---

### Post by kingkong22 on 2008-04-04
take a look :
[http://ubuntuforums.org/showthread.php?t=744319](http://ubuntuforums.org/showthread.php?t=744319)
for gtk linking options

---

