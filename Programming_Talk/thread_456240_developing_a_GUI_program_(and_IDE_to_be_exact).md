---
title: "developing a GUI program (and IDE to be exact)"
date: 2007-05-27
forum: Programming Talk
---

### Post by rbprogrammer on 2007-05-27
whenever i use an IDE, there are always way too many features i think that over complicate the program.  and there are always features missing that i think would be a nice touch to the program.  and then, if there is something that i want to do with a feature, i have to figure out how to do it.  so i decided that i want to develop my own IDE.  a very basic one.  i'm not looking to make it the next best thing, i just want it for myself.  and since i have some extra time to spare, i'll make it now.  i'm just going to make an extremely basic IDE, or an advanced text editor, depending on how you look at it.

i've decided to make it using C/C++ since those are my most favorite languages.  the only thing is that i am not too good with GUI programming.  so i am wondering how i should go about doing that part.

some features that i would put in are syntax highlighting, some way of developing a project (ie with multiple files), and a run/execute button.

the only feature that i see a problem with is the syntax highlighting.  i'm not familiar with GUI programming so i dont know what to use.  QT3, QT4, wxWidgets, GTK+, etc...

**i guess my question is what should i use to do the GUI?**

---

### Post by ankursethi on 2007-05-27
If you want to use C, go with GTK+. For C++, use Qt. These two are the most widely used toolkits.

---

### Post by kknd on 2007-05-27
> **rbprogrammer said:**
> 

...

**i guess my question is what should i use to do the GUI?**


My advice:

GUI "toolkit": **wxWidget**s + **Scintilla**("code editing widget") (wxWidgets now have a wrapper to it), for portability and because its good too =).

For code-completion / tag navigation you could use ctags / icomplete! With icomplete the code completion for C++ becomes more easy to do!

---

### Post by rbprogrammer on 2007-06-02
> **ankursethi said:**
> If you want to use C, go with GTK+. For C++, use Qt. These two are the most widely used toolkits.

now i was lokoing on the wxWidgets website and it said:
> ...wxWidgets gives you: online help, network programming, streams, clipboard and drag and drop, multithreading, image loading and saving in a variety of popular formats, database support, **HTML viewing and printing**, and much much more.

[http://www.wxwidgets.org/about/](http://www.wxwidgets.org/about/)


would GTK+ or Qt have the ability to display html files as well?

---

### Post by engla on 2007-06-02
gtksourceview is a gtk object that is essentially a text editor view with syntax highlighting for you, it is what gedit uses and it is quite simple to use.

For gtk you can also display html with gtkhtml, but it is rudimentary in some ways (it is made to display html, not be a web browser for you)

---

### Post by ankursethi on 2007-06-03
I think simple HTML can be displayed with gtkhtml. Even Qt has something similar. But I don't think these would support JavaScript or even CSS. You might want to do a Google search.

---

### Post by loell on 2007-06-03
use mozembed for gtk html rendering.

---

### Post by Mr. Picklesworth on 2007-06-19
Whatever you do, do not choose your UI library based on what language you are using!

There are C++ bindings for GTK (gtkmm), and in the regular C bindings cooperate just fine anyhow. (Just a gentle return to procedural code).

Also kind of unrelated (this won't hurt you)... the licensing is as much an issue as the native language. A significant problem with QT is its multiple licenses. I won't say I'm very knowledgeable about QT's licensing, but from what I've gathered, the library is GPLed and has a bunch of pay versions with one version (the GPLed one) for only free / OSS software. For most people this is fine, but in my opinion: What maniacal desktop environment natively uses a GUI library that blocks out commercial developers? Sure, commercial / non-free software will still be developed for it, but if the developers are interested in saving money (very possible!), it will be built with a different library that does not blend in. That is detrimental to the environment as a whole.
GTK, on the other hand, is under Lesser GPL, which is the version of GPL that protects one's work but does not bother any software that links to (uses) it. This means that commercial developers or people who aren't using the GPL license can still use GTK. This makes it an ideal native user interface since it means there is a better chance of everybody supporting it.
I do accept that Trolltech themselves need money, etc. to continue development of their (definitely excellent) library, and that's cool. It is also true that, for everyone building free software, this does not hurt. I also accept that, from what I've done in KDE, I have not seen any out of place programs. Regardless of the license, it seems to do pretty well.


Err, wow, sorry.


What desktop environment do you like? If this IDE is going to be for you, the native UI for that environment is probably the best choice!
For example, if you like Gnome, go for GTK (my favourite, by the way, if you haven't noticed my blatant bias). If you like KDE, go with QT. That platform's native UI is the best way to go since it ensures the fastest loading and cleanest integration of your program!
If you are still having trouble, try the popular UI editors for each library. GTK has Glade, Qt has something whose name I forget, as does wxWidgets.
wxWidgets is a good way to get the native UI everywhere, although it is also really big. If you want easy, widespread support, it is a nice choice.

---

