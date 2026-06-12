---
title: "difference between extern for variables and for functions"
date: 2012-12-12
forum: Programming Talk
---

### Post by IAMTubby on 2012-12-12
Hello,
I have a couple of questions.

1. Am I right in saying that there is a difference between doing extern for variables and for functions. My point is :

When you do extern for variables, say 
```

main.c
#include <stdio.h>

int a = 5;

int main(void)
{
 fun();

 return 0;
}

support.c
#include <stdio.h>

extern int a;

extern int fun()
{
 printf("\nthis is from the supporting file");
}

build line : 
gcc *.c
./a.out

```
Here the extern line in extern int a; says that in some file in the project, the variable a has been defined, and gcc has to go and find that out.

Whereas the extern line in extern int fun(){} says that this function can be used in any other file/module in the project.

Am I right in saying this ?

2. All functions in C are extern by default, which means, they can be used in any file, once defined in any one file in the project assuming that no other storage classes are mentioned(auto, register, static), **even without a header file**
I understand that, we should still go ahead and use a header file as part of good coding standards (as we discussed in another thread : [http://ubuntuforums.org/showthread.php?t=2093269](http://ubuntuforums.org/showthread.php?t=2093269) )

Please advise.
Thanks.

---

### Post by Bachstelze on 2012-12-12
You care too much about technicalities.

---

### Post by IAMTubby on 2012-12-12
> **Bachstelze said:**
> You care too much about technicalities.
Sorry Sir, just wanted to clarify :)

---

### Post by IAMTubby on 2012-12-13
> **Bachstelze said:**
> You care too much about technicalities.
Sir, the reason I'm slightly confused is

extern int a : more like this variable **is basically defined in another file, but can be used in this file also**, gives that kind of a feeling

extern int fun(){} : more like : this function **is basically defined in this file, but can be used in another file also**

So for the same keyword the 2 meanings are quite **contradicting**, if I may say so. Sir, please forgive me, if I'm fetching it too far.

Actually, a function can be used in any other file as long as you do a #include of the header having the corresponding signature of the function(and even without doing a #include, as we discussed on another thread, but as part of good programming practice, I'll go with the header) right, which means the extern keyword **serves no point for functions.** Am I right in saying that?

Thanks :)

---

### Post by ofnuts on 2012-12-13
> **IAMTubby said:**
> Hello,
I have a couple of questions.

1. Am I right in saying that there is a difference between doing extern for variables and for functions. My point is :

When you do extern for variables, say 
```

main.c
#include <stdio.h>

int a = 5;

int main(void)
{
 fun();

 return 0;
}

support.c
#include <stdio.h>

extern int a;

extern int fun()
{
 printf("\nthis is from the supporting file");
}

build line : 
gcc *.c
./a.out

```Here the extern line in extern int a; says that in some file in the project, the variable a has been defined, and gcc has to go and find that out.

Whereas the extern line in extern int fun(){} says that this function can be used in any other file/module in the project.

Am I right in saying this ?

2. All functions in C are extern by default, which means, they can be used in any file, once defined in any one file in the project assuming that no other storage classes are mentioned(auto, register, static), **even without a header file**
I understand that, we should still go ahead and use a header file as part of good coding standards (as we discussed in another thread : [http://ubuntuforums.org/showthread.php?t=2093269](http://ubuntuforums.org/showthread.php?t=2093269) )

Please advise.
Thanks.
In C all functions are 'extern' by default. extern in a function definition serves no purpose.

Declaring the function in a header file is more than "good coding standards"... unless you consider that being able to breathe oxygen is just "good life standards".

---

### Post by IAMTubby on 2012-12-13
> **ofnuts said:**
> In C all functions are 'extern' by default. extern in a function definition serves no purpose.
ofnuts, thanks a lot for the reply. I wonder why people still use it. Probably to tell others browsing the code that this function can be used.

> 
Declaring the function in a header file is more than "good coding standards"... unless you consider that being able to breathe oxygen is just "good life standards".
Hmm, I'm confused again. We had a discussion on [http://ubuntuforums.org/showthread.php?t=2093269](http://ubuntuforums.org/showthread.php?t=2093269) where I kind of deduced that **with respect to functions alone**, code would work fine even if their signatures were not declared in header files because all functions in C are extern by default. And function declarations are added in headers only as part of better coding standards.

Thanks.
Looking forward to your advise on whether headers really are required for functions.

PS : I understand that headers are very much required in terms of variables and without it, code wouldn't compile(you won't be able to access variables defined in other files). I was only talking of functions.

---

### Post by Bachstelze on 2012-12-13
*sigh*

C99 6.2.2 §5

> **If the declaration of an identifier for a function has no storage-class specifier, its linkage is determined exactly as if it were declared with the storage-class specifier extern.** If the declaration of an identifier for an object has file scope and no storage-class specifier, its linkage is external.

This means that if you do specify a storage-class specifier, then it is no longer guaranteed to be extern:

```
firas@aoba ~ % cat func.c 
inline int sum(int a, int b)
{
    return a+b;
}

firas@aoba ~ % cat main.c 
#include <stdio.h>
#include <stdlib.h>

int sum(int, int);

int main(int argc, char **argv)
{
    int a = atoi(argv[1]);
    int b = atoi(argv[2]);
    printf("%d\n", sum(a, b));
}
firas@aoba ~ % gcc -std=c99 -pedantic -Wall -Wextra -c func.c 
firas@aoba ~ % gcc -std=c99 -pedantic -Wall -Wextra -c main.c 
main.c:6: warning: unused parameter &#8216;argc&#8217;
firas@aoba ~ % gcc -o foo main.o func.o 
Undefined symbols:
  "_sum", referenced from:
      _main in main.o
ld: symbol(s) not found
collect2: ld returned 1 exit status

```

So you add an extern declaration:

```
firas@aoba ~ % cat func.c 
inline int sum(int a, int b)
{
    return a+b;
}

extern int sum(int, int);
firas@aoba ~ % gcc -std=c99 -pedantic -Wall -Wextra -c func.c
firas@aoba ~ % gcc -o foo func.o main.o 
firas@aoba ~ % ./foo 1 2
3

```

But no one actually uses inline or other things like it, so it is mostly an irrelevant technicalty.

Headers are not required for functions. This is okay:

```
firas@aoba ~ % cat foo.c 
int printf(const char *restrict, ...);

int main(void)
{
    printf("Hello, world!\n");
}
firas@aoba ~ % gcc -std=c99 -pedantic -Wall -Wextra -o foo foo.c
firas@aoba ~ % ./foo                                            
Hello, world!

```

It is just very very stupid. This is not okay:

```
firas@aoba ~ % cat foo.c 
int main(void)
{
    printf("Hello, world!\n");
}
```

---

### Post by trent.josephsen on 2012-12-13
> **IAMTubby said:**
> extern int a : more like this variable **is basically defined in another file, but can be used in this file also**, gives that kind of a feeling

extern int fun(){} : more like : this function **is basically defined in this file, but can be used in another file also**

No, not really. **extern** just says "This identifier has external linkage."[*] It doesn't say anything about where the variable or function *to which the identifier refers* is defined.

[*] Unless another declaration for the identifier is already in scope. This lets you use **extern** to give an identifier internal linkage, in some cases. Yes, it's a bit complicated.

Function names have external linkage by default. You can give them internal linkage by using **static**, but it's redundant to apply **extern** to a function declaration. (Unless you use **inline**, which introduces its own issues.)

Variables have linkage determined by where they're declared, but probably the most common use of **extern** is to declare a variable in a header file to ensure that wherever it appears, there is already a declaration in scope so you don't introduce potential conflicts by re-declaring it in a million different places. Typically you'll put the actual *definition* in one .c file; the definition is the declaration that causes storage to be reserved, so there can be only one definition for each identifier with external linkage in the entire program.

I picked up most of my esoteric C knowledge from comp.lang.c, so if you're really interested in this level of detail I suggest going there. You can use [Google Groups](https://groups.google.com/forum/?fromgroups#!forum/comp.lang.c) if you don't have a better way to access Usenet. Browse for a while before you post, though, the group has an interesting dynamic to say the least.

---

### Post by JKyleOKC on 2012-12-13
For this kind of technical detail question, it helps immeasurably for you to become intimately familiar with the Windows program loading conventions and the different kinds of definitions required. Granted that the conventions in Linux are quite different, but those for Windows were at one time completely documented in the 5-volume "Win32 Programmer's Reference" manual from Microsoft. They cover how information in one object file is linked to that in another, and the basic requirements are the same no matter what the system just so long as it's allowable to compile separate object files and link them later into a single program.

In addition, C becomes much more mentally manageable once you've grasped the needs of down-at-the-metal assembly language programming. Many critics have called C "simply a PDP-11 assembler" and in many ways that's an accurate description of the original K&R language. Later standards have taken it a bit farther away from that simplicity, but it's still the foundation. Pointers, for instance, correspond to the "index registers" of machine-level operation.

It's very easy to become distracted by such questions, but if you want a working knowledge of the language the best way I know to get there is to pick a small project, program it, work through all the error messages, and finally debug it to a fully usable condition. You'll learn all the essentials by doing this, and the details will be less confusing and will make much more sense once you've done so. In my case, it was a text editor, followed up by a very rudimentary version of the "stdc" library written in Z80 assembler for the TRS-80. I needed such an editor at the time so I was driven to make it work without worrying about language details. Your needs are undoubtedly different but the same principle will work for you!

---

