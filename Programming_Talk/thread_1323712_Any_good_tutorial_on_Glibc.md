---
title: "Any good tutorial on Glibc?"
date: 2009-11-11
forum: Programming Talk
---

### Post by froggyswamp on 2009-11-11
Folks I'm learning Glibc, I'm interested into linked lists, hash tables, arrays etc. Googled and found a tutorial from IBM (attached) but it's from 2005 and I'm afraid it's too old, is it? If so, is there any more recent/better tutorial on Glibc?
I'm using C as the prog lang.

---

### Post by samjh on 2009-11-12
Glibc doesn't have linked lists, tables, etc.  It's just an implementation of the ISO standard C library.

What you should be referring to is GLib, which does have linked lists and other high-level data structures and functions.

I'm not sure if there are any comprehensive tutorials on the subject.  But take a look at the official reference manual [here]("http://library.gnome.org/devel/glib/2.20/").  The [GTK+ tutorial]("http://library.gnome.org/devel/gtk-tutorial/stable/") has a small section on GLib, which seems easy enough to follow.

---

### Post by froggyswamp on 2009-11-12
Yep, I indeed mean Glib, thanks! The reference manual (your referring to) is the api with the usual explanation typical for api docs, the tutorial from IBM seems better to me as a place to start learning Glib, though the code is a bit old and needs subtle changes to get it to compile.

---

