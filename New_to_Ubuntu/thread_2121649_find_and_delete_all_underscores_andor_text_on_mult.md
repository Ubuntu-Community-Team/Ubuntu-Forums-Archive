---
title: "find and delete all underscores and/or text on multiple files"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by Froylan on 2013-03-02
after looking multiple threads about renaming multiple files I messed up trying to leave only numbers on files, my result is this [ATTACH=CONFIG]239647[/ATTACH] I want to keep th first set of numbers


forget it

---

### Post by papibe on 2013-03-02
Hi Froylan.

Try this:
```
rename -nv 's/[^0-9]*([0-9]+)[^0-9].*/$1.mp4/' *
```
That is a verbose dry run. Try it and when you see that it does what you want, remove the 'n' on the options.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Froylan on 2013-03-02
it said it changed the files to the perspective numbers and the mp4 extencion but it did not apear in the folder I did the command on, and also didn't appear in the home folder since i searched for it there

---

### Post by papibe on 2013-03-02
Remove the dry run option: **[COLOR="#FF0000"]-n[/COLOR]**:
```
rename -v 's/[^0-9]*([0-9]+)[^0-9].*/$1.mp4/' *
```
Regards.

EDIT: "dry run" means show the output as if it were running the command, but it actually does nothing. That is, for test purposes.

---

### Post by Froylan on 2013-03-02
> **papibe said:**
> Remove the dry run option: **[COLOR=#FF0000]-n[/COLOR]**:
```
rename -v 's/[^0-9]*([0-9]+)[^0-9].*/$1.mp4/' *
```
Regards.

EDIT: "dry run" means show the output as if it were running the command, but it actually does nothing. That is, for test purposes.

thank you! sorry for being stupid; not understanding your command for if it does the trick, but it did what I want

---

