---
title: "Problem sh:1 not found calling a program during execution of a .out file"
date: 2015-04-03
forum: Packaging and Compiling Programs
---

### Post by iangajan on 2015-04-03
Hi everybody, i'm a new Ubuntu and Linux user and i bumped into a problem with executing a .out file that i've previously compiled with g++ (it was written in c++). 
Briefly, when i try to execute it (it is called prova.out), i get this message:


giulio@giulio-HP-Compaq-dc5100-SFF-PM215AV:~/wrapper$ ./prova.out    [wrapper is the folder that  contains prova.out ]
1 files
/home/febio2-2.2.6/bin/febio2.lnx32 -s P1000_L_HH_opt.feb
sh: 1: /home/febio2-2.2.6/bin/febio2.lnx32: not found
correlation coefficient -nan
giulio@giulio-HP-Compaq-dc5100-SFF-PM215AV:~/wrapper$ 


NB the lines "1 files" and "correlation coefficient -nan" are correct, they are part of the execution
The program prova.out takes the file called P1000_L_HH_opt, and calls the executable file febio2.lnx32 (which is a software of finite elements simulation) during the execution, but it seems to not find this file. If i try to open it separately with the terminal it works, and the path is correct.
Could somebody help me? If you need more informations i will post them as soon as i can. Thanks for the attention

---

### Post by TheFu on 2015-04-05
Are you using system() or fork() or something else?

---

