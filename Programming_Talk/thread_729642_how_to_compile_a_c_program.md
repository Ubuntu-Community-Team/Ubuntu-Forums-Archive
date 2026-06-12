---
title: "how to compile a c program"
date: 2008-03-20
forum: Programming Talk
---

### Post by ankitguptag18 on 2008-03-20
i have created da most comon "Hello World" c program but how do i compile da program.....i have g++ installed

first.c

#include <stdio.h>
void main()
{
printf("Hello World");
getch();
}

---

### Post by lnostdal on 2008-03-20
the faq leads you to [http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635)

---

### Post by Kadrus on 2008-03-20
First of all there is an error in the code..
let's consider this:
[PHP]
#include<stdio.h>
int main()
{
printf("Hello World");
getchar();
return 0;
}
[/PHP]
Save the file ex.c
Alright..I am assuming that you have installed gcc...the compiler of C
if you haven't  type in terminal
```

sudo apt-get install build-essential
```
That will install the compilers..
when it's installed type in terminal
```
gcc ex.c
```
then type 
```
./a.out
```
This should do it
good luck:)

---

### Post by ankitguptag18 on 2008-03-20
do we have a compiler n editor......like borland....

---

### Post by twright on 2008-03-20
you can try eclipse and it's C++ plugin

---

### Post by lnostdal on 2008-03-20
yeah, some like an IDE like kdevelop (similar to borland) .. others prefer an environment where everything is loosely coupled together

but, if you are _serious_(#1) about development (on linux) you *will* learn how each part(#2) works in isolation, and you *will* learn how to hook things together yourself  .. when you know this you can either:

* keep using an IDE

* create your own IDE by "connecting the parts" and adding event-hooks or short-cut keys to them

..regardless of what you do you *will then* understand how things work, and *where*, *why* and *how* things fail when they do

(something about IDEs and development environments should be added to the FAQ so we can end these repeating discussions/questions for good .. )


#1: if someone want to discuss the part about "seriousness" .. just, don't .. you are wasting your time as i am 100% correct anyway(!) .. feel free to ask questions, though; don't question what i've said here as i do not care to discuss it with you .. (yes, i'm tired of these threads/discussions)

#2: the compiler, the linker, the run-time linker/library loader, the debugger .. etc.

---

### Post by MONODA on 2008-03-20
check out geany it is a great IDE which alows you to compile your program. Its also a nice lightweight text editor.

---

### Post by k2t0f12d on 2008-03-20
> **ankitguptag18 said:**
> do we have a compiler n editor......like borland....

anjuta
kdevelop
geany
eclipse
netbeans

---

### Post by Kadrus on 2008-03-20
There is a Gedit which is a great IDE in my mind...check the stickies..for more info..because each person is going to give you a different opinion on what to use..

---

### Post by Wybiral on 2008-03-20
> **Kadrus said:**
> There is a Gedit which is a great IDE in my mind...check the stickies..for more info..because each person is going to give you a different opinion on what to use..

Gedit is more of a "programmers text editor" than it is an IDE. But when you use the embedded terminal plugin, it pretty nicely for developing in most languages.

---

### Post by ruy_lopez on 2008-03-20
Vim + gcc + make

It might not be very integrated. But it's still a development environment.

---

