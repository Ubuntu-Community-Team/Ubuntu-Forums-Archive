---
title: "GTK license"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by nickos on 2011-09-15
A question regarding the GTK toolkit:

what i did read at wikipedia:

" It is licensed under the terms of the [GNU LGPL]("http://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License"), allowing both [free]("http://en.wikipedia.org/wiki/Free_software") and [proprietary]("http://en.wikipedia.org/wiki/Proprietary_software") software to use it"

so does that mean that i can still use it if my software is not free but sold?what about QT?

---

### Post by snip3r8 on 2011-09-15
Yes you may sell software that uses an LGPL base

---

### Post by dniMretsaM on 2011-09-15
Yes. Te LGPL doesn't exclude you from selling your software ( nor does the GPL or most other free or open source licenses). So feel free to charge for your software.

---

### Post by sanderd17 on 2011-09-15
As said above, if you only use software as a library, it's only seen as "using" the software. So you can charge for your own software since it's not a derived work, but it's a project that uses another project.

Otherwise, everything that would run on top of the Linux kernel would have to be open-source.

[s]If you do certain hacks on the GTK library, you do need to make those hacks open source, since that's changing an open-source project.[/s] [I]Sorry, not for LGPL projects.
[/I]
BTW, you can also sell open source programs. Like OsmAnd does here: [https://market.android.com/details?id=net.osmand.plus](https://market.android.com/details?id=net.osmand.plus) .

---

### Post by nickos on 2011-09-15
> **dniMretsaM said:**
> Yes. Te LGPL doesn't exclude you from selling your software ( nor does the GPL or most other free or open source licenses). So feel free to charge for your software.

so will the program have to be open source or can it also be private?

---

### Post by sanderd17 on 2011-09-15
> **nickos said:**
> so will the program have to be open source or can it also be private?

It can be proprietary.

---

### Post by dniMretsaM on 2011-09-15
> **nickos said:**
> so will the program have to be open source or can it also be private?
It doesn't have to open source. It can be proprietary if you so desire (although proprietary=bad in my opinion). If it were under the GPL, it would have to be open source.

> **sanderd17 said:**
> Otherwise, everything that would run on top of the Linux kernel would have to be open-source.

There are other GUI development libraries, so no it wouldn't. Only everything that used GTK.

---

### Post by sanderd17 on 2011-09-16
> **dniMretsaM said:**
> 



There are other GUI development libraries, so no it wouldn't. Only everything that used GTK.

Every program uses kernel libraries, and the kernel is licensed under GPL ...

---

