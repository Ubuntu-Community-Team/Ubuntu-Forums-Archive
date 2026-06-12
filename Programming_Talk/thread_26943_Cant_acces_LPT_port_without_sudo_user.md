---
title: "Cant acces LPT port without sudo user"
date: 2005-04-14
forum: Programming Talk
---

### Post by garfield on 2005-04-14
Hi,
I write simple program to acces lpt port:

```
#include <stdio.h> #include <stdlib.h> #include <unistd.h> #include <asm/io.h>  #define base 0x378           /* printer port base address */  main(int argc, char **argv) {                       int value;    if (argc!=2)     fprintf(stderr, "Error: Wrong number of arguments. This program needs one argument which is number between 0 and 255.\n"), exit(1);   if (sscanf(argv[1],"%i",&value)!=1)     fprintf(stderr, "Error: Parameter is not a number.\n"), exit(1);   if ((value<0) || (value>255))     fprintf(stderr, "Error: Invalid numeric value. The parameter number must be between 0 and 255\n"), exit(1);   if (ioperm(base,1,1))     fprintf(stderr, "Error: Couldn't get the port at %x\n", base), exit(1);    outb((unsigned char)value, base); }  
``` 

When exec without sudo I get ```
garfield@komp:~/devel $ ./lpt_test 1 Error: Couldn't get the port at 378 
``` with sudo of course everything works fine.

How to do this without sudo all the time?
I try chmod 777 /dev/lp0 but still the same problem :(
Please help.

(sorry for bad english :( )
--
Garfield.

---

### Post by Xerampelinae on 2005-04-14
I think accessing ports in this way requires root privileges...

So I guess if you don't want to sudo all the time you could make your program suid root...

An alternative to your program's method, would be to use the open() system call on /dev/lp0.  It's probably slower though.  However, in this case I think your permissions (777 on /dev/lp0) would take effect and you wouldn't need root privs.

---

### Post by garfield on 2005-04-15
[QUOTE=Xerampelinae]So I guess if you don't want to sudo all the time you could make your program suid root...[/QUOTE]
suid root? what does it mean?

[QUOTE=Xerampelinae]An alternative to your program's method, would be to use the open() system call on /dev/lp0.  It's probably slower though.  However, in this case I think your permissions (777 on /dev/lp0) would take effect and you wouldn't need root privs.[/QUOTE]
Do you know how to write such a program?

---

### Post by Xerampelinae on 2005-04-15
If you do
> chmod +s my_program 
Then the program named "my_program" will run with the same privileges as the owner of your program.  To set the owner, you would use the following command:
> chown root my_program 

If you set the owner to root, your program will run with root privileges no matter which user runs it.

I'm sure there's more information available on google or some such, but that's a basic outline.

As far as the open() and read() and write() commands... I don't have time at the moment to write out an example program, but you can find more information by reading the man pages.
> man 2 open
man 2 read
man 2 write

---

