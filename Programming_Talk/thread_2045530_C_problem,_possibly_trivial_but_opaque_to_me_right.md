---
title: "C problem, possibly trivial but opaque to me right now"
date: 2012-08-21
forum: Programming Talk
---

### Post by Santillana on 2012-08-21
I am trying to get a very minuscule C project on the road. The only real purpose is to get to understand modular programming in C with inclusion of header files (.h) which "conjugate" with like-named source code files (.c). Very different from Java where "import ..." solves everything in one go.

My main program is modu_kris.c:

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include "help_file.h"

main()
{
  struct person p;
  p = inperson();
  printf("%s %d",p.namn, p.alder);
}
```The header file from which inclusion is made is help_file.h:

```
struct person {};

struct person inperson(void);
```Here, of course, declarations but no definitions are stored.

The source file is help_file.c:

```
#include <stdio.h>
struct person
{
   int alder;
   char namn[20];
   
};

struct person inperson(void)
{
   struct person p;
   scanf("%s %d", p.namn, &p.alder);
   return p;
}
```with relevant definitions.

The program works as intended when in the form of one whole file with everything, but of course that is not interesting in itself - understanding modularization is the idea.

```
martin@martin-1001PX:~/C_programs$ gcc -o modu_kris.out modu_kris.c help_file.c help_file.h
```gives

```
modu_kris.c: In function ‘main’:
modu_kris.c:13:19: error: ‘struct person’ has no member named ‘namn’
modu_kris.c:13:27: error: ‘struct person’ has no member named ‘alder’
```But I defined the struct 'person' to include those two members/fields in the source code file. Plain to see. I included the header file, which answers for the like-named source file.

What might I be doing wrong, on a more principal plane? Grateful for any constructive input.

---

### Post by Bachstelze on 2012-08-21
There are so many things wrong that I don't know where to start, so I'll just give you a correct version, and also recommend you trash your current learning material and seek a new one.

*EDIT:* Also, you really should learn how to properly do I/O in C, because as it is, your program is vulnerable to buffer overflows.

```
firas@aoba ~ % cat modu_kris.c 
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include "help_file.h"

int main(void)
{
  struct person p;
  p = inperson();
  printf("%s %d",p.namn, p.alder);
}
firas@aoba ~ % cat help_file.c 
#include <stdio.h>
#include "help_file.h"

struct person inperson(void)
{
   struct person p;
   scanf("%s %d", p.namn, &p.alder);
   return p;
}
firas@aoba ~ % cat help_file.h 
struct person {
    int alder;
    char namn[20];
};

struct person inperson(void);
firas@aoba ~ % gcc -std=c99 -pedantic -Wall -Wextra -c modu_kris.c                      
firas@aoba ~ % gcc -std=c99 -pedantic -Wall -Wextra -c help_file.c                      
firas@aoba ~ % gcc -std=c99 -pedantic -Wall -Wextra -o modu_kris modu_kris.o help_file.o
firas@aoba ~ % 

```

---

### Post by trent.josephsen on 2012-08-21
First, this
```
struct person {};
```
is a struct definition. It defines a type called "struct person" that contains no data whatsoever. I'm not sure whether this is even legal. What you wanted was a struct declaration, which declares there is a type called "struct person" but defers the exact details of its implementation to later:

```
struct person;
```

Second, though, you need to think in terms of translation units. The point of having separate .c and .h files is so that you can compile your source files separately. Header files provide information that is needed *during the compilation process* in order to completely compile a program. So when you do

```
#include <stdio.h>
int main(void)
{
    printf("hello, world\n");
    return 0;
}
```

<stdio.h> provides information about the type and signature of the printf function so that the compiler can produce the right object code to call it, without actually linking in the implementation of the function.

Structs and unions are different from functions, though. In order to compile code that calls a function, like the example above, all you need is the function's signature -- type and number of arguments. But if you write code that uses a struct, in order to compile that code to object code, the compiler needs to know how much space it takes up, the types and offsets of its fields, and so forth. *That information is not available if it's in a separate .c file*. Struct definitions need to be available at compile time, so they need to go in header files.

The point of forward struct declarations is to enable nested data structures, like in this example of a linked list in which every element remembers which list it's an element of:

```
struct Node;
struct List {
    size_t length;
    struct Node *head;
};
struct Node {
    void *data;
    struct List *parent;
    struct Node *next;
};
```
If not for the first 'struct Node;' declaration at the top, the compiler would fail when trying to define what a 'struct List' is because 'struct Node' is used before it was defined. The forward declaration is a promise to define it later so the compiler can work out the respective sizes post facto.

---

### Post by Santillana on 2012-08-21
Holy smoke. I am very grateful for this input. I will look at it very keenly.  Thank you so mu ch, trent.josephsen and Bachstelze. Hope you can pitch in at least one more time before I am through with this.

---

### Post by Santillana on 2012-08-21
Everything is working beautifully. :) The two of you just swooped down like eagles for the kill. My source material is now in the trash bin, be looking elsewhere for better. Thanks a million.

Just one more question remains in my mind; answer it as you like in your own time or not at all:

Why, more exactly, is ```
int main(void)
``` superior to just ```
main()
```?

---

### Post by trent.josephsen on 2012-08-21
In old versions of C, you could create a function and not give it a return type, and 'int' would be assumed. If you didn't explicitly return a value inside the function, the return value would generally be garbage. The implicit-int feature was taken out in C99, the 1999 revision of the C standard (that is, since C99 all functions, including 'main', must have an explicit return value). main() returns an int indicating success or failure status (which you can test in the shell with the $? variable).

The 'void' part is quite a different issue. Basically it is a way to document that main takes no arguments in a way that the compiler can check it. Google "function prototyping" for more information, or try to compile this program with and without 'void':
```
#include <stdio.h>
static int n = 100;
int main( /* void */ ) {
    printf("n = %d\n", n--)
    if (n) {
        main(n);
    }
}
```

Both versions should generate the same object code (if the build process gets that far), but one of them will warn you of the potentially dangerous mistake.

---

### Post by Santillana on 2012-08-21
> **trent.josephsen said:**
> In old versions of C, you could create a function and not give it a return type, and 'int' would be assumed. If you didn't explicitly return a value inside the function, the return value would generally be garbage. The implicit-int feature was taken out in C99, the 1999 revision of the C standard (that is, since C99 all functions, including 'main', must have an explicit return value). main() returns an int indicating success or failure status (which you can test in the shell with the $? variable).

The 'void' part is quite a different issue. Basically it is a way to document that main takes no arguments in a way that the compiler can check it. Google "function prototyping" for more information, or try to compile this program with and without 'void':
```
#include <stdio.h>
static int n = 100;
int main( /* void */ ) {
    printf("n = %d\n", n--)
    if (n) {
        main(n);
    }
}
```Both versions should generate the same object code (if the build process gets that far), but one of them will warn you of the potentially dangerous mistake.

Ah. Gold mine of knowledge here. As a matter of fact, I have been using Kernighan's and Ritchie's old book based on C89 where all examples have main() only but this has obviously been a mistake for this reason and for a number of other reasons.

---

### Post by satsujinka on 2012-08-21
On the other hand, if you want to have a recursive main then main() can still be useful. Of course, in a "real" program you're going to have main(int argc, char *argv[]), so there's usually not going to be any issue.

---

### Post by SteveHillier on 2012-08-21
> **Santillana said:**
> Ah. Gold mine of knowledge here. As a matter of fact, I have been using Kernighan's and Ritchie's old book based on C89 where all examples have main() only but this has obviously been a mistake for this reason and for a number of other reasons.
Do you mean the old K & R or the ANSI standard K & R.  The original version is the only book I know that started at Chapter 0.
For old guys like me, reared on the non ANSI standard the need to give functions return values (or void) when you know they will never return anything and to have to put in explicitly typed arguments (or void) was a real pain.
We wrote the code that we knew worked and if you came along later and couldn't read it then that was your fault not ours.  And comments, well if you had to I suppose....
On which note I will tell you of a comment in a line of code once seen.
// When this code was written only God and the programmer knew what it did.  Now only God knows!

---

### Post by trent.josephsen on 2012-08-21
> **SteveHillier said:**
> For old guys like me, reared on the non ANSI standard the need to give functions return values (or void) when you know they will never return anything and to have to put in explicitly typed arguments (or void) was a real pain.
We wrote the code that we knew worked and if you came along later and couldn't read it then that was your fault not ours.  And comments, well if you had to I suppose....

Bad documentation is not a problem unique to programmers of the 1970s.

---

### Post by Santillana on 2012-08-22
> **SteveHillier said:**
> Do you mean the old K & R or the ANSI standard K & R. 

It is in fact the old K & R beginning at chapter 0, and in German to boot. It was both that I was greedy, and that I thought I would pick up some German programming trade vocabulary in the process (hard to find a translation for e.g. operating system ("Betriebssystem") in a regular dictionary).

But that's all in the past now. K & R doesn't explain these concepts with header files/source files/modularization, or anything about subtleties with the coordination scheme of *make*. Got to modernize. :p

---

### Post by trent.josephsen on 2012-08-22
K&R's job is to describe the language. It is written (in both editions) to get programmers up to speed with the "new" language. There are other excellent books out there that describe project design and build processes.

FWIW, chapter 4 of K&R2 at least does describe program structure and gives a brief overview of header files, but it doesn't talk about struct definitions.

---

### Post by Santillana on 2012-08-22
> **trent.josephsen said:**
> There are other excellent books out there that describe project design and build processes.


I would be more grateful than ever if you would expound on that or possibly list a few examples. :)

---

### Post by trent.josephsen on 2012-08-22
Well, to be perfectly honest, with regard to splitting programs up among files, that's more like something I've picked up with practice reading and writing (not that I consider myself an expert). I have learned from some books, but none I would feel comfortable recommending. If anything I've learned more (about C, anyway) from browsing the NetHack source code.

But the thing about C is that it's a very small language. It has some nuances that may seem odd at first, but on the whole it doesn't take long to learn the ins and outs, and once you know them, you can hold the whole thing in your head while you program without continually flipping back and forth in a book.

When it comes to make, I most often refer to Unix in a Nutshell, which has a nice chapter on it, but mostly because I don't own any other books that address make. There's also the [GNU Make manual](http://www.gnu.org/software/make/manual/), which is quite readable and more or less definitive.

Part of the problem is that project structures and build procedures vary widely, so it's hard to write a reference material that covers everyone's different use cases. Make would be better suited to a cookbook-style reference, of which I don't know any.

I guess this wasn't as helpful as you would have liked, but I hope it puts you on the right track. I'll look into some other books; I've got Safari Online (*shameless plug for IEEE Computer Society membership*) so maybe I can find something worth recommending.

---

### Post by Santillana on 2012-08-22
> **trent.josephsen said:**
> Well, to be perfectly honest, with regard to splitting programs up among files, that's more like something I've picked up with practice reading and writing (not that I consider myself an expert). I have learned from some books, but none I would feel comfortable recommending. If anything I've learned more (about C, anyway) from browsing the NetHack source code.

Exactly my experience.  No books, manuals, primers or templates exist. You have to self-instruct. Not gonna happen under stress.

> **trent.josephsen said:**
> When it comes to make, I most often refer to Unix in a Nutshell, which has a nice chapter on it, but mostly because I don't own any other books that address make. There's also the [GNU Make manual]("http://www.gnu.org/software/make/manual/"), which is quite readable and more or less definitive.

Very good. This is a sort of corroboration of the wisdom in my decision to download that make manual recently. I have UNIX in 24 hours, but that might not cut the ice. Be looking into Unix in a Nutshell. Thank you! :)

---

### Post by Bachstelze on 2012-08-22
There's not a lot you need to know about make until you start working on very big projects (but then you probably need something like autotools or cmake).  Basically define a bunch of variables (CC, CPPFLAGS, CFLAGS, LDFLAGS, LIBS, etc.) as needed, and let the implicit rules do the rest. A Makefile for your code above would look like this:

```
CC=gcc
CFLAGS=-std=c99 -pedantic -Wall -Wextra -g
OUTFILE=modu_kris
OBJFILES=modu_kris.o \
	 help_file.o

$(OUTFILE): $(OBJFILES)
	$(CC) -o $@ $^

clean:
	rm -f $(OUTFILE) $(OBJFILES)

```

---

### Post by trent.josephsen on 2012-08-23
I believe I was wrong about this.

> **trent.josephsen said:**
> The point of forward struct declarations is to enable nested data structures, like in this example of a linked list in which every element remembers which list it's an element of:

```
struct Node;
struct List {
    size_t length;
    struct Node *head;
};
struct Node {
    void *data;
    struct List *parent;
    struct Node *next;
};
```
If not for the first 'struct Node;' declaration at the top, the compiler would fail when trying to define what a 'struct List' is because 'struct Node' is used before it was defined. The forward declaration is a promise to define it later so the compiler can work out the respective sizes post facto.

Not about the forward declaration part, but the part about it being necessary in order to define mutually referential structs. I was thinking of typedef's ([which I recommend avoiding because they're too often used to hide useful information](http://ubuntuforums.org/showthread.php?t=1927762&page=2#post11705102)), which are done in one pass and will throw errors at compilation if used before they're defined. I believe the forward declaration of the struct is not necessary here.

---

### Post by satsujinka on 2012-08-23
I can verify that, the following compiles fine.
```
#include <stdlib.h>
struct List {
    size_t length;
    struct Node *head;
};
struct Node {
    void *data;
    struct List *parent;
    struct Node *next;
};
int main(){
  return 0;
}
```
@trent
Not sure if it's appropriate here, but I think your opinion on typedef is a little harsh. Certainly, it is abused but I've never found the small loss of information particularly noticeable even when revisiting code I wrote years ago (then again, I've always been consistent in my usage.)

---

### Post by Santillana on 2012-08-23
> **Bachstelze said:**
> There's not a lot you need to know about make until you start working on very big projects (but then you probably need something like autotools or cmake).  Basically define a bunch of variables (CC, CPPFLAGS, CFLAGS, LDFLAGS, LIBS, etc.) as needed, and let the implicit rules do the rest. A Makefile for your code above would look like this:

```
CC=gcc
CFLAGS=-std=c99 -pedantic -Wall -Wextra -g
OUTFILE=modu_kris
OBJFILES=modu_kris.o \
     help_file.o

$(OUTFILE): $(OBJFILES)
    $(CC) -o $@ $^

clean:
    rm -f $(OUTFILE) $(OBJFILES)

```

Good, thanks. I'll copy this for future reference, if that's all right with you. And all I would have to do is to invoke make in the form of

```
$ make all
```

if the makefile in question is the only one in my present working directory, right?

---

### Post by Santillana on 2012-08-23
> **trent.josephsen said:**
> I believe I was wrong about this.



Not about the forward declaration part, but the part about it being necessary in order to define mutually referential structs. I was thinking of typedef's ([which I recommend avoiding because they're too often used to hide useful information]("http://ubuntuforums.org/showthread.php?t=1927762&page=2#post11705102")), which are done in one pass and will throw errors at compilation if used before they're defined. I believe the forward declaration of the struct is not necessary here.

satsujinka compiled this (above) and it worked, so no sweat. Anyway, this is one of the easier types of errors to flush out...rewrite, compile, swear, rewrite, compile...the number of combinations is manageable before you get to the point when you don't have to swear anymore.

The header file/source file/declaration here/definition there-problem is more vacuous. After 45 minutes or more of fruitless experimentation with fluffy issues like this, I usually need a lot of anger management. :mad: :smile:

---

### Post by Santillana on 2012-08-23
> **satsujinka said:**
> I can verify that, the following compiles fine.
```
#include <stdlib.h>
struct List {
    size_t length;
    struct Node *head;
};
struct Node {
    void *data;
    struct List *parent;
    struct Node *next;
};
int main(){
  return 0;
}
```@trent
Not sure if it's appropriate here, but I think your opinion on typedef is a little harsh. Certainly, it is abused but I've never found the small loss of information particularly noticeable even when revisiting code I wrote years ago (then again, I've always been consistent in my usage.)

Thanks. Was gonna look into this, but no need now. Me coming from the Java side as I do, I find typedef's impossible to dispense with. Can't break out of that mindset. Consistent and transparent on typedef's is the thing.

---

### Post by Bachstelze on 2012-08-23
> **Santillana said:**
> And all I would have to do is to invoke make in the form of

```
$ make all
```

if the makefile in question is the only one in my present working directory, right?

No, just [font=monospace]make[/font], there is no rule for "all".

---

### Post by trent.josephsen on 2012-08-23
> **satsujinka said:**
> I can verify that, the following compiles fine.
"This compiles fine" is hardly the ISO Standard Seal of Approval.
> Not sure if it's appropriate here, but I think your opinion on typedef is a little harsh. Certainly, it is abused but I've never found the small loss of information particularly noticeable even when revisiting code I wrote years ago (then again, I've always been consistent in my usage.)
You are entitled to your own opinion.

@OP, I don't think typedefs are an entirely bad thing, but I find that in practice they are rarely used to improve readability and often used to impair it. I suggest avoiding them unless you're absolutely sure it's the former.

---

### Post by muteXe on 2012-08-24
Somebody else who doesn't like typedef'ing! And i thought i was alone in the world.

---

### Post by Bachstelze on 2012-08-24
> **muteXe said:**
> Somebody else who doesn't like typedef'ing! And i thought i was alone in the world.

Others include

[http://www.freebsd.org/cgi/man.cgi?query=style](http://www.freebsd.org/cgi/man.cgi?query=style)

>      Avoid using typedefs for structure types.	Typedefs are problematic
     because they do not properly hide their underlying type; for example you
     need to know if the typedef is the structure itself or a pointer to the
     structure.  In addition they must be declared exactly once, whereas an
     incomplete structure type can be mentioned as many times as necessary.
     Typedefs are difficult to use in stand-alone header files: the header
     that defines the typedef must be included before the header that uses it,
     or by the header that uses it (which causes namespace pollution), or
     there must be a back-door mechanism for obtaining the typedef.


---

