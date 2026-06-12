---
title: "g++ won't compile - missing libs?"
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

### Post by adityakavoor on 2008-06-12
if it is a c file, use the .c extension

try compiling with gcc rather than g++

---

### Post by KingTermite on 2008-06-12
As adityakavoor pointed out, there is nothing in that program that is "c++", however, I still "think" you should be able to compile without errors.

I don't have a clue why you'd be getting that reference error unless it is because it's C only.

Also note, returning 3 will make the OS think the program had an error. Any return value other than 0 is consdiered an error. Not that it will necessarily hurt you in any way, just wanted to point it out in case you didn't realize.

---

### Post by ConMan318 on 2008-06-12
I just tried it and got the same result; it is because of the .cpp extension as others have said.  Changing it to a .c file allows it to work.

Like KingTermite, I thought it should still work.  My guess is that saving it as a .cpp file is like having a shebang line that leads to c++, so compiling it as C disagrees with that and causes the error.



Also, since you are a self-proclaimed noob, if you haven't compiled C before you will probably get some errors when you run that program, even with a '.c' extension.  It'll be an 'undefined reference to printf' or something.  You will probably have to install the build-essential package.  In the command line, just type:
```

sudo apt-get install build-essential

```

---

### Post by Joeb454 on 2008-06-13
True you'll need build-essential installed if you don't already.

And you seem to have made that a little overcomplicated, you would just need [PHP]#include <stdio.h>
int main()
{
   printf("Hello World!\n");
   return 0;
}
[/PHP]

That will return "Hello World!"

---

