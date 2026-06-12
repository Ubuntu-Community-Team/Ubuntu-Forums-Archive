---
title: "C, assigning a char to a string array."
date: 2009-06-03
forum: Programming Talk
---

### Post by RossR on 2009-06-03
I think I understand it, but I would be grateful for someone to double check.

If I run the following code

```

char* strings[MAXSTRINGS];

*strings[0] = 'a';
strings[0]++;
*strings[0] = '\0';

```

I get a segfault, because I am trying to assign a character to a variable that doesn't exist, so I need to use malloc() for every character I want copied. 

However the code:

```

*strings[0] = "A"

```

Will create a string and point to the beginning of the string.

Thanks

---

### Post by Mirge on 2009-06-03
```

#include <stdio.h>

#define MAX_STRINGS 5

int main(int argc, char** argv)
{
    char *strings[MAX_STRINGS]; // Array of char pointers... MAX_STRINGS is 5, so 5.
    
    strings[0] = "This is line 1";
    strings[1] = "This is line 2";
    strings[2] = "This is line 3";
    strings[3] = "This is line 4";
    strings[4] = "This is line 5";
    
    printf("%s\n%s\n%s\n%s\n%s\n", strings[0], strings[1], strings[2], strings[3], strings[4]);
    
    return 0;
}

```

Output:
```

mike@mike-kubuntu:~/c$ ./test
This is line 1
This is line 2
This is line 3
This is line 4
This is line 5
mike@mike-kubuntu:~/c$ 

```

---

### Post by Mirge on 2009-06-03
Another example..

```

#include <stdio.h>
#include <string.h>

#define MAX_STRINGS 5

int main(int argc, char** argv)
{
    char *strings[MAX_STRINGS]; // Array of char pointers... MAX_STRINGS is 5, so 5.
    int i;
    
    strings[0] = "This is line 1";
    strings[1] = "This is line 2";
    strings[2] = "This is line 3";
    strings[3] = "This is line 4";
    strings[4] = "This is line 5";
    
    printf("%s\n%s\n%s\n%s\n%s\n", strings[0], strings[1], strings[2], strings[3], strings[4]);
    
    // This will demonstrate iterating through each character in strings[0] (the first string).
    for(i = 0; i < strlen(strings[0]); i++) {
        printf("strings[i]: %c\n", strings[0][i]);
    }
    
    return 0;
}

```

Output:
```

mike@mike-kubuntu:~/c$ ./test
This is line 1
This is line 2
This is line 3
This is line 4
This is line 5
strings[i]: T
strings[i]: h
strings[i]: i
strings[i]: s
strings[i]:  
strings[i]: i
strings[i]: s
strings[i]:  
strings[i]: l
strings[i]: i
strings[i]: n
strings[i]: e
strings[i]:  
strings[i]: 1
mike@mike-kubuntu:~/c$

```

---

### Post by Can+~ on 2009-06-03
> **RossR said:**
> I think I understand it, but I would be grateful for someone to double check.

If I run the following code

```

char* strings[MAXSTRINGS];

*strings[0] = 'a';
strings[0]++;
*strings[0] = '\0';

```

I get a segfault, because I am trying to assign a character to a variable that doesn't exist, so I need to use malloc() for every character I want copied. 

However the code:

```

*strings[0] = "A"

```

Will create a string and point to the beginning of the string.

Thanks

The thing is that you're creating N (N = MAXSTRINGS) char* with the above syntax.

```
char *p;
```

One char pointer named p.

```
char *p[5];
```

Five char pointers inside, where the first one is pointed by p.

I feel that you're trying to create N strings of a length of L, say:

```
#define MAX_LENGTH 100
...
char strings[MAX_STRINGS][MAX_LENGTH];
```

The biggest issue about strings in C, is that, in fact, creating a new "char mystring[20]" creates a pointer to the first element of a reserved space on the call stack, where [x] is a wrapper for pointer arithmetic. Creating a "char *mystring[20]" creates a pointer to the first element of a set of char*, each one of this char* could be pointing anywhere in memory.

---

### Post by Habbit on 2009-06-03
By the way, you should not assign a string literal "like this one" to a char* pointer because many compilers (among them gcc) like to put the string literals in read-only data memory, so that repeated literals don't waste more memory and more optimization-related reasons. If you assign them to a char*, you are either getting in the way the compiler, or (even worse) heading towards a painful bug. Thus, use const char* for string literals and "char* strdup(const char* str)" when you need to modify (a copy of) one.

---

### Post by monkeyking on 2009-06-04
> **Habbit said:**
> Thus, use const char* for string literals and "char* strdup(const char* str)" when you need to modify (a copy of) one.

Yes this is quite important.

But strdup is not part of ansi c,
so a malloc followed by a strcpy could be better.

---

### Post by alternatealias on 2009-06-04
> **monkeyking said:**
> Yes this is quite important.

But strdup is not part of ansi c,
so a malloc followed by a strcpy could be better.

Every system you are ever likely to come across has strdup(). It is part of POSIX, SVr4, and 4.3BSD which means every modern UNIX system (as in, the last 10-15 years) has it as does Windows since at least Windows98.

---

### Post by monkeyking on 2009-06-04
If you are programming for computers thats correct.

But embedded devices, is not likely to have it.

---

