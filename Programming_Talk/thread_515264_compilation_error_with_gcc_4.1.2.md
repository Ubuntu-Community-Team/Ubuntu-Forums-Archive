---
title: "compilation error with gcc 4.1.2"
date: 2007-08-01
forum: Programming Talk
---

### Post by airfoil on 2007-08-01
Hi,
    I encounter problem when compiling a simple code from book example by using gcc 4.1.2 on ubuntu 7.04. I pasted the error message below. Please help. Thank you very much.



airfoil@Ubuntu-laptop:~/programming/deitel/C_HTP5e_Examples/C_HTP5e_Examples/ch02$ gcc fig02_01.c 
fig02_01.c:3:19: error: stdio.h: No such file or directory
fig02_01.c: In function â€˜mainâ€™:
fig02_01.c:8: warning: incompatible implicit declaration of built-in function â€˜printfâ€™
airfoil@Ubuntu-laptop:~/programming/deitel/C_HTP5e_Examples/C_HTP5e_Examples/ch02$ gcc --version
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

airfoil@Ubuntu-laptop:~/programming/deitel/C_HTP5e_Examples/C_HTP5e_Examples/ch02$

---

### Post by Rocket2DMn on 2007-08-01
Can you post some of the relevant code?
If "#include <stdio.h>" doesn't work, try just "#include <stdio>"
You will also need to put "using namespace std;" after your includes to use functions like printf() which are available in stdio.

---

### Post by airfoil on 2007-08-01
Rockect2DMN,
           Thank you for the reply. I just bought a book from Deitel titled " C How To Programming 5 Edition".  When I try to compile the first example, I encounter this problem.  It also happen to my another Kubuntu machine.  However, I try on my friend Ubuntu machine and it run with problem.  The GCC version is same.  Is it installation problem?
Below is the mentioned code. 




/* Fig. 2.1: fig02_01.c
   A first program in C */
#include <stdio.h>

/* function main begins program execution */
int main( void )
{
   printf( "Welcome to C!\n" );

   return 0; /* indicate that program ended successfully */

} /* end function main */

---

### Post by Rocket2DMn on 2007-08-02
I just ran that code and it worked fine for me, too, I'm using the same compiler

Try this:
```
sudo apt-get autoremove gcc
sudo apt-get update
sudo apt-get build-dep gcc
```
This should reinstall gcc and all necessary components for you.

---

### Post by hod139 on 2007-08-02
> **Rocket2DMn said:**
> 
Try this:
```
sudo apt-get autoremove gcc
sudo apt-get update
sudo apt-get build-dep gcc
```This should reinstall gcc and all necessary components for you.
To install the compiler among other components necessary for building code you should install the package build-essential.
```
sudo apt-get install build-essential
```

---

### Post by Rocket2DMn on 2007-08-02
Knew I was forgetting something in there, thanks for the additional input.

---

