---
title: "c programming parallel (378) port"
date: 2007-05-27
forum: Programming Talk
---

### Post by riski_lana on 2007-05-27
i h've problem with paralel port programming in c, i use edgy

this is my code

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <asm/io.h>
#define pport 0x378
void delay(void)
{
        int i;
        for (i=0;i<=1000000000;i++);
}
main(int argc,char **argv)
{
        int i;
        if(ioperm(pport, 1, 1))
        fprintf(stderr,"connection error %x\n",pport), exit(1);
        
            outb(0x01,pport);delay();
	    outb(0x02,pport);delay();
	    outb(0x04,pport);delay();
	    outb(0x08,pport);delay();
}

after that i compile in terminal : gcc  asm.c
and i get this error
in file inclueded from /usr/include/asm/io.h:7, from asm.c:4:
/usr/include/asm-i386/io.h:4:26: error: linux/string.h: No such file or directory

after that i try to change the #include <asm/io.h> with #include <sys/io.h> and i able to compile that code but when i run the program still cant connect, & i get the connection error message

anyone can help me ?? tx 
yahoo messenger [email]riski.lana@yahoo.com[/email]

---

### Post by moma on 2007-05-27
Hello Lana,

Well done, however consider to do the following changes:

1) You may need to be "root" or sudo to be able to write to I/O ports. Especially ioperm() requires admin privileges.

2) "asm.c" is not a good name for your code.  Rename it to test1.c or something like that.

3) Yes, I think <sys/io.h> is the right include file. Read the note 1) below.

4) Delays: Use usleep() or sleep() instead of loop. Loops are not accurate and they occupy the CPU,  [u]sleep does not.

5) Use perror() to report possible errors. It will reveal the accurate cause of error.
---

Compile it
$ [COLOR="SeaGreen"]gcc test1.c -o test1 [/COLOR]

Run it (as sudo)
$ [COLOR="SeaGreen"]sudo ./test1[/COLOR]

Note 1:
If you want to use the <asm/io.h> then you must get the include file from kernel headers. 
[ requires Ubuntu package: linux-headers-$(uname -r) or linux-headers-generic, apt-get it. ]. An example:

$ gcc test1.c -o test1 -I/usr/src/linux-headers-2.6.20-15-generic/include/linux/asm
---------

Read this guide
[http://www.faqs.org/docs/Linux-mini/IO-Port-Programming.html](http://www.faqs.org/docs/Linux-mini/IO-Port-Programming.html)
You will find a good example code in Chapter 9) 
Compile as normal user, run it as sudo.

See also
[http://tldp.org/HOWTO/IO-Port-Programming-2.html](http://tldp.org/HOWTO/IO-Port-Programming-2.html)

Study also the guides on my [opportunities page...]("http://www.futuredesktop.org/opportunities.html")

Note 2:
exit(0) will require <stdlib.h>.  You can suppress exit(0) warnings by using the -f no-builtin-exit directive.
$ gcc -fno-builtin-exit test1.c -o test1

Note 3:  Use the -Wall compile directive to report all possible warnings.
$ gcc -O2 -Wall -o test1 test1.c

---

### Post by nobtiba on 2007-05-30
can I control parallel port if I am not a root user ? Could you give me a simple code that work with parallel port in case of mine ?

---

### Post by kedarm on 2010-04-16
> **nobtiba said:**
> can I control parallel port if I am not a root user ? Could you give me a simple code that work with parallel port in case of mine ?

If you see the section on parallel port programming in [this]("http://www.epanorama.net/circuits/parallel_output.html") article, it gives a method to control the parallel port without root privileges.

"Save the source code to file lpt_test.c and compile it with command:

gcc -O lpt_test.c -o lpt_test

"[I]The user has to have the previledges to have access to the ports for the program to run, so you have to be root to be able to ron this kind of programs without access problems. If you want to make a program which can be run by anybody then you have to first set the owner of the program to be root (for example do compilation when yhou are root), give the users rights to execute the program and then set the program to be always executed with owner (root) rights instead of the right of the user who runs it. You can set the programn to be run on owner rights by using following command:

chmod +s lpt_test[/I]"

However, you will still need root access to compile (as root)..

HTH

---

### Post by Cool Javelin on 2010-10-12
This is good kedarm.

you say 

> However, you will still need root access to compile (as root) 

Could the same be achieved by chaging the owner after compiling as a normal user?

```
sudo chown mark:root lpt_test
```

then, later, allow anyone to run the program

```
sudo chmod 555 lpt_test
```

Mark.

---

