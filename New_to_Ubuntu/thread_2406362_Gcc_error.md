---
title: "Gcc error"
date: 2018-11-19
forum: New to Ubuntu
---

### Post by thecoderouss on 2018-11-19
Hi , i tried to compile lex.yy.c file using the command gcc lex.yy.c -ll 
i keep getting error 
/usr/bin/ld :cannot find -ll

i have flex installed 2.6.4 version 
i also have bison installed 
i also installed build-essential 
i tried to change the file ld with another that works on my friend PC 
but still the same ! 
can anyone help please ! 
?
:(:(

---

### Post by spjackson on 2018-11-20
> **thecoderouss said:**
> Hi , i tried to compile lex.yy.c file using the command gcc lex.yy.c -ll 
i keep getting error 
/usr/bin/ld :cannot find -ll

This means that it cannot find the libl library.
> 
i have flex installed 2.6.4 version 
i also have bison installed 
i also installed build-essential 

libl.a is provided by the libfl-dev package. You need to install that. It is recommended by the flex package.
> 
i tried to change the file ld with another that works on my friend PC 

That is very unwise and could lead to all sorts of problems unless your friend is running precisely the same version of precisely the same operating system.

---

