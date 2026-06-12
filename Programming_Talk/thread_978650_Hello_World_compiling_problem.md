---
title: "Hello World compiling problem"
date: 2008-11-11
forum: Programming Talk
---

### Post by JoFrRi on 2008-11-11
Hi.  I'm new to Ubuntu and C programming.  I have written the first example program that prints "Hello World" as the following:

```
#include <stdio.h>
 
int main()
{
   printf("Hello World\n");
   return 0;
}
``` 

The file is saved as test.c.  I have tried the following commands:

```
gcc test.c -otest
```

and I get the following error:

```
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
```

I have installed the build-essential package already.

Any help, much appreciated.

---

### Post by Shwefty on 2008-11-11
I'm relatively fresh on C programming too, but I always used the command:

gcc test.c - lm
a.out

---

### Post by JoFrRi on 2008-11-11
> **Shwefty said:**
> I'm relatively fresh on C programming too, but I always used the command:

gcc test.c - lm
a.out

```
joshua@TeamJRMobile1:~/C/test$ gcc test.c - lm
gcc: lm: No such file or directory
gcc: -E or -x required when input is from standard input
joshua@TeamJRMobile1:~/C/test$ a.out
bash: a.out: command not found
```

---

### Post by zwaardmeester on 2008-11-11
try compiling with ```
gcc ./test.c -otest
```
to be sure that you give the right file (test.c in current directory) as input

---

### Post by mtausig on 2008-11-11
The code and the compile command look OK to me.
The file where the compiler finds the error, /usr/lib/crt1.o, is part of libc6-dev. Check if you have it installed and maybe try updating it.

---

### Post by Joeb454 on 2008-11-11
It might sound stupid - but have you installed [build-essential]("apt://build-essential") ?

---

### Post by JoFrRi on 2008-11-11
Yes I have installed build-essential as per the first message.  I have version 2.8 of libc6-dev.  I reinstalled it but unfortunately the same error message.

---

### Post by Joeb454 on 2008-11-11
When in the correct directory, try running ```
gcc ./test.c -o prog
./prog

```

I can't see anything wrong with the code...

Also - moved to Programming Talk :) (I noticed it wasn't in the correct sub-forum)

---

### Post by ichi@YUKI on 2008-11-11
```
gcc test.c -otest
```

this might sound silly but, the code you typed has no space between the switch (-o) and the output file. It should have been

```
gcc test.c -o test
```

and then you might be able to run it using a dot-slash.

```
./test
```

---

### Post by malloq on 2008-11-11
What does

```
dpkg -S crt1.o
```

say?

---

### Post by snikrot on 2008-11-11
You forgot the -c option.

```

gcc -cHelloworld.c -oHelloword

```

See also [http://fixunix.com/linux/6304-undefined-reference-main.html]("http://fixunix.com/linux/6304-undefined-reference-main.html")

---

### Post by dwhitney67 on 2008-11-11
> **Shwefty said:**
> I'm relatively fresh on C programming too, but I always used the command:

gcc test.c - lm
a.out
The -lm is used to link in the math library.  For applications that do not require such library, it is not necessary to specify -lm.

---

### Post by fiddler616 on 2008-11-11
Others seem to have beat me to this, but in general (and IMHO) :
```
gcc *programname.c* -o *outputname*
./*outputname*
```
is the way to do it.

---

### Post by ichi@YUKI on 2008-11-11
guys.. dont forget the spaces between the switches and input/output files.. this proves that most programming problems are due to syntax. lol..

---

### Post by JoFrRi on 2008-11-11
> **ichi@YUKI said:**
> ```
gcc test.c -otest
```

this might sound silly but, the code you typed has no space between the switch (-o) and the output file. It should have been

```
gcc test.c -o test
```

and then you might be able to run it using a dot-slash.

```
./test
```

Gives the exact same message.

Also, trying dpkg -S crt1.o gave:

joshua@TeamJRMobile1:~/C/test$ dpkg -S crt1.o
libc6-dev: /usr/lib/Scrt1.o
libc6-dev: /usr/lib/Mcrt1.o
libc6-dev: /usr/lib/gcrt1.o
libc6-dev: /usr/lib/crt1.o

---

### Post by JoFrRi on 2008-11-11
> **malloq said:**
> What does

```
dpkg -S crt1.o
```

say?

joshua@TeamJRMobile1:~/C/test$ dpkg -S crt1.o
libc6-dev: /usr/lib/Scrt1.o
libc6-dev: /usr/lib/Mcrt1.o
libc6-dev: /usr/lib/gcrt1.o
libc6-dev: /usr/lib/crt1.o

---

### Post by JoFrRi on 2008-11-11
> **malloq said:**
> What does

```
dpkg -S crt1.o
```

say?

joshua@TeamJRMobile1:~/C/test$ dpkg -S crt1.o
libc6-dev: /usr/lib/Scrt1.o
libc6-dev: /usr/lib/Mcrt1.o
libc6-dev: /usr/lib/gcrt1.o
libc6-dev: /usr/lib/crt1.o

---

### Post by JoFrRi on 2008-11-11
Sorry about the multiple posts, the site kept freezing not showing a post and I don't know how to remove them.

---

### Post by stevescripts on 2008-11-11
Did you ever get your hello world program to succesfully compile and run?

Steve

---

### Post by JoFrRi on 2008-11-11
> **stevescripts said:**
> Did you ever get your hello world program to succesfully compile and run?

Steve

Nope.  Still haven't got it working.

---

### Post by stevescripts on 2008-11-11
Are you trying to build it from the same directory as the source file?

Are you getting any errors now?  If so, please post the output.

The results of building the code sample you pasted, on my Ubuntu box:
```

steveo@delldesktop:~/Desktop$ gcc test.c -o test
steveo@delldesktop:~/Desktop$ ./test
Hello World

```

Hope this helps.  Hang in there.

Steve

---

### Post by gnusci on 2008-11-11
It seems you have a serious damage in your system, hopefully only your compiler. I recommend you to uninstall and then install the gcc compiler, and then try again. There is anything wrong in your code and procedure to compile it.

---

### Post by cmay on 2008-11-11
actaully more a question. but is there not a warning against using the name "test" instead of hello or testprog ? as there should be on bsd unix and linux a program called test. which can confuse the shell . not that i do not think there is as above post suggest somekind of damage but i posted this as i was not sure if it is correct information i have and if so others that reads this tread  whit same problem then maybe might as well rule that one out also.

---

### Post by dwhitney67 on 2008-11-11
You are correct cmay; there is a utility called 'test' (in /usr/bin), thus one should avoid naming their executable the same name.

Though based on the help I've seen so far in this thread, it shouldn't be an issue, if the OP happens to use the name 'test', and runs his application such as:
```
./test
```
This ensures that the file in the local directory is executed, and not the one in /usr/bin.

---

### Post by JoFrRi on 2008-11-11
Hey everyone, thanks for all your help.  I've removed and am reinstalling Ubuntu from scratch.  Doing some system updates and then I will get back at it.  I will let you guys know how it goes.

---

### Post by JoFrRi on 2008-11-12
Well it's a new day and a new Ubuntu.  I removed the old copy, reinstalled a new copy, installed all the system updates and build-essential and now the program compiles and runs fine.  Thanks for all the help, you guys are great!

---

### Post by Tony Flury on 2008-11-12
As a matter of interest why did you reinstall Ubuntu - that might be a normal tactic for Windows (i know somone who reinstalls Windows XP every month), but I can't see that being neccessary for Ubuntu, unless it was massively messed up (like giving kernel panics etc).

---

### Post by JoFrRi on 2008-11-12
I reinstalled Ubuntu because I had just installed it and there were issues.  If there is an issue with one thing chances are, there are going to be more problems.  From past experience, if an install went bad, I would wipe it and start over and it has worked well so far.

---

