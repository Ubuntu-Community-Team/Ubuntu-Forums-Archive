---
title: "Create a application menu entry at install"
date: 2008-04-05
forum: Programming Talk
---

### Post by Sh4wn on 2008-04-05
Hi guys,

I'm creating a C++ Program using GTKmm and libglademm, with anjuta as my IDE.

The program itself is almost finished, but I want that when someone installs my program using make install, an entry to the Gnome app menu will be added.

I couldn't find anything useful on the internet, does anybody know here what's the best way?

---

### Post by stroyan on 2008-04-05
The specification for adding menu items is at
[http://standards.freedesktop.org/menu-spec/menu-spec-latest.html](http://standards.freedesktop.org/menu-spec/menu-spec-latest.html)

---

### Post by CptPicard on 2008-04-05
And do not hook that up into make install. That should be reserved only for compilation and copying of files into proper places. What you want to do should be performed by distribution package manager-specific installation scripts.

---

### Post by Sh4wn on 2008-04-06
> **CptPicard said:**
> And do not hook that up into make install. That should be reserved only for compilation and copying of files into proper places. What you want to do should be performed by distribution package manager-specific installation scripts.

Hmm, most programs do create an entry with make install, or am I wrong?

---

