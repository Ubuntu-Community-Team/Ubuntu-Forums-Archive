---
title: "[SOLVED] Pointer Troubles"
date: 2008-07-22
forum: Programming Talk
---

### Post by British0zzy on 2008-07-22
I have only just learned about pointers in C and as practice I am writing a function which finds the rightmost occurrence of the string t in a string s.
The program I wrote to test the function prints the input, and only prints the output if the function returns a positive integer.
Here are my test input and output:
```
oula //input
oula //output: incorrect
1    //output
oulb //input
oulb //output: incorrect
1
could
could //output: correct
2
coulb
coulb //output: incorrect
2
ould ould
ould ould //output: correct
6
ould could o
ould could o //output: incorrect
8
ould could ou
ould could ou //output: correct
7
ould could oul
ould could oul //output: incorrect
9
ould could ould
ould could ould //output: correct
12

```

Here is the function so far:
```
/* strrindex: returns the position of the rightmost
   occurance of t in s, or -1 if there is none. */
int strrindex(char *s, char *t)
{
    int i = 0;
    char *p = t;    /* p is a temporary pointer to preserve t and s */
    
    while (*(s+i))      /* find end of s */
        i++;
    while (*p) {    /* find first space available for t */
        p++;
        i--;
    }
    for (p = (s+i); i >= 0; p = (s + (--i))) {  /* check each position of s for t */
        while (*(p++) == *(t++) && *t != '\0')
            ;
        if (*t == '\0')
            return i + 1;
    }
    return -1;
}
```

Do you have any suggestions to attacking this problem? Am I doing it right or is there a much easier way?
Thanks.

---

### Post by British0zzy on 2008-07-22
ok, i have just realized the first problem. t is not reset when the for loop resets itself. Is there any way to point t to the beginning of the array?

Here is what I have now:
```
/* strrindex: returns the position of the rightmost
   occurence of t in s, or -1 if there is none. */
int strrindex(char *s, char *t)
{
    int i = 0;
    char *p = t;    /* p is a temporary pointer to preserve t and s */
    
    while (*(s+i))      /* find end of s */
        i++;
    while (*p) {    /* find first space available for t */
        p++;
        i--;
    }
    for (p = (s+i); i >= 0; p = (s + (--i))) {  /* check each position of s for t */
        while (*(p++) == *(t++) && *t != '\0')
            if (*t == '\0'
                return i + 1;
        /* need to point t to beginning of array */
    }
    return -1;
}
```

---

### Post by nvteighen on 2008-07-23
What you probably need is:

1. Use a[i] notation for arrays instead of the more obfuscated *(a+i). That will avoid any pointer arithmetics and you'll not need to "reset" t to the beginning, just access t[0] instead.

2. To calculate strings' length, we have strlen() in the C Standard Library. Use #include <string.h>.

And, if I recall correctly (and if I understood what you want), in string.h there's also a function that does exactly what you're trying to do. But, of course, if you're learning, it's worth to "waste" your time reimplementing things... just be always aware of the alternatives, even if you don't use them. A nice experiment would be, after having got your version work, to try using that function and compare how it works compared to yours.


3. Reverse traversing could be done this way, for example:
```

int i;
for(i = 1; i <= length; i++)
    a[length - i] = 0;

```

*I* personally like to have always i incremented... and I believe it's more understandable... The reasonale behind is this: arrays go from 0 to length - 1, so with i = 1, (length - i) starts effectively in the last member. Then, i must be incremented that way till we reach length - i = 0, hence the condition (i <= length). Of course, there are probably a million ways to do this... Just showing what I like most.

Some ideas...

---

