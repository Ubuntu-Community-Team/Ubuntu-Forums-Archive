---
title: "For loop condition evaluted each time?"
date: 2010-05-14
forum: Programming Talk
---

### Post by pokebirdd on 2010-05-14
Suppose I had a simple for loop:
[HTML]for(ii = 0; ii < strlen(s); ii++)[/HTML]Will the strlen(s) function inside be reevaluated with each pass of the loop or will the compiler some how magically optimize it away?

If it is reevaluated each time, it would be better to write
[HTML]n = strlen(s);
for(ii = 0; ii < n; ii++)[/HTML]wouldn't it?

---

### Post by simeon87 on 2010-05-14
This is PHP right? I don't know how PHP handles this but it depends on the compiler or interpreter. Unless it's a really expensive function to compute, you probably won't notice it anyway so this is premature optimization. The first code fragment is what you meant to write so write that instead, no need to introduce a new variable.

---

### Post by Milliways on 2010-05-14
> **pokebirdd said:**
> Suppose I had a simple for loop:
[HTML]for(ii = 0; ii < strlen(s); ii++)[/HTML]Will the strlen(s) function inside be reevaluated with each pass of the loop or will the compiler some how magically optimize it away?

If it is reevaluated each time, it would be better to write
[HTML]n = strlen(s);
for(ii = 0; ii < n; ii++)[/HTML]wouldn't it?

It will be evaluated at the end of each loop.
If s is not changed in the loop it is poor programming practice, not to mention inefficient.

I assume you are iterating through the string for some reason.
It is more usual to use a pointer, and iterate until it reaches the null byte terminator.

---

### Post by pokebirdd on 2010-05-14
I actually just copied that code from a site illustrating a basic hash function and wondered if it was really inefficient (it's in C by the way).

So the best way would be to simply:
[HTML]for (ii = 0; s[ii] != '\0'; ii++)[/HTML]Is this correct?

EDIT:
Here's the program I was working on while using the code for the hash table. It just reads a file and stores each line in a hash table then prompts the user for a key and retrieves the corresponding entry in the table. I haven't really worked out how to deal with collisions yet though so if someone could point me in the right direction, that'd be great :)
[HTML]#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#define HASHELEMENTS 100
#define MAXLINES 100
#define MAXCHAR 1000

unsigned int hash (char *s) {
    int ii;
    unsigned int n = 0;

    for (ii = 0; s[ii] != '\0'; ii++)
        n += s[ii]*(HASHELEMENTS-1);

    return n % HASHELEMENTS;
}

int main(int argc, char *argv[]){
    if (argc != 2){
        printf("Usage: %s [FILE]\n", argv[0]);
        return 1;
    }
    FILE *fp = fopen(argv[1], "r");
    int ii, c;
    char *lines[MAXLINES];
    char buf[MAXCHAR];
    char *hash_table[HASHELEMENTS] = {0}; //all entries set to NULL
    int n;

    /* read file into lines */
    for (ii = 0; ii < MAXLINES; ii++){
        //fgets keeps the '\n'
        if (fgets(buf, MAXCHAR, fp) == NULL)
            break; //end of file
        lines[ii] = malloc(strlen(buf)+1);
        strncpy(lines[ii], buf, strlen(buf));
        hash_table[hash(lines[ii])] = lines[ii];
    }
    /* n contains number of lines read */
    n = ii;

    printf("Enter a key:\n");
    fgets(buf, MAXCHAR, stdin);
    if (hash_table[hash(buf)] != NULL)
        printf("The corresponding entry for %s is %sThe hash number is %d\n", buf, hash_table[hash(buf)], hash(buf));
    else
        printf("No such entry exists for key %s\n", buf);

    return 0;
}[/HTML]

---

### Post by simeon87 on 2010-05-14
Ah, yeah.. my mind linked strlen and PHP but in PHP, you'd have $ before variables too.

That would work. But it's actually the same as a while loop.

---

### Post by roccivic on 2010-05-14
Here's some benchmark using a 300,000 character long string. You be the judge.

Code:
```
	int ii, foo = 0;
	for(ii = 0; ii < strlen(bar); ii++) {
		foo++;
	}
```
Result:
```
roccivic@roccivic-pc:~/Desktop$ gcc t1.c
roccivic@roccivic-pc:~/Desktop$ time ./a.out

**real	0m5.029s**
user	0m5.030s
sys	0m0.000s
```

Code:
```
	int ii, foo = 0;
	int n = strlen(bar);
	for(ii = 0; ii < n; ii++) {
		foo++;
	}
```
Result:
```
roccivic@roccivic-pc:~/Desktop$ gcc t2.c
roccivic@roccivic-pc:~/Desktop$ time ./a.out

**real	0m0.002s**
user	0m0.000s
sys	0m0.000s
```

Code:
```
	int ii, foo = 0;
	for(ii = 0; bar[ii] != '\0'; ii++) {
		foo++;
	}
```
Result:
```
roccivic@roccivic-pc:~/Desktop$ gcc t3.c
roccivic@roccivic-pc:~/Desktop$ time ./a.out

**real	0m0.002s**
user	0m0.000s
sys	0m0.000s
```

---

### Post by Milliways on 2010-05-14
This would work but most c programmers would do something like:-
unsigned int hash (char *s)
    {
    unsigned int n = 0;

    for(; *s; s++)
        n += *s * (HASHELEMENTS-1);

    return n % HASHELEMENTS;
    }

Although most would probably simplify this to
    for(; *s; )
        n += *s++ * (HASHELEMENTS-1);

or to be clearer use a while loop.

---

### Post by pokebirdd on 2010-05-14
> **roccivic said:**
> Here's some benchmark using a 300,000 character long string. You be the judge.


Wow, that's really interesting. But what I don't understand is that if gcc detects that s isn't changing during the loop, why doesn't it just store the value of strlen in a temporary variable anyways in order to speed things up?

> **Milliways said:**
> This would work but most c programmers would do  something like:-

That looks much simpler :) Although if I wanted to do stuff with s after the loop, I would have to store a pointer to the beginning of s I suppose.

---

### Post by Some Penguin on 2010-05-14
> **pokebirdd said:**
> Wow, that's really interesting. But what I don't understand is that if gcc detects that s isn't changing during the loop, why doesn't it just store the value of strlen in a temporary variable anyways in order to speed things up?

It would be entirely legal for another thread in the same process space to be writing over the character array, for instance -- or even another process, if the pointer points to shared memory such as might be used by a device driver.  There are few guarantees in C.

---

### Post by MadCow108 on 2010-05-14
not only another thread, it is also legal to manipulate the string inside the loop body, thus changing the length in every iteration.
As C has pointers it is very very hard for the compiler to see if this happens. So it almost always chooses the pessimistic approach.

In non pointer oriented languages, like fortran, this is often much easier. That why you very often see fortran used in high performance computing because the compiler can do so many more optimizations.

---

### Post by soltanis on 2010-05-14
The compiler can only optimize what it sees at compile-time. It can't possible know if the length of your string is changing which is why it will happily repeat the strlen function for every iteration of the loop. Bear in mind that strlen itself is a loop which iterates through the entire string to find the null terminating character, which is why you notice that when you simply iterate until you reach the null terminator it is way faster.

Languages like Haskell, where there is a very strict separation of functions (things whose outputs don't change) with monads (things which cause side-effects and are unpredictable), you will see massive performance improvements stemming from the compiler being able to perform beastly optimizations.

---

### Post by lisati on 2010-05-14
My $.02: Sometimes it's a matter of efficiency versus clarity of the code: having the strlen() function in the for statement tells me more about when the loop is meant to finish (and with less mental strain on my part) than having it separately.


edit: Yes, I agree, having strlen() outside the loop can result in more efficient code, as long as you can be sure that the result isn't going to change. I'd also suggest choose a variable name to make it clearer what the variable's for, e.g. StringLength=strlen(...) instead of s=strlen(...)

---

### Post by StephenF on 2010-05-14
> **pokebirdd said:**
> Wow, that's really interesting. But what I don't understand is that if gcc detects that s isn't changing during the loop, why doesn't it just store the value of strlen in a temporary variable anyways in order to speed things up?
Because strlen is not part of the C programming language. It is an external function. How many of these do you think the optimizer should know about? Also, there are no strings in C. Variable s is effectively just an address of a block of memory of indeterminate size.

---

### Post by MadCow108 on 2010-05-14
of course strlen is part of the C programming language (C standard library to be exact).
As such it also carries as much information as supported by the compiler in the definition:
e.g. the glibc definition:
extern size_t strlen (__const char *__s)
      __THROW __attribute_pure__ __nonnull ((1));

so the compiler knows its pure and it takes no NULL arguments. There is not more to know.
But that does not mean it that helps by these kind of decisions because of already mentioned difficulties.

---

### Post by lostinxlation on 2010-05-14
It's very easy for the compiler to analyze the context and figure out strlen isn't being modified in the loop, and the compiler can optimize it to evaluate strlen only once before the loop.
It depends on the compiler, but the compiler guys want to squeeze out the last bit of the performance, and I'm sure they don't want to evaluate the same thing over and over.

---

### Post by StephenF on 2010-05-14
> **MadCow108 said:**
> So the compiler knows it's pure and it takes no NULL arguments.
Let's suppose there is more than one thread and the string is writeable during part of the body of the loop due to mutex unlocking.

---

### Post by MadCow108 on 2010-05-14
> **StephenF said:**
> Let's suppose there is more than one thread and the string is writeable during part of the body of the loop due to mutex unlocking.

there are much simpler single threaded situations where the compiler cannot do anything.
e.g.
```

void f(int * a char *s) {
  for (int i =0; i < strlen(s); i++)
    *(a+i)++;
}

```

what is the compiler supposed to do?
it can't remove the strlen from the loop because a could alias s! This would mean the string gets modified by the loop.
It is near impossible for the compiler to resolve such situations, it often requires very expensive global interprocedual analysis. And even that can fail.

of course this situation could be theoretically resolved by use of restrict, but the implementation of that in gcc is not very reliable.

C although very powerful (however you like to define that ;) ) thanks to its pointers is also strongly limited in its performance unless used by an experienced coder.
In languages without pointers you can write extremely fast programs without much knowledge of the underlying architecture. You leave all that to compilers. You can't do that in C.

---

### Post by Cracauer on 2010-05-14
> **pokebirdd said:**
> Suppose I had a simple for loop:
[HTML]for(ii = 0; ii < strlen(s); ii++)[/HTML]Will the strlen(s) function inside be reevaluated with each pass of the loop or will the compiler some how magically optimize it away?

If it is reevaluated each time, it would be better to write
[HTML]n = strlen(s);
for(ii = 0; ii < n; ii++)[/HTML]wouldn't it?

Yes, the former is a very serious and quite common performance bug (in C).

While a C++ or C99 compiler is free to assume that it knows what strlen(3) does it would also have to proof that the string isn't manipulated. That would be very difficult to do if the loop body calls functions or follows pointers in any way.

---

