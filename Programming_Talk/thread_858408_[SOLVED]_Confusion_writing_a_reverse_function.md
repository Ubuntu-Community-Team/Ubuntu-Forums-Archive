---
title: "[SOLVED] Confusion writing a reverse function"
date: 2008-07-13
forum: Programming Talk
---

### Post by British0zzy on 2008-07-13
Hi,
so I've only been programming for about a week, and it's going pretty well. I got a copy of Prentice Hall's _The C Programming Language Second Edition_. One of the challenges was to reverse each line of text input. I've cobbled together this piece of code (I know, it sucks) and I get a segmentation fault error when I run the program.
```
#include <stdio.h>
#define MAXLINE 1000

int getline(char line[], int maxline);
void reverse(char line[], int length);

main()
{
    int length;
    char line[MAXLINE];
    
    while ((length = getline(line, MAXLINE)) > 0)
        if (length > 1) {
            while (line[length - 2] == ' ' || line[length - 2] == '\t') {
                line[length - 2] = line[length - 1]; // Removes all trailing 
                line[length - 1] = line[length];     // blanks and tabs
                --length;
            }
            reverse(line, length);
            printf("%s", line);
        }
    return 0;
}

int getline(char s[], int lim)
{
    int c, i;
    
    for (i = 0; i < lim - 1 && (c = getchar()) != EOF && c != '\n'; ++i)
        s[i] = c;
    if (c == '\n') {
        s[i] = c;
        ++i;
    }
    s[i] = '\0';
    return i;
}

void reverse(char line[], int l)
{
    int i, j;
    char temp[l + 1];
    
    i = 0;
    while ((temp[l - i] = line[i]) != '\n' || line[i] != '\0')
        ++i;
    for (j = 0; i >= 0; ++j, --i)
        line[j] = temp[l - i];
    line[l + 1] = '\n';
}
```

---

### Post by johnl on 2008-07-13
Take a look at the getline function ('man 3 getline')
```

ssize_t getline(char **lineptr, size_t *n, FILE *stream);

```

That should make reading input easier for you.

Reversing the string is pretty easy:

```

/* not tested! */
void str_reverse(char* str)
{
    char temp;
    int len = strlen(str);
    int halfway = len / 2;
    int i;
    /* go through the halfway point */
    for (i = 0; i < halfway; ++i) {
       /* swap corresponding characters */
       temp = str[i];
       str[i] = str[len = (i + 1)];
       str[len - (i + 1)] = temp;
    }  
    /* tada */
    return;
}

```

---

### Post by Phenax on 2008-07-13
Use GNU Debugger (gdb) to debug your program.

A quick how-to for (very) basic debugging:

Compile your program with debugging symbols:
```

gcc -g -ggdb program.c

```Launch GDB:
```

gdb

```In the GDB console, select executable:
```

file a.out

```Launch Program:
```

run

```Run program like normal, and it will give you the line of code that is causing the problem. Things like the 'backtrace' command are also useful, but you should read gdb manual pages and whatnot for more information.

For reference, in one of your while lines you have "=" instead of "==" which causes the segfault, don't think that was intentional.

---

### Post by British0zzy on 2008-07-13
So I rewrote the reverse function to this:
```
void reverse(char line[], int l)
{
    int i, j;
    char temp[l + 1];
    
    i = 0;
    while (line[i] != '\n' || line[i] != '\0') {
        temp[l - i] = line[i];
        ++i;
    }
    for (j = 0; i >= 0; ++j, --i)
        line[j] = temp[l - i];
    line[l + 1] = '\n';
}
```
And the gdb gave me this message:
```
Program received signal EXC_BAD_ACCESS, Could not access memory.
Reason: KERN_INVALID_ADDRESS at address: 0xc0000000
0x00001fa6 in reverse (line=0xbffff5f4 "reverse\n", l=8) at /Users/Mystery/Sites/Code/ReverseLine.c:45
45	    while (line[i] != '\n' || line[i] != '\0') {

```
From what I gather there is a problem in the while loop?
If so, I can't see any problem with it. Why can't I set temp[l-i]=line[i]?

Could you also point me in the direction of a good GNU Debugger Manual? Btw, I am doing this all on OSX, so do any of you know good tools that would help me debug programs? (I know OSX comes with GNU Compiler and Debugger)

---

### Post by ceclauson on 2008-07-13
I've only spent about a minute looking at your source code, but I very strongly suspect that the error is caused by your trying to access an array element that is beyond the size of the array.  This is a common cause of a segmentation fault runtime error.

For instance, if you declare an array of length 6, and try to access the 7th element, you'll get this error (you'll also get it if you try to access the 6th element, as arrays are indexed from 0).

The other context I've seen this error raised is with null pointers.  But because I don't see anything like that happening in your program, I'm guessing it's an array index out of bounds issue.

Cooper

---

### Post by johnl on 2008-07-13
It looks to me like the problem is with your while statement.  I think you are using an 'or' when you should be using an 'and'.

```

// this loop will never terminate. if the first condition
// is false, the second must be true.  If the second
// condition is false, the first must be true.
while (a != x || a != y) {

}

```

You probably meant:
```

// loop until we encounter newline or null terminator.
while (line[i] != '\n' && line[i] != '\0') {

}
```

---

### Post by British0zzy on 2008-07-13
Ah, yea the OR operator was the problem. For some reason I convinced myself it was the other way round.
Thanks to everyone who posted!
(btw, this forum rocks, i got a response within 25min AND it was constructive :))

---

