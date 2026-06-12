---
title: "GCC questions"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by fmpfmpf on 2008-05-08
i am using Ubuntu 8.04

What is GCC?
How do i know if my Linux has GCC?
How do i check my GCC version?

thank you

---

### Post by cartisdm on 2008-05-08
It's a GUI compiler.  Check out [this]("http://www.xgc.com/misc/tech_note_0.htm")

---

### Post by fmpfmpf on 2008-05-08
but how do i check my GCC version?

---

### Post by Rocket2DMn on 2008-05-08
GCC is for compiling programs (namely C programs).
You can get it by running
```
sudo apt-get install build-essential
```
That metapackage will get you all sorts of compilers needed for building your own programs or compiling other programs from source should you ever need to.
You can check version with
```
gcc --version
```

---

