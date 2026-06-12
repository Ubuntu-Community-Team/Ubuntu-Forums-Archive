---
title: "freeing memory after return"
date: 2012-01-19
forum: Programming Talk
---

### Post by bigrockcrasher on 2012-01-19
I have this stupid question where i know the answer but I need it to come form some one else. my boss has this set of really big code written primarily in c. Several of the functions use malloc  and at the end of the function after the return statement he declares the free() statement after the return statement. The functions that do this do not seem to free up the memory. My boss said he tried changing the order and said it did not fix the problem .can any one explain this to me.

---

### Post by Hetepeperfan on 2012-01-19
ok I'll try to explain. first of all I would like you to recommend valgrind. Valgrind is a program designed to find memory leaks. You can install it by:

```
sudo apt-get install valgrind
```second, your boss is wrong. If a function returns before freeing it's memory you'll loose memory every time you run that function. In the demo program below I've two functions the memleak() looses memory and the no memleak does not. I call the source memleak.c and the program leak. compile the program as:

```
gcc -o leak memleak.c -Wall -W -pedantic -g
``````
#include<stdlib.h>

void memleak( void ){

    int* ptr = (int*) malloc (sizeof(int));

    return;
    free(ptr);
}

void noleak (void){

    int* ptr = (int*) malloc (sizeof(int));

    free(ptr);
    return;
}

int main(){

    memleak();
    noleak();

    return 0;

}

```if you run the program like this:
```
valgrind --leak-check=full ./leak
```valgrind will produce output similar to:

```
==4310== Memcheck, a memory error detector
==4310== Copyright (C) 2002-2010, and GNU GPL'd, by Julian Seward et al.
==4310== Using Valgrind-3.6.0.SVN-Debian and LibVEX; rerun with -h for copyright info
==4310== Command: ./leak
==4310== 
==4310== 
==4310== HEAP SUMMARY:
==4310==     in use at exit: 4 bytes in 1 blocks
==4310==   total heap usage: 2 allocs, 1 frees, 8 bytes allocated
==4310== 
==4310== 4 bytes in 1 blocks are definitely lost in loss record 1 of 1
==4310==    at 0x4C2815C: malloc (vg_replace_malloc.c:236)
==4310==    by 0x400555: memleak (memleak.c:6)
==4310==    by 0x400588: main (memleak.c:22)
==4310== 
==4310== LEAK SUMMARY:
==4310==    definitely lost: 4 bytes in 1 blocks
==4310==    indirectly lost: 0 bytes in 0 blocks
==4310==      possibly lost: 0 bytes in 0 blocks
==4310==    still reachable: 0 bytes in 0 blocks
==4310==         suppressed: 0 bytes in 0 blocks
==4310== 
==4310== For counts of detected and suppressed errors, rerun with: -v
==4310== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 4 from 4)
```where two lines are of big importance:
```
==4310==    definitely lost: 4 bytes in 1 blocks
```which shows you've lost four bytes (one int on my machine)
and
```
==4310==    by 0x400555: memleak (memleak.c:6)
```showing the line in the source code where some memory was allocated but not freed.
thus this is in the function where the memory was freed after the return statement

although there are a lot of functions that will reserve memory for you, which you have to manually free later. mostly functions that will allocate some datastructure. Those are often function like my_structure* create_my_structure() and void destroy_my_structure( my_structure* ptr).

I hope you can use this info!

cheers,

Maarten

---

### Post by fct on 2012-01-19
> **bigrockcrasher said:**
> I have this stupid question where i know the answer but I need it to come form some one else. my boss...

:lolflag:

---

### Post by dwhitney67 on 2012-01-19
> **bigrockcrasher said:**
> My boss said he tried changing the order and said it did not fix the problem.
What "problem" is it that he was trying to solve?

Obviously freeing memory before the return statement (or end of function) should work.  Is the function supposed to return a pointer to the allocated memory?  If this is the case, then you definitely do not want to free the memory when the function returns.  You would need to free it after the function caller is done with using the allocated memory.

P.S.  Post some code with the relevant information so that a better assessment can be made.

---

