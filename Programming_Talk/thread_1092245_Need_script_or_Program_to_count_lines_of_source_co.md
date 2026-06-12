---
title: "Need script or Program to count lines of source code"
date: 2009-03-10
forum: Programming Talk
---

### Post by Olnex on 2009-03-10
Hello, I need a script or a program that can count how many lines are there in a directory contains source code as well as other directories(contain code as well), there are .java files in these directories, the script or program should count number of lines with/without comments(starts with // or surrounded by /**/)

Thanks a lot!!!

---

### Post by simeon87 on 2009-03-10
Try cloc: [http://cloc.sourceforge.net/](http://cloc.sourceforge.net/)

---

### Post by mike_g on 2009-03-10
Or you could just call [wc](http://www.computerhope.com/unix/uwc.htm) from the shell, but Idont think you can exclude comments with it.

---

### Post by bobbocanfly on 2009-03-10
There is a program called sloccount that does this. It (recursively) searches through your source tree and gives you a report of all the languages used and how many lines of code written in each language.

It is in Universe, so you can just run
```
sudo apt-get install sloccount
```

---

