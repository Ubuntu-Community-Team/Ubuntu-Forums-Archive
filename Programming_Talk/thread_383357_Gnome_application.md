---
title: "Gnome application"
date: 2007-03-13
forum: Programming Talk
---

### Post by bluezapper on 2007-03-13
Hi all,

I want to build Gnome or GTK applications. I have seen that I have to include packages gnome.h and gtk/gtk.h for bulding these applications.

I would like to now if these libraries already come in default with Ubuntu or should I download them separately. Also, which IDE is the best one for these kind of development. Is Anjuta fine ?? 

waiting for your replies,

thanks and regards,

bluezapper.

---

### Post by lnostdal on 2007-03-13
I've written down what packages and tools you need to install and use to develop Gnome/GTK+-applications here: [http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/) .. You should be able to get started with GTK+-development regardless of what IDE you chose based on those writings.  Everything is included in the Ubuntu repositories so there is no need to download anything separately.

Use any IDE you like for coding and Glade for GUI-design.  

* I use Emacs for IDE/editor but it has a somewhat steep learning curve.

* KDevelop seems nice. Even if it uses KDE/QT for GUI-toolkit you can of course develop Gnome/GTK+ software with it.

* Eclipse is another alternative: [http://www.eclipse.org/cdt/](http://www.eclipse.org/cdt/)

..I have no specific recommendation besides my own bias of preferring Emacs for everything.

---

### Post by bluezapper on 2007-03-13
Hi Inostdal,

Great Documentation !!

Your link was very helpful and I successfully compiled my first GTK application. Just for information, I would like to what "-std=c99" in your command means

gcc -o gtk-helloworld -Wall -g -std=c99 `pkg-config --cflags --libs gtk+-2.0`
gtk-helloworld.c

thanks again,

best regards,

bluezapper.

---

### Post by lnostdal on 2007-03-13
It enables support for an "updated version" of the C standard called C99: [http://en.wikipedia.org/wiki/C99#C99](http://en.wikipedia.org/wiki/C99#C99)

(I'm hoping to convert the documents to (X)HTML, as PDF-files are somewhat cumbersome. I haven't yet been able to figure out how OpenOffice can include footnotes when exporting to (X)HTML though.)

---

