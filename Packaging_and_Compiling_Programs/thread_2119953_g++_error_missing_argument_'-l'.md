---
title: "g++: error: missing argument '-l'"
date: 2013-02-25
forum: Packaging and Compiling Programs
---

### Post by lockandstrike on 2013-02-25
So here is the thing. I installed ubuntu yesterday in my netbook cause it came with windows by default. I love programming altought it is not my job. I like making games and i do it with the Allegro library. So I instaled codeblocks, compiled the library added the links in codeblocks an tested it out. So I tried making a simple allegro display but when i try to compile it says:

g++: error: missing argument '-l'

This might be a very noobish question but it was the first timed this append to me. If you need any more informationt that could help you help me say what you need and i'll give it to you ;)

A big thanks in advance.

---

### Post by tomzie on 2013-02-25
try g++ -o hello hello.cpp on the command line where hello is your executable and hello.cpp is the file you wanted to compile.

---

### Post by lockandstrike on 2013-02-25
I know I should have said this earlier but I'm doing it on codeblocks and it's a .c source file. So I realy dont know whats wrong.

---

### Post by steeldriver on 2013-02-25
Are you sure it doesn't say 

```
missing argument [COLOR=Blue]**to** [/COLOR]`-l'
```That would indicate that you've tried to specify a library to link against, but omitted the actual library name:

```
$ cat >mytest.c <<EOF
> #include <stdio.h>
> #include <math.h>
>
> int main(void)
> {
>   double x = M_PI/4.0;
>
>   printf("sin %f = %f\n", x, sin(x));
>
>   return 0;
> }
> EOF
$ gcc -Wall -o mytest mytest.c[COLOR=Blue]** -lm**[/COLOR]
$ ./mytest
sin 0.785398 = 0.707107
$ gcc -Wall -o mytest mytest.c** [COLOR=Blue]-l[/COLOR]**
[COLOR=Blue] [/COLOR][B][COLOR=Blue]gcc: error: missing argument to `-l'[/COLOR]
[/B]$

```I don't use codeblocks, but you should find where the build options are defined and check the library / linker sections

---

### Post by lockandstrike on 2013-02-26
Thanks. It is:
> g++: error: missing argument to '-l'
But how do i specify the library name? i only know how to link

---

### Post by lockandstrike on 2013-03-02
Any help would be helpfull

---

### Post by lockandstrike on 2013-03-02
Thanks to everybody who helped but i figured out what was wrong. Now it's all working like i wanted.

---

