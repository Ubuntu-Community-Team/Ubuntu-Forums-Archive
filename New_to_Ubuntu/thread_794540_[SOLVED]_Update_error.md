---
title: "[SOLVED] Update error"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by hufferd on 2008-05-14
I don't think I had anything to do with this but I was running the update manager in gnome. and my system locked up I had to manually restart 

now when I run update manager I get this:

where does this package run from ? 

~D

---

### Post by Thirtysixway on 2008-05-14
Did you try running ```
dpkg --configure -a
``` already?

---

### Post by mkoehler on 2008-05-14
Note: You have to run the command with administrator privileges, so 

```
sudo dpkg --configure -a
```

---

### Post by ZabiGG on 2008-05-14
Question:

Did you add special repositories to your source list before the update? I know I received similar errors when I added repos to source files by mistake... Removing them cleared my problem.

Cheers,

ZabiGG

---

### Post by hufferd on 2008-05-14
I must have had a typo in the line sorry I hate feeling stupid LOL 

:)

---

### Post by ZabiGG on 2008-05-14
Asking a question is not stupid... it's a sign of intelligence! ;)

Being stupid is NOT asking a question when you should have :p

---

