---
title: "Which program should I use to edit and compile C++?"
date: 2006-07-16
forum: Programming Talk
---

### Post by s_h_a_d_o_w_s on 2006-07-16
I've tried writing the source code in gedit, then using g++ to comoile. It's great, but a little too time-consuming. I need like one program, i've tried kdevelop, but it won't compile, maybe I screwed up there. Anyway, maybe, is there a compiler that will spit out my source into a .deb, or .exe (For my MS machine)?

---

### Post by Jagot on 2006-07-16
Anjuta or Eclipse?

---

### Post by chichilalescu on 2006-07-17
I see you want only one program that can do it all.
Personally, I recommend you use Kate for editing, as it's able to work with multiple files, and it has a terminal you can use (I actually open a different terminal, as I like to use mc and like the feel of a console).
The way I work around writing makefiles and stuff like that is with qmake: I just dump all files of a project in a folder, structured in any way, and then qmake writes the makefile (that can obviously be edited later), after wich all compiling and linking is made by typing 'make'; so it's almost like a single program that does everything.

---

### Post by tzulberti on 2006-07-17
I used the night build of codeblocks ([www.codeblocks.org](www.codeblocks.org)) and it works fine for me. I you are using KDE, you might like to tri kdevelop.

---

### Post by thumper on 2006-07-18
Personally, I use emacs and the command line with makefiles.

Edit in emacs, then M-x, compile (which I have bound to F7).  Can middle click on errors to jump to them.  All built in :-)

---

