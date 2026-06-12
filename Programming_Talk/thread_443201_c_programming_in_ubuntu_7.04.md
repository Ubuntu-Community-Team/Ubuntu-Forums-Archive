---
title: "c programming in ubuntu 7.04"
date: 2007-05-14
forum: Programming Talk
---

### Post by acpsiddhartha on 2007-05-14
hi
i am new in linux. i have just installed ubuntu 7.04. I was trying to run a simple c code by gcc test.c command. it didn't work. is there any other command to compile? or I need to install any other package? and what about c++ ??
Thanks
Sid

---

### Post by rich.bradshaw on 2007-05-14
sudo apt-get install build-essential

wil get you gcc and other compilers.

---

### Post by rich.bradshaw on 2007-05-14
Just noticed that cc is symlinked to gcc. I always just type cc, but they are the same anyway.

---

### Post by acpsiddhartha on 2007-05-14
Thank you so much. I will try this out.

Thanks

---

### Post by tkjacobsen on 2007-05-14
g++ is the GNU c++ compiler, it comes with build-essential

---

