---
title: "required packages for development env"
date: 2006-09-12
forum: Programming Talk
---

### Post by mtnbkr on 2006-09-12
I'd to seek advice on how to setup my laptop (thinkpad t42p running Dapper 2.6.15-26-686 kernel) for a proper development environment. Thanks.

---

### Post by skymt on 2006-09-12
It all depends on what language you use.

C, C++:
    You need to install build-essential to get the compiler and related tools and headers. Popular editors include Emacs, Vim, SciTE, gedit, and many others. I use Vim. If you prefer an IDE, use Anjuta for GNOME or KDevelop for KDE.

Java:
    Get the Sun Java developer tools (JDK, javac, etc). Eclipse is a nice Java IDE.

C#:
    You need mono and related tools. MonoDevelop is a nice IDE for C#.

Python:
    SPE is a good Python IDE. Combine it with wxGlade for RAD-style development.

---

### Post by mtnbkr on 2006-09-12
thanks for the info. it's mainly for C/C++ embedded development.

---

### Post by toojays on 2006-09-12
You will need to make sure that you can get your embedded toolchain running on Ubuntu. Many IDEs do not understand some of the things you may need to do for embedded work, so you will most likely need to write (or at least tweak) your own Makefiles.

Emacs is the most versatile development environment, and is what I use for most of my work. With Makefiles, M-x compile can be made to do pretty much anything you want.

---

