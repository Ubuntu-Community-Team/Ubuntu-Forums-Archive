---
title: "gcc question"
date: 2008-09-27
forum: Programming Talk
---

### Post by sandbird on 2008-09-27
If I want to install either a cross-compiling gcc version, or some specific gcc version then how do I make it to work with my current gcc version?

I mean, is it possible to have more then one gcc working on the same system?

---

### Post by yotam on 2008-09-27
> **sandbird said:**
> If I want to install either a cross-compiling gcc version, or some specific gcc version then how do I make it to work with my current gcc version?

I mean, is it possible to have more then one gcc working on the same system?

Yes, but when you build the alternative version, specify
[FONT="Fixedsys"]--prefix=[/FONT]*AltGccPath*
upon **configure** step.
If *AltGccPath* is under your home directory, you can and should
do the installation without becoming *root*.

---

