---
title: "Programming incorporating outside programs?"
date: 2006-08-26
forum: Programming Talk
---

### Post by tht00 on 2006-08-26
Ok.  I'm kinda curious about this -- how does one invoke another program on the system?  It's quite easy to do within a script, but can this be done from within, say, a C program?

I'm less curious about this, but what about building GUIs on top of console apps?

---

### Post by neilp85 on 2006-08-26
It's possible to do within C programs. Have look at the documentation for execl and fork. Those are the only two I've ever used.

---

### Post by peabody on 2006-08-27
> **tht00 said:**
> 
I'm less curious about this, but what about building GUIs on top of console apps?

This is done all the time in Unix, in fact, it's probably the most common form of GUI, wrapping command line programs into nice guis.

---

### Post by tht00 on 2006-08-27
> **peabody said:**
> This is done all the time in Unix, in fact, it's probably the most common form of GUI, wrapping command line programs into nice guis.

Yeah, I was curious more on the *how* it's done -- I about having console apps first with GUIs built later (ie, K3B and GnomeBaker are likely the same backend/terminal program with a different GUI (gnome/qt) and different configurable options.)

execl and fork look more of what I'm interested in right now.  Thanks!

---

