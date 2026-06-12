---
title: "fflush (stdin): Another reason I dislike MS"
date: 2005-10-29
forum: Programming Talk
---

### Post by Buffalo Soldier on 2005-10-29
ATTN: This is for newbies to programming. I guess the pros must have known this all along.

I'm taking a subject called Programming Principles and Techniques. Basically it's an intro to programing class using C languange. The IDE installed at the computer lab and classroom is MS Visual C++. And after each lecture, I went back home at tried the lesson on Ubuntu using Anjuta. All went fine, until the lecturer teaches about fflush (stdin). Here's what I found out.

This is the problem that my lecturer ask us to solve:
```
#include <stdio.h>

int main()
{
    int n;
    char string[80];
    for (n=0; n<5; n++)
        {
            printf ("Enter some words: ");
            scanf ("%s", string);
            printf ("The first word you entered is : %s\n", string);
        }
    return 0;
}
```

This is the suggested solution:
```
#include <stdio.h>

int main()
{
    int n;
    char string[80];
    for (n=0; n<5; n++)
        {
            printf ("Enter some words: ");
            scanf ("%s", string);
            printf ("The first word you entered is : %s\n", string);
            **fflush (stdin);**
        }
    return 0;
}
```

To my surprise, it only works in Windows. In Linux, it ran the same with and without fflush (stdin). After searching the net, I have found that:[list]
[*] [Why fflush(stdin) is wrong](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1052863818&id=1043284351), and
[*] [Things to Avoid in C/C++ -- fflush(stdin)](http://www.gidnetwork.com/b-57.html).[/list]

According to [Things to Avoid in C/C++ -- fflush(stdin)](http://www.gidnetwork.com/b-57.html), it is best to avoid using **scanf**. But that's the only input method my lecturer has taught so far, and I wish not to confuse myself (and my classmates that I'm gonna have to share this with later) with other input methods.

Further search on the net lead me to these solution that works both in GNU/Linux and Windows:
```
#include <stdio.h>

int main()
{
    int n;
    char string[80];
    for (n=0; n<5; n++)
        {
            printf ("Enter some words: ");
            scanf ("%s", string);
            printf ("The first word you entered is : %s\n", string);
            **while (getchar() != '\n') continue;**
        }
    return 0;
}
```

```
#include <stdio.h>

**void clear_kb(void);**

int main()
{
    int n;
    char string[80];
    for (n=0; n<5; n++)
        {
            printf ("Enter some words: ");
            scanf ("%s", string);
            printf ("The first word you entered is : %s\n", string);
            **clear_kb();**
        }
    return 0;
}

[b]void clear_kb(void)
{
    char junk[255];
    fgets (junk,255,stdin);
}[/b]
```

Why can't MS just use the standard (ANSI) C???

---

### Post by David Marrs on 2005-10-29
Because they don't need to? MS are in the business of supporting Windows, not Linux. You may find that they have a compatibility mode, like gcc does. I know that Windows has a POSIX layer, for example.

---

### Post by twizard on 2013-01-21
thanks man :D

---

### Post by Bachstelze on 2013-01-21
Just to set things straight:

1) The fact that a vendor supports some things that are non-standard in itself is not an argument against that vendor, because all vendors do. Yes, Linux included.

2) The C99 standard (and probably C89 as well) leaves unspecified the behaviour of fflush() on anything other than an output stream or a null pointer. Thus an implementation is free to do whatever it wants when fflush() is given any other kind of argument, and Microsoft is not breaking the standard by making its implementation behave differently from Linux's.

3) It is not Microsoft who wrote the lecture and suggested to use fflush(stdin), so if anything, the blame should be on the instructor. And even then, if the course specifically targets Windows, the blame should be put on the student for enrolling in it and expecting something else.

---

### Post by xb12x on 2013-01-21
***Another reason I dislike MS***

Rather than the exhibiting the popular knee-jerk reaction when confronted with something like this, you should view it as an opportunity. This is the type of knowledge that separates the good programmers from the average, the in-demand professionals from the hobbyists.

Intel's complicated segmented x86 architecture is another such opportunity. Many complain and whine about it, while others have successful careers because of it.

---

