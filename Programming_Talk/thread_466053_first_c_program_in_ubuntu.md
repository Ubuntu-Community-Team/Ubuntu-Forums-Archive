---
title: "first c program in ubuntu"
date: 2007-06-06
forum: Programming Talk
---

### Post by nss0000 on 2007-06-06
Gents:

After many years absence I decided to start writing C-code. So I punchup Gedit and write a HELLO WORLD program: 

Then <gcc hello.c>  buys me the error message "command not found".

OOps. Looks like I haven't PREPARED(?) my system (dapperx64) to compile. Hummm ... I did try to download everything-and-its'-mother  that looked like part of a dev-environment.  

GOOGLE search spins-my-head around. 

What do I need to do to get my kit compiling??

nss
****

---

### Post by WW on 2007-06-06
To start, install the package **build-essential**:
```

$ sudo apt-get install build-essential

```
That will get you the C and C++ compilers (gcc and g++), the standard libraries, and the **make** command.

---

### Post by nss0000 on 2007-06-06
WW:

me@asusm2n:~/cprogs0$ gcc hello.c
hello.c: In function ‘main’:
hello.c:4: warning: return type of ‘main’ is not ‘int’
me@asusm2n:~/cprogs0$ ls
a.out  hello.c
me@asusm2n:~/cprogs0$ ./a.out

Hello World

**********************


WOOOHOOO --- thanks WW.

nss
******

---

### Post by Lord Illidan on 2007-06-06
You can also do like this:

```
gcc hello.c -o hello
```

and then run ./hello instead of a.out

---

