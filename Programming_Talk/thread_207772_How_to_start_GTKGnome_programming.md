---
title: "How to start GTK/Gnome programming?"
date: 2006-07-02
forum: Programming Talk
---

### Post by el3ktro on 2006-07-02
Hello,
I'm currently diving into C++ programming, and I've read a lot of books, followed many tutorials etc. but all for plain C++. I now want to start programming with GTK/Gnome, but I'm just wondering what I all need for this. I suppose I need some gtk-dev packages? I've already installed Anjuta, but was surprised that it doesn install any dependencies needed to actually be able to compile a program.

How would you start? What do I need to install to get everything working? Any good GTK/Glade tutorials on the web?

Thanks a lot,
Tom

---

### Post by psychicdragon on 2006-07-02
Installing these packages should give you everything you need to get started:
libgtk2.0-dev, libglade2-dev, libgtkmm-2.4-dev

If you're planning on coding in C++, you'll want to use gtkmm which is the C++ bindings for GTK+. Gtkmm is quite well documented, there's a full api reference and good tutorial on the [Gtkmm Documentation]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/") page.

---

### Post by el3ktro on 2006-07-02
Thanks very much, this will surely help me a lot. What exactly are the differences between using pure gtk and gtkmm (besides that the first is C and the latter is C++ ;-) )? Is gtkmm somewhat limite? Which one is more encouraged or which one would you recommend for me to use?

Tom

---

### Post by Daverz on 2006-07-02
You might want to check out the gideon GUI builder.  It seems to be much further along than glade, though since I haven't used it for anything, I can't really judge its stability:

[http://gideon.sourceforge.net/cgi-bin/wiki](http://gideon.sourceforge.net/cgi-bin/wiki)

---

### Post by Max Luebbe on 2006-07-02
Doing GTK/Gnome work in C++ could get awkward.

Both are C libraries that operate on the assumption that you need to do massive workarounds inside the language to trick structs into being objects via gobject.

If you know C++, C shouldn't be a stretch.
You'll probably save yourself a lot of headaches this way.

If you're a book fan, I'm a fan of the Gnome2 Programming book by No Starch Press

---

### Post by el3ktro on 2006-07-02
Yes I've read about that. Of course C isn't object oriented, but the Gnome/GTK APIs do some tricks to give the programmer a object-oriented interface, although the language usesd is not object-oriented? Hmm. I was playing around with Qt for a while, and I really liked it, very clean & straight-forward. But unfortunately I've switched to Gnome, and I'd like to program for "my" DE ;-) But in other words, you'd recommend me to do GTK programming in pure plain C?

Tom

---

### Post by Max Luebbe on 2006-07-03
Depends what your ultimate goal is and how you'd like to get there.

If you know C++ well, I'd go the C route, because thats how the librarys were written, and it might be the easiest way.

If you're looking to get GUIs on the screen with minimal effort, and aren't afraid to try a new language: try using Python with pygtk.

Python is a very friendly language, and an experienced programmer could probably do some pretty competant stuff in under a week with modest effort.

If you liked C++ and Qt, why not just go that route?
Figure out what your end goals are, do you really want to learn GTK? Or do you just want to take the plunge from developing console apps, and move up to making GUIs, regardless of toolkit?

---

### Post by el3ktro on 2006-07-03
[QUOTE=Max Luebbe]Depends what your ultimate goal is and how you'd like to get there.

If you know C++ well, I'd go the C route, because thats how the librarys were written, and it might be the easiest way.

If you're looking to get GUIs on the screen with minimal effort, and aren't afraid to try a new language: try using Python with pygtk.

Python is a very friendly language, and an experienced programmer could probably do some pretty competant stuff in under a week with modest effort.

If you liked C++ and Qt, why not just go that route?
Figure out what your end goals are, do you really want to learn GTK? Or do you just want to take the plunge from developing console apps, and move up to making GUIs, regardless of toolkit?[/QUOTE]

Tough decisions to make. Well I have always been playing around with Java and/or C/C++, I'm not sure if I'm very fond of learning a new language, especially because C/C++ seems to be the most widely accepted language. Well, I kind of just want to "take the plunge" and learn GUI programming. Did that in Java a little, and I liked it, but I definitely want to go with C/C++. I like Qt, it's somewhat similar to Java, but as I said I'm a Gnome user, and I would prefer programming for "my" desktop environment.

Well, tough decisions, I'll have to think about it ... ;-)

Tom

---

### Post by Daverz on 2006-07-04
I don't know why Max thinks gtkmm would be more awkward than straight C-gtk.  I think it's the other way around.  At the very least, gtkmm does not require all the obnoxious casting that C-gtk does.  The best thing is that if you want to derive a custom widget in gtkmm, you don't have to learn all the intracacies of the gobject system.  But this is all explained clearly on the gtkmm homepage:

[http://www.gtkmm.org/](http://www.gtkmm.org/)

I'd certainly go for gtkmm before C-gtk if I needed native compilation.  Even though my knowledge of C is much more secure than my knowledge of ideomatic C++, I think the advantages would pay off pretty quickly.

---

