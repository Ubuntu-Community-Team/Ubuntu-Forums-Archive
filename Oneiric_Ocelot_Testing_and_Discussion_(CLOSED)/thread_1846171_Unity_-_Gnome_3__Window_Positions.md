---
title: "Unity - Gnome 3  Window Positions"
date: 2011-09-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by makitso on 2011-09-18
I am testing both the 11.10 Unity and Gnome 3 shells on the beta.  One item I noticed is that most all apps open windows on Unity positioned left top of the screen.  Whereas, with G3 the same apps open center on the screen.  Is this configurable on Unity or should I just wait till someone fixes it?

Rob

---

### Post by pelle.k on 2011-09-18
Compiz can be configured to place windows in several modes, centered windows being one possible mode (i assume that's what you're after). Some windows save and restore their last position though, and some windows even open up completely centered (app specific), which you can force-override in compiz, should you want to.
The plugin to look at in compizconfig-settings-manager is the "Place" plugin.

---

### Post by makitso on 2011-09-18
However, both G3 and Unity have the same Compiz / Place Windows parameters.  Yet, using Terminal as an example, that app opens center on G3 and top left on Unity.  This same difference is noted on several other apps I use.  Any idea why?

---

### Post by pelle.k on 2011-09-18
> However, both G3 and Unity have the same Compiz / Place Windows parameters
No, AFAIK, the window manager in gnome-shell, called "mutter", places window in a cascading mode. This is not configurable (unless they've added some option to the development version of gnome 3.1), and means new windows are placed just ~20 pixels lower+right of the top-left corner of the previous window (visible or not visible). The effect is sort of when you place a deck of cards on a table and just move the deck, leaving a trail of cards obscuring most of the card behind it.

In unity, the window manager is called "compiz". It has several modes of placing windows, with the default in ubuntu being the "smart" method. It starts by placing a window in the top left corner, and from there, it tries to place new windows as far from that window as possible, trying to use up as much free screen space as possible. Some applications like nautilus though, start where you last closed that window, overriding the "smart" placement of compiz window manager.
You may configure compiz to use "cascading" layout, as well as "centered", "new windows under mouse pointer" and other modes of placing windows as well.

---

### Post by makitso on 2011-09-20
pelle.k, thanks for the explanation.  Cascade did solve the problem!:)

---

### Post by pelle.k on 2011-09-20
np! Good to hear :)

---

