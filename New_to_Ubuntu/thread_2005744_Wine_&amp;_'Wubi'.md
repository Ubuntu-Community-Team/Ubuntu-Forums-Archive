---
title: "Wine &amp; 'Wubi'"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by Unknown Fella on 2012-06-18
Well guys, I'm running Ubuntu installed as a Windows program (Windows installer), as far as I have read it's not Wubi exactly, but it's pretty much the same. Well, in Windows I used to use Ares, then one day I used it on 'Wubi' with Wine. It works perfectly. The issue is that now, when I go to Windows and try to run it, nothing happens, as if it won't work anymore on Windows.

I don't really need to fix it as much as I want to know what happened and why, if you can provide me a way to fix it, then that's very cool too.

Thank you for giving me some of your time and for your answers, I do appreciate it a lot.

---

### Post by afixane on 2012-06-18
Are you run the .exe directly from C:/Program File/Ares ??

---

### Post by mastablasta on 2012-06-18
afixane has a point. if you used it on wubi with wine then you owuld have to install it in wine first.

---

### Post by Mark Phelps on 2012-06-18
> **Unknown Fella said:**
> Well guys, I'm running Ubuntu installed as a Windows program (Windows installer), as far as I have read it's not Wubi exactly, but it's pretty much the same. 

There is no "nearly Wubi" -- it either IS a Wubi install, or it is not.

There are two differences with a Wubi install:
1) It is installed from INSIDE MS Windows -- other installs are not
2) It creates a single file (root-disk) on a Windows partition, not files on a separate Linux filesystem partition.

When it runs, it does NOT run INSIDE Windows; instead, it runs by itself just like any other install.

---

### Post by Unknown Fella on 2012-06-18
> **afixane said:**
> Are you run the .exe directly from C:/Program File/Ares ??
Yes I did. What should I have done? O.O

---

