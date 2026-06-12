---
title: "Windows programmer wants to convert"
date: 2006-09-14
forum: Programming Talk
---

### Post by wombat20 on 2006-09-14
I'm a professional software engineer with experience of Pascal, C++, C# and Ada, but all on Windows.

So I have no idea about how I compile, build and eventually make packages in Linux (and particularly Ubuntu).

Can anyone recommend me a good book or resource that would point me in the right direction?

---

### Post by Jussi Kukkonen on 2006-09-14
Debian packaging (which is what Ubuntu packaging in practice is) is an artform in itself. You can achieve very nice results with the tools, but be prepared learn a lot before that happens...

Book recommendations are probably quite development environment/language/framework -specific...

A very handy resource (regardless of language and dev. environment) is the Debian New Maintainers' Guide: ([http://www.us.debian.org/doc/devel-manuals#maint-guide)](http://www.us.debian.org/doc/devel-manuals#maint-guide)), and other documents on the same page.

---

### Post by toojays on 2006-09-14
Most Free Software written in C or C++ is built using GNU Make. I suggest you read the first few chapters of the [GNU Make Manual](http://www.gnu.org/software/make/manual/html_node/index.html#Top), you will learn quite a lot.

If you want to make graphical applications for Ubuntu, check out the [GTK Tutorial](http://www.gtk.org/tutorial/).

As Jussi has already mentioned, the Debian New Maintainer's Guide explains how to make packages for Ubuntu.

---

### Post by yota on 2006-09-14
Welcome!

One main difference between windows development and linux development is that in windows usually everything is integrated in the IDE (editor, modeler, compiler, linker and debugger), so chosen the IDE, all comes as consequence. On linux, even if some things are ubiquitous, at opposite you are more free to combine different tools as you want.
First of all you have to see one by one the main tools (and the main libraries, cause there's not only one Linux API as WinAPI), and see what are best suited for your needs.

To give some directions, most (but not all) development on linux involves gcc (GNU compiler collection).
At [http://www.gnu.org/software/gcc/](http://www.gnu.org/software/gcc/) you can find a documentation section, wiki and faq.
If you are interested in Java instead, Netbeans and Eclipse are available and are pretty much like windows versions.

IMHO I would suggest to start from the very basics (and from command line) to understand how the "engines" work (mostly 'gcc' and 'make' commands) and only after choose a  more modern environment like one of many IDEs available.

---

### Post by X.Cyclop on 2006-09-14
Type this:
```
sudo apt-get install manpages-dev gcc-4.0-doc gnome-dev-doc
```

;)

But, do you know something about *nix-GNU/Linux?:confused:

---

### Post by moephan on 2006-09-14
I would choose what programming language and framework you want to use based on the type of program(s) that you are planning to write. For GUI data bound apps, I think using the Python language with pyGtk UI framework will be most intuitive and productive for someone coming from a windows application developement background. Plus, Python is fun.

Here are some links I copied from another thread:

Dive into Python to get you rolling:
[http://diveintopython.org/](http://diveintopython.org/)

Python tutorial:
[http://docs.python.org/tut/tut.html](http://docs.python.org/tut/tut.html)

The Python language reference:
[http://docs.python.org/ref/ref.html](http://docs.python.org/ref/ref.html)

The Python class library:
[http://docs.python.org/lib/lib.html](http://docs.python.org/lib/lib.html)

the pyGtk tutorial:
[http://www.moeraki.com/pygtkreference/pygtk2tutorial/](http://www.moeraki.com/pygtkreference/pygtk2tutorial/)

You might also want to link to the Gtk class library documentation. Unfortunately, it is all written in C, so a lot of the code is different then what you will write using the Python bindings:
[http://developer.gnome.org/doc/API/2.0/gtk/index.html](http://developer.gnome.org/doc/API/2.0/gtk/index.html)


Cheers, Rick

---

