---
title: "geany tty placement"
date: 2009-11-06
forum: Programming Talk
---

### Post by iMisspell on 2009-11-06
Ive searched around with no luck...
Is there a way to change the screen position of Geany when you are testing scripts ?

Right in the middle of the screen will do if possible.
As of now, Geany places the terminal in the upper left, which i do not care for.

_

---

### Post by iMisspell on 2009-11-08
Edit -> Preferences -> [Tools]
Then edit how the terminal is loaded with -arguments

For window size and position
```
-geometry 125x40+100+500
```
**-geometry** width(x)Height(+)px from left(+)px from top


Heres what i ended up using, beefs up font size and also window size and location.
```
xterm -font -*-fixed-medium-r-*-*-18-*-*-*-*-*-iso8859-* -geometry 125x40+100+500
```

_

---

