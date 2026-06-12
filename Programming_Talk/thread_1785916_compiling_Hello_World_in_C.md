---
title: "compiling Hello World in C"
date: 2011-06-18
forum: Programming Talk
---

### Post by Coach McGurk on 2011-06-18
I would like to get some C and C++ going on Ubuntu 11. I've been trying for a few hours to get Hello World going in C. I have some programming experience in Java and PHP but not C or C++.

```
#include < stdio.h>

void main()
{
    printf("\nHello World\n");
}
```I get this error: 
stdio.h: No such file or directory
compilation terminated.

After googling I tried sudo apt-get install build-essentials with no change. Do I need to put my source file in a specific directory?

p.s.
When running locate stdio.h i get:
/usr/include/stdio.h
/usr/include/bits/stdio.h
/usr/lib/perl/5.10.1/CORE/nostdio.h
/usr/lib/syslinux/com32/include/stdio.h

---

### Post by zobayer1 on 2011-06-18
> **Coach McGurk said:**
> I would like to get some C and C++ going on Ubuntu 11. I've been trying for a few hours to get Hello World going in C. I have some programming experience in Java and PHP but not C or C++.

```
#include < stdio.h>

void main()
{
    printf("\nHello World\n");
}
```I get this error: 
stdio.h: No such file or directory
compilation terminated.

After googling I tried sudo apt-get install build-essentials with no change. Do I need to put my source file in a specific directory?

It should be:
```

#include <stdio.h>

``` You were giving extra space. Hope it helps.

---

### Post by Coach McGurk on 2011-06-18
zobayer1 you are awsome!!
Thanks so much

---

### Post by cgroza on 2011-06-18
And I think main should return an int.

---

### Post by zobayer1 on 2011-06-18
You are always welcome.

When your problem is solved, you can mark your thread 'SOLVED'. You will get that option from 'thread tools' just above the first post in this page.

---

### Post by Coach McGurk on 2011-06-18
> **cgroza said:**
> And I think main should return an int.

Is having it void a bad idea? I copy pasted it from a tutorial I can't find now.

---

### Post by zobayer1 on 2011-06-18
> **cgroza said:**
> And I think main should return an int.
That's indeed a good practice, but gcc won't cause trouble with it. But a must for g++.

---

### Post by cgroza on 2011-06-18
> **Coach McGurk said:**
> Is having it void a bad idea? I copy pasted it from a tutorial I can't find now.

The OS expects a program exit code. It is a good practice anyway.

---

### Post by nvteighen on 2011-06-19
About main:

I'm not sure whether "void main()" is a pre-standard fossile or just a non-standard extension someone invented. But what is sure is that the C Standard defined three signatures for main, which are exactly these:

```

int main(void); /* Not int main() */
int main(int argc, char **argv);
int main(int argc, char **argv, char **envp); 

```

The two first are the most used ones: the first is the default and the second gives access to command line arguments. The third allows access to environment variables, but it's a bit useless in GNU/Linux systems: getenv.h is much better.

Be aware that *int main()* is not *int main(void)*. In C, *type f()* means that function *f* returns a value of type *type* and accepts an arbitrary number of arguments (which will be ignored, as you're not creating any variable to store those values). This prevents the compiler to check arguments for that function.

It is in **C++** where *type f()* = *type f(void)*. Therefore, in C++ there's a "fourth" signature for main, which is *int main()*, but equivalent to *int main(void)*.

I know gcc is quite permissive with this, but IMO, one should write things correctly.

---

### Post by Arndt on 2011-06-19
> **nvteighen said:**
> About main:

I'm not sure whether "void main()" is a pre-standard fossile or just a non-standard extension someone invented. But what is sure is that the C Standard defined three signatures for main, which are exactly these:

```

int main(void); /* Not int main() */
int main(int argc, char **argv);
int main(int argc, char **argv, char **envp); 

```

The two first are the most used ones: the first is the default and the second gives access to command line arguments. The third allows access to environment variables, but it's a bit useless in GNU/Linux systems: getenv.h is much better.

Be aware that *int main()* is not *int main(void)*. In C, *type f()* means that function *f* returns a value of type *type* and accepts an arbitrary number of arguments (which will be ignored, as you're not creating any variable to store those values). This prevents the compiler to check arguments for that function.

It is in **C++** where *type f()* = *type f(void)*. Therefore, in C++ there's a "fourth" signature for main, which is *int main()*, but equivalent to *int main(void)*.

I know gcc is quite permissive with this, but IMO, one should write things correctly.

In C, main() was the same as main(void) in the fossile period, though, because at one time, the keyword "void" didn't exist.

---

### Post by JupiterV2 on 2011-06-19
> **nvteighen said:**
> About main:

I'm not sure whether "void main()" is a pre-standard fossile or just a non-standard extension someone invented. But what is sure is that the C Standard defined three signatures for main, which are exactly these:

```

int main(void); /* Not int main() */
int main(int argc, char **argv);
int main(int argc, char **argv, char **envp); 

```I know gcc is quite permissive with this, but IMO, one should write things correctly.

Use the gcc flag -Wstrict-prototypes to turn on a warning when you don't properly prototype a function. For functions which don't accept an argument, you must explicitly use 'void' for a function parameter, as in: int main (**void**) {...}

Also, the -Wall flag will issue a warning you if main() returns void. At a minimum, you should always compile your programs with -Wall:
```
gcc -Wall my_program.c
```

---

### Post by nvteighen on 2011-06-19
> **JupiterV2 said:**
> Use the gcc flag -Wstrict-prototypes to turn on a warning when you don't properly prototype a function. For functions which don't accept an argument, you must explicitly use 'void' for a function parameter, as in: int main (**void**) {...}

Also, the -Wall flag will issue a warning you if main() returns void. At a minimum, you should always compile your programs with -Wall:
```
gcc -Wall my_program.c
```

Uh, thanks for clarifying this for the OP... When I said that gcc is permissive, my intention was to refer to gcc's default behaivor :P

---

