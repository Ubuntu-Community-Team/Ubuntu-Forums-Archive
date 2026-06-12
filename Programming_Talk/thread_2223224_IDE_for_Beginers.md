---
title: "IDE for Beginers"
date: 2014-05-10
forum: Programming Talk
---

### Post by oldsmobile2 on 2014-05-10
Hi people.

I am currently learning C language so I needed an IDE for it.first i used ajnuta but it had a c99 error for most of my programs (said that i can's initialize a variable in loops but now i saw a program known as Emacs.

I need to know how to use it for making C programs i.e Compile them and also run them.
can someone give me step by step instructions as to using this program I've gone to their site and all they tell are shortcuts for it and that makes it more confusing.
Pictures will be increasingly helpfull.

The version is
GNU Emacs 24.3.1  GTK+ Version 3.10.7

---

### Post by bapoumba on 2014-05-10
*Thread moved to **Programming Talk**.*

---

### Post by oldsmobile2 on 2014-05-10
Anyone???

:(

---

### Post by steeldriver on 2014-05-10
Are you set on using emacs? A different editor/IDE such as geany might have a less steep learning curve. IIRC it will do simple C/C++ builds out of the box provided you have the basic development tools installed (easiest way is to install the **build-essential** metapackage, which contains gcc, g++, make and the supporting libraries).

---

### Post by oldsmobile2 on 2014-05-10
As a matter of fact i installed geaney just now because Emacs was seemingly tough to use.
but now i am stuck with another problem.
I have an Computer Programming class where i am taught C language in Dev c,so I have to do projects and small programs ocassionally but now I have learnt that there is a C99 problem in Linux and furthermore the libraries like Conio.h are not used in linux so i don't know how to use gets() for char and  initializing variables in for loop.

Can you atleast tell me the solutions to these problems and any other advice you may have.

---

### Post by ofnuts on 2014-05-10
1) [http://stackoverflow.com/questions/8792317/why-cant-i-find-conio-h-on-linux](http://stackoverflow.com/questions/8792317/why-cant-i-find-conio-h-on-linux)

2) All these IDE/editors use the same compiler under the hood (gcc). May you could envision that the problem of variable initialization isn't with the compiler but with your code or the way you compile it. After all, you are just a beginner and these compilers are not distributed in the wild without running some very heavy testing. They are also used to compile most Linux apps, so if there were such a blatant bug it would have been fixed already. Post your loop code and someone may tell you why you get the error.

---

### Post by oldsmobile2 on 2014-05-10
Thank you for your reply.
I got around the c99 error by initializing them outside the loop but i still don't know the library which contains the gets() function for scanning the char strings.
in linux(In windows i think it was conio.h) could you help me with that .

---

### Post by steeldriver on 2014-05-10
In Linux, gets() is available from <stdio.h> HOWEVER afaik **you should use fgets() instead** because it takes an explicit buffer size (to prevent overflow)

See [FONT=courier new]man fgets[/FONT] for more info

---

### Post by oldsmobile2 on 2014-05-10
Thanks your help is much appreciated.

---

