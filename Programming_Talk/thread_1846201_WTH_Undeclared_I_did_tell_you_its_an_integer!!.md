---
title: "WTH?? Undeclared? I did tell you its an integer!!"
date: 2011-09-18
forum: Programming Talk
---

### Post by debd on 2011-09-18
```
#include <stdio.h>
#define buff 2000
#define in 1
#define out 0
void main(void)
{
    int i, buff, state, beg, j, space_indx;
    char s[buff], ch;
    state = 1, beg = 0, space_indx = 0;
    for (i=1; i<=buff; i++)
    {
        ch=getchar();
        s[i]=ch;
    }
    for (i=1; i<=(buff/30); i++)
    {
        for (j=(beg+1); j<=(30+beg); j++)
        {
            if (s[j]== '\b')
            {
                //state=out;
                if (j>space_indx)
                    space_indx=j;
            }
        }
        while (beg<=space_indx)
        {
            printf("%c", s[beg]);
            beg++;
        }
        printf("\n");
        beg=space_indx;
    }
}

```I was trying to make a little line wrap program....
but the programming context isn't an issue here. I'm using geany to write the code and gcc to compile.
and all the while these errors are bugging me the most:

```
gcc -Wall -c "linewrap.c" (in directory: /home/debd/scripts)
Compilation failed.
linewrap.c:8: error: expected identifier or &#8216;(&#8217; before numeric constant
linewrap.c:10: error: &#8216;[COLOR=DarkRed]state[/COLOR]&#8217; undeclared (first use in this function)
linewrap.c:10: error: (Each undeclared identifier is reported only once
linewrap.c:10: error: for each function it appears in.)
linewrap.c:10: error: &#8216;[COLOR=DarkRed]beg[/COLOR]&#8217; undeclared (first use in this function)
linewrap.c:10: error: &#8216;[COLOR=DarkRed]space_indx[/COLOR]&#8217; undeclared (first use in this function)
linewrap.c:10: warning: left-hand operand of comma expression has no effect
linewrap.c:18: error: &#8216;[COLOR=DarkRed]j[/COLOR]&#8217; undeclared (first use in this function)

```now HTH  [COLOR=DarkRed]j[/COLOR], [COLOR=DarkRed]space_indx[/COLOR], [COLOR=DarkRed]state[/COLOR] and [COLOR=DarkRed]beg[/COLOR] went undeclared??

---

### Post by JDShu on 2011-09-18
You've defined buff as a constant, and then tried to initialize a variable to buff. So in line 8 you have the equivalent of "int 2000" which doesn't make sense to the compiler.

---

### Post by N1GHTS on 2011-09-18
**debd:**

I know what you were trying to do, but you didn't do it right.

```

// This is what you did and got an error
#define buff 2000
int buff;

// This is what you meant to do and should do
#define BUFF 2000
int buff = BUFF;

```The compiler will use your #define macro kind of like a "search and replace" using the given number. So since you cant make a variable name that is a number, "int 2000;" is wrong, but "int buff = 2000;" is right.

---

### Post by debd on 2011-09-19
oww.. thanks guys!

---

