---
title: "Is there any GTK+  IDE?"
date: 2009-03-13
forum: Programming Talk
---

### Post by ivikas on 2009-03-13
Hello all,

          I am  plannig to learn the GUI Application development using GTK 2.0 Toolkit.I am a beginner to this and i want to know if there is any IDE for The GTK+ Toolkit and if so how to install it.That the IDE should be like we should drag and drop to create windows,buttons etc... so we can focus on the functionality rather than on coding windows ,buttons etc..

Which is the best programming language for doing GUI Application development on Linux.

Thanks

---

### Post by cabalas on 2009-03-13
Have a look at [Anjuta]("http://anjuta.sourceforge.net/") which you can install using apt

Also try checking this sticky [http://ubuntuforums.org/showthread.php?t=1006662](http://ubuntuforums.org/showthread.php?t=1006662)

---

### Post by cb951303 on 2009-03-13
there is also glade3 which let's you design GUIs in GTK and exports them to xml files. you can then fire up your IDE of choice and use these xml files to create your application. you can use, C/C++, Python, Perl even PHP for GTK programming. Python seems to be a popular choice.

anjuta is better if you need an all-in-one solution though.

another choice is monodevelop. it's a very polished IDE with a GTK# gui designer. You'd have to write you applications in C# though (not that there is something worng with it, C# is my new favorite)

---

### Post by mmix on 2009-03-13
I would suggest to learn vala with gedit.

[http://www.valaide.org/doku.php](http://www.valaide.org/doku.php) : vala

[https://launchpad.net/valable](https://launchpad.net/valable) : Eclipse

[http://code.google.com/p/vtg/](http://code.google.com/p/vtg/) : Gedit

[http://abderrahim.arablug.org/blog/](http://abderrahim.arablug.org/blog/) : anjuta

---

### Post by jimi_hendrix on 2009-03-13
code::blocks has a feature for it if i recall

---

### Post by listener on 2009-03-13
I am currently working with pygtk in Python, and find it works well.  I am not using a GUI designer right now, but hope to work with Glade sometime.  I think that learning some of the basics by building them 'manually' is a good idea, for me anyway.

The DevHelp package has all the documentation resources for Gnome, GTK, PyGtk, etc.  It is invaluable.  There are some very good online tutorials for Glade and GTK as well.

---

### Post by SKLP on 2009-03-14
MonoDevelop is probably your best bet.

---

### Post by rich1939 on 2009-03-15
> **jimi_hendrix said:**
> code::blocks has a feature for it if i recall

I've used CODE::BLOCKS with GTK+ and GLADE quite a bit. It works very well for me. You can specify a "pre-build" step that automatically converts GLADE 3's XML file to GTK+'s GBuilder format. They all play very well together.

---

### Post by ivikas on 2009-03-25
Thanks you all guys for sharing your knowledge and wonderfull response.

---

### Post by slavik on 2009-03-25
glade in repo can now  save to gtkbuilder xml

---

