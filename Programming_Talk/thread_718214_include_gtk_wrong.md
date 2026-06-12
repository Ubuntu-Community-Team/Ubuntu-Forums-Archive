---
title: "include gtk wrong?"
date: 2008-03-07
forum: Programming Talk
---

### Post by Zeotronic on 2008-03-07
I have aquired code that makes use of gtk... the code askes for the gtk header as <gtk/gtk.h> which geany said was wrong... and after investigation, set it to <gtk-2.0/gtk/gtk.h> which seems to be right... however the gtk.h points to all of it's gtk... 'stuff' as <gtk/ *etc* >... which as I said seems to be wrong. I figure I'm messing up pretty badly somewhere along the lines, can anyone tell me what I'm doing wrong?

For the record, I am trying to compile Word War VI.

Sorry if my information isn't very helpful... I'm not used to headers causing me problems.

---

### Post by WW on 2008-03-07
I've never used geany, but it sounds like geany is "wrong".  You should be able to tell geany that you want to add the option **-I/usr/include/gtk-2.0** to the compiler command.  [This](http://geany.uvena.de/manual/0.13/index.html#set-includes-and-arguments) looks relevant.

---

### Post by Can+~ on 2008-03-07
Found something:

[http://library.gnome.org/devel/gtk-tutorial/stable/x111.html](http://library.gnome.org/devel/gtk-tutorial/stable/x111.html)

---

### Post by Zeotronic on 2008-03-07
Oh... duh.

---

### Post by Zeotronic on 2008-03-10
Ok, maybe not so 'duh' but still a major oversight on my part. Regardless, I cannot manage to figure out what I should be using... -lgtk doesn't seem to work, and my attempts at modifying the command to make it right are also wrong. Can+~'s link, therefore, doesn't seem to help. Does anyone else know anything?

---

### Post by WW on 2008-03-10
I still think the problem is getting geany configured correctly.  To be sure that you have gtk+ installed, try compiling and running the simple example [here](http://library.gnome.org/devel/gtk-tutorial/stable/c39.html). You can use geany to create the file base.c, but use the command shown in the web page in a terminal to compile the program.  You might first have to install **pkg-config**, e.g.
> 
$ sudo apt-get install pkg-config


If that works, then your installation of gtk+ is fine.  For help with geany, you could try their mailing list; see the link on the [geany web page](http://geany.uvena.de/).

---

