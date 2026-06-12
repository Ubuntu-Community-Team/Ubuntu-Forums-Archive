---
title: "[SOLVED] CLI - run apps"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by adamogardner on 2008-06-28
ok so how do I open firefox or a game  or anything in a menu for that matter.

---

### Post by wolfen69 on 2008-06-28
```
firefox
```
just type the name

---

### Post by adamogardner on 2008-06-28
oh  well there you go!  thanks

---

### Post by ChameleonDave on 2008-06-28
Yes, you just type the name.

Sometimes it is not exactly the name you will see in the app though.  For example, *Mozilla Firefox* becomes "**firefox**"; the *Compiz Fusion* icon becomes "**fusion-icon**"; *Image Magick* becomes "**display**"; "*Image Viewer*" or "*Eye of GNOME*" becomes "**eog**".

---

### Post by adamogardner on 2008-06-28
wel that complicates things a bit.  is there a way to learn these monikers or get suggestions from the terminal?

---

### Post by ChameleonDave on 2008-06-28
> **adamogardner said:**
> wel that complicates things a bit.  is there a way to learn these monikers or get suggestions from the terminal?

Type the first few letters of the name in lower case, and then press Tab for autocompletion.  If that fails, try initialisms such as "eog".

---

### Post by cariboo on 2008-06-28
Most user application are located in /usr/bin if your not sure what you're looking you can always have a look there.

Warning: on my system the last time I looked there where over 1500 programs listed.

Jim

---

### Post by ChameleonDave on 2008-06-28
If all else fails, open Synaptic, find the relevant package, and look at the list of "Installed Files" for it.  The ones marked as being installed at */usr/bin* are the executable files that you call from the command line.

---

