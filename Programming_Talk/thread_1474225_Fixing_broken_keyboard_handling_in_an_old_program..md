---
title: "Fixing broken keyboard handling in an old program."
date: 2010-05-05
forum: Programming Talk
---

### Post by jwbrase on 2010-05-05
I've been messing around with a PDP-8 emulator lately, and while it generally runs well, it was written in the 90's for some unspecified flavor of Unix, and I've been having trouble getting it to accept keypresses (The interface is mouse driven enough that I can live without the keyboard, especially given that if I launch it in a terminal window, it will accept input from the terminal, but it would be convenient to be able to use the keyboard directly).

The emulator can be downloaded here: 

[ftp://ftp.cs.uiowa.edu/pub/jones/pdp8/emulator.txt.Z](ftp://ftp.cs.uiowa.edu/pub/jones/pdp8/emulator.txt.Z)

The guy uploaded as a compressed *.txt file, but it functions as a shell script that cats its contents into the various source files. I have no idea why he did it that way...

In any case, I believe the relevant file is kc8e.c. I've tried putting in statements to print a message to the console in all the keypress handling functions in that file, and none of them ever seem to trigger in the compiled program. (It's also irritatingly difficult to get the window in focus).

Since it was written over a decade ago for a different (if related) OS, I figure some compatibility issue in how the mid-90's Unix and late-2000's versions of X handle keyboard input, but I'm not familiar enough with X keyboard handling to know exactly what I might need to change.

Can anybody hazard a guess as to what might be broken here?

---

### Post by jwbrase on 2010-05-10
OK. I've figured something out: If I start a TWM session instead of a Gnome session, the keyboard handling works fine. Problem is that TWM is a pain in the butt to use (and ugly too)...

I also had a look at the source, and noticed it uses Xt. I looked that up on Wikipedia and saw that Xt normally has a widget toolkit running on top of it, which this program seems not to use.

So my question now is "How is Gnome/Gtk/whatever interfering with the keyboard handling of this program?" Actually, having looked at it more I think it may be a focus problem than a keyboard handling problem, since it's difficult to bring the window into focus under Gnome. It's possible that even when it's being decorated like a focused Window that it doesn't really have focus. But then, I don't know enough about these things to be sure and may be talking through my hat, which is why I'm asking for advice here.

---

### Post by jwbrase on 2010-05-17
Well, I happened to discover that TVM was overkill. The program works perfectly when I turn off Compiz.

So now I think it's a problem with focusing in Compiz, perhaps combined with old code in the program.

It would still be nice if I could find some hints on what kind of old code can create problems with Compiz, but it's no longer quite so critical.

---

