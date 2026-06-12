---
title: "[C] segfault - valgrind v/s gdb"
date: 2009-03-04
forum: Programming Talk
---

### Post by hey_ram on 2009-03-04
hi!

i was writing a program for some simple stack operations (push, pop, print the top-two and clear).

the program runs normally by executing the binary (./a.out). on using valgrind though, the program segfaults.
i tried to diagnose the problem with gdb, but upon running gdb, the program works just fine!!!

my questions are as follows:
1. has anyone encountered this before? any hints on what might be happening and how to encounter it?

2. i try to make my programs with as much dynamic memory allocation as possible (malloc, realloc etc.). consequently, i use valgrind to ensure that there are no memory leaks. 

the following is the line i use:

valgrind --tool=memcheck --leak-check=full --show-reachable=yes ./a.out

should i be satisfied with the line: "all heap blocks were freed - no leaks are possible"

or should i be worried about the detailed reports put out by valgrind that invariably contain "invalid read" and "invalid write"

thanks..

---

### Post by monkeyking on 2009-03-04
I think your program is non-working,
and the reason gdb hasn't caught it,
is that no signal from the system has been raised.

Try posting some of you valgrind errors.

---

### Post by hey_ram on 2009-03-04
here is what i get when i run it with valgrind..

```

 valgrind --tool=memcheck --leak-check=full --show-reachable=yes ./h
==16275== Memcheck, a memory error detector.
==16275== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==16275== Using LibVEX rev 1804, a library for dynamic binary translation.
==16275== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.
==16275== Using valgrind-3.3.0-Debian, a dynamic binary instrumentation framework.
==16275== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.
==16275== For more details, rerun with: -v
==16275== 


Menu:
1: Push an element onto the stack.
2: Pop top-most element from the stack.
3: Print the top two elements from the stack.
4: Clear the stack.
5: Display the stack.
6: Exit.
Enter your choice:1

Enter an elements to push onto the stack:12

Go again?y

Menu:
1: Push an element onto the stack.
2: Pop top-most element from the stack.
3: Print the top two elements from the stack.
4: Clear the stack.
5: Display the stack.
6: Exit.
Enter your choice:1

Enter an elements to push onto the stack:2

Go again?y

Menu:
1: Push an element onto the stack.
2: Pop top-most element from the stack.
3: Print the top two elements from the stack.
4: Clear the stack.
5: Display the stack.
6: Exit.
Enter your choice:1

Enter an elements to push onto the stack:4
==16275== Invalid free() / delete / delete[]
==16275==    at 0x4022B8E: realloc (vg_replace_malloc.c:429)
==16275==    by 0x804887E: push (stackOps.c:81)
==16275==    by 0x80486E2: main (stackOps.c:39)
==16275==  Address 0x418c028 is 0 bytes inside a block of size 8 free'd
==16275==    at 0x4022B8E: realloc (vg_replace_malloc.c:429)
==16275==    by 0x804887E: push (stackOps.c:81)
==16275==    by 0x80486E2: main (stackOps.c:39)
==16275== 
==16275== Invalid write of size 8
==16275==    at 0x8048893: push (stackOps.c:82)
==16275==    by 0x80486E2: main (stackOps.c:39)
==16275==  Address 0x10 is not stack'd, malloc'd or (recently) free'd
==16275== 
==16275== Process terminating with default action of signal 11 (SIGSEGV)
==16275==  Access not within mapped region at address 0x10
==16275==    at 0x8048893: push (stackOps.c:82)
==16275==    by 0x80486E2: main (stackOps.c:39)
==16275== 
==16275== ERROR SUMMARY: 2 errors from 2 contexts (suppressed: 11 from 1)
==16275== malloc/free: in use at exit: 16 bytes in 1 blocks.
==16275== malloc/free: 4 allocs, 3 frees, 56 bytes allocated.
==16275== For counts of detected errors, rerun with: -v
==16275== searching for pointers to 1 not-freed blocks.
==16275== checked 64,428 bytes.
==16275== 
==16275== 
==16275== 16 bytes in 1 blocks are definitely lost in loss record 1 of 1
==16275==    at 0x4022B8E: realloc (vg_replace_malloc.c:429)
==16275==    by 0x804887E: push (stackOps.c:81)
==16275==    by 0x80486E2: main (stackOps.c:39)
==16275== 
==16275== LEAK SUMMARY:
==16275==    definitely lost: 16 bytes in 1 blocks.
==16275==      possibly lost: 0 bytes in 0 blocks.
==16275==    still reachable: 0 bytes in 0 blocks.
==16275==         suppressed: 0 bytes in 0 blocks.
Segmentation fault

```

---

### Post by monkeyking on 2009-03-04
Well the program tells you that you have problems at
stackOps.c line 81

but also at stackOps.c:82 line 82
the errors are an invalid free (you might be trying a dbl free)
and then you try to input data in the freed block.


I can't really tell without your code

---

### Post by hey_ram on 2009-03-04
the code:

```
/*program to generate and perform some elementary operations on the stack. includes setting up, pushing, popping elements of     and from the stack. printing top two elements from the stack. adding a command to clear the stack. */
  2 
  3 #include<stdio.h>
  4 #include<stdlib.h>
  5 
  6 double *stack;
  7 int stackIndex = 0;
  8 
  9 void push(double num, double *stack);
 10 double pop(double *stack);
 11 void clear(double *stack);
 12 void printTop2(double *stack);
 13 void display(double *stack);
 14 
 15 int main(int argc, char *argv[])
 16 {
 17     char choice, ch = 'y';
 18     double in = 0.0;
 19 
 20     stack = (double *)malloc(1*sizeof(double));
 21     while( (ch != 'n') || (ch != 'N') )
 22     {
 23         getchar();
 24         fprintf(stdout, "\nMenu:");
 25         fprintf(stdout, "\n1: Push an element onto the stack.");
 26         fprintf(stdout, "\n2: Pop top-most element from the stack.");
 27         fprintf(stdout, "\n3: Print the top two elements from the stack.");
 28         fprintf(stdout, "\n4: Clear the stack.");
 29         fprintf(stdout, "\n5: Display the stack.");
 30         fprintf(stdout, "\n6: Exit.");
 31         fprintf(stdout, "\nEnter your choice:");
 32         scanf("%c", &choice);

 34         switch(choice)
 35         {
 36             case '1':
 37                 fprintf(stdout, "\nEnter an elements to push onto the stack:");
 38                 scanf("%lf", &in);
 39                 push(in, stack);
 40                 break;
 41 
 42             case '2':
 43                 fprintf(stdout, "\nThe top-most element in the stack is:%f", pop(stack));
 44                 break;
 45 
 46             case '3':
 47                 fprintf(stdout, "\nTop two elements in the stack are:");
 48                  printTop2(stack);
 49                 break;
 50 
 51             case '4':
 52                 fprintf(stdout, "\nClearing the stack.");
 53                 clear(stack);
 54                 break;
 55 
 56             case '5':
 57                 fprintf(stdout, "\ndisplaying the stack.");
 58                 display(stack);
 59                 break;
 60 
 61             case '6':
 62                 exit(-1);
 63                 break;
 64 
 65             default:
 66                 fprintf(stdout, "\nWrong choice.");
 67                 break;
 68         }
 70         fprintf(stdout, "\nGo again?");
 71         getchar();
 72         scanf("%c", &ch);
 73     }
 74 
 75     free(stack);
 76     return 0;
 77 }
 78 
 79 void push(double num, double *stack)
 80 {
 81     stack = (double *)realloc(stack, (stackIndex + 1)*sizeof(double));
 82     *(stack + stackIndex++) = num;
 83 }
 84 
 85 double pop(double *stack)
 86 {
 87     if( stackIndex < 0 )
 88     {
 89         stackIndex = 0;
 90         return 0;
 91     }
 92     else
 93     {
 94         return (*(stack + --stackIndex));
 95     }
 96 }
 97 
 98 void printTop2(double *stack)
 99 {
100     if( stackIndex <= 1 )
101     {
102         fprintf(stdout, "\nCannot print. No. of elements is less than two.");
103     }
104     else
105     {  
106         fprintf(stdout, "%f\t%f", *(stack + stackIndex - 1), *(stack + stackIndex - 2));
107     }
108 }
109 
110 void clear(double *stack)
111 {
112     fprintf(stdout, "\nClearing the stack.");
113     free(stack);
114 }
115 
116 void display(double *stack)
117 {
118     int i = 0;
119 
120     for(i = 0; i < stackIndex; i++)
121     {
122         fprintf(stdout, "%f\t", *(stack + i));
123     }
124 }




```

---

### Post by dwhitney67 on 2009-03-04
Your code is fine.

A couple of suggestions though:

1)  Consider allocating more than one block at a time for your stack.  Allocate 10 or 20 blocks, thus allowing the user to push that many values before a realloc must take place.

2)  Use the [] operators for accessing your stack.  The arithmetic method you use, although proper and functional, makes the code harder to read and can be an area where a bug can be introduced.

3)  When posting code, do not include the line numbers; it makes it difficult for another programmer to copy your code and compile/test it.

I tested "your" code with the following:
```

#include <stdlib.h>
#include <assert.h>

double* stack      = 0;
int     stackIndex = 0;

void push(double value, double* stack);
double pop(double* stack);

int main()
{
  stack = malloc((stackIndex + 1) * sizeof(double));

  push(10.0, stack);
  push(20.0, stack);
  push(30.0, stack);

  assert(stackIndex == 3);
  assert(pop(stack) == 30.0);
  assert(pop(stack) == 20.0);
  assert(pop(stack) == 10.0);
  assert(stackIndex == 0);

  free(stack);
}

void push(double value, double* stack)
{
  stack = realloc(stack, (stackIndex + 1) * sizeof(double));
  *(stack + stackIndex++) = value;
}

double pop(double* stack)
{
  return *(stack + --stackIndex);
}

```

---

### Post by hey_ram on 2009-03-04
> 2) Use the [] operators for accessing your stack. The arithmetic method you use, although proper and functional, makes the code harder to read and can be an area where a bug can be introduced.


i changed that in the code i wrote.

> 
3) When posting code, do not include the line numbers; it makes it difficult for another programmer to copy your code and compile/test it.


got that. il be more careful in future.

some questions:
i tried running your code on my machine. the same problem occurs again. it runs well in debugging mode with gdb or otherwise with just ./a.out, but produces a segmentation fault when run using valgrind.

Q.) did you have the same problem on your machine??

i found this piece of information on the documentation for valgrind:
> 4.4. 	My program crashes normally, but doesn't under Valgrind, or vice versa. What's happening?
	

When a program runs under Valgrind, its environment is slightly different to when it runs natively. For example, the memory layout is different, and the way that threads are scheduled is different.

Most of the time this doesn't make any difference, but it can, particularly if your program is buggy. For example, if your program crashes because it erroneously accesses memory that is unaddressable, it's possible that this memory will not be unaddressable when run under Valgrind. Alternatively, if your program has data races, these may not manifest under Valgrind.

There isn't anything you can do to change this, it's just the nature of the way Valgrind works that it cannot exactly replicate a native execution environment. In the case where your program crashes due to a memory error when run natively but not when run under Valgrind, in most cases Memcheck should identify the bad memory operation.


but i am not sure if it solves my problem.
Also, should I be worried about the "invalid read" and "invalid write" operations i get along with the output by valgrind?

the record printed out by valgrind is as follows:

> 
valgrind --tool=memcheck --leak-check=yes ./h
==18359== Memcheck, a memory error detector.
==18359== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==18359== Using LibVEX rev 1804, a library for dynamic binary translation.
==18359== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.
==18359== Using valgrind-3.3.0-Debian, a dynamic binary instrumentation framework.
==18359== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.
==18359== For more details, rerun with: -v
==18359== 
==18359== Invalid free() / delete / delete[]
==18359==    at 0x4022B8E: realloc (vg_replace_malloc.c:429)
==18359==    by 0x8048604: push (stackOps2.c:30)
==18359==    by 0x8048481: main (stackOps2.c:16)
==18359==  Address 0x418c028 is 0 bytes inside a block of size 8 free'd
==18359==    at 0x4022B8E: realloc (vg_replace_malloc.c:429)
==18359==    by 0x8048604: push (stackOps2.c:30)
==18359==    by 0x804846A: main (stackOps2.c:15)
==18359== 
==18359== Invalid write of size 8
==18359==    at 0x8048619: push (stackOps2.c:31)
==18359==    by 0x8048481: main (stackOps2.c:16)
==18359==  Address 0x10 is not stack'd, malloc'd or (recently) free'd
==18359== 
==18359== Process terminating with default action of signal 11 (SIGSEGV)
==18359==  Access not within mapped region at address 0x10
==18359==    at 0x8048619: push (stackOps2.c:31)
==18359==    by 0x8048481: main (stackOps2.c:16)
==18359== 
==18359== ERROR SUMMARY: 2 errors from 2 contexts (suppressed: 11 from 1)
==18359== malloc/free: in use at exit: 16 bytes in 1 blocks.
==18359== malloc/free: 4 allocs, 3 frees, 56 bytes allocated.
==18359== For counts of detected errors, rerun with: -v
==18359== searching for pointers to 1 not-freed blocks.
==18359== checked 60,316 bytes.
==18359== 
==18359== 
==18359== 16 bytes in 1 blocks are definitely lost in loss record 1 of 1
==18359==    at 0x4022B8E: realloc (vg_replace_malloc.c:429)
==18359==    by 0x8048604: push (stackOps2.c:30)
==18359==    by 0x804846A: main (stackOps2.c:15)
==18359== 
==18359== LEAK SUMMARY:
==18359==    definitely lost: 16 bytes in 1 blocks.
==18359==      possibly lost: 0 bytes in 0 blocks.
==18359==    still reachable: 0 bytes in 0 blocks.
==18359==         suppressed: 0 bytes in 0 blocks.
Segmentation fault



---

### Post by dwhitney67 on 2009-03-05
@ hey_ram

The last post where you included your valgrind report appears to be different from the one you supplied earlier in this thread.

Did you modify your code erroneously?  These statements from valgrind are not "pretty":
```

...
==18359== LEAK SUMMARY:
==18359== definitely lost: 16 bytes in 1 blocks.
==18359== possibly lost: 0 bytes in 0 blocks.
==18359== still reachable: 0 bytes in 0 blocks.
==18359== suppressed: 0 bytes in 0 blocks.

```

Obviously the segfault is not good either.  A segfault generally indicates that your program is attempting to access an address that falls outside its program-space.  Most errors are because the address is zero.

---

### Post by tneva82 on 2009-03-05
> **dwhitney67 said:**
> Did you modify your code erroneously?  These statements from valgrind are not "pretty":

Any other reason than the definetly lost?

Just wondering since you said statements and pasted everything. As far as I understand valgrind(albeit not much since I just found out about it today :D) only the definetly lost is bad and rest is good.

---

### Post by hey_ram on 2009-03-05
got it!

the error lay in the way i had been passing "stack" to the function. i was passing pointer to stack (double *stack) to the function. changes would be made to stack and thrown as soon as the function was exited. (thats my guess anyways).

i had been facing a similiar problem regarding character arrays a few days ago. inside the function, the character array would show the correct output and as soon as the function would exit, the contents of the character array would be the same as before the function had been entered. 

i tried passing a pointer to a pointer to the stack variable. and it worked!!! the segmentation fault in the valgrind is also gone!!!!

@dwhitney67: no, i did not alter the code beyond the suggestions you had made => changed the code from *(stack + stackIndex) to stack[stackIndex]. thats just about it.
and i think you were one of the posters who helped me out that day too, with the character arrays, right?

i am posting the code and the valgrind report:

```

#include <stdlib.h>
#include <assert.h>

double* stack2      = 0;
int     stackIndex = 0;

void push(double value, double** stack);
double pop(double** stack);

int main()
{
    stack2 = (double *)malloc((stackIndex + 1) * sizeof(double));

    push(10.0, &stack2);
    push(20.0, &stack2);
    push(30.0, &stack2);

    assert(stackIndex == 3); 
    assert(pop(&stack2) == 30.0);
    assert(pop(&stack2) == 20.0);
    assert(pop(&stack2) == 10.0);
    assert(stackIndex == 0); 

    free(stack2);
    return 0;
}

void push(double value, double** stack)
{
      stack2 = (double *)realloc(stack2, (stackIndex + 1) * sizeof(double));
      stack2[stackIndex++] = value;
}

double pop(double** stack)
{
    *stack = stack2;
     return stack2[--stackIndex];
}

```

the valgrind report is as follows:
> 
valgrind --tool=memcheck --leak-check=full --show-reachable=yes ./h
==4971== Memcheck, a memory error detector.
==4971== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==4971== Using LibVEX rev 1804, a library for dynamic binary translation.
==4971== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.
==4971== Using valgrind-3.3.0-Debian, a dynamic binary instrumentation framework.
==4971== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.
==4971== For more details, rerun with: -v
==4971== 
==4971== 
==4971== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 11 from 1)
==4971== malloc/free: in use at exit: 0 bytes in 0 blocks.
==4971== malloc/free: 4 allocs, 4 frees, 56 bytes allocated.
==4971== For counts of detected errors, rerun with: -v
==4971== All heap blocks were freed -- no leaks are possible.


:D

---

