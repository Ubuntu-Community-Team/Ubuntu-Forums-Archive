---
title: "I need help with a simple program."
date: 2008-01-03
forum: Programming Talk
---

### Post by JunsuinoKokoro on 2008-01-03
I am trying to get the infamous HelloWorld program to work in C, but I can not figure out how.  Could someone please list out the steps necessary to compile and run this program?  Here's my source code:

#include <stdio.h>
int main()
{
     printf("Hello World!\n");
     return 0;
}

The above is saved as *main.c* in its own directory.  I've tried using the gcc o- command and I get errors.  I've tried using Eclipse and using its Hello World tutorial, but I can't get the same results the tutorial produces.

For the record, I'm using Ubuntu 7.10, and I've installed both *make* and the GNU C compiler using the Synaptic Package Manager.

If anyone is willing to help, I'd be very grateful.  Thank you.

---

### Post by LaRoza on 2008-01-03
See [http://laroza.wikidot.com/C](http://laroza.wikidot.com/C)

(It is linked to in my main wiki, which is in my sig)

---

### Post by cheahk on 2008-01-03
I am assuming that you have already installed gcc.

To compile main.c, enter:

```
gcc -o main main.c
```

This creates the executable (or the program) called "main".  To run it, just type "main", or "./main".

-K

---

### Post by JunsuinoKokoro on 2008-01-03
LaRoza,

Thank you for the tutorial.  I did what it instructed and I'll show you what happens on my terminal window:

====================
brien@BRIENBLIATOU-PC:~/temp$ sudo aptitude install build-essential
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
brien@BRIENBLIATOU-PC:~/temp$ gcc main.c -o main
main.c:1:19: error: stdio.h: No such file or directory
main.c: In function ‘main’:
main.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
brien@BRIENBLIATOU-PC:~/temp$ ls
main.c
brien@BRIENBLIATOU-PC:~/temp$ 
====================

In short, I wasn't able to get it to work.



And thank you cheahk, but here's the results of your suggestion:

====================
brien@BRIENBLIATOU-PC:~/temp$ gcc -o main main.c
main.c:1:19: error: stdio.h: No such file or directory
main.c: In function ‘main’:
main.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
brien@BRIENBLIATOU-PC:~/temp$ ls
main.c
brien@BRIENBLIATOU-PC:~/temp$ 
====================

I'm puzzled.

---

### Post by Auria on 2008-01-03
It looks like the "install build-essential" command failed because you had another admin app running (synaptic?) at the same time. Try without it running, or just install build-essential from synaptic

---

### Post by JunsuinoKokoro on 2008-01-03
LaRoza,

After rebooting and attempting the tutorial again, everything worked out.  Sorry about responding so hastily earlier.  Thank you!

---

### Post by ryanVickers on 2008-01-03
> **JunsuinoKokoro said:**
> I am trying to get the infamous HelloWorld program to work in C, but I can not figure out how.  Could someone please list out the steps necessary to compile and run this program?  Here's my source code:

#include <stdio.h>
int main()
{
     printf("Hello World!\n");
     return 0;
}

The above is saved as *main.c* in its own directory.  I've tried using the gcc o- command and I get errors.  I've tried using Eclipse and using its Hello World tutorial, but I can't get the same results the tutorial produces.

For the record, I'm using Ubuntu 7.10, and I've installed both *make* and the GNU C compiler using the Synaptic Package Manager.

If anyone is willing to help, I'd be very grateful.  Thank you.

maybe C is different than C++ in things even as simple as this, maybe theres multiple ways to do it, etc. I don't know what, but when I did some simple work making calculators back when in C++, is was always "cout" and "cin", not "printf", and the "main" thing had the fancy brackets, like {} ;)

but like I said, maybe theres different ways...

---

### Post by Auria on 2008-01-03
ryanVickers  : cout and cin are for C++ only.

---

### Post by ryanVickers on 2008-01-03
ok, I thought it was probably something like that ;)

man, actually thinking back to what I was doing, and I was like 10... :shock: :p

---

### Post by JupiterV2 on 2008-01-03
I would also recommend adding the -Wall (Warnings-all) flag when running gcc so the compiler will spit out warnings in your code that can help you avoid issues future issues.

Example gcc -Wall -o hello_world hello_world.c

---

### Post by Kadrus on 2008-01-04
Maybe you haven't install build-essential
```
sudo apt-get update
```
```
sudo apt-get installed  build-essential
```
Now that you have everything installed
```

#include<stdio.h>
int main()
{
printf("Hello World\n");
getchar();
return 0;
}

```
In terminal type:
```
gcc ex.c
```
I am supposing that the file's name is ex.c
then write in terminal
```
./a.out
```
And you should see your program..good luck :)

---

