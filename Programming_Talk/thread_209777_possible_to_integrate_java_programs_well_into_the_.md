---
title: "possible to integrate java programs well into the gnome environment ?"
date: 2006-07-05
forum: Programming Talk
---

### Post by samir85 on 2006-07-05
Hey,

I've been programming java command line applicationsfor  a year now within my study course. I want to take the next step and start making programs with GUI.

However, I often hear complains from linux users that don't like java programs, because they don't fit so well into the gnome environment. So after all, is it possible to make java programs integrate nicely into the gnome environment ? I mean there's SWT and also I discovered gtkjava, what about that ?

---

### Post by Daverz on 2006-07-05
[http://java-gnome.sourceforge.net/cgi-bin/bin/view](http://java-gnome.sourceforge.net/cgi-bin/bin/view)
[http://gtk.org/bindings.html](http://gtk.org/bindings.html)

---

### Post by samir85 on 2006-07-05
[QUOTE=Daverz][http://java-gnome.sourceforge.net/cgi-bin/bin/view](http://java-gnome.sourceforge.net/cgi-bin/bin/view)
[http://gtk.org/bindings.html](http://gtk.org/bindings.html)[/QUOTE]

Im already aware of the java gtk bindings. However, can you tell me how it perfoms compared to SWT and Swing ?

Which GUI libs should I use after all ?

---

### Post by Daverz on 2006-07-05
I don't have any experience with java/gnome or java/swt (aside from playing with eclipse).  I've been pretty happy with the performance of Swing in Java 1.5 in a small database app I wrote, and the API is much better than either gtk or swt.

For java/gnome, I'd suggest trying some of the applications they link to on that page.   One of the major advantages that I can see is native compilation, though I have no idea how well that works in practice.

---

### Post by samir85 on 2006-07-05
Once, I heard that SWT is opensource, does that mean that Swing is closed-sourced ? If yes what does that im in practical experience ?

Also, I was being told that SWT perfoms better than Swing, can somebody eleborate that ?

---

### Post by Daverz on 2006-07-05
[QUOTE=samir85]Once, I heard that SWT is opensource, does that mean that Swing is closed-sourced ? If yes what does that im in practical experience ?
[/quote]

In practice it means you can compile SWT with gcj, but you can't do that with Swing.

> 
Also, I was being told that SWT perfoms better than Swing, can somebody eleborate that ?

Yeah, I've heard that, too, but it's never seemed like a hugely compelling difference to me.  And it seems to me that the SWT API is more geared to writing Eclipse plugins than writing general purpose apps.  In fact, the only SWT app I've ever heard of is Eclipse.

---

