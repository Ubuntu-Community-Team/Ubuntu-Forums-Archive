---
title: "c in ubuntu"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by ettercap on 2008-06-18
hello every 1
i installed ubuntu 8.04 
i wanna knw how to run c programs in ubuntu
i can't quite use gcc
wen i use it in the terminal i get this...

god@ubuntu:~/Desktop$ gcc -o c c.c
c.c:1:18: error: stdio.h: No such file or directory
c.c: In function ‘main’:
c.c:4: warning: incompatible implicit declaration of built-in function ‘printf’
god@ubuntu:~/Desktop$ 


help............

---

### Post by bumanie on 2008-06-18
You have to run command  > sudo apt-get install build-essential in terminal. This installs the gcc "C" compiler. Then you should have more luck.

---

### Post by the_doc on 2008-06-18
> **bumanie said:**
> You have to run command   in terminal. This installs the gcc "C" compiler. Then you should have more luck.

It also gives access to all the header files.

---

