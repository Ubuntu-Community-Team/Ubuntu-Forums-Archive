---
title: "where to find c/c++ source code"
date: 2007-01-31
forum: Programming Talk
---

### Post by nite owl on 2007-01-31
Hi I'm begining to learn c/c++, was looking for a site where i could download the source code of full applications for the two to see how they work instead of just trying to go off the little examples I find I learn better dealing with real program source code???Thanks guys.:)

---

### Post by lnostdal on 2007-01-31
> **nite owl said:**
> Hi I'm begining to learn c/c++, was looking for a site where i could download the source code of full applications for the two to see how they work

Take the name of any open source program and type it into google. Let's try "gaim".  This leads me to: [http://gaim.sourceforge.net/downloads.php](http://gaim.sourceforge.net/downloads.php) and you'll see "Gaim 1.5.0 (Source)" mentioned at the bottom there.

But in general developers work with or against source code "repositories" using tools like CVS and SVN. You'll see a way of getting the source code using SVN at the same page also.


[quote=nite owl] instead of just trying to go off the little examples I find I learn better dealing with real program source code???[/QUOTE]

I very much doubt this will work as intended. (edit: correction; i _know_ with 100% certainty that it won't) The right way to learn for instance how to create the GUI-part of an application like Gaim is to follow the GTK+ tutorial with its small examples with explanations of concepts while at the same time browsing reference-docs:

[http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)
[http://developer.gnome.org/doc/API/2.0/gtk/index.html](http://developer.gnome.org/doc/API/2.0/gtk/index.html)

---

### Post by ansi on 2007-01-31
You can use
                [http://www.google.com/codesearch](http://www.google.com/codesearch)
or
                sudo apt-get source <package> [COLOR="Silver"](if you have configured *sources.list* and stable internet-connection, of course)[/COLOR]

---

### Post by pythonbite77 on 2007-01-31
The Freshmeat site: 

[http://freshmeat.net/browse/160/]("http://freshmeat.net/browse/160/")

contains OSS for Unix/Linux and has a search by language feature. Currently there are over 4000 C++ projects and over 8000 C projects.

---

### Post by nite owl on 2007-01-31
Thanks pythonbite77, ansi & lnostdal...exactly what I was looking for

---

