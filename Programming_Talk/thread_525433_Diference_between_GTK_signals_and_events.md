---
title: "Diference between GTK signals and events?"
date: 2007-08-14
forum: Programming Talk
---

### Post by cybrid on 2007-08-14
Well, that's the question; I've begun reading the GTK 2.0  tutorial and I'm confused about the difference between signals and events; from the explanation in the tutorial I only get that they're pretty much the same thing. Could someone more versed in GTK development explain it, please?.

Thanks in advance.

---

### Post by AlexThomson_NZ on 2007-08-14
From what I understand, signals are emitted from GtkObjects as a response to an action (eg. a button click).  Events are a continual stream of messages from gnome (eg. the gnome 'main loop').

---

### Post by cybrid on 2007-08-14
So . . . a signal is emmited whenever an event occurrs?

---

### Post by slavik on 2007-08-15
signals are sent, events occur.

some event happens, and a signal is sent.

thing of it this way, when someone calls you (an event), your phone rings (signaling the incoming phone call)

---

### Post by cybrid on 2007-08-15
Hey, thanks a lot, I think I understand it now :D

---

