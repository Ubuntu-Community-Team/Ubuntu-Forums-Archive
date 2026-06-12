---
title: "How many input buffers?"
date: 2011-01-01
forum: Programming Talk
---

### Post by c2tarun on 2011-01-01
```

#include<stdio.h>

int main(void)
{
char *a;
size_t n=10;
getline(&a,&n,stdin);
}

```

I the above code, pointer 'a' have no memory initialized to it. So getline will make it point to input buffer.
My question is how many input buffers can a program have?

first I guessed there can be only one and wrote the following program.

```

#include<stdio.h>

int main(void)
{
    char *a,*b;
    size_t n=10;
    getline(&a,&n,stdin);
    printf("%s\n",a);
    getline(&b,&n,stdin);
    printf("%s\n",a);
}

```

in case of only one input buffer, output should be different for two different inputs, but that didn't happen.
Please reply

---

### Post by MadCow108 on 2011-01-01
a program can have as many buffers as you like (as long as memory is available)
there is no single "input" buffer.
(stdin/stdout have a internal buffers, but you do not have to care about these, the system handles them)

your code is faulty in that a is not initialized.
see man getline:
> 
If *lineptr is NULL, then getline() will allocate a buffer for storing the line, which should be freed by the  user  pro&#8208;
gram.  (The value in *n is ignored.)

Alternatively, before calling getline(), *lineptr can contain a pointer to a malloc(3)-allocated buffer *n bytes in size.
If the buffer is not large enough to hold the line, getline() resizes it with realloc(3), updating  *lineptr  and  *n  as
       necessary.


a should either be NULL in which case getline will allocate a buffer of correct size, set n to the size and a points to this buffer.
each call to getline with a pointer to NULL as first argument will create a new buffer.

or it points to an already existing buffer in which case it will use (and overwrite) this buffer and only resize it if required.

your a is uninitialized so the behavior of getline is undefined.
this is correct:
```

char *a = NULL;
size_t n; // getline will initialize this
getline(&a,&n,stdin);

// or
size_t n = 100; // getline might update this
char *a = malloc(n);
getline(&a,&n,stdin);

```

---

### Post by c2tarun on 2011-01-01
> **MadCow108 said:**
> a program can have as many buffers as you like (as long as memory is available)
there is no single "input" buffer.
(stdin/stdout have a internal buffers, but you do not have to care about these, the system handles them)

your code is faulty in that a is not initialized.
see man getline:


a should either be NULL in which case getline will allocate a buffer of correct size, set n to the size and a points to this buffer.
each call to getline with a pointer to NULL as first argument will create a new buffer.

or it points to an already existing buffer in which case it will use (and overwrite) this buffer and only resize it if required.

your a is uninitialized so the behavior of getline is undefined.
this is correct:
```

char *a = NULL;
size_t n; // getline will initialize this
getline(&a,&n,stdin);

// or
size_t n = 100; // getline might update this
char *a = malloc(n);
getline(&a,&n,stdin);

```

awsome explanation, Thanks :)
Can you please tell me the difference between:
char *p="Hello World"; and 
char p[]="Hello World";

one functional difference I found is in first case we can't change the value, in second we can.

---

### Post by MadCow108 on 2011-01-01
> **c2tarun said:**
> awsome explanation, Thanks :)
Can you please tell me the difference between:
char *p="Hello World"; and 
char p[]="Hello World";

one functional difference I found is in first case we can't change the value, in second we can.

The difference is one is a pointer and one is an array. Although these two objects behave similar they are not equivalent.

string literals (= "Hello world" in source) are saved into a read only section of the process. In the code the literal then gets replaced with a pointer to this location.
So
const char * a = "literal";
is a pointer to this read only memory which you cannot change.

Whereas:
const char a[] = "literal";
is an array on the stack (which is read/write memory) which gets filled with a copy from the data in read only memory.
Thus it can be modified but it will also be deleted when it goes out of scope.

to illustrate see this:
```

#include<stdio.h>

int main(void)
{
  const char * a = "Hello World";
  const char * b = "Hello World";
  char p[]="Hello World";
  const char r[]="Hello World";
  printf("%p\n", a);
  printf("%p\n", b);
  printf("%p\n", "Hello World");
  printf("%p\n", p); // implicit conversion of array to const char*
  printf("%p\n", r);
  printf("%llu\n", p -r);
}

output:
0x40075c
0x40075c
0x40075c
0x7fff422bd7c0
0x7fff422bd7b0
16

```
"Hello World" is saved only once, so each reference points to the same location
but the array has a different address (on the stack)
you also see the second stack array gets placed 16 byte after the first, not 12 bytes as the string is long.
This is because it is aligned on a 8byte boundary (for 64 bit systems) to speed up memory access

---

### Post by c2tarun on 2011-01-01
> **MadCow108 said:**
> The difference is one is a pointer and one is an array. Although these two objects behave similar they are not equivalent.

string literals (= "Hello world" in source) are saved into a read only section of the process. In the code the literal then gets replaced with a pointer to this location.
So
const char * a = "literal";
is a pointer to this read only memory which you cannot change.

Whereas:
const char a[] = "literal";
is an array on the stack (which is read/write memory) which gets filled with a copy from the data in read only memory.
Thus it can be modified but it will also be deleted when it goes out of scope.

to illustrate see this:
```

#include<stdio.h>

int main(void)
{
  const char * a = "Hello World";
  const char * b = "Hello World";
  char p[]="Hello World";
  const char r[]="Hello World";
  printf("%p\n", a);
  printf("%p\n", b);
  printf("%p\n", "Hello World");
  printf("%p\n", p); // implicit conversion of array to const char*
  printf("%p\n", r);
  printf("%llu\n", p -r);
}

output:
0x40075c
0x40075c
0x40075c
0x7fff422bd7c0
0x7fff422bd7b0
16

```"Hello World" is saved only once, so each reference points to the same location
but the array has a different address (on the stack)
you also see the second stack array gets placed 16 byte after the first, not 12 bytes as the string is long.
This is because it is aligned on a 8byte boundary (for 64 bit systems) to speed up memory access

So this means that whenever we try to initialize a String literal, compiler checks it against all the string literals saved and then operate accordingly. For a big applications having millions of string literals, these comparisons could be a considerable overhead?

---

### Post by MadCow108 on 2011-01-01
it is only overhead during the compilation/linking. But it is not high as string lookups can be done in constant times when using a hash table or a radix tree.
Compared to other steps in creating an executable (like the optimization) this is completely negligible.
The gain is decreased memory usage as each literal is only saved once no matter how often is used.
Also how exactly literals are handled may be implementation dependent, other compilers could handle them differently (like using reference counting and removing them when not needed anymore).

During application runtime it plays no role as the literals are just replaced by pointers.

---

### Post by c2tarun on 2011-01-01
> **MadCow108 said:**
> it is only overhead during the compilation/linking. But it is not high as string lookups can be done in constant times when using a hash table or a radix tree.
Compared to other steps in creating an executable (like the optimization) this is completely negligible.
The gain is decreased memory usage as each literal is only saved once no matter how often is used.

During application runtime it plays no role as the literals are just replaced by pointers.


Thanx a lot :)

---

