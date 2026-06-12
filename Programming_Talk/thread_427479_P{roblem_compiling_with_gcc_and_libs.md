---
title: "P{roblem compiling with gcc and libs"
date: 2007-04-29
forum: Programming Talk
---

### Post by MichalisZ on 2007-04-29
Hello.
I 'm new to this community and I 'm really happy!
I have installed Ubuntu feisty 7.04 and I tried to compile a hello world program with gcc.
I 've used gcc in the past wioth no problem but now I receive tha message 

test.c :1:19: error: stdio.h: No such file or directory

This means that there are no libraries? How can I find them?
Thanks everyone.

---

### Post by g3k0 on 2007-04-29
sudo apt-get install build-essential

---

### Post by TeamMicron on 2007-04-29
Would installing make on this also work?  I am new to this also so I am getting an understanding of what everything does.  Thanks.
 TeamMicron

---

### Post by MichalisZ on 2007-04-29
I tried it but there are dependencies.
libc6-dev, libc-dev, g++ and goes on....
Is there a command to install dependencies?
or to overcome them?

---

### Post by Riemann on 2007-04-30
Thanks for the answer to this post. I was getting mad ](*,) looking for that libraries too. Finally 
**sudo apt-get install build-essential** solve the problem  at once.

 :guitar: 

It would be nice if further releases of Ubuntu include them by default. :D

---

### Post by MichalisZ on 2007-04-30
I still cannot install the build-essential package.
It seems that ubuntu prefer to install only their prefered packages but dependencies need other.

---

