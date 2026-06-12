---
title: "No headers"
date: 2007-11-26
forum: Packaging and Compiling Programs
---

### Post by Envergure on 2007-11-26
I can't compile anything because the compiler can't find any headers.
```

//  Hello.c

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char** argv)
{
	printf ("Hello World!");
	return 0;
}

```

When I compile I get this:[FONT="Fixedsys"]
Error:  stdio.h:  No such file or directory.
Error:  stdlib.h:  No such file or directory.
Warning:  Implicit declaration of function 'printf'
Warning:  Incompatible implicit declaration of built-in function 'printf'.[/FONT]


Compiled by Geany with command
[FONT="Fixedsys"]gcc -Wall -c "Hello.c"[/FONT]
Other IDEs do the same thing.

Do I have to install something to get the headers?

I've been using C under win32 for some time, but this is my first time using Linux.  I have a book about Linux programming (not sure why), but it's old and not very well-written.

---

### Post by geraldm on 2007-11-26
ls /usr/include/stdio.h
# gcc can pick up its location where it is expected to be; 
# if it is there, pass gcc another flag -I/usr/include
# if not there
```

sudo apt-get install build-essential

```

---

### Post by Envergure on 2007-11-27
Okay...  Now I hit "compile" and it creates an object file, but no executable.
I haven't changed the compile command, just installed the header files.


EDIT:  Never mind, that was my fault!
I got it now.  It compiled properly, but I just forgot to build it (oops..).

EDIT:
I can run the program with the "run" button in the IDE, but double-clicking it doesn't seem to do anything.  How do I get it to execute from outside the IDE?

---

### Post by geraldm on 2007-12-01
On the command line, one way is to issue the full path to the executable program.  Another way if you are in the same directory as the executable is to issue the command "./Hello"  where Hello is the name of the executable.

---

### Post by Envergure on 2007-12-01
Thanks :)

---

