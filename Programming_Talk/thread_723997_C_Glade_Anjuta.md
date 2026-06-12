---
title: "C Glade Anjuta"
date: 2008-03-14
forum: Programming Talk
---

### Post by inyoka on 2008-03-14
I would like to develop small C & Glade apps for system administration tasks such as: tying together command line applications, configuring text files, with basic GUI's.  

I have two problems, first all the tutorials I have found concentrate on the IDE's, and mine never seems to be the same version as in the example causing endless frustration.  Second most concentrate on developing desktop applications.  

So I am looking for a small open source, C & Glade based system administration program/project which I can use as a working example to cut my teeth on.  It only wants to be very simple, and easy to understand, has anyone any suggestions?  The plan is that my knowledge might develop with the project and I might get some experience using CVS and other development tools.

Any suggestions would be gratefully received.

---

### Post by inyoka on 2008-03-16
Okay I found something to get me up to speed on C its : [http://www2.its.strath.ac.uk/courses/c/](http://www2.its.strath.ac.uk/courses/c/)
Its an award winning C course from 10 years ago.  If you :
> wget -r [http://www2.its.strath.ac.uk/courses/c/](http://www2.its.strath.ac.uk/courses/c/) 
You can get the course locally.  Alternatively:
> wget [http://publications.gbdirect.co.uk/c_book/the_c_book.pdf](http://publications.gbdirect.co.uk/c_book/the_c_book.pdf)
Should get you a complete out of print book on C and although I have only read the first Chapter it appears to be very good.  It will at the very least explain why it feels much better coding in C than in C# and Java.

I am giving up on Anjuta for the moment, I plan to learn Glade in the future, and I use vim for coding.  For Glade a basic user guide can be found here:

> [http://glade.gnome.org/manual/index.html](http://glade.gnome.org/manual/index.html)

As for CVS I'll probably find equally good documentation at their web-site when I get my Sys Admin program into a releasable state.

Hope somebody finds this info useful in the future.

---

### Post by inyoka on 2008-03-17
Hmm, this is in danger of turning into a blog, but anyway I used krugle to search for a the mdb tools source code and of course the source is located at sourceforge :
```
[http://mdbtools.sourceforge.net/]("http://mdbtools.sourceforge.net/")
```
This is a C and Glade app, although theres some java code in their for some reason, but it makes a good example, I will try to look for a smaller app, but in the mean time does anyone know of a small, well-coded, Glade & C project? Preferably using mysql in some way but that's not essential.  I just want a working  example of writing a C app using a .glade interface.

---

### Post by sq377 on 2008-03-18
If you want to learn gtk, I really have to suggest the Foundations of GTK+ Development [http://www.gtkbook.com/](http://www.gtkbook.com/).  You can find a few pages on google books to get a good intro.  Also [http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/) is the best place to startBut you really dont need to learn gtk/glade at the same time.  Learn gtk+ well, and glade will just make sense when you get to it.  However if you must jump right into it, [http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html).

---

