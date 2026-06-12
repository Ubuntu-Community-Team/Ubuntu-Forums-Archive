---
title: "NO sudo password for certain commands"
date: 2009-04-30
forum: Programming Talk
---

### Post by acrane1 on 2009-04-30
hey, I am having some trouble getting the syntax right for editing my visudo file. What I am looking to do is edit the visudo file so that when I use the command sudo mount I am not required to enter a password. I am doing this so that a stat up script I've written can be done without having to have my root password unprotected, in a basic script. I have looked around and found ways to stop sudo all together but I dont want that. I just want it so that a password is not required when I do sudo mount. can someone help me out?

---

### Post by unutbu on 2009-04-30
I believe this would work:
```

Cmnd_Alias MYCMD=/bin/mount
acrane1 ALL=NOPASSWD: MYCMD
```
See also [http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

---

### Post by acrane1 on 2009-04-30
thanks that site is perfect

---

