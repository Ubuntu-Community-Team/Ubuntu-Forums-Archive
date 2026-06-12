---
title: "How to use only one processor to run my program"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by tollyfather on 2013-06-20
I need help to figure out how to run my program using only one processor...I'm using AMD Athlon(tm) II Dual-Core M320 and will like to disable the other processor from running.. I only need one core to execute my code..

---

### Post by Paqman on 2013-06-20
Unless you deliberately write your program to be multi-threaded then it'll only use a single core. You can't stop other processes from using the other core while your stuff is running though.

---

### Post by Doug S on 2013-06-20
If you want to run your computer using just one CPU, then you could boot using "maxcpus=1". See also this [thread. ]("http://ubuntuforums.org/showthread.php?t=2151095")
If you want to have your computer running normally but force your program to only use one CPU, and not have the scheduler change CPU's sometimes then do (to use CPU 0)```
taskset -c 0 ./your_program
```

---

### Post by tollyfather on 2013-06-20
Thank.. It work perfectly.

---

