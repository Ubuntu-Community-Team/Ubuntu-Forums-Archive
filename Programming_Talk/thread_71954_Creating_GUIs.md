---
title: "Creating GUIs"
date: 2005-10-04
forum: Programming Talk
---

### Post by gflores on 2005-10-04
I've always wondered, do developers always create it manually by typing in the code for all the checkboxes, menus, etc or do they use some sort of WYSIWYG editor? From what I read, a lot of developers do it by hand, which to me seems tedious and not advantageous.

---

### Post by brentoboy on 2005-10-04
As a professional windows developer (yeah, I admit it) I would have to say - both

I use VB for most gui stuff, C for some stuff. There are advantages everywhere.

I must admit though - glade (gnome's forms creator) is cooler than anything else I have ever used.  It even generates the C code for the form after you are done painting it - if you want, or you can use the form file in its non-code form from python scripts and things.

I actually prefer to build C code for windows stuff from scratch, but when you get paid to do it, development speed is more valuable than doing things the "best" way - so long as it does a good job accomplishing the need.

This seems true in lunux as well. most of the Ubuntu add ons to debain seem to be python scripts behind glade forms.  The aletrnative C code would take forever to write and maintain - even though some programmers would claim that if it isnt done the hard way, somehow it isnt actually software.  I guess the programmers who do things that way develop for the debian base, and gnome.

:)

---

### Post by 23meg on 2005-10-04
in linux they usually choose a widget set that has bindings to the language they're coding with. the two most popular widget sets are gtk (used by gnome) and qt (used by kde).

[glade]("http://glade.gnome.org/") is a very convenient gui builder for use with gtk. it saves gui setups in xml format, and by using libglade, applications can call up gtk+ widget interfaces designed with glade just by loading the xml.

---

### Post by brentoboy on 2005-10-04
at the bookstore yesterday I saw a book on wxWidgets, which is a widget layer that can allow the same gui to be compiled on top of gtk, qt, mac, windows, whatever. It looked pretty cool, but I didnt see a forms editor for it.  I guess right now its a "edit the code yourself" widget set, but it perked my interest.

Its like java without needing a virtual machine - write once, run anywhere - so long as you compile it for each target.

---

### Post by 23meg on 2005-10-04
yes, a friend of mine is using wxwidgets for a multiplatform project and it's really convenient for that purpose. by the way, trolltech, the developer of qt, also makes it available for mac and windows as well; for a price.

---

### Post by gflores on 2005-10-05
[QUOTE=brentoboy]
I use VB for most gui stuff, C for some stuff. There are advantages everywhere.
:)[/QUOTE]

Care to elaborate? I don't see the advantages. Does it mean better, cleaner code?

brentoboy: I did some googling and I found this. Some attempts to make a GUI designer using wxWidgets. For some reason, the glade one looks fugly.
[http://wxdsgn.sourceforge.net](http://wxdsgn.sourceforge.net)
[http://wxglade.sourceforge.net/index.php#screenshots](http://wxglade.sourceforge.net/index.php#screenshots)

Does Glade/GTK2/wxWidgets/QT have a lot of documentation to make it easy for a beginner? I've created a couple of simple programs using Visual C++ with the help of MSDN, which was very useful.

---

### Post by brentoboy on 2005-10-05
[QUOTE=gflores]
Does Glade/GTK2/wxWidgets/QT have a lot of documentation to make it easy for a beginner? [/QUOTE]

I saw a book at the bookstore 
[http://www.amazon.com/gp/product/0131473816/002-5802310-5484831?v=glance&n=283155&n=507846&s=books&v=glance](http://www.amazon.com/gp/product/0131473816/002-5802310-5484831?v=glance&n=283155&n=507846&s=books&v=glance)

the Bruce Perens Open Source series is really good stuff, they cover lots of in depth topics that are all the sorts of things you would want a consolidated hard copy manual for.  Its a good thing I brought my wife with me to the bookstore, I would have spent next weeks paycheck on the samba guide, and some of their other titles.

Anyway, I dont know enough about wxWidgets to help, I just remember being thouroughly impressed as I browsed the book.

sorry.

---

### Post by dcraven on 2005-10-05
There are several tutorials online for gtk, depending on your language preferences. For example the offical pygtk tutorial is available [here](http://pygtk.org/pygtk2tutorial/index.html) and is very current and  thorough. I'd suggest working through a couple of sections of that to get the hang of it.

Cheers,
~djc

---

### Post by wmcbrine on 2005-10-05
I just started using Glade, and I love it! Really powerful and easy. I didn't quite know what to do when I first started it up, but after one brief tutorial, I was building new apps left and right.

I was kinda upset to read that they're dropping code generation in the next version. Apparently we're all supposed to switch to using libglade, but that seems like more work to me.

I should probably be using wxGlade, because I really want to make cross-platform apps. But I've put off trying it, mainly because Audacity (a wxWidgets app) looks so poor on my system. I don't know if it's typical, but it's the only wxApp I know I've tried. (It's not the app itself I fault, or the way it's laid out, just the way it's rendered here. The menu fonts don't match the native Gtk apps, various elements are misaligned, and the help dialog is very messed up.)

---

### Post by brentoboy on 2005-10-06
[QUOTE=wmcbrine]
I should probably be using wxGlade, because I really want to make cross-platform apps. But I've put off trying it, mainly because Audacity (a wxWidgets app) looks so poor on my system. I don't know if it's typical, but it's the only wxApp I know I've tried. (It's not the app itself I fault, or the way it's laid out, just the way it's rendered here. The menu fonts don't match the native Gtk apps, various elements are misaligned, and the help dialog is very messed up.)[/QUOTE]

when you compile an wxWidget app, you compile it to one of the target platforms.  It might have been compiled to work on the boring X libs instead of the gtk libs, so it could have a wider target audience with one binary.

One of the features of wxWidgets that I thought was coolest was that it will use the native widgets for the target platform you compile it for.

so, to sum up, I dont think that is normal expected behavior.

---

### Post by wmcbrine on 2005-10-06
Nope, it's definitely wxGtk, judging by the output of "ldd `which audacity`". It just doesn't look like it. :-/

---

### Post by macewan on 2005-10-06
[quote=dcraven]There are several tutorials online for gtk, depending on your language preferences. For example the offical pygtk tutorial is available [here]("http://pygtk.org/pygtk2tutorial/index.html") and is very current and  thorough. I'd suggest working through a couple of sections of that to get the hang of it.

Cheers,
~djc[/quote]

thanks for that link

---

