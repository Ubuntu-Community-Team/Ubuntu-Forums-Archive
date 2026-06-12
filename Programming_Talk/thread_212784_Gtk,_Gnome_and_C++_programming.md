---
title: "Gtk, Gnome and C++ programming"
date: 2006-07-10
forum: Programming Talk
---

### Post by kike_coello on 2006-07-10
hey guys, i have a question. does anybody know which software i should download to start writing gui c++ code for gnome? i have some ideas on some applications i would like to write, but i've only coded terminal programs, you know, that only work on the command line. i would like to have a graphical program. and please don't suggest java, i know how to program in java with gui, but i would like to learn more about c++ and c++ gui in gnome. 

also if anybody does have experience programming gnome apps in c++, can you tell me how you got started and which books you found useful? i just have no idea on how to begin, and i only have the rest of the summer cause i'll be very busy this fall.

thanks.

---

### Post by Athropos on 2006-07-10
You may use [Glade](http://glade.gnome.org/) to design your GUI with GTK (it's in the repos). You should easily be able to find good tutorials about Glade and C++.

---

### Post by kike_coello on 2006-07-10
> **Athropos said:**
> You may use [Glade](http://glade.gnome.org/) to design your GUI with GTK (it's in the repos). You should easily be able to find good tutorials about Glade and C++.

i knew somebody would say glade, but the thing is i have no clue on how to work it, is there a book or something where i could get started? i'm looking for tutorials but they aren't very helpful.

if you would like to IM me on messenger, i'm "kike_coello@hotmail.com"

thanks.

---

### Post by Athropos on 2006-07-10
I only use it for my Python apps: Glade generates XML files describing the GUI, and I just have to load them with the python/glade API. I never used Glade with C++, but I believe this should work the same way...

---

### Post by kike_coello on 2006-07-10
> **Athropos said:**
> I only use it for my Python apps: Glade generates XML files describing the GUI, and I just have to load them with the python/glade API. I never used Glade with C++, but I believe this should work the same way...

thanks dude, i'm about to download glade and see where i can find books or something to get me started on the classes and methods. thanks dude

---

### Post by nagilum on 2006-07-10
Glade is a nice tool, but without understanding the underlying widget toolkit you will probably not get very far. Therefore I suggest you try to learn GTK (or GTKMM for C++) at first, or at least have a thourough look at it. Glade has two "operating modes" (as already mentioned), it can either directly produce source code (only C-code IIRC) or save the GUI in a XML file. In your C++ you load the XML file and create event handlers for mouse clicks etc. Either way, you definitely need to know GTK to do this.
As for documentation, there's a tutorial on the GTKMM homepage, which also has a brief section on Glade: [http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html)
For a Glade introduction look here: [http://www.writelinux.com/glade/](http://www.writelinux.com/glade/)

---

### Post by kike_coello on 2006-07-13
thanks dudes, i'll check out that website with the tutorial , but i was kinda hoping somebody could recommend a book or something that i could actually take with me and read and scan real quick, this is the way i am used to learning how to program (c++, java, visual basic and shell). to me a tutorial doesn't really cover everything you need to know about a language or a library in this case.

thanks again.

---

### Post by nagilum on 2006-07-14
Sorry, but I don't know any books about GTK. Of course the tutorial is only a starting point where you "get a feeling" of how the thing works. Once you figured it out the API reference (which you can find on the GTK[MM] homepage) is the next thing to look for. It contains literally everthing about GTK, all widgets, functions, structures (or classes) and the like.

---

### Post by jbmnuke on 2006-07-14
Here are some links that I have found useful in trying to learn gui programming on Ubuntu/Gnome:

Online Book:
[http://developer.gnome.org/doc/GGAD/]("http://developer.gnome.org/doc/GGAD/")

Tutorials:
[http://developer.gnome.org/doc/tutorials/]("http://developer.gnome.org/doc/tutorials/")

Hope this helps.

---

### Post by yanxizhen on 2006-07-15
i use [codeblocks]("http://www.codeblocks.org/")

---

