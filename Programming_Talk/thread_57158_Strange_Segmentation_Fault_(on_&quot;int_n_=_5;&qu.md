---
title: "Strange Segmentation Fault (on &quot;int n = 5;&quot; in C program)"
date: 2005-08-15
forum: Programming Talk
---

### Post by bkasterm on 2005-08-15
I am trying to write a progam that in the end will use binomial coefficients of large numbers.  I have used analogous code to the below with all types changed to integers, and no problems (but can't make MAX below very big then as the numbers will grow too large for the int type).  With this code there also are no problems as long as MAX is not big (900 here appears to be big !?!?).

I am neither an experienced programming nor experienced at using gdb.  I always thought I had some understanding, but this is thoroughly confusing me.

This is the gdb output:
************************* begin output ******************
Program received signal SIGSEGV, Segmentation fault.
main () at chooseTry2.c:13
13          int n = 5;
************************* end output *********************

The progam in total is (it is a bit messy because I have been
working with it a while, think it is readable enough though):

**************************begin program *********************
```

#include <stdio.h>
#include <gmp.h>

#define MAX 900
// maximum index is one less than this

int main()
{
  mpz_t choose[MAX][MAX];   // contains the binomials, note
                            //  choose[i][j] only used if j <= i

  {   // setting the choose array.
    int n = 5;
    int r = 9;

    for (n= 0; n < MAX; n++)
    {
      for ( r = 0 ; r <= n; r++)
      {
        if ( r == 0 || r == n)
        {
          mpz_init(choose[n][r]);
          mpz_set_ui(choose[n][r],1);
        }
        else
        {
          mpz_init(choose[n][r]);
          mpz_add(choose[n][r],choose[n-1][r-1],choose[n-1][r]);
        }
      }
    }
  }
  {   // testing small outputs
    int n,r;
    for (n= 0; n < 10; n++)
    {
      for ( r = 0 ; r <= n; r++)
      {
        printf("n = %i", n);
        printf(" r = %i ", r);
        mpz_out_str( stdout, 10, choose[n][r] );
        printf("\n");
      }
    }
    mpz_out_str( stdout, 10, choose[499][200]);
  }
  return 0;
};

```

******************************end program **************************

Best,
Bart

---

### Post by LordHunter317 on 2005-08-15
You're overflowing the stack.

Here's what's happening:
When the compiler sees the declaration:[quote]```
 mpz_t choose[MAX][MAX];
``` it generates code to allocate of all of that array on that stack.  In IOW, you're asking for enough stack space for 900*900 , or 810000 mpt_z entries.  Assuming an mpz_t was a 32-bit integer, that'd be 3164 KiB, or just over 3 MiB of space.  That's a lot of stack space.

Anyway, then it goes to allocate more space on the stack for the integer.  Only, this space has to go past where that huge array is.  Too far, in fact, it's past the end of the stack.  When the compiler attempts to go there, it goes outside the process space, and your program dies with a SIGSEGV.

The correct solution is to allocate that array dynamically.

---

### Post by LordHunter317 on 2005-08-15
Anyway. what I didn't mention is the reason it fails at the 'int n = 5;' line and not while allocating all that space for the array is that you don't try to access the space until the n initialization.  If you were initializing those values, it'd die somewhere during the process.

---

### Post by bkasterm on 2005-08-15
Thanks. That answers my question perfectly.

I understand part of how stacks operate, but not completely.  As a matter of fact (still witnessed by the "{" and "}" around the piece of code, this used to be a function, and I moved it to main to try to avoid stack overflow.  I did now know main operated on a stack with it's variables too.

What I'll now do is try to learn more about the stack, and how the dynamic memory allocation works (not just how to use it in C/C++, but what the right mental/physical model for this is).  When I find out the details (suggestions of where to look are off course very welcome) I'll post what I learned back into this thread.

Best,
Bart

BTW: mpz_t is the integer type from the [GNU MP Bignum library](http://www.swox.com/gmp/).  It allows for arbitrary large integers, with their memory size dynamically increased as needed.  I do not know it's base memory need.

---

### Post by LordHunter317 on 2005-08-16
> **bkasterm]I did now know main operated on a stack with it's variables too.[/quote]In C, all variables local to a function are allocated on a stack.  Also, under C argument passing, all arguments to a function are on the stack as well.  In reality, optimizations are sometimes done to make the latter not alwasy be true, and pass arguments in registers (usually the first three).

So. saying:```
int n=3 said:**
> What I'll now do is try to learn more about the stack, and how the dynamic memory allocation works (not just how to use it in C/C++, but what the right mental/physical model for this is).Generally, stack should be used only for very small things, or things with limited scope (counter inside a function that's not passed anywhere else).

What "small" should be varies based on application, and such.  There are no hard and fast rules.

Have a look at the C FAQ, which helps clarify this for C programming.  Also, K&R C, Second edition or whatever the latest is.

---

### Post by bkasterm on 2005-08-16
Thanks.  My picture of the situation is improving.  It seems a bit hard to find good information about this on the web.  The C FAQ clearly has [code](http://www.eskimo.com/~scs/C-faq/q6.16.html) I can use (after inserting error checking: checking that return value of malloc != NULL), so that should solve my practical problem (I am assuming that some of the things mentioned below are true).  Now with some of the reading online I have done, the theory is not quite clear though.

At
[User-Level Memory Management In Linux Programming](http://www.phptr.com/articles/article.asp?p=173438&rl=1) 
the picture shown is
[Picture of memory for program](http://www.phptr.com/content/images/chap3_0131429647/elementLinks/03fig01.jpg) .
(these pages are consistent with, but better presented than most of the other things I have found)

With this picture in mind it seems not true that the stack can hold less than the heap (where the dynamic allocation happens).  So if I understand correctly, the heap should be theoretically unlimited, but the stack should be drawn with a definite bound (this would break the ["no arbitrary limits" (first paragraph)](http://www.gnu.org/prep/standards/html_node/Semantics.html#Semantics) principle.  So apparently not followed by Linux.  Or maybe the situation is more interesting, and this limit has a good reason.).

Best,
Bart

---

### Post by bkasterm on 2005-08-16
[QUOTE=LordHunter317]
Have a look at the C FAQ, which helps clarify this for C programming.  Also, K&R C, Second edition or whatever the latest is.[/QUOTE]

Unfortunately where I am right now I don't have easy access to a library, so I can't look at the book.  I'll be back at the home institution in th US in a couple of weeks, so then I can look at it.  Also I think that my remaining questions are probably OS dependent.

---

### Post by LordHunter317 on 2005-08-16
[QUOTE=bkasterm]  The C FAQ clearly has [code](http://www.eskimo.com/~scs/C-faq/q6.16.html) I can use (after inserting error checking: checking that return value of malloc != NULL),[/quote]Also, clear the casts they're inserting.

> With this picture in mind it seems not true that the stack can hold less than the heap (where the dynamic allocation happens).It is.  You should treat the gap in the picture as unallocated memory, that will be consumed by the heap, not by the stack.

> So if I understand correctly, the heap should be theoretically unlimited, but the stack should be drawn with a definite boundYes.  Usually, the stack segment bound is fixed at load-time, and you cannot change it from your application.

> ["no arbitrary limits" (first paragraph)](http://www.gnu.org/prep/standards/html_node/Semantics.html#Semantics) principle.No, it doesn't really.

Stack is intentionally limited on purpose, and it doesn't provide an arbitrary limit in the sense that page is talking about .  You shouldn't provide arbitrary limits to the users of your programs.  The system providing a limit on how much stack you can have is a good thing.

Moreover, you can get around this limitation by allocating on the heap, not the stack.

> Or maybe the situation is more interesting, and this limit has a good reason.).It does, as a huge stack is normally a sign of a bug, in C anyway.

---

### Post by bkasterm on 2005-08-17
[QUOTE=LordHunter317]
Also, clear the casts they're inserting.
[/QUOTE]

These casts are done automatically, but do you have a reason other than cleanliness of the code to want them gone?

> 
Yes.  Usually, the stack segment bound is fixed at load-time, and you cannot change it from your application.


Can you change the heap limit from your application?  Or see how much you are using?  At [User-Level Memory Managemant](http://www.phptr.com/articles/article.asp?p=173438&seqNum=2) there are functions mentioned for seeing the memory management, but they are system functions that he/she sais you should/can not use with malloc/free.

I have checked (with the below program) that I have about 2.98 GB heap available.  I would like to keep an eye on heap use in the final program (it will be very data intensive, and much of the memory management is out of my hands (in the libraries hands) and I would like to keep an eye on it).

So anyway, this is the program for using a dynamically allocated array (here I have used int instead of the final type).  Also, the values in the array are not what I care about.

```

#include <stdlib.h>
#include <stdio.h>

#define MAX 100

int main()
{
  int n,r;                                  // loop counters used in
                                            // different places
  int **arr;
  printf("Allocating memory for array.");
  fflush( stdout );
  arr = malloc(MAX * sizeof(int *));        // allocating row pointers.
  if ( NULL == arr)
  {
    printf("\nmain 1 error: malloc failed on row pointers");
    return 1;
  }
  for ( n = 0; n < MAX; n++)                // allocating rows.
  {
    arr[n] = malloc(MAX * sizeof(int));
    if ( NULL == arr[n] )
    {
      printf("\nmain 2 error: malloc failed on row %i.", n);
      return 1;
    }
  }
  printf("        [OK]\n");

  printf("Setting array with some values:");
  fflush( stdout );
  for ( n = 0; n < MAX; n++)
  {
    for ( r = 0; r <= n; r++)
    {
      arr[n][r] = n*r;
    }
  }
  printf("        [OK]\n");
  
  printf(" sizeof(int): %i", sizeof(int));
  return 0;
}

```

I found out the approx size of the heap by using MAX = 100000.  Then I got output:

Allocating memory for array.
main 2 error: malloc failed on row 8019.
shell returned 1

Best,
Bart

---

### Post by LordHunter317 on 2005-08-17
[QUOTE=bkasterm]These casts are done automatically, but do you have a reason other than cleanliness of the code to want them gone?[/quote]Yeah, type-saftey and maintaince purposes.  If you let C perform the cast automatically, the type of the lvalue doesn't matter.  If you manually cast, your code may/will break if the type is changed.  That's also why you'll see sizeof(*var) where var is some pointer type.  If the type pointed to is changed, no further changes are needed.

> Can you change the heap limit from your application?Upwards?  No, not unless you're root.  I believe you could drop your own heap limit, but there's little point to that.

Well, to be very-specific, you can only adjust the max size of your data segment, which is principally heap.  And you can only grow it as root.

> I have checked (with the below program) that I have about 2.98 GB heap available.What architecture are you using?  On x86, you shouldn't be able to allocate more than 2GB of data without special tricks, due to the way the virtual address space is laid out.

Unless you enabled the 1GB/3GB split, in which case, that number sounds about right.

> I would like to keep an eye on heap use in the final program (it will be very data intensive, and much of the memory management is out of my hands (in the libraries hands) and I would like to keep an eye on it).A better idea would be to profile the program externally, using tools like purify or valgrind or maybe a special purpose malloc library to determine if there is an issue, where it is, and how to deal with it.

> So anyway, this is the program for using a dynamically allocated array (here I have used int instead of the final type).Understand you can probalby squeeze more memory, as this setup is potentially causing some heap fragmentation issues.  You'd also save memory on pointer space ;)

Generally, when you need maximum memory usage, you allocate memory contiguously, much like the C FAQ entry shows.

---

### Post by LordHunter317 on 2005-08-17
Ahh, my bad, 3G/1G is teh default on the kernel these days, so your heap limit makes perfect sense.

[edit]And to be clear, you can't et anymore than that trivally on x86.  There are ways, but they come with horrible performance costs if you're doing any I/O or any context switching, so you don't want to consider them.

Most virtual memory you can have is 3G at a time in userspace.  If you know you'll need more than that, you have two options:[list][*]Go 64-bits[*]Develop a paging system to save unneeded data on disk to be mapped back in later. This would involve learning about mmap() and friends.[/list]

---

### Post by bkasterm on 2005-08-17
Thanks LordHunter137.  This discussion has been a great help to me.  

Now I will first complete my program, and then try the profiling to see where the restrictions are.  It might be that my calculations turn to be too slow before memory limits become the limit (part of it are very easy calculations, part more complicated).  My first guess at the limit will be that when physical memory runs out, the paging will be too slow (iirc, paging: writing parts of memory to hard disk to free memory for other data). 

I am using x86 (at least on the computer on which I am writing the program, if it turns too slow and I can't optimize I'll go shopping for faster options at the university).  Allocating memory contiguously I don't think will help as the number types I use dynamically grow, giving the fragmentation anyway.

Again, thanks for your help,

Best,
Bart

---

### Post by LordHunter317 on 2005-08-17
Make sure you're using appropriate data structures for your data, and you haven't missed obvious data storage optimizations that way.  For example, if you're dealing with spare matricies, there are better storage options than what you'd use for a dense one.  There are libraries out there that can help for this stuff, depending on exactly what you're doing.  However, I'm not familiar with many C math libraries.

---

### Post by LordHunter317 on 2005-08-17
Another thing worth mentioning is that if you intend to use that much memory, you may want to google online for information about Linux overcommit behavior and the OOM killer, so you can tell your users how to configure their systems so they don't run afoul of it.

---

### Post by bkasterm on 2005-08-19
For readers of this thread what I have found about this:

linux overcommit:  the linux kernel will commit to more memory than it has available.  This is under the reasoning that many times much of what is asked for is not actually used (example I saw: in a fork of a process the whole memory space "should be available" for both parts after the fork, but large parts are not changed by either process.  Can then not copy the whole memory space, and only copy pages on changes.).

OOM killer: Out of Memory killer.  Because of the overcommit it can be that there is no memory available where in the past it was promised by successes of malloc/new.  Then the course of action is to kill some processes.  In the pages I found there is much discussion on what the strategy should be for this, or if this is a good idea at all.

The best page I have found on this (which has some code showing the effects as well) is
[http://www.win.tue.nl/~aeb/linux/lk/lk-9.html](http://www.win.tue.nl/~aeb/linux/lk/lk-9.html) 
section "9.6 Overcommit and OOM" is the relavant one.

My program is not a user program (that is a program that will be used by people other than me, or more accurately people without my direct presence), so I have no worries about educating users.  

The worry at this time is speed, it slow down a lot when the swap starts getting used.  There are some strong ways to reduce the total amount of memory used, but as far as I can see really used memory is as contiguous as I can make it in memory.  With my current understanding I don't yet see how then reducing memory use will speed things up beyond some relatively minor reduction in organisorial swapping that will happen anyway when the program runs long enough.

Actually the real worry is a bug in my calculations, but I am confident I'll get that soon.  If I actually start analyzing my program properly I might start a new thread to show and discuss my analysis.

Best,
Bart

---

