---
title: "Serious bug in QT4?"
date: 2009-01-03
forum: Programming Talk
---

### Post by cdekter on 2009-01-03
OK maybe it's not that serious for most purposes, but in my case... fatal. I am one of the developers on a program called AutoKey ([http://sourceforge.net/projects/autokey](http://sourceforge.net/projects/autokey)). It is basically a utility designed to save typing by automatically inserting text in response to abbreviations, hotkeys etc. To do this, it monitors keyboard events via the X server's record extensions, and sends them via the X server's XTest extension.

It is in the nature of this program that the generated keyboard events are sent much more rapidly than a human user would normally generate by typing. It works perfectly in GTK apps, both under GNOME and KDE. However, with QT apps, (e.g. Kate, Konqueror), the events don't appear to be received synchronously. That is, the text that my application sends via the X server come out garbled. 

The only workaround I've found so far is to slow down the sending of events from my application, and also flushing the server after each event. Unfortunately, this makes sending the text very slow. 

Since this issue seems to be limited to QT-based apps, I'm hypothesising that its some sort of problem with how QT is receiving keyboard events from the X server. However, I have no idea where to start with posting a bug etc... any advice would be greatly appreciated.

---

### Post by dribeas on 2009-01-04
You should probably post this in Trolltech forums. I doubt you will get help in such a particular issue in this forum.

---

