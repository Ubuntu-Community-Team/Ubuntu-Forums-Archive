---
title: "Hidden folders won't stay hidden"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by huxley2 on 2013-10-20
Hi, everybody

When I go to home files all of the hidden folders are in view. I can hide them with ctrl H or via view options but once I leave and re-enter the hidden folders are all back again. How can I keep them hidden?

Thanks..

---

### Post by fantab on 2013-10-20
Open dconf. Then navigate to org-> gtk-> settings-> file-chooser-> uncheck 'show-hidden'.

```
$ dconf-editor
```

---

### Post by rburkartjo on 2013-10-20
try this go to your home folder than hit control h. once the hidden folders are showing right click your mouse and then uncheck show hidden files. i just checked and works at my end. good luck

---

### Post by ruddi on 2013-10-20
Have you tried to change the settings in Files -> Preferences and untick Show hidden and bakup files?

---

### Post by huxley2 on 2013-10-20
Thanks for the replies, guys. I tried fantabs idea first and it worked a dream so didn't get round to testing the other suggestions, but thanks for all the top tips.

Case solved

---

