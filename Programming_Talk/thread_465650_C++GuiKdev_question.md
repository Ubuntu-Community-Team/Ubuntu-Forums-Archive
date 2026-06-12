---
title: "C++/Gui/Kdev question"
date: 2007-06-05
forum: Programming Talk
---

### Post by tmasboa on 2007-06-05
What is teh best way to start programming GUI (gtk?) applications in C++. Right now I am using Gnome but Kdevelop and (kate and g++)

---

### Post by PandaGoat on 2007-06-05
If you want to use C++ go with gtkmm or wxWidgets.

---

### Post by tmasboa on 2007-06-05
alright I think i'll try wxWidgets. It says it's cross platform, so can I make a program in *nix/ubuntu and compile it for windows?

---

### Post by josesanders on 2007-06-06
Is there an IDE that automates the GUI development like in Microsoft Visual Studio?  I've tried Anjuta with gtkmm, but I can't figure out how to get it to compile with the right options.  I end up getting frustrated with it and just going back to the command line.  Ideally I would like to just draw controls into the gui and link them to event handlers automatically, rather than reinventing the wheel, trying to figure out how to use each control manually.

---

### Post by PandaGoat on 2007-06-06
I do not use, so I might be off on some things.  Anjuta has the capabilities to use an xml file to generate a GUI.  You can create the xml file using Glade which incorporates into anjuta--Project->Edit GUI will open glade to edit the GUI. Glade can be used for Gtk+, gtkmm, a some others I believe.  If you want to use C#/mono get Monodevelop they have a design time interface.  Kdevelop has a QT gui designer.

If you want anjuta to work with gtkmm you have to add the linker tag -lgtkmm.

---

### Post by snoop on 2007-06-06
> **josesanders said:**
> Is there an IDE that automates the GUI development like in Microsoft Visual Studio?  I've tried Anjuta with gtkmm, but I can't figure out how to get it to compile with the right options.  I end up getting frustrated with it and just going back to the command line.  Ideally I would like to just draw controls into the gui and link them to event handlers automatically, rather than reinventing the wheel, trying to figure out how to use each control manually.

You can do that with glade (or QT designer). You can simply draw the controls onto an application and then it can be exported as an xml file which can be used to make the gui run.


edit: PandaGoat beat me to it.

---

