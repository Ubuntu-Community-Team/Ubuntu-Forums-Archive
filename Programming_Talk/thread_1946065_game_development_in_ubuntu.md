---
title: "game development in ubuntu"
date: 2012-03-24
forum: Programming Talk
---

### Post by chuchi on 2012-03-24
p { margin-bottom: 0.21cm; }  Hi all!! I am planning to develop a network game for Ubuntu and I would like to ask you a couple of questions...
 

 I am going to use gtk in C language for using sockets, Do you recommend me to use other language/technology??
 

 Once I have finished the application, What are the steps to convert the application in a package for ubuntu?? So that an user could type “apt-get install mygame” to install the application on his/her computer??
 

 Thank you very much!!!!

---

### Post by MG&amp;TL on 2012-03-24
Gtk is an interface, there are appropiate libraries for sockets....but anyway. Depends on what sort of game you intend to do.

Well, I recommend you use SDL for your game, it's a really good, simple library with a good API reference.

If you're doing a game, C is a very bad idea. Use C++ or similiar.

Ubuntu is derived from Debian, as I'm sure you're aware. Make a debian package, conforming to their policy manual, and see if they'll take it. After a while, Ubuntu will sync packages from debian, and Ubuntu will have your package.

---

### Post by satsujinka on 2012-03-24
There's nothing wrong with C in itself. However, C++ has better documentation, thus you're sort of forced to use it.

---

### Post by MG&amp;TL on 2012-03-24
> **satsujinka said:**
> There's nothing wrong with C in itself. However, C++ has better documentation, thus you're sort of forced to use it.

If you're making a game, you tend to have a lot of objects. Try doing this in C. :P

---

### Post by chuchi on 2012-03-24
Thank you all very much!!!
Well..... Maybe C++ is more suitable for this project. In my opinion, C can be used for OOP, as it is used in the Linux Kernel, with lots of structures like trees, stacks, lists........

Until now, I have always developed under a supervisor, this is my first time developing on my own.... and thus I can make some stupid questions... so thank you very much for your patience!!!!

Kind Regards!!

---

### Post by Simian Man on 2012-03-24
> **chuchi said:**
> Once I have finished the application, What are the steps to convert the application in a package for ubuntu?? So that an user could type “apt-get install mygame” to install the application on his/her computer??
Usually "upstream" developers only distribute source code that people on all systems can use.  These source packages are normally trivial to convert into packages.  This is normally done by distribution packagers.  That way you don't have to build and maintain packages for all different distros which is a pain.

> **MG&TL said:**
> Well, I recommend you use SDL for your game, it's a really good, simple library with a good API reference.
+1.  SDL is a great library.  There is also an SDL_net add-on library that provides a socket interface that works the same across all platforms.  Using something like that will make your life easier.  It is written in C and can be used natively from C or C++.  There are also bindings for many other languages.

> **satsujinka said:**
> There's nothing wrong with C in itself. However, C++ has better documentation, thus you're sort of forced to use it.
That's not true, both languages have adequate documentation.  There are many reasons not to use C, but that's not one of them.

Regarding C vs. C++, I don't think being able to use objects directly is the main benefit of C++ over C.  You can do object-oriented programming easily enough in C.  SDL itself presents an object-oriented interface in C for example.  The biggest benefit of C++ is templates and the standard template library.  These really reduce the amount of crap you have to build from scratch yourself.

Knowing what kind of game you want to make will also help us give you better recommendations.

---

### Post by trent.josephsen on 2012-03-24
C defense reporting for duty.

There's nothing wrong with using C for game programming.  Especially if you want to use Gtk.  It just means you'll be using some different techniques than if you had chosen C++.  If you're familiar with C already, or have some other languages under your belt and just feel like learning C, go for it.

HOWEVER, if you're not very familiar with C, and you are not already an experienced programmer, I do NOT recommend using C and would advise you to be very careful with C++ as well.  Both languages have a lot of pitfalls for the inexperienced and suffer from a lot of poorly researched and/or out-of-date documentation (on various websites and in print).  Whatever you choose, be sure to use a learning resource that's recommended by people who actually use the language in real life.

Edit: Lest I appear to be in disagreement with the esteemed Simian Man, let me clarify that by "documentation" I'm referring to online guides, tutorials, "Learn X in 72 hours" type books, and of course the notorious "C: the Complete Reference".  Not all of them are bad, but there are a lot of bad ones, simply because there are a lot of crappy programmers who use these languages and think they know enough to write a book about it.

---

### Post by chuchi on 2012-03-29
I have been surfing the net. If I want to develop in C++, I should use GTKMM, not GTK, so..... which one do you recommend me? GTKMM or GTK???

Thank you very much!!

---

