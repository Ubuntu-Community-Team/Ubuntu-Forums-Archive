---
title: "Best C/CPP IDE ? Way to GUI Programming With C/CPP..."
date: 2011-02-21
forum: Programming Talk
---

### Post by etdsbastar on 2011-02-21
Hello there...

I am currently using Geany as my C/CPP needs. There are many IDEs out there and I found Geany as the best. 

Anyways, there are many GUI packages created using C or C++. I had tried many source codes like for GAMBAS, Brasero etc. etc. they are all made with 'C'. But, I couldn't find any GUI interfaces with them.

Is there anyone who can tell me how to start building a proper GUI package with C or CPP and Where to start it, i mean the strategy ???

---

### Post by johnl on 2011-02-21
There are a myriad of libraries available for building graphical interfaces in C/C++: GTK+ (used by gnome), Qt (used by KDE), wxWidgets, and plenty of others.

Here are some links to get you started:
[list]
[*][gtkmm (C++)](http://library.gnome.org/devel/gtkmm-tutorial/unstable/index.html)
[*][gtk (C)](http://library.gnome.org/devel/gtk-tutorial/unstable/)
[*][Qt (C++)](http://doc.trolltech.com/4.7-snapshot/gettingstarted.html)
[*][wxWidgets (C++)](http://www.wxwidgets.org/docs/tutorials.htm)
[/list]

Qt comes with a graphical designer called **qtcreator**; with GTK+ and GTKmm you can design your gui with a program called **glade** and load it from your program.

---

### Post by fct on 2011-02-22
Plus Code::Blocks for wxwidgets and anjuta+glade for Gtk+.

---

### Post by foxmuldr on 2011-02-23
> **etdsbastar said:**
> I am currently using Geany as my C/CPP needs. There are many IDEs out there and I found Geany as the best.

Is there anyone who can tell me how to start building a proper GUI package with C or CPP and Where to start it, i mean the strategy ???

The CodeLite IDE has built-in Qt support. Plus, Qt by itself comes with a lot of supporting apps for form builder, code generators, etc.

- Rick C. Hodgin

---

### Post by teddfox on 2011-02-23
> **etdsbastar said:**
> Hello there...

I am currently using Geany as my C/CPP needs. There are many IDEs out there and I found Geany as the best. 

Anyways, there are many GUI packages created using C or C++. I had tried many source codes like for GAMBAS, Brasero etc. etc. they are all made with 'C'. But, I couldn't find any GUI interfaces with them.

Is there anyone who can tell me how to start building a proper GUI package with C or CPP and Where to start it, i mean the strategy ???

I downloaded Geany and I must say, pretty cool.  If you are Programmer in college using something like gcc+(on windows) as an editor, this will fit right in with you.

I quickly did a Hello World to play with it and it does a great job for a simple IDE.  Compiled, build, run, etc in one app.  

Not bad.  I think I will stick with this one for a while for C/C++.  Eclipse will always be for Java / Android for me though. 

Have you used it for Perl or Python?

---

### Post by etdsbastar on 2011-02-23
> **teddfox said:**
> I downloaded Geany and I must say, pretty cool.  If you are Programmer in college using something like gcc+(on windows) as an editor, this will fit right in with you.

I quickly did a Hello World to play with it and it does a great job for a simple IDE.  Compiled, build, run, etc in one app.  

Not bad.  I think I will stick with this one for a while for C/C++.  Eclipse will always be for Java / Android for me though. 

Have you used it for Perl or Python?

No Dear,

I haven't used it for Perl or Python. And I am not a college student, I am a professional programmer. Anyways, presently I am using Code::Blocks for my C/CPP needs... 

I found CB is the best for C/CPP with complete features. Its GUI with QT is stunningly great...

---

### Post by Jacks0n on 2011-02-23
Try [Qt Creator]("http://qt.nokia.com/products/developer-tools/") with Qt! I think Qt's a fantastic library, and Qt Creator compliments it very well - they work in together.

---

### Post by etdsbastar on 2011-02-24
> **Jacks0n said:**
> Try [Qt Creator]("http://qt.nokia.com/products/developer-tools/") with Qt! I think Qt's a fantastic library, and Qt Creator compliments it very well - they work in together.

QT is great, i know and using it dear... Thanks for your suggestion, i really appreciated it.

---

