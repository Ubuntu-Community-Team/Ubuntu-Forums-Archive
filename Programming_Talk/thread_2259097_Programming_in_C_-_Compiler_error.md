---
title: "Programming in C - Compiler error?"
date: 2015-01-01
forum: Programming Talk
---

### Post by flaymond on 2015-01-01
Hi guys, I'm having error in my compiler that when I run this -

```

                #include <stdio.h>

                 int main(void)

                 {
                      unsigned int un = 3000000000;
 
                      printf("un = %u and not %d\n", un, un);
                      
                       getchar();

                       return 0;
                      
                    }


```

and always getting the same error -

```
||=== Build: Debug in c (compiler: GNU GCC Compiler) ===|
/home/alex/Documents/C/c/main.c||In function ‘main’: |
/home/alex/Documents/C/c/main.c|7|warning: this decimal constant is unsigned only in ISO C90 [enabled by default]|

```

Is that my code is expired for ANSII/C99 version?

Is there any workaround?

(I'm using C Primer Plus 5th edition, and I'm stuck at data types chapter)

---

### Post by spjackson on 2015-01-02
Which version of gcc are you using (gcc --version) and on which platform (uname -a)?

What compiler flags are you using?
```

gcc -o u u.c -std=c99 -Wall -pedantic -Woverflow

```
does not produce that warning for me with either gcc 4.8.2 or 4.4.3.

I would be inclined to be explicit and write 3000000000u

---

### Post by flaymond on 2015-01-02
My version is the latest..im compiling with this command -```
 make file 
```Is this the reason I can't compile?

My platform is -

```
 Linux Inter76 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:44 UTC 2014 i686 i686 i686 GNU/Linux

```

---

### Post by spjackson on 2015-01-02
> **InterProg said:**
> My version is the latest
I'm not quite sure what you mean by that. 4.9.2?
> 
```
 make file 
```Is this the reason I can't compile?

That would depend on the content of your Makefile (if any).
> 
```
 Linux Inter76 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:44 UTC 2014 i686 i686 i686 GNU/Linux

```
Aha! 32-bit. I only tried on a few 64-bit systems. I indeed get the same warning on 32-bit (gcc 4.8.2). You should use -std=c99 if that is what you are writing.
```


$ cat u.c
#include <stdio.h>

int main(void)
{
unsigned int un = 3000000000;

printf("un = %u and not %d\n", un, un);

getchar();

return 0;

}
$ gcc -o u u.c
u.c: In function ‘main’:
u.c:5:1: warning: this decimal constant is unsigned only in ISO C90 [enabled by default]
 unsigned int un = 3000000000;
 ^
$ gcc -o u u.c -std=c99
$

```
If you are using C90, then write 3000000000u.

---

### Post by flaymond on 2015-01-02
Wait what, am I using C90? (I need to read more about gcc )...I don't understand...:(


Anyway, thanks for your help! It make me learn using the book with ease and smooth.(actually I wanna give up and change to more user-friendly book, but thanks to you, don't need to do that)

and my compiling working good and again, thanks to you. I really need to buy a book about gcc and the commands.

---

### Post by ofnuts on 2015-01-03
> **InterProg said:**
> Wait what, am I using C90? (I need to read more about gcc )...I don't understand...:(

GCC supports severals levels of the C standard. The latest C standard is C99, but GCC doesn't support it fully (although I doubt the missing bits make a difference for the programs you are writing currently). So the current default is the latest fully supported C standard, C90. See the doc for the "-std" parameter in "man gcc".

---

### Post by flaymond on 2015-01-05
Actually...why 64 bit pc can compile the code (above) ?.  Is that the bit of the code is different than the bit in 32 bit pc?

---

### Post by spjackson on 2015-01-05
> **InterProg said:**
> Actually...why 64 bit pc can compile the code (above) ?.  Is that the bit of the code is different than the bit in 32 bit pc?
It's because of the C90 rules for determining the type of a numeric constant and the fact that your number fits in a long int on 64-bit but not on 32-bit.

---

### Post by flaymond on 2015-01-06
So, should I use int only or long long int?

---

### Post by spjackson on 2015-01-06
> **InterProg said:**
> So, should I use int only or long long int?
I'm afraid I don't understand the question. Could you please express that in code? As I said earlier:
> 
I would be inclined to be explicit and write 3000000000u


---

