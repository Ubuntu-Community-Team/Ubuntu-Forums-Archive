---
title: "[SOLVED] Making a C program with multiple files"
date: 2008-05-29
forum: Packaging and Compiling Programs
---

### Post by Majiq on 2008-05-29
Hello friends,

I'm trying to delve into the world of programming, and I created a program and I can't quite get it to compile when I split it into separate files. Not wanting to actually put up hundreds of lines of code, I've modelled the error.

file.h
```

#ifndef O_M_G_IT_S_SO_
#define O_M_G_IT_S_SO_
#include <stdio.h>
const char phrase[]="Hello World";
#endif

```

a.c
```

#include "file.h"

int main()
{
  char newphrase[30];

  printf("Orginal stream: %s", phrase);

  generator(newphrase, phrase);

  printf("New stream: %s", newphrase);

  return 0;
}

```

b.c
```

  #include "file.h"

void generator(char newPhrase[], const char phrase[])
{
  int i;
  for(i = 0; i < 11; i++)
    newPhrase[i] = phrase[i]+1;
}

```

and I compile
```

majiq@Hero:/tmp$ gcc a.c -c
majiq@Hero:/tmp$ gcc b.c -c
majiq@Hero:/tmp$ gcc a.o b.o -o product
b.o:(.rodata+0x0): multiple definition of `phrase'
a.o:(.rodata+0x0): first defined here
collect2: ld returned 1 exit status

```

I thought the #ifndef would keep it from duplicating the definitions. What should I do? And before you ask, yes, I need to have the global constants because they're used all over my program.

---

### Post by LaRoza on 2008-05-29
> **Majiq said:**
> 
I thought the #ifndef would keep it from duplicating the definitions. What should I do? And before you ask, yes, I need to have the global constants because they're used all over my program.

That isn't the proper use of headers. 

You don't include code that like. Look up "extern"

---

### Post by Vhann on 2008-05-29
First off, you didn't declare the prototype for function generator.

Also, including a header (stdio.h) in a header (file.h) isn't very proper imo (although it works). 

Third, the only accepted synthax of main() are 'int main( void )' and 'int main( int argc, char* argv[] )'

Anyway, your main problem comes from your global variable. You don't need it declared as a global (declare it in main()) since you are passing it as a parameter to function. Just declare your global variable in main() and it'll work.

P.S.: If you want a fully ISO C90/ANSI compatible C code, you should compile with these options (that's how I do): gcc -Wall -pedantic -ansi {files.c} [ -o nameOfTheExecutable]

---

### Post by Majiq on 2008-05-29
> **Vhann said:**
> First off, you didn't declare the prototype for function generator.

Also, including a header (stdio.h) in a header (file.h) isn't very proper imo (although it works). 

Third, the only accepted synthax of main() are 'int main( void )' and 'int main( int argc, char* argv[] )'

Anyway, your main problem comes from your global variable. You don't need it declared as a global (declare it in main()) since you are passing it as a parameter to function. Just declare your global variable in main() and it'll work.

P.S.: If you want a fully ISO C90/ANSI compatible C code, you should compile with these options (that's how I do): gcc -Wall -pedantic -ansi {files.c} [ -o nameOfTheExecutable]

Thanks Vhann, but like I said, I was just modeling the error. That's why it's only used in one of the files. In reality, at the least, I need to use three constants through four files which indicate array sizes, and I really hate having to pass length arguments for things that stay the same the whole program. 

Before I respond to your points (all of which are helpful, thanks) let me just say that I'm coming to C after learning on C++. For your points: 1) I was told C didn't have prototypes, 2) what do you do if you need the same library in two different files, for example stdio.h? 3) I was taught in C++ starting out that main() was acceptable, but my professor a) only coded academically and b) never coded after C went ANSI.

Long story short, I was taught lazy-style off C++ and never learned C properly.

---

### Post by Majiq on 2008-05-29
> **LaRoza said:**
> That isn't the proper use of headers. 

You don't include code that like. Look up "extern"

First off, thanks for the pointer in the right direction.

EDIT: Stupid, unhelpful rant removed.

---

### Post by LaRoza on 2008-05-29
> **Majiq said:**
> 
Maybe it's been a long day, maybe something's happened and you're edgy, maybe you thought it was just the right response. Just please try regardless of mood to not be abrasive because we lose enough people over compiling problems.

It was the right response. If it wasn't explicit enough, I would have gladly given more information if prompted.

(Note, I am ignoring the lecture...)

---

### Post by Majiq on 2008-05-29
> **LaRoza said:**
> It was the right response. If it wasn't explicit enough, I would have gladly given more information if prompted.

(Note, I am ignoring the lecture...)

I expected you would. It's more of a rant after spending about three hours on this one issue. Quite aggravated. And I'm not understanding extern, insofar as arrays and structs are concerned. Care to explain?

---

### Post by Majiq on 2008-05-29
> **LaRoza said:**
> It was the right response. If it wasn't explicit enough, I would have gladly given more information if prompted.

(Note, I am ignoring the lecture...)
Also, what is the right way to use a header. Say, for example, that I wanted a struct to be available in multiple files. I imagine that is a good use for a header file, no? How should I do it?

---

### Post by LaRoza on 2008-05-29
> **Majiq said:**
> Also, what is the right way to use a header. Say, for example, that I wanted a struct to be available in multiple files. I imagine that is a good use for a header file, no? How should I do it?

A header holds the declarations and macro definitions. It shouldn't hold C code. For example, stdio.h just has macros and function declarations of various functions.

```

cat /usr/include/stdio.h

```

You should have the globals defined in the source file (if you really need to use globals) and use extern to use that variable elsewhere. [http://en.wikipedia.org/wiki/External_variable](http://en.wikipedia.org/wiki/External_variable)

---

### Post by Vhann on 2008-05-29
> **Majiq said:**
> Thanks Vhann, but like I said, I was just modeling the error. That's why it's only used in one of the files. In reality, at the least, I need to use three constants through four files which indicate array sizes, and I really hate having to pass length arguments for things that stay the same the whole program. 

Before I respond to your points (all of which are helpful, thanks) let me just say that I'm coming to C after learning on C++. For your points: 1) I was told C didn't have prototypes, 2) what do you do if you need the same library in two different files, for example stdio.h? 3) I was taught in C++ starting out that main() was acceptable, but my professor a) only coded academically and b) never coded after C went ANSI.

Long story short, I was taught lazy-style off C++ and never learned C properly.
The proper way to define array sizes in C is through macros not via constant

for example, you could declare this macro in a file macros.h (or file.h or whatever).

#define SIZE_OF_ARRAY 15

which you could use like this:

char array[SIZE_OF_ARRAY]={0};

macros are, at compile-time, replaced by their value in code (in fact, this is done before compiling since it's done by the preprocessor).

Global variables should generally be avoided either by replacing them by a variable passed as a parameter (pointer or not) or using macros.

I think the english word used to describe the problems generated by globals is "side-effects".

"1) I was told C didn't have prototypes,"
In fact, if the function body (the function itself) is declared before main(), there is no need for prototypes. Although, this is mostly used to restrict access to certain functions in a library for example. Generally speaking, you'll always specify prototypes.

"2) what do you do if you need the same library in two different files, for example stdio.h?"
I include it directly in each file that needs it. I usually have around 10 "#include" type lines at the beginning of each of my source code file (and that's probably nothing compared to bigger projects).

Regards,
Vhann.

---

### Post by lisati on 2008-05-29
> **Majiq said:**
> Hello friends,

I'm trying to delve into the world of programming, and I created a program and I can't quite get it to compile when I split it into separate files. Not wanting to actually put up hundreds of lines of code, I've modelled the error.

file.h
```

#ifndef O_M_G_IT_S_SO_
#define O_M_G_IT_S_SO_
#include <stdio.h>
const char phrase[]="Hello World";
#endif

```

a.c
```

#include "file.h"

int main()
{
  char newphrase[30];

  printf("Orginal stream: %s", phrase);

  generator(newphrase, phrase);

  printf("New stream: %s", newphrase);

  return 0;
}

```

b.c
```

  #include "file.h"

void generator(char newPhrase[], const char phrase[])
{
  int i;
  for(i = 0; i < 11; i++)
    newPhrase[i] = phrase[i]+1;
}

```

and I compile
```

majiq@Hero:/tmp$ gcc a.c -c
majiq@Hero:/tmp$ gcc b.c -c
majiq@Hero:/tmp$ gcc a.o b.o -o product
b.o:(.rodata+0x0): multiple definition of `phrase'
a.o:(.rodata+0x0): first defined here
collect2: ld returned 1 exit status

```

I thought the #ifndef would keep it from duplicating the definitions. What should I do? And before you ask, yes, I need to have the global constants because they're used all over my program.

I think that part of the problem is that the compiler won't remember the definition of O_M_G_IT_S_SO_ in file a.c when it comes to b.c unless you are able to do something like
```

gcc a.c b.c

```
(i.e. compile the C files all in one go like you can with Turbo C under DOS or Windows command prompt)

---

### Post by Vhann on 2008-05-30
For sure, you have to compile all your files in a single shot (otherwise you'll have to link the .o together or so). Anyway, the very problem is the fact that the global has name phrase and that a function parameter has name phrase. They are in conflit in the function body because when you write "phrase" in that function body, the compiler doesn't know if you're refering to the global or to the parameter (although here they are the same).

That's one of the reasons why globals should be avoided and are not needed here: if you can pass them via parameters, global are not needed.

Regards,
Vhann.

---

