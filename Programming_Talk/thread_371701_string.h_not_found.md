---
title: "string.h not found?"
date: 2007-02-27
forum: Programming Talk
---

### Post by ZDemon on 2007-02-27
Hi there.

I need to access a certain port in my pc. To do this, i want to use asm/io.h in my main source code. Here is a shortened version of my program : 

```
#include <stdio.h>
#include <asm/io.h>

int main()
{
	int x=8;
	iopl(3);
	outl(0x80024814,0xCF8);
	x=inl(0xCFC);
	printf("PCI data = %X\n",x);
	return (0);
}
```


My makefile is just a direct gcc compile command.

My problem is, it doesn't compile, and it says that string.h is not found. Here is the error in detail:-
> 
In file included from /usr/include/asm/io.h:7,
                 from main.c:2:
/usr/include/asm-i386/io.h:4:26: error: linux/string.h: No such file or directory

Any idea why? Do i need to change the makefile?

Any help would be appreciated. Thanks.

---

### Post by hod139 on 2007-02-27
I get no errors compiling your code fragment, only one warning.
```

gcc foo.c
In file included from /usr/include/asm/io.h:11,
                 from foo.c:2:
/usr/include/asm-i386/io.h:1:2: warning: #warning "You should include <sys/io.h>. This time I will do it for you."

```

---

### Post by wdk on 2007-02-27
When I tried to compile your code on my system I got the same error, but I was able to get a clean compile by replacing <asm/io.h> with <sys/io.h> (as implied by hod139's post). I also checked some of my own code, and found that I was using <sys/io.h> rather than <asm/io.h>. 

It seems that some newer systems prefer <sys/io.h> although I'm not sure exactly why that is, and I haven't had time to research it in depth.

happy hacking!

---

### Post by ZDemon on 2007-02-27
Hey thanks guys,

It compiles now. Actually this code compiled in Dapper, when i was using it.

When i started using Edgy it didn't compile anymore.

But it compiles now. Thanks a lot   :)   :KS

---

