---
title: "Compiling/Running C Programs?"
date: 2005-04-25
forum: Programming Talk
---

### Post by Loft on 2005-04-25
Okay , after deciding to take the plunge and learn C/C++, I installed the build essential packages.  After looking at a few tutorials, I create first.c in gedit and put in the following code:
```
#include <stdio.h>

int main() 
{
  printf("Hello, world\n");
  return 0;
}
``` 

Then I used 'gcc -o first first.c'  This created the executable first.  Now according to the tutorial I read ([http://farside.ph.utexas.edu/teaching/329/lectures/node35.html](http://farside.ph.utexas.edu/teaching/329/lectures/node35.html)) I have to enter first into the terminal and it should run.  However, it doesn't, I just get a '$ bash: first: command not found' error.  How can I run my programs after compiling and linking?  Or am I compiling/linking properly in the first place?  Thanks.

---

### Post by lorap on 2005-04-25
hi friend!
it'd run :-)
you just have to write:
./first

dot then slash

you work this way,firstly compile the code:

cc -c first.c

that would produce an object file you may need to add to the library.

then create an executable:

cc -o first first.c

after what run it:

./first


have a nice day!
pavel

---

### Post by Loft on 2005-04-25
Thanks! I knew it would be something simple!  ](*,)

---

### Post by rmjokers on 2005-04-25
Just a note:

The reason you have to add the "./" to the filename is because your current working directory is not included in your path.  The "./" means run the executable file first from the current directory.  Excluding the current directory from the path is common on unix systems to prevent certain security problems.

---

### Post by Johnhatton09 on 2006-08-20
I dont know what to do when i put in "GCC -o hello.c" but it says "bash: gcc: command not found" What do I do?

---

### Post by gerbman on 2006-08-20
> **Johnhatton09 said:**
> I dont know what to do when i put in "GCC -o hello.c" but it says "bash: gcc: command not found" What do I do?Install the 'build-essential' package.

---

### Post by X.Cyclop on 2006-08-20
```
sudo apt-get install build-essential
```
;)

---

### Post by bukwirm on 2006-08-21
gcc has to be lowercase.

---

### Post by coolyog on 2007-09-12
i tried the same program but it gavve the following erroe
#include <stdio.h>

int main() 
{
  printf("Hello, world\n");
  return 0;
}
 error: stdio.h: No such file or directory
first.c: In function ‘main’:
first.c:6: warning: incompatible implicit declaration of built-in function ‘printf’

---

### Post by gnusci on 2007-09-12
> **coolyog said:**
> i tried the same program but it gavve the following erroe
#include <stdio.h>

int main() 
{
  printf("Hello, world\n");
  return 0;
}
 error: stdio.h: No such file or directory
first.c: In function ‘main’:
first.c:6: warning: incompatible implicit declaration of built-in function ‘printf’

Did you try first?, if not, open a terminal and type:

**> sudo apt-get install build-essential**

after that youll be able to do:

**> gcc first.c -o first**

and then:

**>./first**

---

### Post by coolyog on 2007-09-12
it says cudnt find package

---

### Post by fct on 2007-09-12
Make sure you have added the universe and multiverse repositories.

Here is the information:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by LaRoza on 2007-09-12
> **coolyog said:**
> it says cudnt find package

It is also on the CD.

---

### Post by debasish_deka on 2007-12-24
Hi,
I too tried the _sudo apt -get install build-essential_
but *it gave the following error message*...
_[COLOR="Red"]sudo: apt: command not found[/COLOR]_
I am not getting what to do next...
kindly help me...
Regards,
Debasish

---

### Post by adityakavoor on 2007-12-24
no space there

```
sudo apt-get install build-essential
```

---

### Post by linjava on 2007-12-25
So typing gcc -v at the command line doesn't give any output? For example something like:

```

> gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)


```
I thought that gcc was installed by default but maybe not. If the sudo apt-get...is throwing you off (you may have to set up universe and some other things) you could also try the gui (I'm on kubuntu and that uses adept manager and I'm not sure if ubuntu uses something different). The build essential sounds like it will give you everything you need in one shot, but if you do decide to use a gui manager, just make sure you grab all of the gcc stuff like: gcc, gdb, as/gas, and anything that has these names - I believe the manager will tell you what dependencies there are so unless you're hard up for disk space install all dependencies with gcc library. I believe ld stuff (the linker that links your objects into an executable) will be in there too, but make sure. Also, make sure you have the man pages for looking up functions and such - I believe these are something like manpages-dev posix-dev. That way you can do man printf for example and read about the printf function (this wasn't installed automatically on my system) Of course the suggestion to do the build essential might be easier if you can get it to work...just an alternative. Which ever route you go remember to try boiler-plate commands out to make sure you have everything intalled: gcc -v...ld -v...gdb...as (assembly you really don't need this)...man <some_function> or man 3 <c_function>(like sqrt for math)...ar for archiving if you want to create libraries. I believe this is the bare-bones stuff you'll need to get up and running with c programs.

---

### Post by seren6ipity on 2008-11-11
Thank you all. This information worked for me too.
I had all the installs already. This is how I understand the commands given here - 

gcc pgmname.c -o pgmname <-- compiles program pgmname and overrides any previous load module for the program

./pgmname <-- will run the program from current directory

---

### Post by oponto on 2009-11-13
```
#include <stdio.h>

int main(void) {
   int a, b, ergo;
   printf("one side: ");
   scanf("%d\n",&a);
   printf("another side: ");  
   scanf("%d\n",&b);
   ergo = a * b²;
   printf("result area:%d\n",ergo);
   return 0;
}
```

```
gcc -o output math.c
```

results in:

```

/home/math.c:9: error: stray &#8216;\302&#8217; in program
/home/math.c:9: error: stray &#8216;\262&#8217; in program

```

I guess gcc is missing sth., or stdio got corrupted ?
Read about the """" layout error for 302, however, this should be the proper """" ^^

---

### Post by Arndt on 2009-11-13
> **oponto said:**
> ```
#include <stdio.h>

int main(void) {
   int a, b, ergo;
   printf("one side: ");
   scanf("%d\n",&a);
   printf("another side: ");  
   scanf("%d\n",&b);
   ergo = a * b²;
   printf("result area:%d\n",ergo);
   return 0;
}
```

```
gcc -o output math.c
```

results in:

```

/home/math.c:9: error: stray ‘\302’ in program
/home/math.c:9: error: stray ‘\262’ in program

```

I guess gcc is missing sth., or stdio got corrupted ?
Read about the """" layout error for 302, however, this should be the proper """" ^^

Your source code is corrupted. Don't you see the extra ² thing on line 9?

---

### Post by oponto on 2009-11-13
thanku!

now another program for my first compiles:

```
./output
```

```
one side: 2

2
another side: 2

```

means i have to type anything+enter before the program continues- correctly, actually !

---

### Post by HarrisonNapper on 2009-11-13
Why is "void" required in int main(void)? Couldn't you just do int main();? I'm pretty sure main doesn't require arguments. Any explanation of the difference would be useful, as I am a nub.

---

### Post by slavik on 2009-11-14
Everyone:

Read this: [http://www.amazon.com/Programming-Language-2nd-Brian-Kernighan/dp/0131103628/ref=sr_1_5?ie=UTF8&s=books&qid=1258177409&sr=8-5](http://www.amazon.com/Programming-Language-2nd-Brian-Kernighan/dp/0131103628/ref=sr_1_5?ie=UTF8&s=books&qid=1258177409&sr=8-5)

It will explain everything.

---

### Post by nvteighen on 2009-11-14
> **HarrisonNapper said:**
> Why is "void" required in int main(void)? Couldn't you just do int main();? I'm pretty sure main doesn't require arguments. Any explanation of the difference would be useful, as I am a nub.

There's a difference between blah() and blah(void), though it doesn't affect main. () means an indeterminate number of arguments of any type and (void) means exactly no arguments. This is a critical issue when using function pointers, though as you'll see, it means no harm in other contexts.

```

#include <stdio.h>

int sum(int a, int b)
{
    return a + b;
}

int substract(int a, int b)
{
    return a - b;
}

int sum3(int a, int b, int c)
{
    return a + b + c;
}

int main(void)
{

    /* When declaring a function pointer, you have to by stating its return and
     * argument types. Afterwards, as with any other C variable, you can't
     * change its type. */
    int (*restricted)(int, int) = sum;
    printf("%d\n", (*restricted)(5, 7));

    /* This is possible because substract has the same interface as sum (int,
     * int)->int. */
    restricted = substract;
    printf("%d\n", (*restricted)(7, 9));

    /* This is impossible. Uncommenting this will yield a compiler error:
     *
     * restricted = sum3;
     * printf("%d\n", (*restricted)(8, 9, 0)); */

    /* To solve this, we can use a function pointer that uses an indeterminate
     * parameter list. Only the return type will now be the restriction. */
    int (*free)() = sum;
    printf("%d\n", (*free)(6, 8));

    free = substract;
    printf("%d\n", (*free)(9, 8));

    free = sum3;
    printf("%d\n", (*free)(5, 67, 9));

    return 0;
}

```

I prefer to use int main(void) to be more explicit in my code, because the equivalence of meaning of int main() and int main(void) is produced just because of the context and not because of what the line means itself.

---

### Post by oponto on 2009-11-14
damn I failed,

```
return 0;
```

was reuqired for sure

---

### Post by HarrisonNapper on 2009-11-14
> **nvteighen said:**
> There's a difference between blah() and blah(void), though it doesn't affect main. () means an indeterminate number of arguments of any type and (void) means exactly no arguments. This is a critical issue when using function pointers, though as you'll see, it means no harm in other contexts.

```

#include <stdio.h>

int sum(int a, int b)
{
    return a + b;
}

int substract(int a, int b)
{
    return a - b;
}

int sum3(int a, int b, int c)
{
    return a + b + c;
}

int main(void)
{

    /* When declaring a function pointer, you have to by stating its return and
     * argument types. Afterwards, as with any other C variable, you can't
     * change its type. */
    int (*restricted)(int, int) = sum;
    printf("%d\n", (*restricted)(5, 7));

    /* This is possible because substract has the same interface as sum (int,
     * int)->int. */
    restricted = substract;
    printf("%d\n", (*restricted)(7, 9));

    /* This is impossible. Uncommenting this will yield a compiler error:
     *
     * restricted = sum3;
     * printf("%d\n", (*restricted)(8, 9, 0)); */

    /* To solve this, we can use a function pointer that uses an indeterminate
     * parameter list. Only the return type will now be the restriction. */
    int (*free)() = sum;
    printf("%d\n", (*free)(6, 8));

    free = substract;
    printf("%d\n", (*free)(9, 8));

    free = sum3;
    printf("%d\n", (*free)(5, 67, 9));

    return 0;
}

```I prefer to use int main(void) to be more explicit in my code, because the equivalence of meaning of int main() and int main(void) is produced just because of the context and not because of what the line means itself.

Excellent explanation. Thank you.

---

### Post by Arndt on 2009-11-14
> **HarrisonNapper said:**
> Excellent explanation. Thank you.

I usually write int main(int argc, char **argv) from the start, since a program which takes no command line arguments/options is very rare in my experience.

---

### Post by king_009 on 2009-12-14
Thanks Guys!!!!
After a long headBangs of 3 hours on ubuntu, i was able to run my simple "Hello World" C++ program!!!

I just got a lesson.. its not so easy as of windows but actually exciting than windows!!!
i liked ubuntu so much that this time's my college project will be made on ubuntu's C++

feeling like won a battle by running hello world program!!! hahaha...:) ;)

good day guys!!!
Akshit

---

### Post by enzo_ven_arg on 2009-12-28
Hi, I'm making programs in C, using code blocks, and I constantly have to open terminal gcc main.c then ./a.out to try my program and change stuff. Is there any other way in which i can avoid all this clicking, so I just have to click on build and run at it executes the program automatically like in windows? Maybe a script, something? Thanks.

---

