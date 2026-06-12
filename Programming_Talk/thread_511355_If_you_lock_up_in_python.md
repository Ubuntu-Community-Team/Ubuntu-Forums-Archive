---
title: "If you lock up in python"
date: 2007-07-27
forum: Programming Talk
---

### Post by tc101 on 2007-07-27
I was just working with some test code in SPE (Stani's Python Editor).  I think I created an endless loop but am  not sure exactly what happened for sure but I got a bunch of popup error message boxes and could not close them.  I could not close SPE either or figure any way to get out of it.

On the main ubuntu menu I went to System/Administration/System Monitor and did a Kill Process on the Python process.  This worked.  It closed SPE and I was able to reopen it with no problem and keep working.  Is there a better way to handle something like this?

---

### Post by tc101 on 2007-07-27
I got the error again.  What does this mean and what is the best way to get out of it:

Assertion failure
Assertion [useCount == 0] failed at ../../../../contrib/src/stc/scintilla/src/Editor.cxx 216

---

### Post by pmasiar on 2007-07-27
If you would have better title (with SPE), you have chance that Stani would answer your question in person - since he switched to Ubuntu, he sometimes hands around. Otherwise, you are better of to ask directly in SPE dev list for this kind of specific question

---

### Post by tc101 on 2007-07-28
Thanks.  I'll try that.

---

### Post by smartbei on 2007-07-28
This happened to me a lot with SPE - a crashing python program you are testing will crash SPE with it. This is the main thing that caused me to switch to Geany.

---

