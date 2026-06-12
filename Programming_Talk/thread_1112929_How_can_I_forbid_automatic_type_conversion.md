---
title: "How can I forbid automatic type conversion?"
date: 2009-04-01
forum: Programming Talk
---

### Post by KIAaze on 2009-04-01
I would like to get a warning or an error message during compilation, when an "int" is automatically cast/converted to a "long long int".

How can I achieve this?

Here's what I tried so far:
cast.cpp:
```
int main(void)
{
        int x=2;
        long long int y;
        y=x;
        long long int z=3;
        int t;
        t=z;
        double D=2.5;
        int iD;
        iD=D;
        signed int A=5;
        unsigned int B=6;
        A<B;
        return 0;
}

```

```
$  g++  -Wall -Wconversion -Wextra -Wcast-qual -Wcast-align   cast.cpp   -o cast
cast.cpp: In function 'int main()':
cast.cpp:11: warning: converting to 'int' from 'double'
cast.cpp:14: warning: comparison between signed and unsigned integer expressions
cast.cpp:14: warning: statement has no effect

```

What's interesting is that I get a warning for converting a double to int, but not for converting a long long int to int.

---

### Post by slavik on 2009-04-01
please clarify what you want

---

### Post by KIAaze on 2009-04-01
I want a warning like this:
```
cast.cpp:5: warning: converting to 'long long int' from 'int'

```

I know that "int->long long int" conversion isn't dangerous (it is in the other direction), but it would allow me to quickly find error sources in my code.

P.S: Is it just me or did the forum just turn pink?

edit: Actually, now that I think of it, it probably won't help me at all, since I'm trying to avoid giving the wrong index to a vector, i.e. vector <int> V should only accept V[long long int] and not V[int]. That's the main problem...

---

### Post by Arndt on 2009-04-01
> **KIAaze said:**
> I would like to get a warning or an error message during compilation, when an "int" is automatically cast/converted to a "long long int".

How can I achieve this?

Here's what I tried so far:
cast.cpp:
```
int main(void)
{
        int x=2;
        long long int y;
        y=x;
        long long int z=3;
        int t;
        t=z;
        double D=2.5;
        int iD;
        iD=D;
        signed int A=5;
        unsigned int B=6;
        A<B;
        return 0;
}

```

```
$  g++  -Wall -Wconversion -Wextra -Wcast-qual -Wcast-align   cast.cpp   -o cast
cast.cpp: In function 'int main()':
cast.cpp:11: warning: converting to 'int' from 'double'
cast.cpp:14: warning: comparison between signed and unsigned integer expressions
cast.cpp:14: warning: statement has no effect

```

What's interesting is that I get a warning for converting a double to int, but not for converting a long long int to int.

I think you want the -Wconversion option.

```
$ gcc -Wconversion -c cast.c
cast.c: In function ‘main’:
cast.c:12: warning: conversion to ‘int’ from ‘long long int’ may alter its value
```

---

### Post by KIAaze on 2009-04-01
Mmh, I didn't get that. Apparently my gcc version is too old. I seem to have v4.2.1 instead of v4.3.2 (current Ubuntu).

It doesn't solve my problem, but from what I can see, I'll just have to check things manually and be careful.
Thanks anyway.

---

### Post by monkeyking on 2009-04-01
yes the forum is pink for me also

I don't think there are any warnings like this,
but -Wconversion might help you.

Also consider trying the sun compiler(free) or the intel compiler(free for some).
As these have more elaborate warnings.

---

