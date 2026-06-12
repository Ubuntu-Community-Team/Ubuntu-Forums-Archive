---
title: "Header files calling header files"
date: 2009-09-14
forum: Programming Talk
---

### Post by newport_j on 2009-09-14
Here is a quick absolute. beginner question.

1. Header files can call header files.

2. If a header files name is enclosed in < > then the header is put in the included files directory.

3. If a header file is enclosed in " " then it goes in the same directory as the file that called it.

Now what if a header file in the included directory calls another header file, but that called header file is enclosed in " ". What directory does that called header file go in?

newport_j

---

### Post by Bachstelze on 2009-09-14
Why not try and find out? ;)

```
firas@tsukino test % ls -lR
.:
total 12
-rw-r--r-- 1 firas firas   78 2009-09-14 17:22 bar.h
drwxr-xr-x 2 firas firas 4096 2009-09-14 17:22 include
-rw-r--r-- 1 firas firas   57 2009-09-14 17:20 test.c

./include:
total 4
-rw-r--r-- 1 firas firas 56 2009-09-14 17:20 foo.h
firas@tsukino test % cat test.c
#include <foo.h>

int main(void)
{
        foo();
        return 0;
}

firas@tsukino test % cat include/foo.h
#include "bar.h"

int foo(void)
{
        bar();
        return 0;
}

firas@tsukino test % cat bar.h
#include <stdio.h>

int bar(void)
{
        printf("Hello, world!\n");
        return 0;
}

firas@tsukino test % cc -o test -I/home/firas/test/include test.c
In file included from test.c:1:
/home/firas/test/include/foo.h:1:17: error: bar.h: No such file or directory
firas@tsukino test % mv bar.h include
firas@tsukino test % cc -o test -I/home/firas/test/include test.c
firas@tsukino test % ./test
Hello, world!

```

Also moved to Programming Talk.

---

### Post by dwhitney67 on 2009-09-14
> **newport_j said:**
> ...
Now what if a header file in the included directory calls another header file, but that called header file is enclosed in " ". ...
I would think that this would represent yet another example of bad coding practice.

---

### Post by Bachstelze on 2009-09-14
> **dwhitney67 said:**
> I would think that this would represent yet another example of bad coding practice.

Also true...

---

### Post by Arndt on 2009-09-14
> **newport_j said:**
> Here is a quick absolute. beginner question.

1. Header files can call header files.

2. If a header files name is enclosed in < > then the header is put in the included files directory.

3. If a header file is enclosed in " " then it goes in the same directory as the file that called it.

Now what if a header file in the included directory calls another header file, but that called header file is enclosed in " ". What directory does that called header file go in?

newport_j

It depends on the particular C preprocessor implementation. Or it used to - I don't know if C99 changed anything.

---

### Post by dribeas on 2009-09-15
Within C++, you should use double quotes only to include anything that is not part of the implementation (standard headers), and angle brackets for implementation headers. Now, the fact is that all compilers treat both types of header inclusion declarations pretty similarly and in most cases mixing them is not really a problem.

I think that VS will not look in the current directory when including with angle brackets, only in the solution's include directories. Gcc will look both in the include path and in the current directory, but with a different search order, where double quotes start searching in the local path and angle brackets in the include path.

At the end, you will find that many people do not know the differences, and those who know don't care. Most people will use double quotes for project includes while angle brackets for any external dependency...

---

