---
title: "gcc not compling?"
date: 2007-06-06
forum: Programming Talk
---

### Post by mumble02 on 2007-06-06
I have gcc installed, but what all packages need to be installed with it? I ask because I tried to program a simple 'hello world' program, and when I went to compile it, it did nothing. So I was wondering if I didn't have all the installation packages that are required. I'm learning to programming in the language C.

here's what the 'hello world' stuff looks like when I try to compile:

source code:
> #include <stdio.h>

main()
{
    printf("Hello, World!");
}

Terminal:
> $gcc helloworld.c (I press enter)
               $

I got the programming code from a book called "Teach Yourself C In 21 Days" by Peter Aitken & Bradley Jones.

Oh, and if it matters, I used gedit.

So any help would be appreciated!:-)
P.S. I also know very little about Linux, and for that matter Ubuntu Linux. :-P

---

### Post by the_darkside_986 on 2007-06-06
Maybe it did do something. A lot of unix commands are quiet and don't spit out a bunch of text unless you tell it to. Type the command ls to see if something got added to the current directory like a hello.o or something.

EDIT: Now I remember what happens when you type it like that. You should get a file called "a.out" in the same directory as helloworld.c. This is the default name of the executable. If you want to call your program something like "helloworld" then you should type the two commands:
```

gcc -c helloworld.c
gcc helloworld.o -o helloworld

```
Now you can run the program by typing
```

./helloworld

```
In Unix-like environments, you have to specify the ./ if you want to run something in the current directory. This is for security reasons.

---

### Post by mumble02 on 2007-06-06
ahh that worked!:-)

Thanks a bunch! Now maybe I can start learning the more complicated things in C programming.;-)

---

### Post by enopepsoo on 2007-06-06
Usually you use the .o extension for examples like these!  Don't ask why.:p

Have fun programming.  I bet you'll be submitting kernel patches in no time!

---

