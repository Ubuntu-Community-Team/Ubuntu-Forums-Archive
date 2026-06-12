---
title: "gcc problem."
date: 2005-10-22
forum: Programming Talk
---

### Post by realno on 2005-10-22
I wrote a small program using multi-thread(pthread_create etc.). I used the command "gcc a.c" to compile it on my old computer. After I install ubuntu 5.10, I have to use "gcc -lpthread a.c" to compile or I will get the information "undefined reference pthread_create". What is the problem here?

Thanks!!!

---

### Post by thumper on 2005-10-22
Did you do a typo in your code or in the message?

pthread_create with an E.

---

### Post by LordHunter317 on 2005-10-22
Don't use -lpthread, use -pthreads.

---

### Post by realno on 2005-10-22
Sorry, that is a typo... But I did it right in the program . Thanks very much for the replys
I can compile the program. I just wonder if there is a way to avoid the command -lpthread or -pthreads.

---

### Post by LordHunter317 on 2005-10-22
Nope.  You must use if it you want multithreading support.

---

### Post by realno on 2005-10-23
But I'm very sure It don't need this command on my old computer and my school's computer:confused: 

so weird:confused:

---

### Post by realno on 2005-10-23
BTW, my previous system is Redhat LINUX.

---

### Post by thumper on 2005-10-23
I don't suppose you have a sample of the work that you compiled on your previous system along with the command line?

---

### Post by realno on 2005-10-23
It just use pthread_create and mutex, very simple program. 

And I used" gcc name.c -o name" to compile it.

---

### Post by LordHunter317 on 2005-10-23
You got lucky, as pthread_Create is in libc, so libc can use it.

Multithreaded programs must be compiled -pthread.  It's not optional.

---

### Post by realno on 2005-10-23
Thanks for all the helps:)
I'm so happy that I was so lucky :p

---

