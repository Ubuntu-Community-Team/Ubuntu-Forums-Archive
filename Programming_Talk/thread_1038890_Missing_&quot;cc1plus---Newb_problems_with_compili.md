---
title: "Missing &quot;cc1plus?---Newb problems with compiling C"
date: 2009-01-14
forum: Programming Talk
---

### Post by Felixworks on 2009-01-14
I'm trying to learn C on Ubuntu 8.10, but when I tried to compile a simple "hello world" program I got this error:
```
gcc: error trying to exec 'cc1plus': execvp: No such file or directory

```

This is probably an easy fix, but in the book I'm following, there's nothing about an error like this.  So what's going on?  Thanks people ;)

---

### Post by kcode on 2009-01-14
Can you post your code? And have you installed virtual package build-essential?? If not, then execute the following command:
```

sudo apt-get install build-essential

```

Cheers

---

### Post by monkeyking on 2009-01-14
Have you installed the dev headers

```
sudo apt-get install build-essential
```

---

### Post by Felixworks on 2009-01-14
Thanks, I think that should have worked but...I got another error code when I tried compiling again:
```
/tmp/ccnrI4Ih.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

---

### Post by jespdj on 2009-01-14
What does your program look like? And what exactly are you typing to compile it? That's a very strange error for a simple Hello World program.

Try this:
```

#include <iostream>

void main(int argc, char *argv[]) {
    std::cout << "Hello World" << std::endl;
}

```
Save this in a file named hello.cpp and then compile it:
```
g++ hello.cpp -o hello
```
And then to run it:
```
./hello
```

---

### Post by Felixworks on 2009-01-14
Here's my program:```
#include <stdio.h>

int main()
{
	printf("Goodbye, cruel world!/n");
	return(0);
}
``` Hehe...not exactly a 'hello world' program, but it's along the same lines.  I tried to compile it using ```
gcc goodbye.c -o goodbye
``` as that's what the book said.

I tried what you said and I got this error when trying to compile it```
hello.cpp:3: error: &#8216;::main&#8217; must return &#8216;int&#8217;
```

---

### Post by dwhitney67 on 2009-01-14
> **Felixworks said:**
> Here's my program:```
#include <stdio.h>

int main()
{
	printf("Goodbye, cruel world!/n");
	return(0);
}
``` Hehe...not exactly a 'hello world' program, but it's along the same lines.  I tried to compile it using ```
gcc goodbye.c -o goodbye
``` as that's what the book said.

...

That should be a '\' in the printf() statement, not the '/'.

But that's is not what is causing the problem you are having with compiling/linking.

I've tried to duplicate the problem you are having, and the closest I was able to come was in an attempt to compile a C++ program using 'gcc'.  That attempt yielded a few more error messages than you posted, but similar.
```

/usr/bin/gcc test.cpp 
/tmp/ccCXGdoN.o: In function `__static_initialization_and_destruction_0(int, int)':
test.cpp:(.text+0x1d): undefined reference to `std::ios_base::Init::Init()'
test.cpp:(.text+0x22): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccCXGdoN.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```
Anyhow, if you are still having trouble, I would recommend that you verify the steps you are taking to compile, and if the problem persists, uninstall and then install again the build-essential package.

---

### Post by myromance123 on 2009-01-14
Wow what odd errors you're getting !

 The only problem I spotted was the '/n' in the printf function which should be '\n' but that is definitely not the cause of your errors lol


Looks like a compiler or linker problem :P

  Wow must have something to do with a broken or missing package is my guess (i said guess hehe)

---

### Post by myromance123 on 2009-01-14
Ooo, may I ask?

  Are you by any chance using the "C for Dummies" book?

---

### Post by jespdj on 2009-01-15
> **Felixworks said:**
> I tried what you said and I got this error when trying to compile it```
hello.cpp:3: error: &#8216;::main&#8217; must return &#8216;int&#8217;
```
Then change it to this:
```
#include <iostream>

int main(int argc, char *argv[]) {
    std::cout << "Hello World" << std::endl;
    return 0;
}
```
Note: This is a **C++** program. It looks like you are compiling a C program. I assumed you were programming in C++, because the error message suggests that you are trying to compile a C++ program as if it is a C program.

If you're programming in C, then change your main() line to this:
```
int main(int argc, char *argv[])
```
instead of simply "int main()".

The way you are compiling it ("gcc goodbye.c -o goodbye") is correct.

---

### Post by dwhitney67 on 2009-01-15
> **jespdj said:**
> ...

If you're programming in C, then change your main() line to this:
```
int main(int argc, char *argv[])
```
instead of simply "int main()".

...


In C and C++, the usage of "int main()" is acceptable; in either case, one does not have to declare argc and argv.

The C code the OP posted earlier is syntactically correct, although I assume the "/n" should be a "\n" in the printf() statement.  I also assume that the OP had named his/her file with a .c extension.

To compile/link the program, the OP should use "gcc", although "g++" also works for C programs.

For now, the OP appears to be MIA, so until we hear back from him/her, I would consider this thread to be dead.

---

### Post by Felixworks on 2009-01-15
Sorry, I'm back.  I'm trying to learn 'C'.  Yes I am using the "C for Dummies" book...it was the only guide to C at my library :).  It's from 2004 if that's a problem.  So...what exactly was the issue?  I got it working, but I have no idea how.  Last night the original code I listed got that error code but today it works fine.  Anyway, thanks for helping all of you.

---

### Post by myromance123 on 2009-01-16
Lol computer's are strange~

  Many a time a restart will suffice and many it doesnt :P

Glad it works again for ya, I just finished the C for Dummies hehe
 Moved on to C all-in-one desktop reference for Dummies xD

:lolflag:

---

