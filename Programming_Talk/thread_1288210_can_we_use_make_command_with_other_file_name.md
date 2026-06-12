---
title: "can we use make command with other file name?"
date: 2009-10-11
forum: Programming Talk
---

### Post by vksingh on 2009-10-11
Hi, 

I have made a make file of a project with some other name (other than makefile). For example makefile1.

I am trying the following command:

$ make makefile1.

But it is not working.

Kindly help.................:(

---

### Post by wmcbrine on 2009-10-11
If you give a parameter like that, with no option, make assumes it's a target. To tell it to use a different file, use "-f":

make -f makefile1

---

### Post by vksingh on 2009-10-11
Thanks................a lot.

---

