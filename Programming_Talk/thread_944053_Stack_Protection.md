---
title: "Stack Protection"
date: 2008-10-10
forum: Programming Talk
---

### Post by Drezard on 2008-10-10
Messing round with Buffer overflows.

Any ideas how to make gcc have no stack protection. Well ubuntu?

Daniel

---

### Post by dwhitney67 on 2008-10-10
It's not GCC that controls program execution; it merely compiles and links the program for you.

If you want to practice with buffer overflows, then start with something simple:
[php]
#include <stdio.h>
#include <string.h>

int main()
{
  char buf1[5]  = {0};
  char buf2[12] = {0};

  strcpy( buf2, "Hello World" );         // legit copy of data to a buffer
  memcpy( buf1, buf2, sizeof(buf2) );    // will cause a data overflow

  printf( "buf1 = %s\n", buf1 );
  printf( "buf2 = %s\n", buf2 );

  return 0;
}
[/php]

P.S.  Strategy to avoid the error above is to rely on strncpy() so that the size of the destination buffer can be provided; for the memcpy(), always specify the size of the destination buffer, not the source buffer.

P.S.S.  I believe it is the MMU (Memory Management Unit) on your system that prevents programs from writing data into other program spaces.  If you try to write to another program space (including address 0), your program will be hit with a segmentation violation (SIGSEGV).

---

### Post by Drezard on 2008-10-10
Sorry a bit more ground details on what Im doing exactly. 

Im reading the book "Gray Hat Hacking". Attempting to learn the art of security. Theres bits of it using C/C++ and gcc and Linux. I choose ubuntu. 

But... whenver I compile:
```

#include <stdio.h>
#include <string.h>

int main() 
{

    char string[10];

    strcpy(string, "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA");

}

```

The terminal goes:
> 
$gcc -ggdb -o overflow overflow.c
$./overflow


The terminal replies:
> 
*** stack smashing detected ***: ./overflow terminated
========== Backtrace: ==============
memory crap


Which I'm guessing means, Im being rejected by some kind of stack protection. 

I need somewhere to run this buffer overflow and for it to not be protected! Please help. 

Daniel

---

### Post by dwhitney67 on 2008-10-10
> **Drezard said:**
> ...

Which I'm guessing means, Im being rejected by some kind of stack protection. 

I need somewhere to run this buffer overflow and for it to not be protected! Please help. 

Daniel

Do you understand the repercussions of what you are attempting?  It's like playing with matches when you are surrounded with open containers that contain gasoline.

I do know if it is possible (because it may be a kernel feature), but if you were able to overwrite your program's stack buffer and inject data into another process, then your system may become unstable.

In the early days when it would appear that computer security was not such a big deal, one could for instance supply an authentication application (that prompted for userid/password) with very long strings.  This would cause the application to fail, thus dropping control to the shell where the hacker could then do whatever they please.

There are still applications today that are vulnerable to similar types of attack.  But unless you are working on an embedded system, I'm not aware of any desktop OS that will allow data from one application to leak into another.

Good luck with your pursuit of happiness.

---

### Post by Drezard on 2008-10-10
Im doing it a lot more to learn about the principals of security, to do something that involves programming and also im doing it inside a VM. So, i have a safe and fairly controlled enviroment.

---

### Post by rnodal on 2008-10-11
I forgot the name of the feature but there is something in Ubuntu and in a lot of distros now day that protect against those type of exploits out of the box. In other words you need to be more creative to exploit a software. If you want to practice then you need to disable the feature that I'm talking about otherwise your exploits will fail but I can't remember the name of what you need to disable. 

If you check this site you will get an idea of what I'm talking about.
[http://fedoraproject.org/wiki/Security/Features]("http://fedoraproject.org/wiki/Security/Features")

Since you are using a VM then you should install a very old distro where all this features are not available that way it's easier to mess around. Have fun!

-r

---

### Post by era86 on 2008-10-11
I would install "Damn Insecure Linux" or something like that.  Look it up.  It is meant for you to break!

---

### Post by supirman on 2008-10-11
It's a compile time feature of gcc.  Just disable it, as follows:
```
$gcc -ggdb -fno-stack-protector -o overflow overflow.c
```

---

