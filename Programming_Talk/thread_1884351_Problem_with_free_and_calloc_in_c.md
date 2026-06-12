---
title: "Problem with free and calloc in c"
date: 2011-11-21
forum: Programming Talk
---

### Post by Dirich on 2011-11-21
Hi, I wrote two codes and I am experiencing strange issues. The two codes work perfectly on older ubuntu versions, but since I installed the 11.10... :(

PROBLEM 1
EDIT: turns out it is irrelevant for the real problem (PROBLEM 2), so I think it's better to delete this part to avoid any more help on this problem.


PROBLEM 2 (the source code is in page 2, starting from the first post in that page)
Since friday I have a problem with free(). I mean that before friday my two programs worked, then on friday the one that, when compiled, had no problem with the safeCalloc started to not work due to memory problems. And if you think it's something I changed, the answer is that I did not touch the code! The same code that worked before friday didn't work from friday on!
I found out the problem occurs when I free my memory:

```

#define floattype double

typedef complex floattype cpx;

typedef struct
{
    /*! Raw data. */
    cpx * data;
    /*! Total size. */
    size_t size;
    /*! Rows. */
    size_t sizeX;
    /*! Columns. */
    size_t sizeY;
    /*! Rows leading space (for memory alignment). */
    size_t leadX;
} Matrix2D;

#define FREEMATRIX(_MATRIX) free(_MATRIX.data)

void System_Deinit(Matrix2D H[HBASE], Matrix2D Tl[TBASE], Matrix2D Tr[TBASE], Matrix2D *SigmaLeft, Matrix2D *SigmaRight)
{
    int i;

    for (i = HBASE; i--;)
    {
       FREEMATRIX(H[i]);
    }

    for (i = TBASE; i--;)
    {
        FREEMATRIX(Tl[i]);
        FREEMATRIX(Tr[i]);
    }

    FREEMATRIX((*SigmaLeft));
    FREEMATRIX((*SigmaRight));

    return;
}


```Note that I never use a free() in any other place so it's not possible I am freeing twice the same pointer.
Also, HBASE and TBASE are always not zero and all the pointers are not NULL (and to be on the safe side I even checked it with IFs before the FREEMATRIX calls, which I removed since the code I always used, and worked, is this one). I changed to the simple calloc instead of my "safeCalloc" but nothing changed.

I tried to remove the FREEMATRIX for the two arrays of structures, leaving only those for SigmaLeft and SigmaRight, and the program worked again.
The strangest thing though is the following: I tried to add these 3 lines right after the block of declarations at the beginning of the main().

```

... declaration of the variables at the beginning of main()...

int *pp;

pp = calloc(5, sizeof(*pp));
free(pp);

...the rest of main(), mainly initializations and a loop to call the functions that perform the computations...

```I never uses pp in my program, just to be clear. I created it for the purpose of this test only.
What happens is that after executing a few more instructions after these 3, it stops due to memory problems, if I remove the free() line it works again.

I can't figure out what is happening here... Any help is most welcome :(

EDIT:
I added a tarball with the whole program. To compile type "gcc -o drm DRMmain.c", the program will self compile and run at the end of the execution of drm, which creates the DRMmacro.h file.
[http://www.mediafire.com/?pdvpb7mu9rz44e]("http://www.mediafire.com/?pdvpb7mu9rz44e4")
I also found that if you set "Number of chains" to more than 2, the problem disappears. But the matrices are correctly initialized even for that dimension (Number of chains = n, matrices are n by n square matrices written in a single monodimensional array for compatibility with the fortran algebraic routines).


EDIT:
I forgot to paste the error, which can maybe be useful. This is what I get when I run my program with the line "valgrind <myprogram> -l", using valgrind as suggested by Arndt:

==13647== Memcheck, a memory error detector
==13647== Copyright (C) 2002-2010, and GNU GPL'd, by Julian Seward et al.
==13647== Using Valgrind-3.6.1-Debian and LibVEX; rerun with -h for copyright info
==13647== Command: ./DRMsimulator -l
==13647== 
==13647== Invalid write of size 8
==13647==    at 0x8048C83: System_Init (DRMsimulator.c:77)
==13647==    by 0x8048EE4: main (DRMsimulator.c:276)
==13647==  Address 0x4cabfd0 is 0 bytes after a block of size 64 alloc'd
==13647==    at 0x402732C: calloc (vg_replace_malloc.c:467)
==13647==    by 0x80487BB: safeCalloc (DRMsimulator.c:9)
==13647==    by 0x80488BD: System_Init (DRMsimulator.c:26)
==13647==    by 0x8048EE4: main (DRMsimulator.c:276)
==13647== 
==13647== Invalid write of size 8
==13647==    at 0x8048C8B: System_Init (DRMsimulator.c:77)
==13647==    by 0x8048EE4: main (DRMsimulator.c:276)
==13647==  Address 0x4cabfd8 is 8 bytes after a block of size 64 alloc'd
==13647==    at 0x402732C: calloc (vg_replace_malloc.c:467)
==13647==    by 0x80487BB: safeCalloc (DRMsimulator.c:9)
==13647==    by 0x80488BD: System_Init (DRMsimulator.c:26)
==13647==    by 0x8048EE4: main (DRMsimulator.c:276)
==13647== 
==13647== Invalid write of size 8
==13647==    at 0x8048CAA: System_Init (DRMsimulator.c:78)
==13647==    by 0x8048EE4: main (DRMsimulator.c:276)
==13647==  Address 0x4cabf60 is 0 bytes after a block of size 64 alloc'd
==13647==    at 0x402732C: calloc (vg_replace_malloc.c:467)
==13647==    by 0x80487BB: safeCalloc (DRMsimulator.c:9)
==13647==    by 0x80488BD: System_Init (DRMsimulator.c:26)
==13647==    by 0x8048EE4: main (DRMsimulator.c:276)
==13647== 
==13647== Invalid write of size 8
==13647==    at 0x8048CB2: System_Init (DRMsimulator.c:78)
==13647==    by 0x8048EE4: main (DRMsimulator.c:276)
==13647==  Address 0x4cabf68 is 8 bytes after a block of size 64 alloc'd
==13647==    at 0x402732C: calloc (vg_replace_malloc.c:467)
==13647==    by 0x80487BB: safeCalloc (DRMsimulator.c:9)
==13647==    by 0x80488BD: System_Init (DRMsimulator.c:26)
==13647==    by 0x8048EE4: main (DRMsimulator.c:276)
==13647== 
==13647== 
==13647== HEAP SUMMARY:
==13647==     in use at exit: 0 bytes in 0 blocks
==13647==   total heap usage: 11,035 allocs, 11,035 frees, 930,893 bytes allocated
==13647== 
==13647== All heap blocks were freed -- no leaks are possible
==13647== 
==13647== For counts of detected and suppressed errors, rerun with: -v
==13647== ERROR SUMMARY: 4 errors from 4 contexts (suppressed: 23 from 6)

---

### Post by Arndt on 2011-11-21
> **Dirich said:**
> Hi, I wrote two codes and I am experiencing strange issues. The two codes work perfectly on older ubuntu versions, but since I installed the 11.10... :(



If there is some improper handling of memory, it's not unusual to find that adding something completely unrelated (like printf, or your extra allocation) changes something so it appears to work again.

Try using 'valgrind' on your program. It will tell you the point where you do something invalid.

What is the error message from calloc, by the way?

---

### Post by Bachstelze on 2011-11-21
```
    for (i = HBASE; i--;)
    {
       FREEMATRIX(H[i]);
    }
```

You win the prize for this week's most ridiculous [font=monospace]for[/font] loop ! It might not even do what you think, depending on what H and HBASE represent. And the problem is that since you don't give complete code, we have no idea what they represent either, so we can't really help you. There is too much info missing.

---

### Post by Dirich on 2011-11-21
> **Bachstelze said:**
> ```
    for (i = HBASE; i--;)
    {+
       FREEMATRIX(H[i]);
    }
```You win the prize for this week's most ridiculous [FONT=monospace]for[/FONT] loop ! It might not even do what you think, depending on what H and HBASE represent. And the problem is that since you don't give complete code, we have no idea what they represent either, so we can't really help you. There is too much info missing.

Maybe you meant EFFICIENT instead of ridiculous.
I don't know about how the compiler optimizes those things, I guess the best it can do is to rewrite "i < HBASE" as "i - HBASE", which proves that I save at least 1 subtraction per cycle. It surely is totally irrelevant for my code, but still is not ridiculous (I found this idea in a document about optimization).
Only because I am having problems with memory it doesn't mean I can't even get a for loop straight (HBASE is the dimension of H[ ] and for the system I'm currently simulating, it's set to 2, and that kind of for is equivalent to for (i = 0; i < HBASE; i++)).

Also, if I paste hundreds of lines of code no one is going to help me since they would have to understand the whole program, which is a solid state physics simulation program written with my personal style that I'd say is not really "user friendly" as I have no degree in CS.

Anyway, I pasted everything about the memory management that was included in the code. The rest of it is just computations (with no "checkbound" errors on the arrays - I use blas and lapack as you can infer from my compiling command) and initializations of variables, plus some reading from input and writing to output files. Also, the program worked for months (and still works in non 11.10 ubuntu) so I posted the relevant part of the program where the error is supposed to be.
I analyzed my program on my own and excluded the parts of the code where I'm sure it is not, in order have more chances of someone helping. But if you tell me that people around here will go through hundreds of lines of code to look into this problem, I'll be more than happy to post all of my code.

---

### Post by Dirich on 2011-11-21
> **Arndt said:**
> If there is some improper handling of memory, it's not unusual to find that adding something completely unrelated (like printf, or your extra allocation) changes something so it appears to work again.

Try using 'valgrind' on your program. It will tell you the point where you do something invalid.

What is the error message from calloc, by the way?


What it gives me at the moment is a warning actually:

warning: assignment makes pointer from integer without a cast

probably my memory tricked me and it was never an error (at the time I had library problems too due to some flag for gcc used by 11.10, so I guess I mixed the problems togheter?).

Altough the point remains: why a different behavoiur for the very same code in two different programs by the same compiler (in which I use no options, besides the linking of libraries)?


P.S.
I didn't know of valgrind, thanks for the info, I'll try it.

EDIT:
I added the output from valgrind in the first post.

---

### Post by Arndt on 2011-11-21
> **Dirich said:**
> What it gives me at the moment is a warning actually:

warning: assignment makes pointer from integer without a cast

probably my memory tricked me and it was never an error (at the time I had library problems too due to some flag for gcc used by 11.10, so I guess I mixed the problems togheter?).

P.S.
I didn't know of valgrind, thanks for the info, I'll try it.

EDIT:
I added the output from valgrind in the first post.

It wasn't as informative as I hoped it would be. Often it points out the place in the code very clearly.

As for the warning, you haven't told the compiler what calloc is, so it assumes it returns an int. If you include <stdlib.h> (which one should always do, in all C programs), that warning should disappear. I'm not sure whether it has something to do with your error, though.

---

### Post by Dirich on 2011-11-21
> **Arndt said:**
> It wasn't as informative as I hoped it would be. Often it points out the place in the code very clearly.

As for the warning, you haven't told the compiler what calloc is, so it assumes it returns an int. If you include <stdlib.h> (which one should always do, in all C programs), that warning should disappear. I'm not sure whether it has something to do with your error, though.

Actually I included <stdlib.h>, infact calloc is recognized when I don't use it inside my safeCalloc function. I have an #ifdef directive that I use to switch from a code with direct calls to calloc and one with safeCalloc calls.
I am thinking that it is due to some new flag stuff in gcc by Ubuntu 11.10. Like they did for lilbraries (they now must be called after the files they are used in). In C it is not required to cast a void pointer, and the compiler is assuming that the void returned from calloc is an int in that warning message, a warning message that shouldn't be there in theory, so maybe it's just that the warning used turns out not to be properly worded for this specific case?

I guess this has nothing to do with PROBLEM 2, so I am deleting PROBLEM 1 in order to avoid confusion if someone else jumps into the discussion.

---

### Post by gmargo on 2011-11-21
--deleted--

---

### Post by trent.josephsen on 2011-11-21
> **Dirich said:**
> 
```

#define FREEMATRIX(_MATRIX) free(_MATRIX.data)

```

This is the first time I've seen someone use macros to actually make more work for themselves.  Not only is the meaning unnecessarily obfuscated, but FREEMATRIX(*p) won't even work because of operator precedence.  Macros should be used to make code *less* complicated, not more.

The symptoms you describe are typical of memory mismanagement (sometimes works, sometimes doesn't, and changing ridiculous things change the output significantly).  You probably just have a fencepost error somewhere, but we can't tell because you haven't posted complete code.  Everything you've posted looks okay, but I have to admit I didn't bother to do a line-by-line analysis because you didn't bother to post the rest of the code.

Finally, no, I'm pretty sure Bachstelze meant "ridiculous".  If I have to stare at a for loop for fifteen seconds and look up a macro definition to figure out that it's doing this:
```
for (i = 0; i < HBASE; i++)
    free(H[i].data);
```
then you need to learn some lessons about code readability.  You should know what they say about premature optimization.

---

### Post by Dirich on 2011-11-21
As I said, I have no CS degree, what I know I learned on my own, and I always only wrote code by myself and for myself, ergo I don't know about readibility (beside that the concept exists and I'm sure I'm not following it because I developed my personal standard of "readibility" which is, obviously, mine alone).
I use macros to give the code a uniform look too, not only to make it more easy to read, it's kind of like trying to make the code transparent to the use of memory management instruction when I work with matrixes. I don't want to see the structure Matrix2D, it must work a new type would work when defined in C++ by using a class.

All of this is exactly the reason why I feared posting my whole code would be not useful to my cause.
But since it seems you are indeed fine with looking at long codes, I'll post it in the following posts.

I would only like to underline that I never used FREEMATRIX(*p), there's a (*p) inside the brackets exactly for the reason you wrote.
Also, the code is a continous work in progress, that's why I already "optimized", even though it's a pointless optimization to be honest. I just like it written that way.

---

### Post by Dirich on 2011-11-21
DELETED: added a tarball with the code in the main post.

---

### Post by Dirich on 2011-11-21
DELETED: added a tarball with the code in the main post.

---

### Post by Dirich on 2011-11-21
DELETED: added a tarball with the code in the main post.

---

### Post by Dirich on 2011-11-21
DELETED: added a tarball with the code in the main post.

---

### Post by Dirich on 2011-11-21
DELETED: added a tarball with the code in the main post.

---

### Post by Dirich on 2011-11-21
DELETED: added a tarball with the code in the main post.

---

### Post by Dirich on 2011-11-21
DELETED: added a tarball with the code in the main post.

---

### Post by Dirich on 2011-11-21
DELETED: added a tarball with the code in the main post.

---

### Post by Dirich on 2011-11-21
Every header I didn't post is just like this:

#include "DRMgeneral.h"

<declaration of functions in the .c file>

---

### Post by Arndt on 2011-11-21
> **Arndt said:**
> It wasn't as informative as I hoped it would be. Often it points out the place in the code very clearly.


Maybe you didn't compile and link with the debug flag -g?

---

### Post by gmargo on 2011-11-21
(It would have been easier to just zip up all the sources.  All this cut & paste is a pain.)

What are "DeltaBetadenom" and "Betadenom"?  These are not defined.

```

DRMsimulator.c: In function &#8216;main&#8217;:
DRMsimulator.c:143:9: error: &#8216;DeltaBetadenom&#8217; undeclared (first use in this function)
DRMsimulator.c:143:26: error: &#8216;Betadenom&#8217; undeclared (first use in this function)

```

---

### Post by Dirich on 2011-11-22
> **gmargo said:**
> (It would have been easier to just zip up all the sources.  All this cut & paste is a pain.)

What are "DeltaBetadenom" and "Betadenom"?  These are not defined.

```

DRMsimulator.c: In function &#8216;main&#8217;:
DRMsimulator.c:143:9: error: &#8216;DeltaBetadenom&#8217; undeclared (first use in this function)
DRMsimulator.c:143:26: error: &#8216;Betadenom&#8217; undeclared (first use in this function)

```

I posted an old DRMmacro.h, which was generated before I added that feature (Deltabetadenom is a typo for DeltaBetadenom).

I added the code in a tarball to the main post. Sorry but it's the first time I am asking help so in detail on a problem and I totally didn't expect people to look in depth at my code or to run it.

I also found that the memory problem happens if I set "Number of chains of the ribbon = 2" but it doesn't happen if I set it to 3, 4 or 5 or more (I tried some other random value). I checked and the matrixes are there and are properly initialized right before I free them even with 2 chains (it's the dimension of the complex matrix).

---

### Post by Dirich on 2011-11-22
> **Arndt said:**
> Maybe you didn't compile and link with the debug flag -g?

Here is a more informative valgrind report.
I don't understand it, though... the write at line 77 and 78 of DRMsimulator.c are fine when I check them. H[0].data and H[1].data are both 2x2 matrices (written in an array of dimension 4) and I am putting 0. in the (1,1) position.
Also, valgrind gives the very same output even if I change the value of the matrix dimension to more than 2, which gives me no memory error.


==13647== Memcheck, a memory error detector
==13647== Copyright (C) 2002-2010, and GNU GPL'd, by Julian Seward et al.
==13647== Using Valgrind-3.6.1-Debian and LibVEX; rerun with -h for copyright info
==13647== Command: ./DRMsimulator -l
==13647== 
==13647== Invalid write of size 8
==13647==    at 0x8048C83: System_Init (DRMsimulator.c:77)
==13647==    by 0x8048EE4: main (DRMsimulator.c:276)
==13647==  Address 0x4cabfd0 is 0 bytes after a block of size 64 alloc'd
==13647==    at 0x402732C: calloc (vg_replace_malloc.c:467)
==13647==    by 0x80487BB: safeCalloc (DRMsimulator.c:9)
==13647==    by 0x80488BD: System_Init (DRMsimulator.c:26)
==13647==    by 0x8048EE4: main (DRMsimulator.c:276)
==13647== 
==13647== Invalid write of size 8
==13647==    at 0x8048C8B: System_Init (DRMsimulator.c:77)
==13647==    by 0x8048EE4: main (DRMsimulator.c:276)
==13647==  Address 0x4cabfd8 is 8 bytes after a block of size 64 alloc'd
==13647==    at 0x402732C: calloc (vg_replace_malloc.c:467)
==13647==    by 0x80487BB: safeCalloc (DRMsimulator.c:9)
==13647==    by 0x80488BD: System_Init (DRMsimulator.c:26)
==13647==    by 0x8048EE4: main (DRMsimulator.c:276)
==13647== 
==13647== Invalid write of size 8
==13647==    at 0x8048CAA: System_Init (DRMsimulator.c:78)
==13647==    by 0x8048EE4: main (DRMsimulator.c:276)
==13647==  Address 0x4cabf60 is 0 bytes after a block of size 64 alloc'd
==13647==    at 0x402732C: calloc (vg_replace_malloc.c:467)
==13647==    by 0x80487BB: safeCalloc (DRMsimulator.c:9)
==13647==    by 0x80488BD: System_Init (DRMsimulator.c:26)
==13647==    by 0x8048EE4: main (DRMsimulator.c:276)
==13647== 
==13647== Invalid write of size 8
==13647==    at 0x8048CB2: System_Init (DRMsimulator.c:78)
==13647==    by 0x8048EE4: main (DRMsimulator.c:276)
==13647==  Address 0x4cabf68 is 8 bytes after a block of size 64 alloc'd
==13647==    at 0x402732C: calloc (vg_replace_malloc.c:467)
==13647==    by 0x80487BB: safeCalloc (DRMsimulator.c:9)
==13647==    by 0x80488BD: System_Init (DRMsimulator.c:26)
==13647==    by 0x8048EE4: main (DRMsimulator.c:276)
==13647== 
==13647== 
==13647== HEAP SUMMARY:
==13647==     in use at exit: 0 bytes in 0 blocks
==13647==   total heap usage: 11,035 allocs, 11,035 frees, 930,893 bytes allocated
==13647== 
==13647== All heap blocks were freed -- no leaks are possible
==13647== 
==13647== For counts of detected and suppressed errors, rerun with: -v
==13647== ERROR SUMMARY: 4 errors from 4 contexts (suppressed: 23 from 6)

---

### Post by gmargo on 2011-11-22
> **Dirich said:**
> 
I added the code in a tarball to the main post. 

I got your source tarball.  Sidenote: You can add attachments to your posts, which is better than using the third-party website.

Where's the Makefile?

---

### Post by Dirich on 2011-11-22
> **gmargo said:**
> I got your source tarball.  Sidenote: You can add attachments to your posts, which is better than using the third-party website.

Where's the Makefile?

I have no idea how to make one.

You just need to compile DRMmain.c ("gcc -o drm DRMmain.c", i.e.).
The drm program will compile and launches the real program after writing the DRMmacro.h file which includes the data from the input files.

---

### Post by 11jmb on 2011-11-22
> **Dirich said:**
> I don't know about readibility (beside that the concept exists and I'm sure I'm not following it because I developed my personal standard of "readibility" which is, obviously, mine alone).

If you have time, I suggest teaching yourself some good practices for readable code. For C, the below link is a good starting point.

[http://www.cprogramming.com/tutorial/programming-style-readability.html](http://www.cprogramming.com/tutorial/programming-style-readability.html)

I understand that you are a hobbyist and that in general you have no need to write software-quality code, but you will still reap significant benefit from conforming to basic style standards. Just as a simple example, when asking for help on these boards, we will be able to help you better. Also, as you write more and more code over the years, you will forget exactly how old programs work if you need to do some updating or debugging. The more readable your code is, the easier it will be to work with.

---

### Post by 11jmb on 2011-11-22
> **Dirich said:**
> I have no idea how to make one.

You just need to compile DRMmain.c ("gcc -o drm DRMmain.c", i.e.).
The drm program will compile and launches the real program after writing the DRMmacro.h file which includes the data from the input files.

How are you compiling your other source files? your executable will have to link the other compiled objects

---

### Post by Dirich on 2011-11-22
> **11jmb said:**
> How are you compiling your other source files? your executable will have to link the other compiled objects

inside DRMmain.c I fork and the son process execute an execl command that makes the system perform the command:

gcc -o DRMsimulator DRMsimulator.c DRMinit.c DRMalgebra.c DRMadatom.c DRMscripting.c DRMleads.c DRMtransport.c DRMdatastorage.c -lm -lblas -llapack


Done that the father checks if the compile command ended without errors and, if so, forks again and launches via execl the DRMsimulator program. Done this, it ends.

Essentially DRMmain.c is a program, all the rest of the files are another program. I used it to macro the array dimension since at the beginning I had static arrays (I hoped in a boost in speed), but sometimes I need array too big for the stack  (I think? I can't remember what I was told was too small for my array) so I had to switch to dynamic arrays.
Also, when debugging/running the program multiple times, it saves me to write all that painfully long statement with 300 source files and libraries to link.

EDIT: thanks for the link btw

---

### Post by gmargo on 2011-11-22
I'd say your DRMmain.c is pretty impressive.  It could potentially be integrated into the main program so that it would read the config file into variables, instead of requiring a recompile for every change.

Since you don't have a Makefile, I've written one for you.  It replaces the compiling part of DRMmain.c. The only change you need to make to your source is to remove the TEST_MODE_OFF definition in DRMmain.c - all that stuff will be done by the Makefile instead.

I've attached the Makefile as "Makefile.txt"; you'll have to remove the .txt part of the name.  I've attached it rather than copy/paste it because tabs are important in a Makefile, and they tend to get lost during copy/paste/copy/paste cycles.

Once you put that Makefile in the directory, just run "make".  (Actually, run "make distclean" first.)  The Makefile takes care of creating the DRMmacro.h file (and DRMinput), and all the compiling.  You'll have to run DRMsimulator next (or type "make run").  See also the "make clean", "make distclean", and "make superclean" entries.

If nothing else, perhaps this can help you get started with Makefiles.  I've also added the -Wall option, and as you'll see, this generates quite a few warnings that should be looked into.

Update: you should also comment out the sections in DRMsimulator.c and DRMplot.c where they remove their own binaries.
Update 2: Updated Makefile.txt a bit.

---

### Post by Dirich on 2011-11-22
> **gmargo said:**
> I'd say your DRMmain.c is pretty impressive.  It could potentially be integrated into the main program so that it would read the config file into variables, instead of requiring a recompile for every change.

Since you don't have a Makefile, I've written one for you.  It replaces the compiling part of DRMmain.c. The only change you need to make to your source is to remove the TEST_MODE_OFF definition in DRMmain.c - all that stuff will be done by the Makefile instead.

I've attached the Makefile as "Makefile.txt"; you'll have to remove the .txt part of the name.  I've attached it rather than copy/paste it because tabs are important in a Makefile, and they tend to get lost during copy/paste/copy/paste cycles.

Once you put that Makefile in the directory, just run "make".  (Actually, run "make distclean" first.)  The Makefile takes care of creating the DRMmacro.h file (and DRMinput), and all the compiling.  You'll have to run DRMsimulator next (or type "make run").  See also the "make clean", "make distclean", and "make superclean" entries.

If nothing else, perhaps this can help you get started with Makefiles.  I've also added the -Wall option, and as you'll see, this generates quite a few warnings that should be looked into.

Update: you should also comment out the sections in DRMsimulator.c and DRMplot.c where they remove their own binaries.
Update 2: Updated Makefile.txt a bit.

Thanks a lot!
I'll be doing what you suggest first thing in the morning as I've been working for 12 hours (lunch pause included though) and I need a pause! xD

Also, I think I just understood what makefiles are for... essentially what my typical PROGRAMmain.c is all about. I guess I just have to learn this makefile stuff :)

---

### Post by jwbrase on 2011-11-22
> **Dirich said:**
> Here is a more informative valgrind report.
I don't understand it, though... the write at line 77 and 78 of DRMsimulator.c are fine when I check them. H[0].data and H[1].data are both 2x2 matrices (written in an array of dimension 4) and I am putting 0. in the (1,1) position.
Also, valgrind gives the very same output even if I change the value of the matrix dimension to more than 2, which gives me no memory error.

That's because a memory bug is in fact *occuring* but isn't being *caught*. Valgrind checks more carefully than is practical in normal operation, which allows it to catch more subtle errors.

Memory bugs can have very odd and inconsistent symptoms, because they generally involve something like the right data being written to the wrong place. Depending on the exact nature of the place the data gets written to, the results can range from nothing at all, to an immediate crash, to a delayed crash, to a bizarre and confusing bug in some other part of the program (such as your simulation doing weird things because data from one part got written over data from another).

---

### Post by Dirich on 2011-11-23
> **gmargo said:**
> 
Once you put that Makefile in the directory, just run "make".  (Actually, run "make distclean" first.)  The Makefile takes care of creating the DRMmacro.h file (and DRMinput), and all the compiling.  You'll have to run DRMsimulator next (or type "make run").  See also the "make clean", "make distclean", and "make superclean" entries.


I got this output from a run of "make" (after running make distclean):
gcc -g -Wall    DRMmain.c   -o DRMmain
DRMmain.c: In function &#8216;main&#8217;:
DRMmain.c:1012:3: warning: suggest parentheses around assignment used as truth value [-Wparentheses]
DRMmain.c:1046:4: warning: suggest parentheses around assignment used as truth value [-Wparentheses]
DRMmain.c:1050:4: warning: suggest parentheses around assignment used as truth value [-Wparentheses]
DRMmain.c:88:34: warning: variable &#8216;equivH&#8217; set but not used [-Wunused-but-set-variable]
DRMmain.c:87:56: warning: variable &#8216;wribsize&#8217; set but not used [-Wunused-but-set-variable]
DRMmain.c:86:85: warning: variable &#8216;sweeptype&#8217; set but not used [-Wunused-but-set-variable]
DRMmain.c:85:31: warning: unused variable &#8216;steps&#8217; [-Wunused-variable]
DRMmain.c:85:6: warning: unused variable &#8216;pid&#8217; [-Wunused-variable]
./DRMmain
gcc -g -Wall   -c -o DRMadatom.o DRMadatom.c
DRMadatom.c: In function &#8216;Add_Adatom&#8217;:
DRMadatom.c:11:2: warning: implicit declaration of function &#8216;safeCalloc&#8217; [-Wimplicit-function-declaration]
gcc -g -Wall   -c -o DRMalgebra.o DRMalgebra.c
DRMalgebra.c: In function &#8216;green_function_evaluation&#8217;:
DRMalgebra.c:9:2: warning: implicit declaration of function &#8216;safeCalloc&#8217; [-Wimplicit-function-declaration]
gcc -g -Wall   -c -o DRMdatastorage.o DRMdatastorage.c
gcc -g -Wall   -c -o DRMleads.o DRMleads.c
DRMleads.c: In function &#8216;Sigma_Leads&#8217;:
DRMleads.c:20:2: warning: implicit declaration of function &#8216;safeCalloc&#8217; [-Wimplicit-function-declaration]
DRMleads.c:43:2: warning: implicit declaration of function &#8216;green_function_evaluation&#8217; [-Wimplicit-function-declaration]
DRMleads.c:47:2: warning: implicit declaration of function &#8216;zgemm_&#8217; [-Wimplicit-function-declaration]
gcc -g -Wall   -c -o DRMprobleminit.o DRMprobleminit.c
gcc -g -Wall   -c -o DRMscripting.o DRMscripting.c
gcc -g -Wall   -c -o DRMsimulator.o DRMsimulator.c
DRMsimulator.c: In function &#8216;main&#8217;:
DRMsimulator.c:243:4: warning: implicit declaration of function &#8216;Problem_Init&#8217; [-Wimplicit-function-declaration]
DRMsimulator.c:252:5: warning: implicit declaration of function &#8216;Sigma_Leads&#8217; [-Wimplicit-function-declaration]
DRMsimulator.c:253:6: warning: implicit declaration of function &#8216;Transport_Data_1&#8217; [-Wimplicit-function-declaration]
DRMsimulator.c:257:4: warning: implicit declaration of function &#8216;Storage&#8217; [-Wimplicit-function-declaration]
DRMsimulator.c:258:4: warning: implicit declaration of function &#8216;Scripting&#8217; [-Wimplicit-function-declaration]
gcc -g -Wall   -c -o DRMtransport.o DRMtransport.c
DRMtransport.c: In function &#8216;Transport_Data_1&#8217;:
DRMtransport.c:18:2: warning: implicit declaration of function &#8216;safeCalloc&#8217; [-Wimplicit-function-declaration]
DRMtransport.c:28:2: warning: implicit declaration of function &#8216;green_function_evaluation&#8217; [-Wimplicit-function-declaration]
DRMtransport.c:36:2: warning: implicit declaration of function &#8216;inversion&#8217; [-Wimplicit-function-declaration]
DRMtransport.c:48:2: warning: implicit declaration of function &#8216;zgemm_&#8217; [-Wimplicit-function-declaration]
gcc -g -Wall -o DRMsimulator DRMadatom.o DRMalgebra.o DRMdatastorage.o DRMleads.o DRMprobleminit.o DRMscripting.o DRMsimulator.o DRMtransport.o -lm -lblas -llapack
gcc -g -Wall    DRMplot.c   -o DRMplot
DRMplot.c: In function &#8216;main&#8217;:
DRMplot.c:36:6: warning: implicit declaration of function &#8216;wait&#8217; [-Wimplicit-function-declaration]
DRMplot.c:15:8: warning: unused variable &#8216;fh&#8217; [-Wunused-variable]


I have a doubt: how do I get rid of those implicit declaration warnings?
Could there be some error by my part in how I include the headers?
At the moment the structure is like this:

Everything includes DRMgeneral.h, which includes DRMmacro.h. These 2 headers have declarations needed by every source file.
DRMsimulator.c needs to use functions defined in many other source files (and declared in their respective headers).
Many of the source files that contains definition of functions needed by DRMsimulator.c use the function safeCalloc which is declared in DRMsimulator.h and defined in DRMsimulator.c.

Putting an include directive for every .h of the program inside DRMgeneral.h spawns a stream of errors like there's no knowledge of anything in DRMgeneral.h in any source file.
Adding in xxx.h the list of includes for the .h that contains declarations for functions used in the xxx.c instead generates multiple definition errors (but I think this may be due to the makefile that is already taking care of of the linking?).


P.S.
The unused variables are there for additions I have to do :P

---

### Post by Arndt on 2011-11-23
> **Dirich said:**
> 
Putting an include directive for every .h of the program inside DRMgeneral.h spawns a stream of errors like there's no knowledge of anything in DRMgeneral.h in any source file.
Adding in xxx.h the list of includes for the .h that contains declarations for functions used in the xxx.c instead generates multiple definition errors (but I think this may be due to the makefile that is already taking care of of the linking?).




Common practice is to surround the whole contents of an include file with an ifndef using a preprocessor name derived in some way from the filename, like this, in DRMblipblop.h:

#ifndef DRMblipblop_h
#define DRMblipblop_h

...


#endif

Letting the h file include all h files that its c file is using seems bizarre to me. Let the c file include the h files that it needs, and the h file declare what the c file provides. The h file can include other h files, if there is some encapsulation going on in the h file which the c files doesn't need to know about, like using preprocessor symbols from another h file, or defining a type.

---

### Post by trent.josephsen on 2011-11-23
I've just gotten around to downloading the tarball and examining the source, and I'm going to try to be nice, because I know you're a hobbyist and everything, but the fact of the matter is, if someone offered me $100,000 a year to maintain code that looks like yours, I'd probably turn it down.  (Granted I have other options.)

[QUOTE=Eric S. Raymond]Learning to program is like learning to write good natural language. The best way to do it is to read some stuff written by masters of the form, write some things yourself, read a lot more, write a little more, read a lot more, write some more ... and repeat until your writing begins to develop the kind of strength and economy you see in your models.[/QUOTE]

Did you ever look at code written by other people?  You could save yourself a lot of pain by imitating a competent programmer instead of going it alone.  Notably, if you'd started by looking at established projects, you'd probably already know how to use Makefiles and configure scripts, and you wouldn't have reinvented the wheel with your DRMmain.c.

That said, I applaud you for knowing that main returns int.

---

### Post by Dirich on 2011-11-23
> **trent.josephsen said:**
> I've just gotten around to downloading the tarball and examining the source, and I'm going to try to be nice, because I know you're a hobbyist and everything, but the fact of the matter is, if someone offered me $100,000 a year to maintain code that looks like yours, I'd probably turn it down.  (Granted I have other options.)

I am the first to agree that the code is illegible by anyone other than me (the me of the present, and the me of the future that perfectly recall the details after an excrutiatingly painfully re-read). Unluckly for me, my nature seems to like the most obscure way to write code, and justifies its action in name of an optmization that, if it actually exists, is surely negligible.

More seriously, but equally truthfully, I am trying to improve on the readybility side. :(
Btw, I write the programs to do simulations of physical systems I am working with -at work-, I think I am more under the category of (semi-)noob than under hobbist. :sad_panda: :(

> **trent.josephsen said:**
> Did you ever look at code written by other people?  You could save yourself a lot of pain by imitating a competent programmer instead of going it alone.  Notably, if you'd started by looking at established projects, you'd probably already know how to use Makefiles and configure scripts, and you wouldn't have reinvented the wheel with your DRMmain.c.

I am kind of proud of my new wheel!
This said, I blame the books I read about C for never really explaining makefiles and what they are about. DAMMIT YOU BOOK WRITERS!!! >:(

> **trent.josephsen said:**
> That said, I applaud you for knowing that main returns int.

I don't know if this is ironic or a "seriously meant joking remark", but I bet on the second interpetation! Thanks! :D

---

### Post by gmargo on 2011-11-23
> **Dirich said:**
> 
I have a doubt: how do I get rid of those implicit declaration warnings?
Could there be some error by my part in how I include the headers?


I fixed all of the "implicit declaration of function" warnings by editing each affected .c file and adding a #include for additional headers as required.  
For instance DRMadatom.c needed a "#include "DRMsimulator.h".  Just work through them one-by-one until all these "implicit declaration" warnings are gone.

Alternatively, add all the .h files at the end of DRMgeneral.h (after all the #defines).  That's really the simplest method, which I realized after I did the other work. :)

In the Makefile, I've already marked all of the .o files as being dependent on all of the .h files.  Not strictly true, but it doesn't hurt, plus I avoided having to enumerate each specific .h dependency.

NOTE: since you're a 'make' newbie, here's another important bit (ignore if you know all this):
After you edit a .c or .h file, just type "make" to compile.  There is no need to do any sort of "make clean" operation every time.  **make** knows the .o depends on the .c (a built in dependency that did not need to be enumerated in the Makefile).  So if the .c changes, **make** knows to recompile that one .c.  And since the generated .o is a dependency of the main target (like DRMsimulator), **make** knows to relink the target with the new .o file.

---

### Post by gateway67 on 2011-11-23
> **gmargo said:**
> 
NOTE: since you're a 'make' newbie, here's another important bit (ignore if you know all this):
After you edit a .c or .h file, just type "make" to compile.  There is no need to do any sort of "make clean" operation every time.  **make** knows the .o depends on the .c (a built in dependency that did not need to be enumerated in the Makefile).  So if the .c changes, **make** knows to recompile that one .c.  And since the generated .o is a dependency of the main target (like DRMsimulator), **make** knows to relink the target with the new .o file.
Unfortunately 'make' will not always recompile all modules (.c files) when a header file is modified.  Creating dependency file(s) is a way to mitigate this problem.

It has been a while since I dealt with Makefiles to build C applications, but from an old Makefile I have, I used to following compiler flags (see DEPENDS below) to generate the dependencies:
```

...
DEPS     = $(wildcard *.d)
DEPENDS  = -MT $@ -MD -MP -MF $(subst .o,.d,$@)

...

%.o: %.c
        $(CC) $(CFLAGS) $(DEPENDS) $< -o $@

...

# include dependency file(s)
-include $(DEPS)

```

---

### Post by gmargo on 2011-11-23
> **gateway67 said:**
> Unfortunately 'make' will not always recompile all modules (.c files) when a header file is modified. 

Which is why I have this rule in the Makefile:
```

$(OBJS):        $(HSRC) $(GENHSRC)

```The generated dependency file method is fine and necessary for bigger projects.  This whole project compiles in about 0.5 seconds, so my simplistic method works (and is more newb friendly? - hey I'm trying to get him excited about makefiles!). :)

---

### Post by Dirich on 2011-11-24
> **gmargo said:**
>  hey I'm trying to get him excited about makefiles!. :)
I am! :D

One day I'll be able to write a program with a makefile and a beautiful python interface while the computing part of the program is in c.
That day it'll be a shining day for my CS skills! :D


On another note, thanks to valgrind I found the damn error!


Thanks again to everyone!

---

