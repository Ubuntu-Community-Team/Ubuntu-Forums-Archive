---
title: "Using C libraries with Korn Shell Scripts"
date: 2008-07-21
forum: Programming Talk
---

### Post by J05HYYY on 2008-07-21
Why hello there.
I am writing shell script and would like to include a standard C library but I am having some difficulties.

```

#This korn shell program is called hello.sh
#!bin/sh
#include <stdio.h>

main()
{
	printf("hello, world\n");
}

echo "hello world"

```

is it possible to compile non-c code with the cc command?
I want to be able to compile Korn Shell script with libc.
The Korn Shell compiler is shcomp but I really have no idea how to compile sh script with library includes. Any help would be great :)

---

### Post by Martin Witte on 2008-07-21
On what the Korn shell can and cann't this [book]("http://www.unix.com.ua/orelly/unix/ksh/index.htm") might be of use. See also the [faq]("http://ubuntuforums.org/showthread.php?t=832449") of this forum on how to learn C programming and much more

---

### Post by J05HYYY on 2008-07-23
This website looks informative:
[http://tldp.org/HOWTO/From-PowerUp-To-Bash-Prompt-HOWTO-5.html]("http://tldp.org/HOWTO/From-PowerUp-To-Bash-Prompt-HOWTO-5.html")
I skim read the guide and faq but could make no head nor tail. :(

---

### Post by Martin Witte on 2008-07-23
To clarify: the Korn shell is a command interpreter, just like the default linux shell bash - but ksh understands a different set of commands. You can collect these commands in a shell script, make this executable, and the run it, eg.
```
martin@toshibap200:~$ cat test.ksh
#!/bin/ksh

echo "Hello World"
martin@toshibap200:~$ chmod u+x test.ksh
martin@toshibap200:~$ ./test.ksh
Hello World
martin@toshibap200:~$ 
```

C is a programming language -  you can create a program, compile this and then run it, eg. 
```
martin@toshibap200:~$ cat test.c
#include <stdio.h>

int main()
{
	printf("Hello World\n");
	return 0;
}
martin@toshibap200:~$ gcc test.c -o testprogram 
martin@toshibap200:~$ ./testprogram 
Hello World

```

You could use this program from then on in a (Korn) shell script, e.g
```
martin@toshibap200:~$ cat test.ksh
#!/bin/ksh
./testprogram
martin@toshibap200:~$ ./test.ksh
Hello World
martin@toshibap200:~$ 

```

Hope this clarifies the difference between a shell script and a C program.

With shcomp you can create a binary Korn shell understands from a shell script, eg.
```
martin@toshibap200:~$ cat  test.ksh
#!/usr/bin/ksh

echo "Hello world"
martin@toshibap200:~$ shcomp test.ksh testprogram
martin@toshibap200:~$ ksh testprogram 
Hello world
martin@toshibap200:~$ 

```

The C program uses libc, you can show that using ldd:
```

martin@toshibap200:~$ cat test.c
#include <stdio.h>

int main()
{
	printf("Hello World\n");
	return 0;
}
martin@toshibap200:~$ gcc test.c -o testprogram
martin@toshibap200:~$ ./testprogram 
Hello World
martin@toshibap200:~$ ldd testprogram 
	linux-gate.so.1 =>  (0xb7f12000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7db4000)
	/lib/ld-linux.so.2 (0xb7f13000)
martin@toshibap200:~$ 

```

---

### Post by J05HYYY on 2008-07-24
Okay, I think I'm starting to get it a little. You managed to explain it way better :)

Now i just need to work out how to open a binary in C to get it to work both ways. Shouldn't be too hard I guess ...


Much appreciated.

---

