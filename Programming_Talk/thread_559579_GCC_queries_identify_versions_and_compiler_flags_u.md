---
title: "GCC queries: identify versions and compiler flags used"
date: 2007-09-25
forum: Programming Talk
---

### Post by kcy29581 on 2007-09-25
Hi all, 
 
I work as a video games tester, and I need some help regarding GCC. These are regarding tests that I need to perform. 
 
Things I need to identify: 
 - What version of the GCC compiler was used to compile our games, and 
 - Identify what compiler flags were used by our development teams 
 
Please note, I only have the final product, not the source code. 
 
I believe I know how to identify the GCC version used; I use the following command on .BIN files:
```
strings *application* | grep GCC
```
 This was answered in the following thread:
[http://ubuntuforums.org/showthread.php?t=532806](http://ubuntuforums.org/showthread.php?t=532806)
(many thanks ghostdog74!)
 
Now all I need is to figure out how to identify the compiler flags used... Any ideas? 
 


Thanks, 
 
KCy29581

---

### Post by duff on 2007-09-25
If you could get in contact with the developers, you could have them make a small change to their build system.

```
# cat hello.c 

#include <stdio.h>
int main (int argc, char *argv[]) {
        printf ("Hello, world\n");
}

# cat Makefile 

CC=gcc
CFLAGS=-O3 -Wall

LD=ld
LDFLAGS=

flags.txt:
        echo "CFLAGS=$(CFLAGS)" >$@

%.o: %.txt
        $(LD) -r -b binary -o $@ $<
        rm $<

%.o: %.c
        $(CC) $(CFLAGS) -c $< -o $@

hello: hello.o flags.o
        $(CC) $^ -o $@

# make hello
gcc -O3 -Wall -c hello.c -o hello.o
hello.c: In function ‘main’:
hello.c:5: warning: control reaches end of non-void function
echo "CFLAGS=-O3 -Wall" >flags.txt
ld -r -b binary -o flags.o flags.txt
rm flags.txt
gcc hello.o flags.o -o hello

# ./hello 
Hello, world

# strings hello | grep CFLAGS
CFLAGS=-O3 -Wall

```

Basically it injects a binary file that has the CFLAGS embeded in it, so you can strings/grep it out later.

---

### Post by kcy29581 on 2007-09-25
> **duff said:**
> If you could get in contact with the developers, you could have them make a small change to their build system.

```
# cat hello.c 

#include <stdio.h>
int main (int argc, char *argv[]) {
        printf ("Hello, world\n");
}

# cat Makefile 

CC=gcc
CFLAGS=-O3 -Wall

LD=ld
LDFLAGS=

flags.txt:
        echo "CFLAGS=$(CFLAGS)" >$@

%.o: %.txt
        $(LD) -r -b binary -o $@ $<
        rm $<

%.o: %.c
        $(CC) $(CFLAGS) -c $< -o $@

hello: hello.o flags.o
        $(CC) $^ -o $@

# make hello
gcc -O3 -Wall -c hello.c -o hello.o
hello.c: In function ‘main’:
hello.c:5: warning: control reaches end of non-void function
echo "CFLAGS=-O3 -Wall" >flags.txt
ld -r -b binary -o flags.o flags.txt
rm flags.txt
gcc hello.o flags.o -o hello

# ./hello 
Hello, world

# strings hello | grep CFLAGS
CFLAGS=-O3 -Wall

```Basically it injects a binary file that has the CFLAGS embeded in it, so you can strings/grep it out later.

Thanks. I'll give it a go, but trust me, it's not going to happen. Any other way?

---

### Post by Compyx on 2007-09-25
Why do you have to figure out which flags where passed to the compiler? The dev-team should tell you this when they send/give you a binary to test, or rather they should keep track of things like that and not bother you with it.

This all seems a bit backwards to me.

---

### Post by LaRoza on 2007-09-25
> **Compyx said:**
> 
This all seems a bit backwards to me.

Probably a PHB.

---

### Post by kcy29581 on 2007-09-26
> **Compyx said:**
> Why do you have to figure out which flags where passed to the compiler? The dev-team should tell you this when they send/give you a binary to test, or rather they should keep track of things like that and not bother you with it.

This all seems a bit backwards to me.
It seems a bit backwards to me as well. There are only certain parts of the code that we are allowed to know (security, blah, etc).

Plus, I could never trust them: they would simply say that they comply with the requirements and that they are using the right flags... I need a bullet-proof way of figuring this out.

---

### Post by samjh on 2007-09-26
Sounds like some ultra-secret black box testing arrangement.

For video games, this sort of secrecy seems laughable.

It's not like they're making flight simulators for the F-22A! :p

But on the other hand, just why do you have to know the compiler flags? :confused:  Your job is to simply test the game, no?

---

### Post by kcy29581 on 2007-09-26
> **samjh said:**
> Sounds like some ultra-secret black box testing arrangement.

For video games, this sort of secrecy seems laughable.

It's not like they're making flight simulators for the F-22A! :p

But on the other hand, just why do you have to know the compiler flags? :confused:  Your job is to simply test the game, no?
The secrecy/piracy/paranoia factor is high in the games industry! I'd love to sit down and explain this to them. :)

I'm a compliance tester; I need to make sure the games comply with specific requirements before we ship them to the console manufacturers for their checks/tests. So it's more than just testing, which complicates things for me. :D

---

