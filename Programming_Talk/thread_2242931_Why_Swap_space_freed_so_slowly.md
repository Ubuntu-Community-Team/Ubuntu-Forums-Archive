---
title: "Why Swap space freed so slowly?"
date: 2014-09-05
forum: Programming Talk
---

### Post by bak&#305;r on 2014-09-05
Dear all,

I accidentally realized some weird behavior of the Linux system in releasing swap space: if a program requires too much RAM, some space in swap area of the hard disk quite rapidly, as quick as the hard drive's speed allows, I suppose. However when a program deallocates the variables, the swap space is not released immediately, but it takes more than 10 hours to do so. This is the case even if I kill the terminal that the program runs in.

Attached is a plot of RAM and SWAP usage (in kB) with respect to time (s). I create a very huge array at around t=1000 s and the program terminates successfully soon after. Can anybody explain the mechanism behind this? 

[ATTACH=CONFIG]256158[/ATTACH]

---

### Post by CharlesA on 2014-09-05
That's normally. Even my box with 16GB of RAM uses some swap. If you want to modify that behavior, check out how to modify swappiness.

---

### Post by bak&#305;r on 2014-09-05
Maybe I could not express myself very well. I do not have any problems with that occurring. But I want to know what kind of mechanism causes such a gradual release of space.

---

### Post by CharlesA on 2014-09-05
This might help:
[http://askubuntu.com/questions/103915/how-do-i-configure-swappiness](http://askubuntu.com/questions/103915/how-do-i-configure-swappiness)

---

