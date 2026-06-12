---
title: "Ruby backend but a pure frontend?"
date: 2007-12-16
forum: Programming Talk
---

### Post by EnvoyRising on 2007-12-16
I want to make a Gnome panel applet, and was looking for a way to do it in Ruby. The PanelApplet is depreciated in ruby-gnome2, so this can't be done using GTK bindings as far as I know (without using some legacy code).  As such, I was wondering, is would be possible to write the backend for my applet in Ruby, but use straight GTK for the frontend. If so, could someone point me to some tutorials or examples outlining scripting languages being used as a backend to GTK application?

For the record anything python or QT related is not an option.

---

### Post by Quikee on 2007-12-16
> **EnvoyRising said:**
> I want to make a Gnome panel applet, and was looking for a way to do it in Ruby. The PanelApplet is depreciated in ruby-gnome2, so this can't be done using GTK bindings as far as I know (without using some legacy code)...

What about libpanel-applet2-ruby? This one should not be deprecated.

---

### Post by EnvoyRising on 2007-12-16
It's the one the ruby-gnome2 maintainer was talking about deprecating, I believe. I can't find ANY documentation on it. Thanks though. i got excited for a second, lol.

---

### Post by Quikee on 2007-12-18
> **EnvoyRising said:**
> It's the one the ruby-gnome2 maintainer was talking about deprecating, I believe. I can't find ANY documentation on it. Thanks though. i got excited for a second, lol.

I see now what you mean. On the page it states: 
> Ruby/PanelApplet? (deprecated)
panel applets library for the GNOME panel. Deprecated. Use Gtk::StatusIcon in Ruby/GTK instead. 

Notification area is not the same as gnome panels applets.. I don't see the logic behind his thinking on deprecating the PanelApplet library.

---

### Post by EnvoyRising on 2007-12-19
> **Quikee said:**
> I see now what you mean. On the page it states: 


Notification area is not the same as gnome panels applets.. I don't see the logic behind his thinking on deprecating the PanelApplet library.

Neither do I, therein my dilemma, lol. Damn you python for being more mature!

---

### Post by EnvoyRising on 2007-12-20
it seems I can do this by creating a C interface.

Now I just have to learn C :-|. Thats ok, it shouldn't; be that bad, considering I know C++.

---

### Post by Nekiruhs on 2007-12-20
> **EnvoyRising said:**
> it seems I can do this by creating a C interface.

Now I just have to learn C :-|. Thats ok, it shouldn't; be that bad, considering I know C++.
You sort of know C then. Just unlearn C++'s OOP stuff and stick with the basics and you should be OK with C.

---

