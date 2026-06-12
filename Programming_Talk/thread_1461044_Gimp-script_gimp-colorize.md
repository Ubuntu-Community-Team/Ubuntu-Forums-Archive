---
title: "Gimp-script gimp-colorize?"
date: 2010-04-23
forum: Programming Talk
---

### Post by jfca283 on 2010-04-23
hi
i need to colorize a folder with this parameters
gimp -i -b (colorize $i 180 50 0) (gimp-quit 0)
i get nothing
help

---

### Post by geirha on 2010-04-23
It's very hard to help you when you don't provide any information. colorize, is that a function you've made yourself? or did you find it on the net? what does it look like?

What is the shell variable **i** set to? A line from a script, without its context, is not very useful. 

According to gimp's man-page, -b takes ONE argument, not several, so you definitely need quotes around it. Possibly it should be something like
```
gimp -i -b "(colorize \"$i\" 180 50 0)" -b "(gimp-quit 0)"
```

---

