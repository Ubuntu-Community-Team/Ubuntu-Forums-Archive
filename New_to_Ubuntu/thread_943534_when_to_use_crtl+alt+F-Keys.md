---
title: "when to use crtl+alt+F-Keys"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Mzwo on 2008-10-10
hi all,

what exactly happens when using the crtl-alt-f-keys combos? 
i know it opens terminals - how do i get back to my desktop? 
could anybody tell me what the differetn combos f1 - f12 do?

thanks
Mzwo

---

### Post by AndyCooll on 2008-10-10
CTRL+ALT+F7 is the one for your desktop.

These are virtual terminals and you login to them the same way that you would normally login to Ubuntu. In effect they are the commandline version of Ubuntu. They work similar to the terminal you may (or may not) have used in Accessories > Terminal

They originally come from the time when Unix was commandline only, and provide users with multiple (commandline) screens. So you could login to F1 (for instance) and set a task running, and then login to F2 and continue working on a completely different task etc 

:cool:

---

### Post by Nepherte on 2008-10-10
ctrl+alt+F1 through F6 are virtual terminals. To switch back ctrl+alt+F7.

---

### Post by Mzwo on 2008-10-10
thanks!

what do f8 - 12 do?

Mzwo

---

### Post by jrothwell97 on 2008-10-10
They're more virtual terminals, but they don't have a shell running in them by default. If you, say, switch user from the graphical environment, the X server will be started in vt8, vt9, and so on.

---

