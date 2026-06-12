---
title: "[SOLVED] g++ won't compile - missing libs?"
date: 2008-06-12
forum: Packaging and Compiling Programs
---

### Post by samjetski on 2008-06-12
Hey, my first post woo lol.

Well, I'm a noob coder trying to compile with g++.
I tried to compile this (very) simple program:
```
#include <stdlib.h>
#include <stdio.h>
 
int main (int argc, char *argv[])
{
    printf ("Hello World!\n");
    return 3;
}
```and got this:
```
$ gcc -o hello hello.cpp
/tmp/ccJrgyaG.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
```What's `__gxx_personality_v0' got to do with anything and why is it breaking my code?
(No, I did not compile it in /tmp/. I executed the above command in /myfiles/c/)

I'm using Ubuntu 8.04 Hardy.
Initially I had the problem described in this thread: [http://ubuntuforums.org/showthread.php?t=345201]("http://ubuntuforums.org/showthread.php?t=345201") and I've gotten this far by following the instructions in that post.
(ie: I've [apt-get install]'d 'g++' and 'build-essential')
Is there a problem with my libraries or something?
And if so what do I do?

Thanks in advance,
SamJ ;D

---

### Post by samjetski on 2008-06-12
Oops. Should have been using g++ instead of gcc.
Sorry lol.

---

### Post by jspolen on 2008-06-12
This has nothing to do with your original question, but I was wondering what the *return 3* in your main function means. I'm kind of new to C++ and I've always used return 0 not really knowing what it means.

---

### Post by Joeb454 on 2008-06-13
> **jspolen said:**
> This has nothing to do with your original question, but I was wondering what the *return 3* in your main function means. I'm kind of new to C++ and I've always used return 0 not really knowing what it means.

Using "return 0;" means that your program has return with no errors. This usually comes in handy when you have a few functions.

So if functionA() returns 1, you could say that function has failed somewhere, but if functionA() returns 0, you could say it's succeeded :)

---

