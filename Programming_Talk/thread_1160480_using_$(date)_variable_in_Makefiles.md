---
title: "using $(date) variable in Makefiles"
date: 2009-05-15
forum: Programming Talk
---

### Post by hraiesi on 2009-05-15
Hi,
I would like to stamp my binary files with a text that shows the date of compilation and other information (ie svn version or so on) through the makefile. for examples,

```

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char* argv[])
{
    printf("BUILD_INFO = %s\n", BUILDINFO);
}

```

then I compile:
$cc -DBUILDINFO="\"$(date)\"" stampinfo.c -o stamp.exe

and run

$./stamp.exe
the output would be
BUILD_INFO = Fri May 15 16:53:07 EDT 2009

now if I put the same code in a makefile, 

```

CC = cc
CFLAGS = -DBUILDINFO="\"$$(date)\""

all:
    $(CC) $(CFLAGS) -o stamp.exe stampinfo.c

```

$make
cc -DBUILDINFO="\"$(date)\"" -o stamp.exe stampinfo.c

when I run, It gives me "$(date)", the literal characters, not the actual date of compilation!

$./stamp.exe
BUILD_INFO = $(date)

any help would be appreciated.

-h

---

### Post by dwhitney67 on 2009-05-15
This works for me....

showdate.c:
```

#include <stdio.h>

#ifndef DATE
#define DATE "unknown"
#endif

int main()
{
  printf("%s\n", DATE);
  return 0;
}

```

Makefile:
```

APP  = showdate

SRCS = showdate.c
OBJS = $(SRCS:.c=.o)

CFLAGS = -DDATE="\"`date`\""

$(APP): $(OBJS)
        $(CC) $^ -o $@

clean:
        $(RM) $(OBJS)
        $(RM) $(APP)

```

---

### Post by Arndt on 2009-05-16
> **dwhitney67 said:**
> This works for me....

showdate.c:
```

#include <stdio.h>

#ifndef DATE
#define DATE "unknown"
#endif

int main()
{
  printf("%s\n", DATE);
  return 0;
}

```

Makefile:
```

APP  = showdate

SRCS = showdate.c
OBJS = $(SRCS:.c=.o)

CFLAGS = -DDATE="\"`date`\""

$(APP): $(OBJS)
        $(CC) $^ -o $@

clean:
        $(RM) $(OBJS)
        $(RM) $(APP)

```

The original version works for me. I wonder what the difference is between my environment and that of the OP. Maybe what shell 'make' uses, or something about 'make' itself.

---

