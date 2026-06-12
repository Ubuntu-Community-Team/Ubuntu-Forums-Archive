---
title: "Error with compilation + C"
date: 2008-09-10
forum: Programming Talk
---

### Post by R_Oliven on 2008-09-10
Dear All,

I´ve just started leaning C and there is a error message, when I try to compile the program, written in C, after typing: g++ -lm -O3 fctopfthermal.c -o test

"/usr/lib64/gcc/x86_64-suse-linux/4.1.2/../../../../lib64/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld returned 1 exit status"

The problem is: the same program had worked until yesterday (I didn´t change anything).

I would appreciate a lot if someone can give me some tips.

---

### Post by Kinetic_lord on 2008-09-10
to compile : 

g++ filename.cpp -o filename

to open

./filename

---

### Post by R_Oliven on 2008-09-10
Thank you but it still doesn´t work....

---

### Post by Kinetic_lord on 2008-09-10
are you sure the program is well-written? try to make a simple one:

#include <iostream>

using namespace std;

void main () {
cout<<"Hello World";
return 0;
}

u talking about C or C++...?

---

### Post by WRDN on 2008-09-10
Can you post the source code here so it can be checked.

---

### Post by revanb on 2008-09-10
Have you installed the essentials package? You need it to compile.

I'm not sure why it's not installed by default. I cant remember the exact package name its either

devel-essentials
or
essentials-dev

Just search for it in aptitude.

Good luck.

---

### Post by WRDN on 2008-09-10
> **revanb said:**
> Have you installed the essentials package? You need it to compile.

I'm not sure why it's not installed by default. I cant remember the exact package name its either

devel-essentials
or
essentials-dev

Just search for it in aptitude.

Good luck.

It's:

```
sudo apt-get install build-essential
```

If the OP could compile the program before though, then he should have this installed already. The problem is in the source code itself (an undefined reference) but I we will need to see the actual source before it can be solved.

---

### Post by R_Oliven on 2008-09-10
it works!!!

Thanks a lot once more!

---

### Post by Sef on 2008-09-10
Moved to Programming Talk.

---

