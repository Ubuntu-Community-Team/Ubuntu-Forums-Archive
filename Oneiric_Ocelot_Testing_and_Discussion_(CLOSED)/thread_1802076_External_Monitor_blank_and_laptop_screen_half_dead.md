---
title: "External Monitor blank and laptop screen half dead."
date: 2011-07-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2011-07-11
I just installed the 7/10 alternate image. As soon as i connect it to my dell external monitor it goes blank and laptop's top half go dead and unresponsive black.

I have installed experimental 3d drivers. I have a Thinkpad T420 4177-CTO with nvidia optimus. It should be using the integrated graphic card.

Thanks.

---

### Post by benjamimgois on 2011-07-11
This is currently a bug in the intel video drivers that isn't fixed for more than a year.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614238](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614238)
[https://bugs.freedesktop.org/show_bug.cgi?id=28306#c48](https://bugs.freedesktop.org/show_bug.cgi?id=28306#c48)


There's currently a patched version of 2.6.39rc7 that fix it, but the patch hasn't being merged to the upstream yet.
[http://people.canonical.com/~sforshee/lp614238/linux-2.6.39-020639rc7.201105192014~lp614238/]("http://people.canonical.com/%7Esforshee/lp614238/linux-2.6.39-020639rc7.201105192014%7Elp614238/")

---

### Post by donniezazen on 2011-07-11
> **benjamimgois said:**
> This is currently a bug in the intel video drivers that isn't fixed for more than a year.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614238](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614238)
[https://bugs.freedesktop.org/show_bug.cgi?id=28306#c48](https://bugs.freedesktop.org/show_bug.cgi?id=28306#c48)


There's currently a patched version of 2.6.39rc7 that fix it, but the patch hasn't being merged to the upstream yet.
[http://people.canonical.com/~sforshee/lp614238/linux-2.6.39-020639rc7.201105192014~lp614238/]("http://people.canonical.com/%7Esforshee/lp614238/linux-2.6.39-020639rc7.201105192014%7Elp614238/")


Dang! no more latest kernels...

Thanks anyways. I will get back to ya as soon as i apply your solution.

---

### Post by flanker on 2011-08-18
Sounds like your having the same issue as me (see end of post):
[https://bugs.launchpad.net/ubuntu/oneiric/+source/compiz/+bug/808677](https://bugs.launchpad.net/ubuntu/oneiric/+source/compiz/+bug/808677)

---

