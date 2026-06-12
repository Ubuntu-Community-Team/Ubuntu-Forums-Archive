---
title: "Linked Lists and general C advice needed"
date: 2010-04-22
forum: Programming Talk
---

### Post by Vichfret on 2010-04-22
Hi, I'm learning data structures in c, these are my libraries, can you give me some advice? also I'm trying to implement a dynamic stack and queue with these linked lists functions but when I try to compile them gcc says some functions are not defined this made me think that I don't know how to work with various libraries at the same time, please post some recommendations, corrections, etc.

---

### Post by slavik on 2010-04-22
what commands do you use to compile your code?

---

### Post by Vichfret on 2010-04-22
I use this makefile ```
all: pila

pila: stack.o cdllist.o
    gcc stack.o cdllist.o -o pila

stack.o: stack.c
    gcc -c stack.c

cdllist.o: cdllist.c
    gcc -c cdllist.c

clean:
    rm -rf *o pila
```

---

### Post by MadCow108 on 2010-04-22
you are missing a proper rule for pila.c

```
all: pila

pila: pila.o stack.o cdllist.o
	gcc pila.o stack.o cdllist.o -o pila

pila.o: pila.c
	gcc -c pila.c -o pila.o

stack.o: stack.c
	gcc -c stack.c

cdllist.o: cdllist.c
	gcc -c cdllist.c

clean:
	rm -rf *o posfija

```

---

### Post by gmargo on 2010-04-22
Off-topic Vim note:  You will be a lot happier using vim if you configure it to store your .swp files elsewhere so they don't pollute your local directory (and become part of the tar file.)

I have a $HOME/tmp/swp directory and the following in my .vimrc:
```

 set   directory=~/tmp/swp,~/tmp,~,.,/var/tmp,/tmp  " put .swp files here

```

---

### Post by gmargo on 2010-04-22
Here's the makefile the way I would write it, to leverage the built in rules.  I've added CFLAGS and LDFLAGS for demonstration purposes.  (Plus the -Wall flag which shows you a cdl_cargo declaration problem.)

```

CC=gcc
CFLAGS=-O -g -Wall
LDFLAGS=-g

OBJ=cdllist.o pila.o stack.o

all: pila

pila: $(OBJ)

cdllist.o: cdllist.c lib/cdllist.h
pila.o: pila.c lib/stack.h lib/cdllist.h
stack.o: stack.c lib/stack.h lib/cdllist.h

clean:
        rm -f *.o pila

``````

$ make
gcc -O -g -Wall   -c -o pila.o pila.c
pila.c: In function &#8216;main&#8217;:
pila.c:7: warning: unused variable &#8216;s&#8217;
pila.c:8: warning: control reaches end of non-void function
gcc -O -g -Wall   -c -o cdllist.o cdllist.c
gcc -O -g -Wall   -c -o stack.o stack.c
stack.c: In function &#8216;pop&#8217;:
stack.c:16: warning: implicit declaration of function &#8216;cdl_cargo&#8217;
gcc -g  pila.o cdllist.o stack.o   -o pila


```I don't know what problem you are seeing.  I added some crude test code to pila.c and it seems to work.

pila.c with test code:
```

#include <stdlib.h>
#include <stdio.h>

#include "lib/stack.h"

int main(int argc, char **argv) {
    int i;
    int val;

    stack s = cdl_create();

    for (i=0; i <= 9; i++)
    {
        push(s, i);
        printf("push i=%d\n", i);
    }

    for (i=9; i >= 0; i--)
    {
        val = pop(s);
        printf("pop val=%d %s\n", val, (i == val ? "OK" : "ERROR"));
    }

    val = pop(s);
    printf("pop val=%d\n", val);

    return 0;
}

```

---

