---
title: "Qt4: reserve screen space / prevent overlapping"
date: 2011-05-08
forum: Programming Talk
---

### Post by jesuisbenjamin on 2011-05-08
Hello there,

I posted this question on several forums already, without much success so far. I am going to try my luck here anyway.

I am trying to find out how to prevent window overlapping or reserve space for a window using Qt4. The idea is to be able to make a desktop panel/dock application, much like gnome-panel or docky, cairo-dock. I have found [how to do this with Gtk on StackOverflow]("http://stackoverflow.com/questions/3859045/preventing-window-overlap-in-gtk")

I suppose the idea is to tell X Window the application needs reserved space. Window properties, [as described in in the freedesktop standards]("http://standards.freedesktop.org/wm-spec/wm-spec-latest.html#id2552069"), should be set with _NET_NW_STRUT / _NET_NW_STRUT_PARTIAL. I have found no way yet to do that with Qt. QtWindowFlags offer the possibility to set some window properties by not STRUT :(

Is there anyone here with an idea? NB: i am using Python for my app, but that shouldn't make much difference.

Cheers.
Benjamin

---

### Post by jesuisbenjamin on 2011-05-19
Hi there,

I get no luck on the entire internet with my question :(
Is there any generic way to address window overlap on X window systems?
Can i get Compiz to reserve space for an application?

Thanks.
Benjamin

---

### Post by loell on 2011-05-19
hello, this is a Kwin related issue and has probably nothing to do with Qt4 per se.

---

### Post by jesuisbenjamin on 2011-05-20
> **loell said:**
> hello, this is a Kwin related issue and has probably nothing to do with Qt4 per se.

Could you elaborate please? 
Isn't Kwin KDE specific? How about Gnome DE then? or any other Unix DE?

---

### Post by krazyd on 2011-05-20
This has nothing to do with gtk/qt *per se*; it is about sending hints to the wm (if it is ewmh compliant).

I would look at python-xlib, or a project like pekwm:
[http://pekwm.org/projects/pekwm](http://pekwm.org/projects/pekwm)

Why not try their mailing list? If anyone knows about this stuff, it would be those guys.

---

### Post by jesuisbenjamin on 2011-05-20
> **krazyd said:**
> This has nothing to do with gtk/qt *per se*; it is about sending hints to the wm (if it is ewmh compliant).
That's indeed what i reckoned as well.

> **krazyd said:**
> 
I would look at python-xlib, or a project like pekwm:
[http://pekwm.org/projects/pekwm](http://pekwm.org/projects/pekwm)

Why not try their mailing list? If anyone knows about this stuff, it would be those guys.

You mean the Pekwm mainlinglist?
Is there no X wm team?

---

### Post by krazyd on 2011-05-20
> **jesuisbenjamin said:**
> Is there no X wm team?

There is, but I don't know if they maintain python bindings (I don't think they do). There's no harm in asking either way :-)

---

