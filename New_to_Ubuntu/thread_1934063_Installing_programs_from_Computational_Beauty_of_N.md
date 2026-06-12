---
title: "Installing programs from Computational Beauty of Nature"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by Griffiss on 2012-03-01
Hi all

I'm trying to install the programs that accompany the book "Computational Beauty of Nature" from 1998. The code is available from the book's homepage at [http://mitpress.mit.edu/books/FLAOH/cbnhtml/download.html](http://mitpress.mit.edu/books/FLAOH/cbnhtml/download.html)

I downloaded the file "cbn-linux-bin.tgz", which has the description: "contains everything prebuilt for an i386 linux box with glibc and glibm (498 KB)."

I extracted this to my home folder, then in terminal went to the directory where the Makefile was, then entered the command make. I just got error messages though.

Is this code just too old and having compatibility issues or did I do something wrong?

Griff

---

### Post by jerome1232 on 2012-03-01
Firstly, do you have build-essential installed? If not, install it.

Secondly what errors exactly? Copy paste the relevant output, enclose it in code tags for readability (go advanced, highlight all output, press the # symbol on your toolbar.)

---

### Post by Griffiss on 2012-03-01
I have build-essential installed. As far as I know though, this code should be precompiled, so will I need this? I know pretty much nothing about this.

Here's the output:


```
hywel@Nagarjuna:~/cbn/code$ make
cd bin; make
make[1]: Entering directory `/home/hywel/cbn/code/bin'
gcc -O3  -Wall  -D__dest_os=unix -I/usr/X11/include -DPLOTX11   -c -o stutter.o ../src/stutter.c
../src/stutter.c: In function ‘garbage_collect’:
../src/stutter.c:189: error: lvalue required as left operand of assignment
../src/stutter.c: In function ‘new_cell’:
../src/stutter.c:208: warning: type defaults to ‘int’ in declaration of ‘init’
../src/stutter.c:216: error: lvalue required as left operand of assignment
../src/stutter.c:217: error: lvalue required as left operand of assignment
../src/stutter.c:224: error: lvalue required as left operand of assignment
../src/stutter.c:225: error: lvalue required as left operand of assignment
../src/stutter.c: In function ‘new_atom’:
../src/stutter.c:249: error: lvalue required as left operand of assignment
../src/stutter.c:250: error: lvalue required as left operand of assignment
../src/stutter.c:251: error: lvalue required as left operand of assignment
../src/stutter.c:255: error: lvalue required as left operand of assignment
../src/stutter.c:256: error: lvalue required as left operand of assignment
../src/stutter.c: In function ‘cons’:
../src/stutter.c:343: error: lvalue required as left operand of assignment
../src/stutter.c:345: error: lvalue required as left operand of assignment
../src/stutter.c:347: error: lvalue required as left operand of assignment
../src/stutter.c: In function ‘set’:
../src/stutter.c:405: error: lvalue required as left operand of assignment
../src/stutter.c:414: error: lvalue required as left operand of assignment
../src/stutter.c:415: error: lvalue required as left operand of assignment
../src/stutter.c:419: error: lvalue required as left operand of assignment
../src/stutter.c:420: error: lvalue required as left operand of assignment
../src/stutter.c: In function ‘lambda’:
../src/stutter.c:458: error: lvalue required as left operand of assignment
../src/stutter.c:459: error: lvalue required as left operand of assignment
../src/stutter.c: In function ‘eval_lambda’:
../src/stutter.c:569: error: lvalue required as left operand of assignment
../src/stutter.c:570: error: lvalue required as left operand of assignment
../src/stutter.c: In function ‘initialize’:
../src/stutter.c:702: error: lvalue required as left operand of assignment
../src/stutter.c:705: error: lvalue required as left operand of assignment
../src/stutter.c:708: error: lvalue required as left operand of assignment
../src/stutter.c:711: error: lvalue required as left operand of assignment
../src/stutter.c:714: error: lvalue required as left operand of assignment
../src/stutter.c:718: error: lvalue required as left operand of assignment
../src/stutter.c:721: error: lvalue required as left operand of assignment
../src/stutter.c:724: error: lvalue required as left operand of assignment
make[1]: *** [stutter.o] Error 1
make[1]: Leaving directory `/home/hywel/cbn/code/bin'
make: *** [progs] Error 2

```

---

### Post by jerome1232 on 2012-03-01
hmmm well there are a bunch of binaries in the bin folder, I executed the termites one, and it began but froze up (maybe I was just impatient) I am on a 64 bit machine so there may be an issue there for me, I believe those are all the compiled binaries right there though.

---

### Post by Griffiss on 2012-03-01
So that means I didn't need to use the make command? How do I execute a binary?? Thanks for your help

---

### Post by jerome1232 on 2012-03-01
cd into it, ./binary name


ie i extracted the tarbal to my home so

```
cd cbn/code/bin/
./termites
```

---

### Post by Griffiss on 2012-03-01
Ok thanks. Well, the commands aren't working anyway it seems. Perhaps I should try to compile them from the source..........

---

### Post by Griffiss on 2012-03-01
Well, that didn't work either. I get the same error messages as earlier when trying to run make with the source code. Wish I knew more about computers:(

---

### Post by Griffiss on 2012-03-01
Ok, I found this in the FAQ:

> How do I compile the code under Linux?

You'll need to tweak one or two things to build it all from scratch. I wrote the code a few years back when /usr/X11 was a fairly reasonable default for the base directory of X-windows. These days, /usr/X11R6 is much more common. As a result, you'll need to edit the file cbn/code/bin/Makefile so that it references the correct base directory of your X11 installation.

I think it's a few years since this FAQ was written too:)

Anybody knows what would be the base directory of X11? I found an X11 directory in /etc and /usr/lib... don't know which if either of these it would be

---

