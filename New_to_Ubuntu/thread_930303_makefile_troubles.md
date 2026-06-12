---
title: "makefile troubles"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by xboxbman on 2008-09-25
I have 3 .c files I need to compile into 3 different executables using only one makefile.  Can anyone give me some tips?

---

### Post by kjohansen on 2008-09-25
put this in makefile.  
```

all: prog1 prog2 prog3

prog1:
    gcc prog1.c -o prog1

prog2:
    gcc prog2.c -o prog2

prog3:
    gcc prog3.c -o prog3


```

---

### Post by abhi_nit_jsr20 on 2008-09-25
Suppose we have three files final.c,main.c and reciprocal.c the following code must be put in a file named  "Makefile":

final.out: final.c
        gcc -o final.out final.c
main.out: main.c 
        gcc  -o main.out main.c
reciprocal.out: reciprocal.c 
        gcc -o reciprocal.out reciprocal.c

name on the left of colon is target name(our executable name), filenames on the right of colon are the files on which the target(our executable) depends.You can specify more than one dependencies seperated by spaces.

The actual command for compilation lies on second line. You must give a tab before every second line.

---

### Post by abhi_nit_jsr20 on 2008-09-25
Suppose we have three files final.c,main.c and reciprocal.c the following code must be put in a file named  "Makefile" in same directory containing .c files:

final.out: final.c
        gcc -o final.out final.c
main.out: main.c 
        gcc  -o main.out main.c
reciprocal.out: reciprocal.c 
        gcc -o reciprocal.out reciprocal.c

name on the left of colon is target name(our executable name), filenames on the right of colon are the files on which the target(our executable) depends.You can specify more than one dependencies seperated by spaces.

The actual command for compilation lies on second line. You must give a tab before every second line.

---

### Post by xboxbman on 2008-09-25
thanks guys.  I got it sorted.  I appreciate the help

---

