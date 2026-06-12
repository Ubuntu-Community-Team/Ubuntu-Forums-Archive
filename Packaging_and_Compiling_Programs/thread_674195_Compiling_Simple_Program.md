---
title: "Compiling Simple Program"
date: 2008-01-21
forum: Packaging and Compiling Programs
---

### Post by Georgeboy on 2008-01-21
Ok I have just wrote a very simple program nothing special I am still getting used to the ropes. I type gcc program.c and all I get is a.out is this it. I am very new to ubuntu in fact only 2 days I have used it for so I am still getting used to it. 

so how do I get my program to run

thanks

George

---

### Post by geraldm on 2008-01-21
From the directory containing a.out:
./a.out

# compile another program, use "-o" + program_name
gcc -I/usr/include -o program program.c
./program

Gerald

---

### Post by Georgeboy on 2008-01-21
Thanks

---

