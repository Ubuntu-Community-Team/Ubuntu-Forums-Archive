---
title: "C++ with GUI for Ubuntu?"
date: 2007-05-31
forum: Programming Talk
---

### Post by Eric the Red on 2007-05-31
I'm wondering what you guys would use for creating GUI in C++?? With windows I would be using the win32 API. But since this is my first week using linux, I don't know the linux / Ubuntu  GUI library that you would use. 

Can anyone please point me in the right direction?

---

### Post by PandaGoat on 2007-05-31
You have many choices.  GTK+ is a good one, but it is more C. gtkmm is a C++ wrapper.  There is QT [ :( ], gnome [ :( ], kde [ :( ].  If you are lazy I suggest getting Monodevelop and using their designer and Gtk# or use glade.

---

### Post by Eric the Red on 2007-05-31
Well, I'm using Gnome.. Does that mean that the application I create in C++ for my environment won't work with someone else using KDE for instance?

Sorry, I'm confused. All I want to do is create a GUI application for C++... as opposed to a console application. I'm using a Gnome environment.

---

### Post by PandaGoat on 2007-05-31
Oh.  By gnome and by kde I mean you can use gnome's libraries and kde's libraries to create a gui.  If you use them they will only run if you have the correct environment.  I suggest using GTK+, gtkmm, or gtk#.  They will run on any environment.

If you want to strictly use C++, then use gtkmm. [http://www.gtkmm.org/]("http://www.gtkmm.org/")

Install the libraries:
```
sudo apt-get install libgtkmm-dev
```

Find where your IDE has its linker tags and add -lgtkmm.  If you are having trouble with this tell me what IDE you use and I'll help.

Start [here](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03.html).

---

### Post by Eric the Red on 2007-05-31
Thanks that cleared it up.

---

### Post by xtacocorex on 2007-05-31
> **PandaGoat said:**
> If you use them they will only run if you have the correct environment.
By this he means you need the libraries to run them.  It is very easy to run KDE apps in Gnome and vice-versa.

---

### Post by Eric the Red on 2007-06-01
I'm using Eclipse, and having problems getting a simple program to run. I'm guessing there's a problem with the linking stage or the build stage. But I can't say for sure.

---

### Post by loell on 2007-06-01
try wxwidgets if youre using c++, and you wont have to worry the desktop environment your program runs.

yeah, eclipse can be a pain, setting up the linker and such.

personally i like anjuta , it all sets it for you.

---

### Post by Eric the Red on 2007-06-01
I must keep Eclipse, sorry. Does anyone know how to do this in Eclipse with the c++ plugin?

---

