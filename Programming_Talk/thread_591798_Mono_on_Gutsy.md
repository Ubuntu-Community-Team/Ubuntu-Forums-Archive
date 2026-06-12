---
title: "Mono on Gutsy?"
date: 2007-10-25
forum: Programming Talk
---

### Post by jsight on 2007-10-25
I tried the official distribution agnostic installer, but it doesn't seem to work (even when requesting text mode).  It just exits immediately with no errors.

Unfortunately mono and the tools with it are woefully out of date in gutsy.

Has anyone had success getting a current mono dev stack up and running in gutsy?

---

### Post by ankursethi on 2007-10-26
Is there nothing at GetDeb.net?

---

### Post by jsight on 2007-10-26
> **ankursethi said:**
> Is there nothing at GetDeb.net?

Searching for mono didn't yield any promising results.  :(

---

### Post by jsight on 2007-10-29
I found this for up to date mono builds:
deb [http://www.viraptor.info/repo](http://www.viraptor.info/repo) feisty-custombackports contrib

Unfortunately, that only has the core mono stuff (no up to date monodevelop).  It does seem to work nicely, though, and fixed up a few asp.net issues for me.  :)

---

