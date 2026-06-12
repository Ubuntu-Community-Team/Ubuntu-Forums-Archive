---
title: "Where to put new liberary (new to c programming)"
date: 2008-04-07
forum: Packaging and Compiling Programs
---

### Post by fatalfurry on 2008-04-07
I have a c library cs50.h which I need to use it in some of the programs I am writing. I was wondering where would be the best place to put this. I have read on line that c libraries are located in /usr/lib and /usr/local/lib. I would like to follow best practice when it comes to using libraries just so I get used to programming in C.

---

### Post by WW on 2008-04-07
Your header file can go in /usr/local/include. (Of course, if you are the only person using your computer who will also use the library, you can put it anywhere.)  /usr/local/lib is generally used for compiled binary files.  It is usually a good idea to reserve /usr/include (and /usr/lib) for files installed by Ubuntu packages.

---

### Post by fatalfurry on 2008-04-08
I have moved the cs50.h and cs50.c files to the /usr/local/include directory. Now when I compile the program it complains about the GetInt function call. The two cs50 files I received from a Harvard cs50 course found here [http://cs50.net/index.php](http://cs50.net/index.php), If you would like me to post these i can but here is my code thus far. 

```
#include <cs50.h>
#include <stdio.h>
int
main(int argc, char * argv[])
{
    int x, y;
    /* ask user for input */
    printf("Give me an integer: ");
    x = GetInt();
    printf("Give me another integer: ");
    y = GetInt();
    /* do the math */
    printf("The sum of %d and %d is %d!\n", x, y, x + y);
}

```

My errors are 
> 
adder.c:(.text+0x1e): undefined reference to `GetInt'
adder.c:(.text+0x32): undefined reference to `GetInt'



I am used to programming with visual studio in c++. So learning the vim/gcc is very different then what I am used to but so far I like seeing the flexibility. Can you point me in the right direction.

---

### Post by WW on 2008-04-09
The header file (cs50.h) goes into /usr/local/include, but not the C source cs50.c.  Instead, you should compile cs50.c, make a library file from cs50.o, and put that in /usr/local/lib.  For example, in a temporary directory (somewhere in your home directory, say) where you have a copy of cs50.c and cs50.h:
> 
$ gcc -c cs50.c
$ ar rcs libcs50.a cs50.o
$ sudo cp libcs50.a /usr/local/lib

Now to compile and link adder.c, these commands should work:
> 
$ gcc adder.c -I/usr/local/include -L/usr/local/lib -lcs50  -o adder

This should create the executable called adder, which you can run like this:
> 
$ ./adder

The option **-I/usr/local/include** tells gcc to also look in /usr/local/include for header files.  The option **-L/usr/local/lib** tells gcc (in the linking phase) to also look for libraries in /usr/local/lib, and the option **-lcs50** tells gcc which libraries you need.


*Alternatively*, you could simply keep a copy of cs50.c and cs50.h with each project (i.e. have cs50.h, cs50.c and adder.c all in the same directory, somewhere in your home direcotry).  Change the **#include** directive in adder.c to **#include "cs50.h"**, and compile with these commands:
> 
$ gcc -c cs50.c     # Do this once
$ gcc adder.c cs50.o -o adder   #  Do this whenever you change adder.c


---

### Post by fatalfurry on 2008-04-14
thanks for the great advice so far. my last question is with one of the methods in the library. It gets a long long from the user


```
long long
GetLongLong()
{
    char c;
    long long n;
    string line;

    /* try to get a long long from user */
    while (TRUE)
    {
        /* get line of text, returning LLONG_MAX on failure */
        line = GetString();
        if (line == NULL)
            return LLONG_MAX;

        /* return long long equivalent to text if possible */
        if (sscanf(line, " %lld %c", &n, &c) == 1)
        {
            free(line);
            return n;
        }
        else
        {
            free(line);
            printf("Retry: ");
        }
    }
}
```

when I compile it now it complains about LLONG_MAX being undeclared. I have researched a little online and had to compile the c file in c99 mode (-std=c99). I was wondering where I could find more information about this. I haven't found anything online as of yet. 

oh and now everything works great. thanks for your help again.

---

### Post by fnjordy on 2008-04-17
> **fatalfurry said:**
> when I compile it now it complains about LLONG_MAX being undeclared. I have researched a little online and had to compile the c file in c99 mode (-std=c99). I was wondering where I could find more information about this.

Check out /usr/include/limits.h:
```
#  ifdef __USE_ISOC99

/* Minimum and maximum values a `signed long long int' can hold.  */
#   define LLONG_MAX    9223372036854775807LL
#   define LLONG_MIN    (-LLONG_MAX - 1LL)

/* Maximum value an `unsigned long long int' can hold.  (Minimum is 0.)  */
#   define ULLONG_MAX   18446744073709551615ULL

#  endif /* ISO C99 */
```

---

### Post by kyriacos on 2008-04-23
Hi fatalfurry,

I'm trying to follow Malan's excellent lecture videos but I can't seem to find the cs50 library anywhere. The link under [http://cs50.net/software/](http://cs50.net/software/) seems to be dead. 
If you know an alternate download location or if you could e-mail them to me i'd very much appreciate it.

Thanks

Kyri

---

### Post by rgirish28 on 2008-05-03
> **fatalfurry said:**
> I have a c library cs50.h which I need to use it in some of the programs I am writing. I was wondering where would be the best place to put this. I have read on line that c libraries are located in /usr/lib and /usr/local/lib. I would like to follow best practice when it comes to using libraries just so I get used to programming in C.

I am sorry to be troubling you, but are you a cs50 student if you are or if u are not, do you have all the files of the 2007 session of the cs50 course.I am a student from India who is doing the course thanks to the great podcasts on offer.I would be much obliged if u could give me the files or tell me how to get hold of the files since i want to do the problem sets in the course either by mail or by posting a reply.
Thank you!

---

### Post by tressajayne on 2008-05-05
To kyriacos and rgirish28:

I think that Malan is currently revising cs50.net for the 2008-2009 school year, but the link [http://cs50.net/software/]("http://cs50.net/software/") should still work (CS50's freeware library is on this page under **Libraries**).


Just in case, I've attached cs50.c and cs50.h (current as of today).

Have fun!

---

### Post by tressajayne on 2008-05-05
Oh, and rgirish28, email me at *tullis at fas dot harvard dot edu* if you'd like copies of the 2007 problem sets (they're a bit large to upload to this forum).

---

### Post by rgirish28 on 2008-05-12
Thank you tressajayne, please expect a mail from rgirish28 at gmail dot com

---

### Post by rgirish28 on 2008-05-12
> **tressajayne said:**
> Oh, and rgirish28, email me at *tullis at fas dot harvard dot edu* if you'd like copies of the 2007 problem sets (they're a bit large to upload to this forum).

Thank you, I have sent the mail..

---

### Post by ciclistadan on 2008-08-16
thanks for the help WW, i've been trying to get that done for a while and truely appreciate your willingness to help out someone trying to learn some programming skills.

---

### Post by StOoZ on 2008-08-18
> **WW said:**
> The header file (cs50.h) goes into /usr/local/include, but not the C source cs50.c.  Instead, you should compile cs50.c, make a library file from cs50.o, and put that in /usr/local/lib.  For example, in a temporary directory (somewhere in your home directory, say) where you have a copy of cs50.c and cs50.h:

Now to compile and link adder.c, these commands should work:

This should create the executable called adder, which you can run like this:

The option **-I/usr/local/include** tells gcc to also look in /usr/local/include for header files.  The option **-L/usr/local/lib** tells gcc (in the linking phase) to also look for libraries in /usr/local/lib, and the option **-lcs50** tells gcc which libraries you need.


*Alternatively*, you could simply keep a copy of cs50.c and cs50.h with each project (i.e. have cs50.h, cs50.c and adder.c all in the same directory, somewhere in your home direcotry).  Change the **#include** directive in adder.c to **#include "cs50.h"**, and compile with these commands:


goog explanation , but , what does this do : 
> ar rcs libcs50.a cs50.o
?

---

### Post by Hoppiesbox on 2009-04-05
> **fatalfurry said:**
> 
when I compile it now it complains about LLONG_MAX being undeclared. I have researched a little online and had to compile the c file in c99 mode (-std=c99). 

This tidbit is very useful ;)

---

### Post by student101 on 2009-04-15
I too am going through Malan's course online. I too am struggling to get the CS50 library working.

What if you're using Windows and say Dev-C++ ?  Can someone list the steps for incorporating the the CS50 library ? I have tried everything and I still get the "Undefined reference to getInt"

I would greatly appreciate a step by step procedure to get the CS50 library working with Dev-C++ on Windows (Vista). I don't even know where/how I would type in these commands that people have posted. 

Thank you kindly

---

### Post by student101 on 2009-04-15
Ah! I figured it out. I will post here for posterity... here's what I did...

1. uploaded cs50.c and cs50.h to my web server via FTP
2. Compiled via SSH (using a program called Putty) with:

$ gcc -c -ggdb -std=c99 cs50.c -o cs50.o
$ ar rcs libcs50.a cs50.o
$ rm -f cs50.o

3. Downloaded the resulting cs50.a file as a binary to my PC (i compiled on my web host's Linux web server because I could not get dev-c++ to compile the cs50.c file--I kept getting an error "no resources")

4. In Dev-C++ I created a project and added all three files to it (cs50.h, cs50.c, and cs50.a)

Anyways, feel free to email me direct for help if you're a noob like me and need help setting up for CS50. 

Thanks!

---

### Post by malan on 2010-05-11
Many thanks for the interest in CS50 expressed in this thread.  Apologies for such a belated reply; I'm afraid Google just informed me of this thread.  For those who may still be subscribed, though, I thought I'd follow up to let you know that we recently released a CS50 Appliance that's intended to make all these headaches go away:

[http://wiki.cs50.net/Appliance](http://wiki.cs50.net/Appliance)

It's actually based on Ubuntu JeOS, so folks in this forum may already be familiar with the distribution.  With this appliance can you tackle all of Fall 2009's problem sets ([http://cs50.tv/2009/fall#l=psets](http://cs50.tv/2009/fall#l=psets)) without having to figure out how to configure your own machine with GCC, etc.  Alternatively, you can infer from the appliance's instructions how to configure your own machine, if you prefer.

Please feel free to subscribe to the course's Google Group ([http://cs50.tv/2009/fall/#r=group](http://cs50.tv/2009/fall/#r=group)) if you'd like to chat with others who've been tackling the psets.

djm

---

