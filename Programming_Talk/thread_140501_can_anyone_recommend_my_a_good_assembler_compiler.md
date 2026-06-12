---
title: "can anyone recommend my a good assembler compiler"
date: 2006-03-06
forum: Programming Talk
---

### Post by edan on 2006-03-06
hi im a bit new on linux and wondered if anyone can recommend me a good compiler, for a 32 bite processor (p4)
i need a compiler with an out-put screen  (i know that som of the compilers dont have that...)
thanks for your help

---

### Post by knalle on 2006-03-06
do you want a **compiler** or an **assembler**, your post is confusing

---

### Post by Gustav on 2006-03-06
If you want an assembler, nasm is probably the way to go (it's in the repos)

---

### Post by edan on 2006-03-06
im sorry if my ad wase confusing i wase kind of confused myself
i whant a compiler....
thnx for all the help

---

### Post by pharcyde on 2006-03-06
What language are you wanting to program in?
gcc is the standard for c/c++ on linux

---

### Post by knalle on 2006-03-06
use this from command line to get the gnu compiler for c/c++

```
sudo apt-get install gcc
```

make your .c and .h files

```
gcc mysource.c -o myprogram.bin
```

---

### Post by toojays on 2006-03-06
Please don't follow the advice in the above post. The correct way to install gcc is "sudo apt-get install build-essential". If you only install the gcc package, you will run in to trouble sooner or later.

---

### Post by knalle on 2006-03-06
[QUOTE=toojays]Please don't follow the advice in the above post. The correct way to install gcc is "sudo apt-get install build-essential". If you only install the gcc package, you will run in to trouble sooner or later.[/QUOTE]

thanx, didn't know that

---

### Post by edan on 2006-03-07
thnx alot you really helped me :)

---

