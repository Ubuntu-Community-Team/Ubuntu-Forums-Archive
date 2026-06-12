---
title: "&quot;****missing separator&quot; and make command"
date: 2012-06-17
forum: Programming Talk
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

### Post by MG&amp;TL on 2012-06-17
You need to indent the commands from the targets with a tab. You can't type a tab on here, so I'll just leave it to your imagination:

```
clean:
    rm *.o helloworld
```

Edit: just saw the bottom lines. Can you attach your files?

---

### Post by indarkness on 2012-06-17
> **MG&TL said:**
> You need to indent the commands from the targets with a tab. You can't type a tab on here, so I'll just leave it to your imagination:
Here , there are the files, I have attached the src folder with both files.
```
clean:
    rm *.o helloworld
```Edit: just saw the bottom lines. Can you attach your files?

Thanks in advance!!

---

### Post by MG&amp;TL on 2012-06-17
Erm. It runs fine here, all I have to do is run:

```
make
```...how are you running it?

Btw, *make* can work out how to create object files, so you can just have a Makefile like this:

```
helloworld: helloworld.o
    $(CC) $(LDFLAGS) helloworld.o -o helloworld

clean:
    rm *.o helloworld

```

---

### Post by dwhitney67 on 2012-06-17
> **MG&TL said:**
> 
Btw, *make* can work out how to create object files, so you can just have a Makefile like this:


And to further simplify matters, a Makefile is not necessary at all for trivial programs.  All the OP has to enter from the command line is:
```

make helloworld

```
P.S.  To further clarify, the OP should remove the Makefile (or rename it).

---

### Post by MG&amp;TL on 2012-06-18
> **dwhitney67 said:**
> And to further simplify matters, a Makefile is not necessary at all for trivial programs.  All the OP has to enter from the command line is:
```

make helloworld

```P.S.  To further clarify, the OP should remove the Makefile (or rename it).


Yes. Just the OP seemed to want a makefile. :D

---

### Post by indarkness on 2012-06-18
> **MG&TL said:**
> Erm. It runs fine here, all I have to do is run:
 
```
make
```...how are you running it?
 
Btw, *make* can work out how to create object files, so you can just have a Makefile like this:
 
```
helloworld: helloworld.o
    $(CC) $(LDFLAGS) helloworld.o -o helloworld
 
clean:
    rm *.o helloworld

```
 
I' running it in the consolo with this command
```
make cc -c helloworld.c cc helloworld.o -o helloworld

```

---

### Post by Tony Flury on 2012-06-18
just type
```

make helloworld

```

as already suggested.

---

### Post by indarkness on 2012-06-18
> **dwhitney67 said:**
> And to further simplify matters, a Makefile is not necessary at all for trivial programs. All the OP has to enter from the command line is:
```

make helloworld

```
P.S. To further clarify, the OP should remove the Makefile (or rename it).
 
Yes I know that it's quite simple code and I don't need to create a make,but this is the pre-phase to create a make file for compiling C code in a router, so I was refreshing how to create the make files.
 
Thanks again, I'm going to run it again.

---

### Post by indarkness on 2012-06-18
> **Tony Flury said:**
> just type
```

make helloworld

```
 
as already suggested.
 
From the directory in which I have my makefile, right??

---

### Post by Tony Flury on 2012-06-18
yes

---

### Post by indarkness on 2012-06-18
Thanks all for helping me, now it works, I've run both( I know only one is necessary but I've try both)

```
make helloworld
```and 
```
make
```from the directory my makefile is in, and it works!!:P:P

---

