---
title: "Mersenne Twister RNG"
date: 2010-03-19
forum: Programming Talk
---

### Post by ppradeep on 2010-03-19
hi 
i want to use **_Mersenne Twister RNG   _**for generating random numbers i have donloded mtwist-0.8. I am not understaning how to use it help me plz

---

### Post by MadCow108 on 2010-03-19
I have never seen nor used that implementation, but on first sight you will just have to compile it, look in the header files for the right interface and just link the compiled code with your code

gsl also has a mersenne twister implemented:
sudo apt-get install libgsl0-dev

the needed compilationflags can be obtained with pkg-config:
pkg-config --libs --cflags gsl

this line can also be used directly when compiling:
gcc myfile.c `pkg-config --libs --cflags gsl`

documentation:
[http://www.gnu.org/software/gsl/manual/html_node/Random-number-generator-algorithms.html](http://www.gnu.org/software/gsl/manual/html_node/Random-number-generator-algorithms.html)

---

