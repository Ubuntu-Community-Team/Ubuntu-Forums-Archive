---
title: "problems with compilation!"
date: 2006-07-16
forum: Programming Talk
---

### Post by defmer on 2006-07-16
hi all,

I am kind new to Linux so really need a help with compiling c++ progs.

when I did "gcc -o test test.cpp" or "cc test.cpp", I Got the following error.

"**gcc: installation problem, cannot exec 'cc1plus': No such file or directory**"

thanks for helping out.

defmer

---

### Post by gborzi on 2006-07-16
You need to use c++ or g++ to compile C++ program, and obviously you have to install the g++ package.

---

### Post by Randomskk on 2006-07-16
Make sure "build-essential" is installed via apt / synaptic, and then use this to compile:
g++ -o test test.cpp

---

