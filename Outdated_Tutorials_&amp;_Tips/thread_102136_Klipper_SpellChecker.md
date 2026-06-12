---
title: "Klipper SpellChecker"
date: 2005-12-11
forum: Outdated Tutorials &amp; Tips
---

### Post by cwaldbieser on 2005-12-11
A simple clipboard spellchecker for KDE.

Requires:
KDE (tested 3.4.3)
python (tested 2.4)
python-dcop
Aspell (tested Aspell 0.60.3)

Overview:
This set of simple shell and python scripts create a system where the user can select text which is copied to the klipper clipboard application and then initiate an interactive spellcheck on that text.  The results are placed back in the clipboard so they may be pasted.

With some script modifications, this could also perform other transformations on the clipboard contents, like sorting lists, etc.

---

### Post by cwaldbieser on 2005-12-18
I made some modifications to the original scripts to correct some bugs I noticed (like removing newlines).  Also, I was able to turn most of the main script into a single pipeline, and that seems to have improved the performance quite a bit as well as making the code a bit easier to follow.

---

