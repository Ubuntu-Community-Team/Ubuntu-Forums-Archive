---
title: "GTK / Aesthetics: Tightly grouping buttons, with single icons, nicely?"
date: 2007-10-26
forum: Programming Talk
---

### Post by Mr. Picklesworth on 2007-10-26
I am trying to implement this in a GNOME panel applet. [http://ubuntuforums.org/showthread.php?t=320315](http://ubuntuforums.org/showthread.php?t=320315)

It is going surprisingly well, pulling code from the existing window list applet.

My first snag is one I didn't expect: Aesthetics!
The mockup there looks great, in my opinion. The feel of the thing is quite similar to the existing window list, but with far more functionality. However, this isn't as easy in practice, because those multiple windows and hotspots are all grouped inside single buttons. Doesn't work well when the bottom button is reacting to clicks...

I don't want to change the visuals too much from the usual window list, and I like the way the items get decorated when drawn with buttons. However, it is bad, stupid and ugly to trick the button control into acting as merely a means of fooling the window decorator to make a container look nice.

Did a few mockups in Glade, and this is what I want to eventually achieve for each process in the list:
[IMG]http://img84.imageshack.us/img84/2454/screenshotmainpyoq9.png[/IMG]

There is a particular smoothness to having button-like containers for the processes there.
Here is the catch:
The icon, and each of those labels, is individually clickable. I do not want the button on the bottom (which I currently have) ever responding to those clicks.

Is there a way I can have something drawn that looks like a button (for example, the gradient and rounded frame we get with Human, but not with ugly arbitrary drawing functions), but which otherwise does not act like a button?

Alternatively, is there some kind of split button widget, where I can have individual widgets that each are either an end or a middle chunk of a button, so that when placed together they resemble a full button but act like individual ones? (Such that when one clicks on [www.google.com](www.google.com), for example, only that part of the button is depressed).

---

