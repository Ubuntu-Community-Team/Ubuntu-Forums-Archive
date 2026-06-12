---
title: "gnome programming api's: confused"
date: 2007-08-21
forum: Programming Talk
---

### Post by stijngysemans on 2007-08-21
Hello,

I'm having a background as a bachelor student in computer science and I'm very comfortable in writing webapplications (asp.net with sql server and java: jsf/jsp, hibernate with spring). I did some Gui development, most of them Swing.

Recently (actually, for more than a year) a switch to Ubuntu on my personal computer. To me, it's a new complex world that is fun to discover. But the terminology is new and the tools are different.

My favorite applications, f-spot and banshee are written in C# with a mono VM, i can't directly start hacking on those projects with monodevelop as IDE. No problem. But my other favorite applications (telepathy and empathy), tracker,  I know tracker is written in C but should be a way to communicate between tracker and F-spot, no? I thought this is why they used something like DBus?

I heared something about Vala, a language that compiles to gobject c, which is, as far as i understand it correctly a library that allows you to program against the object oriented paradigm in C?

A technical problem arises: with Java and .net, i never had to worry about memory management. Maybe something about that also?

Now i haven't talked about GTK (+), clutter, ...

I have some pretty awesome ideas that i want to accomplish but if somebody can help with all those languages and api's. There are a LOT of books on Java and the .net framework. On gnome, I'm a little left in the dark.

Thanks for any input!

---

### Post by AlexThomson_NZ on 2007-08-21
Here's a good tutorial on GTK programming with C

[http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)

Even if you decide to use another language than C, it is still a good introduction to and worth working through.  Look into Glade also for GUI design to speed up development greatly.

---

### Post by fct on 2007-08-22
GTK and gnome are programmed in C, but using a library (gobject) that implements object orientation in C. It has a high learning curve since C is not a language designed for OOP (things like inheritance are hard to use), but it works and is portable, not to mention it makes it possible to create bindings for many programming languages.

Also, the gnome libraries are being progressively deprecated and its functionality integrated directly into GTK+ or desktop-agnostic libraries usually hosted in [http://www.freedesktop.org](http://www.freedesktop.org) . So learning GTK+ and then reading documentation on other libraries should be enough.

These two books seem to have  agood reputation among gnome devs, and are the most recent:

The Official GNOME 2 Developer's Guide (2004)
Foundations of GTK+ Development (2007)

Vala is a C#-like language with a compiler that translates to gobjects in C (and the generated C code is surprisingly readable). The compiler also takes care of memory allocation, but you can do that manually too. It's still experimental, but works for many cases. Anyway it might be better to start with Mono if you're going that route and aren't interested in helping Vala development.

[http://live.gnome.org/Vala](http://live.gnome.org/Vala)

---

