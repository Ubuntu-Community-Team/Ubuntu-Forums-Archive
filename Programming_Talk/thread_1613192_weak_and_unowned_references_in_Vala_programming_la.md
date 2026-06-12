---
title: "weak and unowned references in Vala programming language"
date: 2010-11-04
forum: Programming Talk
---

### Post by opengl_cpp on 2010-11-04
Hi guys, I'm wondering what are the real differences between weak and unowned references. Do they have their distinct usage, and is there any performance penalty if we prefer just one of them in all situation.

If there is a sensible thing to consider about, can anyone give me an example of their usage.

Since I started using Vala, I found this aspect one of the worst documented feature of Vala. 

Thanx in advance.
bye

---

### Post by johnl on 2010-11-04
Hi,

Not sure if you have seen [this page](http://live.gnome.org/Vala/ReferenceHandling), it seems to explain it pretty well.

What I got was:

* there is currently no difference between a 'weak' ref and an 'unowned' ref.
* you should use a 'weak' ref for breaking cyclical references (eg node X references node Y, node Y references node X, so even if both go out of scope they will not be freed)
* you should use 'unowned' references when you need multiple references to a non-gobject based classes that are not reference counted.  This is because there can be only one 'master' reference to a non-gobject object.

---

