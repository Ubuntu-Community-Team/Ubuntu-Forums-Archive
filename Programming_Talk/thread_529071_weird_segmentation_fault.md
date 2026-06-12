---
title: "weird segmentation fault"
date: 2007-08-18
forum: Programming Talk
---

### Post by abadfish on 2007-08-18
I'm not sure why I'm getting a segmentation fault with my code.

here is my code:
```

#include <stdio.h>
#include <string.h>

void revstring(char *pstr);
void printSymbol(char **str, int rows);
void revSymbol(char **str, int rows);

int main(void)
{

    char *str[5] =
    {
        "1    ****   5",
        "2    *      4",
        "3    ***    3",
        "4    *      2",
        "5    *      1"
    };
    char str1[] = "purple is power";

    printf("%s\n", str1);
    revstring(str1);
    printf("%s\n", str1);

    printSymbol(str, 5);
    revSymbol(str, 5);

    return 0;
}

void revSymbol(char **str, int rows)
{
     while (rows--)
    {
            revstring(str[rows]);
    }
}

void printSymbol(char **str, int rows)
{
        int i;

        for (i = 0; i < rows; i++)
        {
                printf("%s\n", str[i]);
        }
}

void revstring(char *pstr)
{
        char *pend;
        char temp;

        if (!pstr) return;

        pend = (char *) (pstr + (strlen(pstr) - 1));
        while (pstr < pend)
        {
                temp = *pstr;
                *pstr++ = *pend;
                *pend-- = temp;
        }
}

```

Here's the output:
```

[FONT="Fixedsys"]% Bubba % revstring
purple is power
rewop si elprup
1    ****   5
2    *      4
3    ***    3
4    *      2
5    *      1
Segmentation fault (core dumped)
% Bubba % [/FONT]

```

The function revstring() is supposed to take in a string and reverse the order of the characters in the string (except for the null terminator).  It works fine for the first string ("purple is power") but  when I try to use it for reversing the ascii block, it chokes when I try to swap the first characters.

Any thoughts??.

---

### Post by abadfish on 2007-08-18
the above code was compiled with gcc with no optional parameters

---

### Post by slavik on 2007-08-19
```
void revSymbol(char **str, int rows)
{
     while (rows--)
    {
            revstring(str[rows]);
    }
}
```

try printing the string right after it is reversed, I have a suspicion that rows-- might occur after the entire body of the loop (since trailing -- doesn't guarantee exactly how much after the statement it gets executed).

or at least print the rows variable in the loop, so we know what piece of memory the code tries to access.

In any case, segfaults happen when you try to access/write memory you have no business touching.

EDIT: I am debugging your code, and it is weird or I am missing something (everything seems kosher in gdb)

---

### Post by Wybiral on 2007-08-19
> **slavik said:**
> ... and it is weird or I am missing something ...

It's called a string literal.

There is a difference in definition between "char[]" and "char*" and that is the fact that "char*" results in a pointer to the string literal... You have an array of literals and you cannot modify their characters (it results in "undefined behavior").

---

### Post by slavik on 2007-08-19
> **Wybiral said:**
> It's called a string literal.

There is a difference in definition between "char[]" and "char*" and that is the fact that "char*" results in a pointer to the string literal... You have an array of literals and you cannot modify their characters (it results in "undefined behavior").

right, now I am starting to remember ... need to code more in C :P

---

### Post by Wybiral on 2007-08-19
For further proof try changing:

```

char str1[] = "purple is power";

```

To:

```

char *str1 = "purple is power";

```

And see where it segfaults. It's a tricky concept... One that often slips by undetected.

---

### Post by slavik on 2007-08-19
I did after your previous and it works out as expected. (segfaults).

---

### Post by abadfish on 2007-08-19
> **Wybiral said:**
> It's called a string literal.

There is a difference in definition between "char[]" and "char*" and that is the fact that "char*" results in a pointer to the string literal... You have an array of literals and you cannot modify their characters (it results in "undefined behavior").

Ok, I see what you're saying.  Here's what I redeclared str to the following to make this work:

```

    char str2[] = "1    ****    5";
    char str3[] = "2    *       4";
    char str4[] = "3    ***     3";
    char str5[] = "4    *       2";
    char str6[] = "5    *       1";
    char *str[5] = 
    {
        str2, str3, str4, str5, str6
    };

```

This seems kludgy to me.  Is there a better way to have declared the "symbol"????

---

### Post by Wybiral on 2007-08-19
> **abadfish said:**
> Is there a better way to have declared the "symbol"????

You can create a type for "symbol". If you plan to use more then one, that's definitely what I'd do.

You can copy the constant strings into a string that's allocated in a write-friendly area of memory.

Here's an example of what I mean:

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void revString(char *pstr)
{
    if (!pstr) return;
    char *pend;
    char temp;
    pend = (char *) (pstr + (strlen(pstr) - 1));
    while (pstr < pend)
    {
        temp = *pstr;
        *pstr++ = *pend;
        *pend-- = temp;
    }
}

typedef struct
{
    int rows;
    char **str;
} symbol;

symbol *newSymbol(char **str, int rows)
{
    symbol *sym = (symbol*)malloc(sizeof(symbol));
    if(sym == NULL) return NULL;
    int i;
    sym->rows = rows;
    sym->str = (char**)malloc(rows * sizeof(char*));
    for(i = 0; i < rows; i++)
    {
        sym->str[i] = (char*)malloc(strlen(str[i]) + 1);
        strcpy(sym->str[i], str[i]);
    }
    return sym;
}

void printSymbol(symbol *sym)
{
    int i;
    for (i = 0; i < sym->rows; i++)
    {
        printf("%s\n", sym->str[i]);
    }
}

void revSymbol(symbol *sym)
{
    int i;
    for(i = 0; i < sym->rows; i++)
    {
        revString(sym->str[i]);
    }
}

void freeSymbol(symbol *sym)
{
    int i;
    for(i = 0; i < sym->rows; i++)
    {
        free(sym->str[i]);
    }
    free(sym->str);
    free(sym);
}

int main(void)
{

    char *str[5] =
    {
        "1    ****   5",
        "2    *      4",
        "3    ***    3",
        "4    *      2",
        "5    *      1"
    };

    symbol *sym = newSymbol(str, 5);

    printSymbol(sym);

    revSymbol(sym);

    printSymbol(sym);

    freeSymbol(sym);

    return 0;
}

```

That would give you a lot more freedom to do other things with them, and it makes them a little more manageable (you can store other data with them, such as the row that I stored).

I'm sure there are quicker hacks for it, something like this definitely makes for more organized use of them.

---

### Post by abadfish on 2007-08-19
Okay, I see what you're saying there.  Because the memory is dynamically allocated, that heap space is able to be modified.

On a more "simpler" note, Is there a way to do it where you don't have to dynamically allocate???  For example, I tried the following:

```

    char[][] =
    {
        "1    ****   5",
        "2    *      4",
        "3    ***    3",
        "4    *      2",
        "5    *      1"
    };

```

But this gives me compile errors.

---

### Post by PandaGoat on 2007-08-19
I am surprised no one noticed this.  In this function:
```

void revSymbol(char **str, int rows)
{
     while (rows--)
    {
            revstring(str[rows]);
    }
}

```

The seg fault is caused by using rows--.  That operator does this:
```

rows = rows - 1;

```

Unless it is a pointer to an integer I am surprised that even works, somewhat.  Do it like this and you'll get rid of your seg fault:
```

void revSymbol(char **str, int rows)
{
     int i = rows;
     while (i--)
    {
            revstring(str[i]);
    }
}

```

---

### Post by Wybiral on 2007-08-19
> **PandaGoat said:**
> I am surprised no one noticed this.  In this function:
```

void revSymbol(char **str, int rows)
{
     while (rows--)
    {
            revstring(str[rows]);
    }
}

```

The seg fault is caused by using rows--.  That operator does this:
```

rows = rows + 1;

```

Unless it is a pointer to an integer I am surprised that even works, somewhat.  Do it like this and you'll get rid of your seg fault:
```

void revSymbol(char **str, int rows)
{
     int i = rows;
     while (i--)
    {
            revstring(str[i]);
    }
}

```

I don't see why that would make a difference, both of them are function scope variables. It would still segfault.

The problem is that (he/she)'s trying to change memory that isn't stored in a writable location.

---

### Post by abadfish on 2007-08-19
> **PandaGoat said:**
> I am surprised no one noticed this.  In this function:
```

void revSymbol(char **str, int rows)
{
     while (rows--)
    {
            revstring(str[rows]);
    }
}

```

The seg fault is caused by using rows--.  That operator does this:
```

rows = rows + 1;

```


Your post doesn't make sense!

how does the --operator, which is decrementing, become an incrementer???

> 
Unless it is a pointer to an integer I am surprised that even works, somewhat.  Do it like this and you'll get rid of your seg fault:
```

void revSymbol(char **str, int rows)
{
     int i = rows;
     while (i--)
    {
            revstring(str[i]);
    }
}

```
No, that's not right.  Your solution is no different.  All you're doing is using i the same way rows is being used.

If you read the previous posts, the cause of the segmentation fault has already been determined.

---

### Post by PandaGoat on 2007-08-19
Can't a brotha make a mistake?  I meant - instead of plus.

For some reason when I tried what I said, it got rid of the seg fault.

---

