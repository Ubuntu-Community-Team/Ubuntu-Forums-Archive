---
title: "Bleachbit question?"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by cairnzi on 2011-10-27
hi people,i have just installed bleachbit and after scanning the APT section it says it can free up 1.8Gb, my question is, is this safe to delete these files? Cheers.

---

### Post by ubupirate on 2011-10-27
Clearing APT just cleans out the cached packages that you get from installing things from apt-get, synaptic or software center.

---

### Post by galacticaboy on 2011-10-27
> **cairnzi said:**
> hi people,i have just installed bleachbit and after scanning the APT section it says it can free up 1.8Gb, my question is, is this safe to delete these files? Cheers.

Yes it is completly safe. I use bleachbit weekly to clean every part of my system and it works like a charm. Just do not use the program called Computer janitor, delete that crap, it can harm your system. But with Bleachbit, clean away!

---

### Post by cairnzi on 2011-10-27
@galacticaboy,ubupirate cheers for the replies,thought it was safe but wanted to double check lol, yeah ive heard computer janitor is a bit iffy so have stayed away from it, Cheers again.

---

### Post by oldos2er on 2011-10-27
```
sudo apt-get clean
``` does the same thing. ```
man apt-get
``` for more info.

---

### Post by cairnzi on 2011-10-27
@oldos2er, Cheers.

---

