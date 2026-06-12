---
title: "desktop launcher puzzle"
date: 2006-12-02
forum: Programming Talk
---

### Post by kornelix on 2006-12-02
Here is a simple script I want to invoke from a desktop launcher:
```
sudo -b /path-to-executable
exit
```If I invoke this script interactively, it works as desired: the executable is launched and bash exits, leaving the executable running.

I cannot find any way to make the same thing work from a desktop launcher. A window appears and disappears in milliseconds.

I have tried combinations of "application" and "application in terminal" with the above command: sudo ...   and with:  bash -c "sudo ..."

What is the magic formula?

---

### Post by Ramses de Norre on 2006-12-02
Try replacing sudo by gksudo and leave out the exit line.
(And check for the -b option, might be different with gksudo, man gksudo will tell)

---

### Post by kornelix on 2006-12-02
> **Ramses de Norre said:**
> Try replacing sudo by gksudo and leave out the exit line.
(And check for the -b option, might be different with gksudo, man gksudo will tell)

Works, with no -b.  Many thanks.

---

