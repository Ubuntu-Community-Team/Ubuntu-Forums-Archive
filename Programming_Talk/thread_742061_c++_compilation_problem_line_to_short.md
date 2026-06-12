---
title: "c++ compilation problem: line to short"
date: 2008-04-01
forum: Programming Talk
---

### Post by Suraine on 2008-04-01
Dear c++ guru,

I am using cygwin to create a c++ environment for my Lego RCX.
I have create a program file in c++ format.

when compile with cygwin,
it shows:

```
 file.ds1: line to short on line 324 
```


can anyone help explain to me what is it?

I am stucked.

thanks.


best regards,
suraine

---

### Post by Zugzwang on 2008-04-01
Please state all the messages of the compiler and the command you used for compiling.

---

### Post by Suraine on 2008-04-01
My program is in text file with the filetype .C

I am using a "makefile" provided by brickOS, a program for the Lego RCX, to compile the .C file.

In cygwin window, i use command "make"

```
 $make 
```

then it will start listing the compilation process as shown below (shortcut):

```
 /usr/local/bin/h8300-hitachi-hms-gcc -M -I/brickos/include/lnp -I. -I/brickos/boot *.[cC] .depend
3DisplayValueOnLCD.C.....
...
...
...
...
6DOE-changemotorbehavior.ds1: line to short on line 324
make: *** [6DOE-changemotorbehavior.dc2 6DOE-changemotorbehavior.dc1 6DOE-changemotorbehavior.ds1 
```


This is partly the messages of the compiler.

---

### Post by Suraine on 2008-04-05
Hey, i found myself the answer.

Apparently it is due to the filename i have enter.
It is too long.

The problem fixed when i shorten my filename.

Sorry, i think i oversee the rule of the c++.
:o:-P\\:D/

---

