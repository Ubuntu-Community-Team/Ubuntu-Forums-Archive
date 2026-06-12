---
title: "Help running C program"
date: 2007-09-06
forum: Programming Talk
---

### Post by DFord425 on 2007-09-06
Im new

---

### Post by Mirrorball on 2007-09-06
What problems are you having?

---

### Post by aks44 on 2007-09-06
> **Mirrorball said:**
> What problems are you having?

He's new.

Check today's date: September, 1993... ;)

---

### Post by DFord425 on 2007-09-06
Sorry, i thought i fixed my post. I am having a problem running and/or compiling a helloworld program in C. It seems to compile i think. When i go to run it from command line though, it doesnt run. I type in the name to run, like i think im supposed to do, and it says command not found. Am i doing something wrong in the way i try to run it?
I compile using: cc helloworld.c -o helloworld
Then try to run using: helloworld and it says command not found.
Any ideas?

---

### Post by happysmileman on 2007-09-06
> **DFord425 said:**
> Sorry, i thought i fixed my post. I am having a problem running and/or compiling a helloworld program in C. It seems to compile i think. When i go to run it from command line though, it doesnt run. I type in the name to run, like i think im supposed to do, and it says command not found. Am i doing something wrong in the way i try to run it?
I compile using: cc helloworld.c -o helloworld
Then try to run using: helloworld and it says command not found.
Any ideas?

```
./helloworld

```
The "./" tells it to look in current folder

---

### Post by gnusci on 2007-09-06
ok if you get your program compiled, I will do it with:

**$ gcc helloworld.c -o helloworld**

and then run it with:

**$ ./helloworld**

---

### Post by DFord425 on 2007-09-06
Thank You

---

