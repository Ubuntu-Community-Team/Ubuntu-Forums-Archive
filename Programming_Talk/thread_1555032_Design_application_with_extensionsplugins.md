---
title: "Design application with extensions/plugins?"
date: 2010-08-17
forum: Programming Talk
---

### Post by NoBugs! on 2010-08-17
When designing a C/C#/Pygtk application, how can you add the ability to make plugins for the application? I haven't found documentation on how to add plugins ability similar to Rhythmbox, Gedit, and other programs.

---

### Post by nvteighen on 2010-08-17
> **NoBugs! said:**
> When designing a C/C#/Pygtk application, how can you add the ability to make plugins for the application? I haven't found documentation on how to add plugins ability similar to Rhythmbox, Gedit, and other programs.

It usually involves creating a shared library or module that is written accordingly to some interface the program knows about. The idea is roughly this: you, for example, define that the plugin's entry point should be a function called "plugin_main" (as in any C program is called "main"). So, the program will load the library at runtime and attempt calling plugin_main. What happens next is up to the plugin, but there are ways to control what and how it does what.

Another possibility involves embedding a language interpreter so that you're C program is able to read Python scripts as plugins.

---

### Post by splicerr on 2010-08-17
The Gedit plugin engine has been moved to its own library so you may want to consider using that.
 
[http://live.gnome.org/Libpeas](http://live.gnome.org/Libpeas)

---

