---
title: "C - Error in malloc line"
date: 2011-10-26
forum: Programming Talk
---

### Post by AlGorism on 2011-10-26
Hi everyone. 
I'm preparing some project. The problem in the code is:
```
typedef struct stmtlist_t stmtlist_t;
typedef stmtlist_t *stmtlist_ptr;

struct stmtlist_t {
    stmt_ptr statement;
    stmtlist_ptr right;
    stmtlist_ptr down;
};

stmtlist_ptr new_node = (stmtlist_ptr) malloc(sizeof(stmtlist_t));
new_node->down = NULL;
```

In the last line, the compiler gives a segmentation fault. 
In a loop, I use this line lots of times. Compiler doesn't give an error first two times, in the third time of loop, program gives seg fault.
Any idea?

---

### Post by karlson on 2011-10-26
> **AlGorism said:**
> Hi everyone. 
I'm preparing some project. The problem in the code is:
```
typedef struct stmtlist_t stmtlist_t;
typedef stmtlist_t *stmtlist_ptr;

struct stmtlist_t {
    stmt_ptr statement;
    stmtlist_ptr right;
    stmtlist_ptr down;
};

stmtlist_ptr new_node = (stmtlist_ptr) malloc(sizeof(stmtlist_t));
new_node->down = NULL;
```

In the last line, the compiler gives a segmentation fault. 
In a loop, I use this line lots of times. Compiler doesn't give an error first two times, in the third time of loop, program gives seg fault.
Any idea?

Have you tried analyzing the core dump?  Are you sure that this is crashing on the last line?

Can you post the entire code?

---

### Post by 11jmb on 2011-10-26
Just a nuance, but compilers do not give segmentation faults, those happen at runtime

Are you sure that you are calling malloc for every single stmtlist_ptr?

Can you post your entire section of code, especially the loop where the error is occurring?

---

### Post by AlGorism on 2011-10-26
Sorry, I can't share the code because it's for an important project.
Compiler tells the error in runtime, of course. 
Error occured in the last line.
Very interesting, if I write like this:
```
stmtlist_ptr new_node;
new_node = (stmtlist_ptr) malloc(sizeof(stmtlist_t));
```
no error occurs. Is codeblocks kidding me?

---

### Post by cgroza on 2011-10-26
Codeblocks is not a complier. All it does is help you write code. Your compiler is probably GCC and Codeblocks is just an interface for it.

So it should be : Is GCC kidding me?
Also, try compiling your code with -Wall to get some warnings that may be hidden.

---

### Post by karlson on 2011-10-26
> **AlGorism said:**
> Sorry, I can't share the code because it's for an important project.
Compiler tells the error in runtime, of course. 
Error occured in the last line.
Very interesting, if I write like this:
```
stmtlist_ptr new_node;
new_node = (stmtlist_ptr) malloc(sizeof(stmtlist_t));
```
no error occurs. Is codeblocks kidding me?

First off the compiler has nothing to do with what occurs during runtime.
Second.  Have you tried backtracing the coredump to see where it's actually dumping core?
Third.  Does malloc actually return you a valid pointer?
Fourth.  Is the code multi-threaded and are you overriding what you have malloc'ed in another thread?

---

### Post by Bachstelze on 2011-10-26
Works For Me&#8482;

```
firas@applejack ~ % cat test.c 
#include <stdlib.h>

typedef struct stmtlist_t stmtlist_t;
typedef stmtlist_t *stmtlist_ptr;
typedef void* stmt_ptr;

struct stmtlist_t {
    stmt_ptr statement;
    stmtlist_ptr right;
    stmtlist_ptr down;
};

int main(void)
{
        stmtlist_ptr new_node = (stmtlist_ptr) malloc(sizeof(stmtlist_t));
        new_node->down = NULL;
}
firas@applejack ~ % gcc -std=c99 -pedantic -Wall -Wextra -o test test.c
firas@applejack ~ % ./test
firas@applejack ~ % 

```

---

### Post by cgroza on 2011-10-26
Another guess (since there is no code to look at...) is that you may try to access the pointer after you set it to NULL.

---

### Post by gsmanners on 2011-10-26
I just tried:

```
#include <stdlib.h>

typedef struct stmtlist_t stmtlist_t;
typedef stmtlist_t *stmtlist_ptr;
typedef void* stmt_ptr;

struct stmtlist_t {
    stmt_ptr statement;
    stmtlist_ptr right;
    stmtlist_ptr down;
};

int main(void)
{
        stmtlist_ptr new_node1 = (stmtlist_ptr) malloc(sizeof(stmtlist_t));
        stmtlist_ptr new_node2 = (stmtlist_ptr) malloc(sizeof(stmtlist_t));
        stmtlist_ptr new_node3 = (stmtlist_ptr) malloc(sizeof(stmtlist_t));
        new_node1->down = NULL;
        new_node2->down = NULL;
        new_node3->down = NULL;
}
```

And that also seems to work fine.

---

### Post by AlGorism on 2011-10-27
There is a problem I don't understand. Can it be about stack overflow or something?

---

### Post by lisati on 2011-10-27
> **AlGorism said:**
> There is a problem I don't understand. Can it be about stack overflow or something?

Possibly, but not necessarily. A segfault usually indicates a rogue pointer somewhere.

---

### Post by Zugzwang on 2011-10-27
@OP: Here is a proposal. Run your program using the tool valgrind, which will track accesses to memory and report about problems at runtime. It often finds the causes of strange behaviour that you are experiencing.

Usage on the terminal is as follows:
```

valgrind --tool=memcheck ./yourprogram

```
where you add the name of your executable as "yourprogram". Also add parameters if your program needs it. Valgrind will warn you about many things that cause segmentation faults. However, there are a few causes that will not be found this way, and you might have to use a debugger or analyse the core dump. Nevertheless, quite often you can find problems quickly and easily this way, so give it a try. 

Valgrind cannot easily be called from Code::Blocks, so you will have to open a terminal and "cd" to the directory in which your executable is put by the compiler first in order to use it.

---

### Post by karlson on 2011-10-27
> **AlGorism said:**
> There is a problem I don't understand. Can it be about stack overflow or something?

At the risk of repeating myself again: Have you performed core analysis?

Get the core dump open it in GDB and look at the variable values in the function that is at the top of the stack.

I would be willing to bet that one of the pointers you are dereferencing has an invalid value.

If you don't feel like putting it in GDB put in debug print statements that would output the values of the pointers to the screen and report that a certain operation is finished.

Asking a question of what is the error without posting the entire code would be fruitless.

---

### Post by nvteighen on 2011-10-27
+1 for running this first on GDB and then on Valgrind.

Compile your program adding the -g flag and then run it like this:
```

gdb your_program

```

In the gdb shell, use *run* to run the program. When it crashes, it'll tell you where it did.

---

