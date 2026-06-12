---
title: "[SOLVED] [C] For loop confusion"
date: 2008-08-16
forum: Programming Talk
---

### Post by British0zzy on 2008-08-16
Why does the compiler not like it when I use this code?
```
for (size_t i = 0; i < count; ++i) {
    /* code */
}
```

It gives me an error:
‘for’ loop initial declaration used outside C99 mode

I've seen other code with this type of syntax. It seems reasonable.

---

### Post by dwhitney67 on 2008-08-16
Use gcc as follows:
```
$ gcc -std=c99 myProg.c
```
I also recommend that you use the -Wall and -pedantic options.

P.S.  An easy way to setup gcc to always use these options is to insert the following statement into your ~/.bashrc file:
```
alias gcc='/usr/bin/gcc -Wall -pedantic -std=c99'
```

---

### Post by British0zzy on 2008-08-16
is std=c99 the latest standard??

---

### Post by dwhitney67 on 2008-08-16
Yes, I believe it is.  The standard, which you are using by default, is the C89 version... almost 20 years old!

With the C89 standard, one would have to declare the for-loop iterator outside the for-loop block.  This appears ugly, and also could cause an absent-minded programmer to shadow another variable with the same name that is also within scope.  Hence C99 came about to mitigate these problems and also allow programmers to declare variables in the middle of a coding block and to initialize them when declared.

---

