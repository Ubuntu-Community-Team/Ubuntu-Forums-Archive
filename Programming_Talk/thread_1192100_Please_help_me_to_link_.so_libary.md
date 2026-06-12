---
title: "Please help me to link .so libary"
date: 2009-06-19
forum: Programming Talk
---

### Post by pablogreen on 2009-06-19
Hi People,
Please help me with linking my libary mylib.so to program prog.c
what am I doing wrong ? (Ubuntu 64bit, g++ 4.3.3.1)

Here is my files (simple example) :

mylib.c
```

#include <stdio.h>
void printMyInt(int i) {
    printf("%i", i);
}

```mylib.h
```

#ifndef MY_LIB_HEADER
#define MY_LIB_HEADER

void printMyInt(int X);
#endif

```prog.c
```

#include "mylib.h"
int main(){
printMyInt(5);
return 0;
}

```And now I'm trying that:
```

g++ -fPIC -c mylib.c          
g++ -shared -Wl,-soname,mylib.so.1 -o mylib.so.1.0 mylib.o
ln -s mylib.so.1.0 mylib.so.1
ln -s mylib.so.1 mylib.so

```(new files created: mylib.so, mylib.so.1, mylib.so.1.0 in /home/mylinux/Desktop/test/  )

but I have some ERROR :mad: after this command  :
```

$ g++ -Wall -g -o prog.exe prog.c -I/home/mylinux/Desktop/test/ -L/home/mylinux/Desktop/test/ 

```[SIZE=2][B][COLOR=Red]-lmylib/usr/bin/ld: cannot find -lmylib
collect2: ld returned 1 exit status[/COLOR][/B][/SIZE]
[I]
and I was trying this:

$ g++ -Wall -g -o prog.exe prog.c -I -lmylib
/tmp/ccaum3hm.o: In function `main':
/home/mylinux/Desktop/test/prog.c:4: undefined reference to `printMyInt'
collect2: ld returned 1 exit status[/I] 
[SIZE=3]
how fix this???? :mad:[/SIZE]

---

### Post by dwhitney67 on 2009-06-19
It's funny... you posted two distinct commands you used in your attempt to compile prog.c, and in each case, something is wrong.

In the first command, you forgot to specify -lmylib.

In the second command, you forgot to specify the -L<path>.

Here's the correct statement:
```

g++ -Wall -g -o prog.exe prog.c -I/home/mylinux/Desktop/test -L/home/mylinux/Desktop/test -lmylib

```
Note that this is identical to the first command you posted, with the addition of the -lmylib at the end.

There are also some steps that you did, while nice, are not necessary.  Those include the ones to create the shared-object library.  The following would have sufficed:
```

g++ -fPIC -c mylib.c          
g++ -shared -o mylib.so mylib.o

```
Undoubtedly when you run your program, you are going to receive an error because the runtime executable won't find the so-library.

To rectify the problem, use this command:
```

LD_LIBRARY_PATH=/home/mylinux/Desktop/test prog.exe

```

---

### Post by Mirge on 2009-06-19
> **dwhitney67 said:**
> **It's funny... you posted two distinct commands you used in your attempt to compile prog.c, and in each case, something is wrong.**

In the first command, you forgot to specify -lmylib.

In the second command, you forgot to specify the -L<path>.

Here's the correct statement:
```

g++ -Wall -g -o prog.exe prog.c -I/home/mylinux/Desktop/test -L/home/mylinux/Desktop/test -lmylib

```Note that this is identical to the first command you posted, with the addition of the -lmylib at the end.

There are also some steps that you did, while nice, are not necessary.  Those include the ones to create the shared-object library.  The following would have sufficed:
```

g++ -fPIC -c mylib.c          
g++ -shared -o mylib.so mylib.o

```Undoubtedly when you run your program, you are going to receive an error because the runtime executable won't find the so-library.

To rectify the problem, use this command:
```

LD_LIBRARY_PATH=/home/mylinux/Desktop/test prog.exe

```

LOL, that made me actually laugh out loud. Just the words "It's funny..." after thinking about his frustration.... cracked me up.

---

### Post by pablogreen on 2009-06-20
Sorry but I was trying before also what you wrote:
```

g++ -Wall -g -o prog.exe prog.c -I/home/mylinux/Desktop/test -L/home/mylinux/Desktop/test [SIZE=2]-lmylib[/SIZE]

```and
I cut&paste all files in one folder (mylib.c  mylib.h  mylib.o  mylib.so  prog.c):
```

g++ -Wall -g -o prog.exe prog.c -I./ -L./ -lmylib

```and
```

g++ prog.c -I./ -L./ -lmylib

```and
```

sudo g++ prog.c -I./ -L./ -lmylib

```but all have the same error :
[SIZE=2][COLOR=Red]
/usr/bin/ld: cannot find -lmylib
collect2: ld returned 1 exit statu[/COLOR][/SIZE]s


[I]and I created mylib.so with this:
g++ -fPIC -c mylib.c          
g++ -shared -o mylib.so mylib.o
but nothing change with trying to link this with prog.c[/I]

---

### Post by pablogreen on 2009-06-20
uff I find out that libary file .so must have prefix lib :)
```

g++ -fPIC -c mylib.c          
g++ -shared -o libmylib.so mylib.o
g++ -Wall -g -o prog.exe prog.c -I./ -lmylib -L./
LD_LIBRARY_PATH=/home/mylinux/Desktop/test ./prog.exe 

```WORK :lolflag:

Now I must try this with my home-made compiler using LLVM :p

---

### Post by pablogreen on 2009-06-20
to create .so file for LLVM use
gcc -fPIC -c mylib.c          
gcc -shared -o libmylib.so mylib.o

---

