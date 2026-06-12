---
title: "What is a C header file?"
date: 2008-11-24
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-24
I have tried looking for C header file explanation, but haven't found any.

I also have a good book about C, but it didn't have almost anything about header files.

So what is a header file and how can I make one and I need a simple example.

Thanks.

---

### Post by dwhitney67 on 2008-11-24
Look in /usr/include.  There are many examples of header files in that directory.

---

### Post by monkeyking on 2008-11-24
Have you checked wikipedia [http://en.wikipedia.org/wiki/Header_file](http://en.wikipedia.org/wiki/Header_file)

Headerfiles contains prototypes, interface or whatever you want to call them.

Header files are quite handy if you have a large program that is seperated into many different files that you link together.

say you have a function that calculates a value.
you have another function that optimzes this function.
But you want to run the optimization some times you're sure it's the best optimized value.

You can put everything in one file.

[PHP]
float myFunction(float *args){
  return SOMETHING;
}

float find_max(float*pars,(float *)(float[]) ){
  return SOMENASTY_OPTIM;
}

float find_best(int times_to_run){
  return RUN_FIND_MAX times_to_run TIMES;
}

int main(){
  find_best(10);
}
[/PHP]

If the optimization function is really nasty, then it would be nice to have it in a seperate file.
Or if multiple people are working on this project, then it would be nice to split up the project into completely different parts.

The person who writes the optimazation algorithm doesnt' care about how the function atually calculates the values.
He just need the function prototype, so the above could be made into


[PHP]
//header for function.h
float myFunction(float *args);
[/PHP]

[PHP]
//implementation for function.cpp
float myFunction(float *args){
return SOMETHING
}
[/PHP]

[PHP]
//implementation for optimization.cpp
#include function.h

float find_max(float*pars,(float *)(float[]) ){
  return SOMENASTY_OPTIM;
}
[/PHP]

Or if the optimazation algorithm is really good then you want to reuse it.

hope that gives you an idea.

---

### Post by crazyfuturamanoob on 2008-11-24
But how can it work? 

The header file doesn't have ANY references to it's .c file, where the actual functions & stuff is.

I still don't get it.


In /usr/include/ there are tons of headers, all of the has prototypes, but no complete functions anywhere. 

Where are the .c files?? No any reference to them.

---

### Post by Npl on 2008-11-24
a header file defines prototypes, ie. tells what functions are availabe somewhere.

its usefull as compilation occurs in smaller modules (each .c file), so instead having the full definition the compiler just leaves blanks for referenced functioncalls. the output of a compiler .c file is an object file .o

You can think of those .o files as some kind of library exposing the functions implemented in the respective .c file. if you have 2 or more .o files which reference functions of one another, the blanks will then by filled in with the correct address during linking those .o files together. to link existing code (like the c runtime library) you only need headers and .o files (or .so files which are a special kind of library, but similar).

do if you have 2 .c files which depend on each other and the c-runtime this is roughly what happens:

```
   compile    link
foo.c -> foo.o \
bar.c -> bar.o -- myexecutable
        libc.0 /
```

Edit: the C-runtime is always linked implicitely, for any other header you will need to tell gcc which library to link.
As example a particulary braindead odditity of gcc is that standard math functions arent in the C-Runtime, so if you use for example sqrt() you will then need to link the maths-library explicitely (gcc -lm myfile.c).

---

### Post by monkeyking on 2008-11-24
> **crazyfuturamanoob said:**
> But how can it work? 

The header file doesn't have ANY references to it's .c file, where the actual functions & stuff is.

I still don't get it.


In /usr/include/ there are tons of headers, all of the has prototypes, but no complete functions anywhere. 

Where are the .c files?? No any reference to them.

You would never try to compile a .h file,
you would compile the corresponding .c file.

And this .c file has a #include .h

---

### Post by geirha on 2008-11-24
Before compilation takes place, the preprocessor is run on the files. The preprocesser handles #defines and the likes, and replaces #include lines with the content of the included files. Then compilation takes place. You can run the preprocessor (cpp) on a file to see how it looks:
```
cpp somefile.c
```
So basicly it turns it into a big c file with all the include files' content included.

---

### Post by pp. on 2008-11-24
May I suggest to google for the term "C header file"? The first hit returned is the Wikipedia entry which gives a very plausible explanation:

[http://en.wikipedia.org/wiki/Header_file](http://en.wikipedia.org/wiki/Header_file)

---

### Post by jimi_hendrix on 2008-11-24
related question...if a headerfile is a group of prototypes that you link in with their definitions then what is a library?

---

### Post by jimi_hendrix on 2008-11-24
related question...if a headerfile is a group of prototypes that you link in with their definitions then what is a library?

---

### Post by monkeyking on 2008-11-24
> **jimi_hendrix said:**
> related question...if a headerfile is a group of prototypes that you link in with their definitions then what is a library?

I'm in no way an expert,
but I think a library is a list of externed functions.

---

### Post by nvteighen on 2008-11-24
A Header file is a file defining a certain interface so that the compiler is aware of it and can therefore enforce it (checking types, return values, etc.).

How does it work? Well, the magic is in the library, actually, not in the header file (which you could actually rewrite on your own and it would be the same...). Libraries are binary object code files that have an index of what they provide. How this index is created is irrelevant for us now (it's different whether the library is a static or a dynamic one). 

If when compiling a C source to ASM (before binary), gcc finds that in a certain source file of yours you have a function call to a non-defined function, instead of translating it into a reference to a memory address (as it is done regularly), it will leave it untouched in order to let the linker take care of it afterwards.

What the linker does after all is to look up for those not resolved references inside the libraries you provided using the -l switch (now you know why you have to put it), except the Std. Lib which is automatically added to that list. So, if there's a match, the reference is finally resolved... if not, gcc will spit out an "undefined reference to ..." error and quit.

If it happens that the interface defined on the header file is different to the library's actual implementation, you won't notice anything... it will result on a runtime error (segfault or whatever).

---

### Post by cmay on 2008-11-24
>          
But how can it work? 

The header file doesn't have ANY references to it's .c file, where the actual functions & stuff is.

I still don't get it.

In /usr/include/ there are tons of headers, all of the has prototypes, but no complete functions anywhere. 

Where are the .c files?? No any reference to them.here is a very very small example .  i found a lot out by reading the stdio.h how printf works. not why it works that is pretty well explained in almost any c tutorial or book i think.

hello.c
[php]
#include "example.h"
int main()
{
hello();
return 0;
}
[/php]and the header file saved as example.h
[php]
#include <stdio.h>
void hello()
{
printf("hello world\n");
}
[/php]you compile as gcc -o hello  ./hello.c 
and run hello ./hello

it will display the hello world message from a function that is written in a header file. 
the most important thing is to remember that you should not ever never try change the files that comes with gcc such as stdio.h or stdlib.h since that would be a very bad idea. at least until you know exactly what your doing and why.
when you write your own then remember to use #include "file" instead of #include <file>
i will let you figure out why for your self by reading the links provided. which i am going to do now btw.

---

### Post by nvteighen on 2008-11-25
> **cmay said:**
> 
[/php]and the header file saved as example.h
[php]
#include <stdio.h>
void hello()
{
printf("hello world\n");
}
[/php]

Excuse me, that header file is not correct. Ok, it will work, but it's not  what a header file is supposed to do. The right way to do this is the one at **Post #3 on this thread**: header includes just prototypes. Why? Because that way you are able to do staged-compiling and therefore save time by only recompiling the modules you have modified into object files and then just linking.

But also, it's highly advisable to not use header files as libraries because it could turn into redundant code (double definitions and such) which sometimes either result in compile-time errors or even worse, run-time errors.

---

### Post by wmcbrine on 2008-11-25
> **jimi_hendrix said:**
> related question...if a headerfile is a group of prototypes that you link in with their definitions then what is a library?The library is the actual code. The header file (mostly) just describes what's in the library. You *include* headers, but *link* libraries.

Technically, there is no formal separation between .h and .c files: either can contain any kind of C code, which includes declarations. But there are very strong conventions as regards the proper use of .h files.

For Pascal users, an .h file is like the Interface of a Unit.

---

### Post by cmay on 2008-11-25
> Excuse me, that header file is not correct. Ok, it will work, but it's not what a header file is supposed to do. The right way to do this is the one at **Post #3 on this thread**: header includes just prototypes. Why? Because that way you are able to do staged-compiling and therefore save time by only recompiling the modules you have modified into object files and then just linking.

But also, it's highly advisable to not use header files as libraries because it could turn into redundant code (double definitions and such) which sometimes either result in compile-time errors or even worse, run-time errors.
tp://nyttf.dk/?pagetype=book&vareid=57122709
tp://nyttf.dk/?pagetype=book&vareid=57122709
this book uses a header file which has a function written in danish this called hentline (getline) and that is done this way. i use the books i can buy and have to trust them for being correct. thanks for correction.

---

### Post by monkeyking on 2008-11-25
> **cmay said:**
> ...and have to trust them for being correct...

Trust no one.
:)

Seriously it seems strange they would write stuff like this in a book.

The whole prototype vs. implementation can be confusing, even more so the staged compilation with makefiles.
This goes especially for templated function.
Since these don't have an headerfile.

---

### Post by nvteighen on 2008-11-25
> **cmay said:**
> tp://nyttf.dk/?pagetype=book&vareid=57122709
this book uses a header file which has a function written in danish this called hentline (getline) and that is done this way. i use the books i can buy and have to trust them for being correct. thanks for correction.
Ok. But you can surely trust the header files ;) Take a look at stdio.h (at least the GNU version) and you won't see any implementation detail, just obscure preprocessor directives and prototypes... (btw, the use of the 'extern' keyword, which you'll see a lot on headers, is optional... IIRC it's just for backwards compatibility)

---

### Post by monkeyking on 2008-11-25
I'm in no way an expert,
But when talking about the system libraries, the .so's.

You can only count on the exported/extern part of the libraries stays the same across different version.

[http://people.redhat.com/drepper/dsohowto.pdf](http://people.redhat.com/drepper/dsohowto.pdf)

The dynamic symbol table will contain all global symbols from the source files. But the libraryprogrammer is free to change all interfaces that are not part of the abi (not api).

So you should only use externed functions.

---

### Post by cmay on 2008-11-25
so this is wrong i figure then? . ok then i managed to make a example on what not to do then :oops: .   thanks for insight in this.  this is a downloaded example file that comes with this book as examples provided to go with the book. i did not change anything.  the funktion hentliine means getline in danish as i mentioned. there are two more examples like this in the book. 
[php]
/* Filnavn = support1.h */


struct personType
{
    int alder;
    char forNavn[20];
    char efterNavn[20];
};

int hentLinie(char linie[], int MAX)
{
    int i = 0;
    char ind;

    while (i < MAX-1 && ( ind = getchar() ) != '\n')
        linie[i++] = ind;
    linie[i] = '\0';
    return i;
}[/php]

---

### Post by monkeyking on 2008-11-25
> **cmay said:**
> so this is wrong i figure then? . ok then i managed to make a example on what not to do then :oops: .   thanks for insight in this.  this is a downloaded example file that comes with this book as examples provided to go with the book. i did not change anything.  the funktion hentliine means getline in danish as i mentioned. there are two more examples like this in the book. 
[php]

/* Filnavn = support1.h */

struct personType
{
    int alder;
    char forNavn[20];
    char efterNavn[20];
};

int hentLinie(char linie[], int MAX)
{
    int i = 0;
    char ind;

    while (i < MAX-1 && ( ind = getchar() ) != '\n')
        linie[i++] = ind;
    linie[i] = '\0';
    return i;
}[/php]

Without checking if your code compiles, you should split it up
something like

[php]
/* Filnavn = support1.h */
struct personType
{
    int alder;
    char forNavn[20];
    char efterNavn[20];
};
int hentLinie(char linie[], int MAX);
[/php]

[php]
/* Filnavn = support1.c */

#include "support1.h" // <- include your header that contains your struct
int hentLinie(char linie[], int MAX)
{
    int i = 0;
    char ind;

    while (i < MAX-1 && ( ind = getchar() ) != '\n')
        linie[i++] = ind;
    linie[i] = '\0';
    return i;
}[/php]

But I don't think it's a complete code example your function doesn't use the struct.

---

### Post by cmay on 2008-11-25
its the c file that comes along with the example. i did not change anything either. its a copy paste of the examples that comes with the book downloaded from the home page of the book. i linked to. while i write in english so everyone can understand it  helps not so much when the things i learn seems wrong. i cant trust books anymore. :(
[php]/* Filnavn = struct3.c */

#include <stdio.h>
#include "support1.h"

int main()
{
    int i;
    int antal = 3;
    char tmp[4];
    struct personType personer[10];

    for (i = 0; i < antal; i++)
    {
        printf("%s", "Indtast fornavn : ");
        hentLinie(personer[i].forNavn, 20);
        printf("%s", "Indtast efternavn : ");
        hentLinie(personer[i].efterNavn, 20);
        printf("%s", "Indtast alder : ");
        hentLinie(tmp, 4);
        personer[i].alder = atoi(tmp);
    }

    printf("%s\n", "Udskriver");
    for (i = 0; i < antal; i++)
    {
        printf("%s\t", personer[i].forNavn);
        printf("%s\t", personer[i].efterNavn);
        printf("%4d\n", personer[i].alder);
    }
    return 0;
}
[/php]

---

### Post by monkeyking on 2008-11-25
Hi again,
Well the code from the book does compile right?

So the example is fine for learning structs, while and other basic programming techniques.

So my guess the example is not meant for explaining the header concept.

Don't worry about,

Bad examples are quite good, once you understand why it's a bad example.

good luck.

---

### Post by crazyfuturamanoob on 2008-11-26
I managed to do this header for my graphics library(?) graphics.c:
```

// graphics.h

SDL_Surface *surface;

int initGL( GLvoid );

int resizeWindow( int width, int height );

struct glTEX
{
    GLuint data;
    int width, height;
};

struct glTEX LoadTexture( char filename[]);

void draw_texture( struct glTEX *texture, float x, float y );
void draw_texture_centered( struct glTEX *texture, float x, float y );

```
I got this error, but I don't think it's anyhow related to graphics.c so I don't post it.
> 
graphics.h:15: error: stray &#8216;\240&#8217; in program

What is stray 240? What's wrong? O.o

And SDL & OpenGL libs are included in the main program, so it isn't necessary to include them in graphics.c/h

Edit: Posted this into a new thread because it will be noticed faster from there.

---

### Post by doojsdad on 2008-11-26
Without going into technical details, just a quick example of why it is bad practice to implement functions in header files. Using this short code:

[php]
/* calcs.h */

int addition(int a, int b);[/php]

[php]
/* calcs.c */
#include "calcs.h" 

int addition(int a, int b)
{
   return (a+b);
}[/php]

If you have a function that is used in several different places in your project, for example, if you have 10 files that include "calcs.h" in this case, then if you included implementation in the header file it would have to recompile all 10 files if you decided to change the implementation of that function in the slightest way. 

Whereas if you just leave the prototype of the function in the header file and changed the function implementation in calcs.c it would only have to recompile calcs.c and none of the 10 files that used the function (unless you modified the function prototype as well).

So if you did:
[php]
/* calcs.c */
#include "calcs.h" 

int addition(int a, int b)
{
   int c = a+b;
   return (c);
}[/php]

It would only recompile calc.c and not the other 10 source files that include calcs.h. Any time you modify the header file, such as adding a member to a struct, added a new function prototype, etc, it will have to recompile any files that include that header.

---

