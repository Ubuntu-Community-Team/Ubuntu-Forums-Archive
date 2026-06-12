---
title: "Basic confusion in C"
date: 2010-08-03
forum: Programming Talk
---

### Post by jfreak_ on 2010-08-03
Is the output of
```

printf("%d", i++)

```
and
```

printf("%d", ++i);

```

remain same across compilers ie gcc, visual c++ and borland?

I am just starting out in C.
some of the assignments questions given to me include conio.h and getchar() functons etc? what to do?

---

### Post by Bachstelze on 2010-08-03
Yes.  The behaviour of the increment operators is standard-defined.  conio.h is MS-DOS-specific, getchar() is also standard.

---

### Post by MadCow108 on 2010-08-03
getchar is not standard. it is part of the long outdated conio library.

Just ignore the assignment and use the standard functions in the stdio header instead.

the getchar equivalent is getc(), but usually it is used in examples to keep the windows terminal from closing. When compiling from a terminal in unix this is unnecessary.

---

### Post by Bachstelze on 2010-08-03
> **MadCow108 said:**
> getchar is not standard. it is part of the outdated conio library.

[quote=ANSI C]4.9.7.6 The getchar function

Synopsis

         #include <stdio.h>
         int getchar(void);

Description

   The getchar function is equivalent to getc with the argument stdin .  

Returns

   The getchar function returns the next character from the input
stream pointed to by stdin .  If the stream is at end-of-file, the
end-of-file indicator for the stream is set and getchar returns EOF .
If a read error occurs, the error indicator for the stream is set and
getchar returns EOF .
[/quote]

Won't let me post without some non-quote.

---

### Post by MadCow108 on 2010-08-03
oops I'm sorry.
I reinstalled and forget the manpages, thus I though no manpage -> no standard ^^

---

### Post by dwhitney67 on 2010-08-03
> **MadCow108 said:**
> getchar is not standard. it is part of the long outdated conio library.

getchar() is standard; you're right about 'conio.h', though.

---

### Post by StephenF on 2010-08-03
I think getch and getche are the droids you are looking for.

---

