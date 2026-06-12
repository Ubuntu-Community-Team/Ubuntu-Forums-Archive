---
title: "How to create a shared memory and some shared objects in linux?"
date: 2010-06-11
forum: Programming Talk
---

### Post by jeremy28 on 2010-06-11
Hi all;
I want to create a "Shared Memory" in linux, then create multiple "Shared Objects" that can access to a Table for example;
And one of them can write something into the Table and the other can access and read it, so that these operations can be handled by programmer!
I'm using Ubuntu 9.04 and I've set it's runlevel at 3 (I have commandline environment now!)
I've searched the Internet so much, but couldn't find a good sample code for this! 
I have no experience about it and need your help to introduce me a sample code about it and advise me how to compile and use it with "GCC"?!

Please help me with this, I'm so hurry!!
TIA

---

### Post by lostinxlation on 2010-06-11
I guess shmget, shmread and shmwrite are what you are looking for.
Google them and you can find a lot of examples.
 
Or another (easier) way is instead of sharing the data on memory, you can do the same on a file.

---

### Post by dwhitney67 on 2010-06-11
> **lostinxlation said:**
>  
Or another (easier) way is instead of sharing the data on memory, you can do the same on a file.
-1.  Way to slow.

Your suggestion for shmget() and related functions is the correct approach.

---

### Post by lostinxlation on 2010-06-11
> **dwhitney67 said:**
> -1. Way to slow.
 .
it depends on how much speed is required. If speed isn't a major factor, using files is much easier since you don't have to pay much attention about structure size.

---

