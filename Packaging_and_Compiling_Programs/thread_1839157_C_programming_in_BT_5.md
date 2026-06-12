---
title: "C programming in BT 5"
date: 2011-09-05
forum: Packaging and Compiling Programs
---

### Post by hezy00 on 2011-09-05
Hello,
how can I write and execute programs in C language with backtrack 5? Do I have to install environment? (I tried to send that question in a BT forum only I don't know if it has published and cannot see it in the threads posted). Thank you,
Hezy.

---

### Post by ~!geek!~ on 2011-09-05
1) Write C program in a file. Save it with filename.c 2) open terminal, konsole in this case. Use cd command to reach directory containing your filename.c 3) Use gcc to compile the file i.e. command: gcc filename.c -o oufile 4) If compiled without error, type ./outfile to run the program you compiled... Done!!!

---

### Post by haqking on 2011-09-05
> **~!geek!~ said:**
> 1) Write C program in a file. Save it with filename.c 2) open terminal, konsole in this case. Use cd command to reach directory containing your filename.c 3) On konsole, type chmod +x filename.c 4) Use gcc to compile the file i.e. command: gcc filename.c -o oufile 5) If compiled without error, type ./outfile to run the program you compiled... Done!!!

+1

BT5 is just a a collection of Pen test and Sec Audit tools packaged together neatly in a Linux environment, BT5 being based on Ubuntu.

So it is just Linux, as in any linux C programming is built in for the most part, you need to gcc and build essentials and thats it.

use an editor, save, compile done.

Enjoy

---

### Post by red_Marvin on 2011-09-05
>> 3) On konsole, type chmod +x filename.c
+x permissions are not needed for compiling the c source, however
the resulting program needs it.

---

### Post by hezy00 on 2011-09-05
Thank you.

---

### Post by hezy00 on 2011-09-05
Thanks.

---

