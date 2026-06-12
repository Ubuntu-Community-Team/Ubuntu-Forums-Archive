---
title: "Getting started with C++ in Ubuntu"
date: 2006-06-12
forum: Programming Talk
---

### Post by speedsix on 2006-06-12
Hi there,

I program mainly in Java but since switching to linux I want to help out with a few programs which are in C++ but would like a bit of advice on where to start.

Obviously in Java all your apis are bundled together as part of the runtime whereas in C I need to use all the various libraries from different places to draw windows, play sounds etc. C only includes very basic apis from reading from input etc. correct?

Firstly any good online tutorials that can get me started in C++ in linux, I need to know what all the different file types are .h .o .so etc and how your programs locate libraries etc.

Next question, how do I know which libraries I need to do basic things like create gnome forms etc.? And do these libraries have documentation online? 

Basically I'd like to write some basic gnome based windowed apps.

Many thanks

Dom

---

### Post by Engnome on 2006-06-12
[QUOTE=speedsix]
Basically I'd like to write some basic gnome based windowed apps.
Dom[/QUOTE]

I havent programmed c++ with GTK2 but I used a version of this guide [http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/) made for another language. It was very good.

If you want to do it graphically you can use glade (its in the repo's) to build the gui. ([http://glade.gnome.org/](http://glade.gnome.org/))  Then link your program and the XML file togehter using libglade. ([http://www.jamesh.id.au/software/libglade/](http://www.jamesh.id.au/software/libglade/))

It's a little tricky finding documentation and tutorials for this stuff (atleast for me (using perl)) . Prepare to spend some time with google finding those good tutorials that surely are out there.

---

### Post by elemental666 on 2006-06-14
I dunno about finding links to tutorials... I mean C/C++ can quickly get to the point where the avg online tutorial doesn't give you the explanation you need.  You have to ability to get very detailed with C/C++, way more so that with Java.  I acn recommend the [Deitel & Deitel book]("http://www.deitel.com/books/cpphtp5/") however.  It covers ANSII C/C++ and is used by a number of universities as their text book.  IT might be a little more expensive than the avg tech book, but its well worth the money.

---

### Post by rickardg on 2006-06-14
You could check out Bruce Eckels [Thinking in C++]("http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html") for an introduction to C++, it assumes you have some background in C (but there is an crash course in basic C included) and if you're already familiar with object orientation it might not be much new there for you, but it is still a pretty nice book (and it's availiable for free download).

---

### Post by xeero on 2006-06-15
Please don't blast me, gnome fans.. but you might want to check out Qt by Trolltech.  haven't used it personally, but i hear that it's clean, easy to use and is done in c++.  oh yeah, it's geared for KDE.  also, there are licensing issues if it's for commercial use.  

[http://www.trolltech.com/products/qt/features](http://www.trolltech.com/products/qt/features)

slightly off-topic: my personal favorite language is still java.  for me, i'd like to write stuff that isn't too native to specific environments if possible.  my main gripe is that the user needs a jvm, but most people seem to have it nowadays.  for java, check out JGoodies for nice cross-platform look and feel.

---

### Post by xeero on 2006-06-15
I forgot to mention that I was a KDE fan recently turned Gnome fan after installing Dapper Drake

---

### Post by raptros-v76 on 2006-06-15
for c++ you need the gnomemm package. (for some reason all the c++ bindings to these graphics libraries have mm at the end.)  let the project generator put together the makefiles and stuff for you. and there is a gtkmm reference doc and tutorial package.

---

