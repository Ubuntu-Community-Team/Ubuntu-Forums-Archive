---
title: "gcc and g++ weird compile error"
date: 2010-01-16
forum: Programming Talk
---

### Post by opengl_cpp on 2010-01-16
Hi guys.

I don't know why, but recently gcc/g++ always give me this error every time i try to compile something.

` C preprocessor "/lib/cpp" fails sanity check `

I checked /lib/cpp, I can't see /cpp directory under /lib, it seems to be removed. 

I downloaded the whole gcc using apt-get but it didnt solve my problem.
if you have any suggestion, ill appreciate?s

---

### Post by denarced on 2010-01-16
> **opengl_cpp said:**
> Hi guys.

I don't know why, but recently gcc/g++ always give me this error every time i try to compile something.

` C preprocessor "/lib/cpp" fails sanity check `

I checked /lib/cpp, I can't see /cpp directory under /lib, it seems to be removed. 

I downloaded the whole gcc using apt-get but it didnt solve my problem.
if you have any suggestion, ill appreciate?s

the source code?
command you used?

---

### Post by deer dance on 2010-01-16
It appears that part of the compiler has gone missing, perhaps reinstalling gcc will solve the problem?

---

### Post by eewoz on 2010-01-16
> **opengl_cpp said:**
> Hi guys.

I don't know why, but recently gcc/g++ always give me this error every time i try to compile something.

` C preprocessor "/lib/cpp" fails sanity check `

I checked /lib/cpp, I can't see /cpp directory under /lib, it seems to be removed. 

I downloaded the whole gcc using apt-get but it didnt solve my problem.
if you have any suggestion, ill appreciate?s

I don't know if this helps or not but on my installation in the /lib directory there is a shortcut called cpp that points to /etc/alternatives/cpp.

---

### Post by opengl_cpp on 2010-01-27
thank you guys. 
Maybe a explained my problem ambiguously. In fact I have no problem at compile time. But the problem is when i want to configure a source package. For example I download an application from sourceforge.com, when I issue ./configure it checks my system for dependencies, and riches to a point and warn me about my c headers, as i said at the top.

Maybe the problem comes from my libtools? i donno how to install that on my ubuntu????

---

### Post by daasdingo on 2010-01-27
have you installed the 

build-essential

package? you should at least have that one for compiling

---

### Post by opengl_cpp on 2010-01-27
oh, i tried to install it before, and ubuntu said it was installed already. i mean i have this package. i searched the nest, but there was nothing useful. 

i fear, if i have to reinstall the os. 

i dont want to lose all of my data.

---

### Post by dwhitney67 on 2010-01-27
> **opengl_cpp said:**
> 
i dont want to lose all of my data.
You wouldn't if you were to create a separate partition for storing your data (including user accounts).

---

### Post by opengl_cpp on 2010-01-28
unfortunately I have a single partition. 
how can i fix this problem. Is it imposibble to shrink my partition and move my home dir to it, before reinstalling ubunut?

---

