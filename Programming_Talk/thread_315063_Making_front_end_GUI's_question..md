---
title: "Making front end GUI's question."
date: 2006-12-08
forum: Programming Talk
---

### Post by Kindred on 2006-12-08
This is probably a somewhat ridiculous question but as a total beginner programmer I was just wondering. 

Say i'm wanting to write a simple PyGTK app for switching theme/icons etc, the config options for which are stored in ~/.gtkrc-2.0 (as paths to gtkrc files etc)

Would you typically use methods of replacing strings and such in this config file directly when you select a different theme in the front end GUI and then calling whatever it is that actually switches the GTK theme, or would you need to be doing something at a lower level which simply modifies the config file as a result?

Hope that made sense, I'm just not sure how it all works or is typically done.  Any pointers are appreciated.

---

### Post by pmasiar on 2006-12-08
> **Kindred said:**
> This is probably a somewhat ridiculous question but as a total beginner programmer I was just wondering. 

For a total beginner, you started at a rather high spot. You may want check [PyGTK tutorials]("http://www.pygtk.org/tutorial.html") or ask experts in mailing list.

If your goal is to learn programming python  while doing something fun and visual, you may want to check [pygame ]("http://en.wikipedia.org/wiki/Pygame") - set of libraries to write games. Dozens games with source codes to learn from, and they have yearly competition. 

Even simpler would be learn programming by processing text files from commandline. Depends what you want to accomplish and what your aspirations are. Tell us more.

---

### Post by Kindred on 2006-12-08
Well I probably exaggerated total beginner just a little, i've been learning python for about 6 months but only through reading books through and going through examples and such.  I'm a few chapters into the large PyGTK manual now.  Yes my goal is to apply python to some GUI stuff and I figured a theme configuration thing would not be too tricky, and if it takes a while it's not a problem. I just wondered how GUIs and config files work together..

---

### Post by pmasiar on 2006-12-09
I have no idea what might be involved in a program for configure themes. But Ubuntu has one I believe (never used it myself), and most likely it is written in python, so find out and look it up.

I am programming for 20+ years now. Let me tell you that any non-trivial application has non-trivial design, and for you to make it right without much experience could be hard.

Instead of biting too much, or getting burned out on non-trivial problem, let me advise you something different: Find a (python-based) project which does 99% of what you want, and try to add your own feature. With any luck project has a workable design by someone experienced, you can ask questions and learn from real working code. Either theme manager, SPE editor or wiki (moinmoin or TRAC bug tracker) would be good start, and usefull to know for any python hacker.

---

