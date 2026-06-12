---
title: "gcc compiling error"
date: 2008-10-11
forum: Packaging and Compiling Programs
---

### Post by irwas twn pistwn on 2008-10-11
Hi, I made a little program written in C on my Ubuntu 8.04, but when I tried to compile it (using the command "gcc test.c"), it told me: " warning: incompactible implicit declaration of built-in function 'printf' "
The program's code was:

#include <stdio.h>

int main(void)
{
printf("Hello world!\n");
return 0;
}


Can anyone help, please?:(

---

### Post by iponeverything on 2008-10-11
Its not a error.. just a warning.

type:

./a.out 


to run your compiled program.

---

### Post by howlingmadhowie on 2008-10-11
> **irwas twn pistwn said:**
> Hi, I made a little program written in C on my Ubuntu 8.04, but when I tried to compile it (using the command "gcc test.c"), it told me: " warning: incompactible implicit declaration of built-in function 'printf' "
The program's code was:

#include <stdio.h>

int main(void)
{
printf("Hello world!\n");
return 0;
}


Can anyone help, please?:(

i wonder if it can't find stdio.h. have you installed the build-essential package?

---

### Post by cmay on 2008-10-11
i have answered this question many times. it is almost always due to missing the build-essential package.
in very rare cases it is a broken gcc compiler installation.
the stdio.h is found cat /usr/include and i have never had a such broken compiler setup myself. solution to your problem is to use gcc for c programs and g++ for c++ programs. install build-essential with [PHP]sudo apt-get install build-essential[/PHP] such tools as automake can come in handy too.
 hope it helps.

---

### Post by irwas twn pistwn on 2008-10-11
> **cmay said:**
> i have answered this question many times. it is almost always due to missing the build-essential package.
in very rare cases it is a broken gcc compiler installation.
the stdio.h is found cat /usr/include and i have never had a such broken compiler setup myself. solution to your problem is to use gcc for c programs and g++ for c++ programs. install build-essential with [PHP]sudo apt-get install build-essential[/PHP] such tools as automake can come in handy too.
 hope it helps.
yes, i installed it

---

### Post by irwas twn pistwn on 2008-10-11
> **iponeverything said:**
> Its not a error.. just a warning.

type:

./a.out 


to run your compiled program.
Where do I have to type it???
EDIT: thank you!!!! IT WORKS!!!

---

### Post by hadynd88 on 2008-11-07
> **iponeverything said:**
> Its not a error.. just a warning.

type:

./a.out 


to run your compiled program.
Thanks for that too. I've been going through the forums for two hours trying to solve this. I had already resolved other issues using build-essentials and libc6. it was compiling fine but would not execute.

Any ideas on making this a stand-alone executable that can be run but clicking on the file?

---

### Post by Jeff250 on 2008-11-08
In general, you cannot double-click binary files to execute them in Linux!  What you are often double-clicking on to run programs are called "launchers."  For example, right click on your desktop and select "Create Launcher..." and then, by pointing it to your recently compiled program, you will create a launcher that, when double-clicked, will run your program.

---

