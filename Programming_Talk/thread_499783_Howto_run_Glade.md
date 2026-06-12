---
title: "Howto run Glade?"
date: 2007-07-13
forum: Programming Talk
---

### Post by zoobave on 2007-07-13
Hi,
After adding all the widgets in Glade-3, How can i run the application? And I need more docs to learn glade from scratch. 

regards
Zoobave
[http://zoobave.blogspot.com](http://zoobave.blogspot.com)

---

### Post by harun on 2007-07-13
For what programming language? C++?

---

### Post by zoobave on 2007-07-13
'C' language

regards
Zoobave
[http://zoobave.blogspot.com](http://zoobave.blogspot.com)

---

### Post by harun on 2007-07-13
I use it with C++ so I am used to it being a little different but a little googling got me this:

[http://www.jamesh.id.au/software/libglade/](http://www.jamesh.id.au/software/libglade/)

Which is a nice simple example to get started. Save your glade file (*.glade) to the directory you want to write your C code. Then refer to it like that example shows.

When compiling remember you will have to link in the libglade dev libraries using `pkg-config blah blah blah`. Need any help with that let us know.

---

### Post by gotthardt on 2007-08-01
Here is a Makefile that worked for me:


all: project1


project1: main.c project1.glade
[INDENT]gcc main.c -o progname `pkg-config --cflags --libs gtk+-2.0` `pkg-config --cflags --libs libglade-2.0`[/INDENT]

---

### Post by PandaGoat on 2007-08-01
To clarify, glade is a library that makes GUI's easier.  The glade application for creating GUI's creates an xml file [.glade] file that your code[generated for you as well] uses to create the GUI. 

I'm only familiar with Anjuta and glade. Anjuta has a plugin to open Glade and edit the GUI  All you must do is build it.  If you are not using Anjuta, I would suggest you do for simplicity.

If you want to write it all out yourself, it would be easier to just use GTK, gtkmm, or some other API.

---

