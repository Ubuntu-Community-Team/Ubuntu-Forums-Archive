---
title: "what program to download to start C programming"
date: 2008-02-22
forum: Programming Talk
---

### Post by simocusi on 2008-02-22
hi

i am doing a project on robotics and need to start learning C to make a program to communicate with hardware via serial port. What program would you recommend me to use? I am using Ubuntu.

thanks!

---

### Post by LaRoza on 2008-02-22
See the sticky.

---

### Post by dwhitney67 on 2008-02-22
I would start by learning the C language.  You will undoubtedly need a compiler to build your practice programs.  Get the compiler and related tools by:

```
$ sudo apt-get install build-essential manpages-dev
```

Communicating via a serial port is an advanced topic.  It would appear that you do not have much/any experience with C, so you will have a while to go before I believe you will be ready to tackle serial ports.  You will also need to become familiar with the Linux OS, in as far as knowing which device node pertains to the serial port you will be using.

Good luck with your studies.

---

### Post by simocusi on 2008-02-22
i have looked up the LasRozas link but I cannot figure out what is the actual program on which I write my C code. Can I get it from ADD/Remove applications?
Is the compiler included in this program?

---

### Post by LaRoza on 2008-02-22
> **simocusi said:**
> i have looked up the LasRozas link but I cannot figure out what is the actual program on which I write my C code. Can I get it from ADD/Remove applications?
Is the compiler included in this program?

There is a link in the sticky for compiling and writing C programs.

For an editor or IDE to use, which is also in the sticky, you can just use Gedit for now. That is what I use. It has the features that are useful for programming, and has plugins to add more functionality.

---

### Post by simocusi on 2008-02-22
so I have to save my gedit file as a .c file? and then, how do I compile and run it?

thanks!!

pd: LaRoza and not LasRozas, sorry

---

### Post by simocusi on 2008-02-22
ok, just found it on your wiki!

---

### Post by simocusi on 2008-02-22
i get this though:

simo@simo-laptop:/$ gcc prova.c -o prova
prova.c:1:17: error: stdio: No such file or directory
prova.c: In function ‘main’:
prova.c:8: warning: incompatible implicit declaration of built-in function ‘printf’
simo@simo-laptop:/$ 

and i did run $ sudo apt-get install build-essential manpages-dev

any clue?

---

### Post by ruy_lopez on 2008-02-23
Did you include stdio.h like this:

```
#include <stdio.h>
```

---

### Post by stevescripts on 2008-02-23
simocusi,

Have you built a simple hello world c program, to make sure things are working?

```

#include <stdio.h>

int main ()
{
	printf("Hello World!\n");

	return 0;
}

```

Save this as hw.c.  Then from the commandline:
```

steveo@delldesktop:~/Desktop$ gcc hw.c -o helloworld
steveo@delldesktop:~/Desktop$ ./helloworld
Hello World!

```

Hope this helps.

Steve

---

### Post by simocusi on 2008-02-24
stupid mistake: forgot de .h at stdio.h..

sorry about that and thanks for the fast help!

---

