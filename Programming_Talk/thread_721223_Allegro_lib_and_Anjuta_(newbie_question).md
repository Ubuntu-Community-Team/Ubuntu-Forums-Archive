---
title: "Allegro lib and Anjuta (newbie question)"
date: 2008-03-11
forum: Programming Talk
---

### Post by mordi05 on 2008-03-11
Hi.
I am trying to learn c++ for fun, and are currently trying to compile with the Allegro library. I am using the Anjuta 2.2.0 IDE.

I get a lot of undefined reference error when trying to compile an easy program with Allegro. I guess my problem is that I need to link to the library.

I read this in another thread:
"Start a regular console project in Anjuta and add `allegro-config --libs` (with the backticks) to
Settings->Compiler and linker options->Options->Linker flags"

However, my settings tab in Anjuta does not have the compiler and linker options. I only have "preferences" and "plugins". Can somebody please enlighten a compiling noob?

Thx in advance.

---

### Post by cdekter on 2008-03-11
Have you tried this:

Switch to the project view in the left pane of the IDE. Right click on the main build target of your project (usually the name of the executable it builds) and select properties. This should bring up a dialog where you can adjust linker/etc flags and compiler settings.

---

### Post by mordi05 on 2008-03-11
Thank, you I have now found it in the right-click menu. That was a great help, and solves my problem.

However I would still like to find out why I am missing several options from my settings tab. As I understand it I am missing quite some options.
Under setting I only have: preferences, shortcuts and plugins.

---

### Post by cdekter on 2008-03-12
It seems like there are quite a few bugs in Anjuta. It crashes rather a lot (at least for me) and there are a few inconsistencies around the GUI. I would probably put it down to that. The only other thing I can think of is if the type of project you have open has some bearing on the menu items that appear in the Settings menu...

---

