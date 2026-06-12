---
title: "Issues compiling Glade-3"
date: 2007-02-26
forum: Programming Talk
---

### Post by Ardoramor on 2007-02-26
Hello everybody!

I have Ubuntu running on vmplayer (waiting for my new laptop to double boot there). I'm pretty new to linux environment but have been programming before and know some way around ubuntu (but definatly little). I have downloaded Glade-3 Glade-Gnome-3 and other libraries like libglade-2.0 and gtk-2.0 and have all the compilers. Oh and I got -dev for glade too.

I designed a simple entry & button window just to test out how glade-3 runs. I saved it to a directory and got a little main.c with example code from a website but it opens the glade file and everything seems to be nice. In main.c I include <gtk/gtk.h> and <glade/glade.h>

I compile with gcc -o main main.c `libglade-config --cflags --libs`

Here are the errors it gives me:
bash: libglade-config: command not found
main.c:1:21: error: gtk/gtk.h: No such file or directory
main.c:2:25: error: glade/glade.h: No such file or directory
and then its program code because include files weren't found... 

I dont know where to find libglade-config. I have added extra repositories. Any suggestions are much appreciated!

---

### Post by lnostdal on 2007-02-27
take a look: [http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/)  

part 3 talk about gtk+/glade .. glade-2 and glade-3 is similar enough for you to figure out stuff .. but let me know if there are any problems and i'll update the guide for glade-3

---

### Post by Ardoramor on 2007-02-27
I have actually just now tried to see maybe something was wrong with libglade2-dev but when i tried to reinstall, it was fine. So i decided to install libglade-dev and it did... i tried to compile and it did. Its a bit weird that libglade2-dev didn't have libglade-config but libglade-dev did. Do you think its a good substitute? Btw, thanks for the link, learned more on glade :)

---

### Post by lnostdal on 2007-02-27
use pkg-config for everything .. libglade-config etc. is obsolete

edit: glad you found some of it useful :)

---

