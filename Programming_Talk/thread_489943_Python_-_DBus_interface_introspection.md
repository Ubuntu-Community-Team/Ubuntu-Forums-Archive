---
title: "Python - DBus interface introspection?"
date: 2007-07-01
forum: Programming Talk
---

### Post by Seine on 2007-07-01
Hi there. 

I'm trying to debug the script on [this page]("http://awn.wetpaint.com/page/Listen+Plugin"). For me at least it is throwing DBus exceptions. The purpose of the script is to launch Listen, Just Listen (if not already present) and report current track info to the Avant Window Navigator.

For me, it succeeds in starting Listen, but does not find the method get_title on the Listen DBus interface. If I change the method to current_playing I can call it OK, but the get_title method does not exist. (Even though this method is [listed in the source]("http://www.listen-project.org/browser/trunk/src/dbus_manager.py#L145")).

Is there a way I can introspect any given DBus interface at runtime to see what methods actually do exist and which don't?

Cheers
Jem

---

### Post by Seine on 2007-07-02
I've just discovered [http://http://dbus.freedesktop.org/doc/dbus-tutorial.html#introspection]("http://http://dbus.freedesktop.org/doc/dbus-tutorial.html#introspection"). I hope it applies to the python bridge as well as direct. I will try it out when I get home tonight and post back. Any info in the meantime is appreciated!

---

### Post by ssam on 2007-07-02
is this the sort of thing you want

[http://www.vitavonni.de/projekte/dbus-inspector.html.en](http://www.vitavonni.de/projekte/dbus-inspector.html.en)

---

### Post by Seine on 2007-07-02
Yes, yes, yes!!! Thanks Sam. :popcorn:

---

