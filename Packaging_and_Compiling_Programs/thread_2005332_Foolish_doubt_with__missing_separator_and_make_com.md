---
title: "Foolish doubt with *** missing separator and make command"
date: 2012-06-17
forum: Packaging and Compiling Programs
---

### Post by indarkness on 2012-06-17
Hi, after so long without using make, I know have to use it again, and I'm having got trouble with it, specially with the parsing...
I have got two files in mi directory src:
helloworld.c
make
 
when I use the make command like this
```
 make cc -f helloworld.c cc helloworld.o -o helloworld

```I get the error 
> helloworld.c:1: *** missing separator. Stop.the content of helloworld.c is
```
/**
*Helloworld.c
*The most simplistic C program ever
**/
#include <stdio.h>
int main(void)
{
    printf("Hello this works\n\n");
    return 0;
}
```and the make is
```
# build helloworld executable when user executes "make" 
 
helloworld: helloworld.o
    $(CC) $(LDFLAGS) helloworld.o -o helloworld
helloworld.o: helloworld.c 
    $(CC) $(CFLAGS) -c helloworld.c 
# remove object files and executable when user executes "make clean"
clean:
    rm *.o helloworld 
```I am using gedit to write the files, I have used the command *od -t c make* with my make file in order to see whether the \t are there or not, and they are, so I don't know the reason of the error... Could you help me?
 
THanks in advance,

---

