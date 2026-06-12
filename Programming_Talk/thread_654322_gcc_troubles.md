---
title: "gcc troubles"
date: 2007-12-30
forum: Programming Talk
---

### Post by stratavarious on 2007-12-30
.

---

### Post by xtacocorex on 2007-12-30
```
sudo apt-get install build-essential
```

---

### Post by stratavarious on 2007-12-30
.

---

### Post by stratavarious on 2007-12-31
.

---

### Post by xtacocorex on 2007-12-31
There have been many debates on whether build-essential should be installed by default, but it is included on the live-cd, just not installed, so if you do have an issue where you don't have internet and need it, just pop the cd in and install from there.

Python is included because a lot of the utility programs UI's are written with it and need the interpreter.

---

### Post by Kadrus on 2007-12-31
I think before trying:
```
sudo apt-get install build-essential
```
you should try:
```
sudo apt-get update
```
then try build-essential.
But you got it to work anyway..

---

