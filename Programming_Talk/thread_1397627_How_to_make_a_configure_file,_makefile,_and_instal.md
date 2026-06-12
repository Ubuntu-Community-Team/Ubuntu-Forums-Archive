---
title: "How to make a configure file, makefile, and install file for a project"
date: 2010-02-03
forum: Programming Talk
---

### Post by Bheklilr on 2010-02-03
I'm a self-taught programmer, and for the last 6 months (approximately) I've been coding small projects; but I've always wondered how to actually make a source package that could be distributed and compiled on any machine.

For example, I've recently written a program that has 4 source files, an icon file, and a Glade XML file.  The project was written in Haskell using Gtk.  Two non-standard libraries, Graphics.UI.Gtk and Graphics.UI.Glade [(here)]("http://www.haskell.org/gtk2hs"), and the [ghc]("http://www.haskell.org/ghc") Haskell compiler are required for compilation.

My real question is, how do I write a makefile, configure file, and install file and include the necessary libraries and dependencies so that I can distribute it as a standalone program?

Thanks!

---

### Post by Linteg on 2010-02-03
I am guessing you want to learn how to use autotools for your project, if so I'd recommend this guide: [http://fsmsh.com/2753](http://fsmsh.com/2753)

---

### Post by Bheklilr on 2010-02-03
Linteg

I will certainly give it a look.  Thanks!

---

### Post by coyotle on 2010-02-03
try cmake, it very simple

---

