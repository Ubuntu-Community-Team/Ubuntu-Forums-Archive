---
title: "python + sound"
date: 2007-02-16
forum: Programming Talk
---

### Post by Choad on 2007-02-16
im thinking of writing a drum loop sequencing program in python, mostly for my own use but if its any good i could gpl and publish it somewhere

whats the best way to go for sound in python? is alsa or oss the prefered sound driver? any tips at all are welcome

---

### Post by ssam on 2007-02-16
gstreamer is very popular these days. you might find some useful code for examples at [http://jokosher.org](http://jokosher.org) .

it is also being ported to windows and mac os x, so your code would be portable. [http://blogs.gnome.org/view/uraeus/2007/02/16/0](http://blogs.gnome.org/view/uraeus/2007/02/16/0)

---

### Post by Choad on 2007-02-16
aha! gstreamer! that sounds about right. anything to keep things integrated. thanks for the link too. is that going to be in u-studio?

---

### Post by ssam on 2007-02-16
> **Choad said:**
> is that going to be in u-studio?

should be. it is already in feisty, and the jokosher devs are making a big effort to get a new stable version (0.9 or 1.0) into feisty before the freeze.

---

