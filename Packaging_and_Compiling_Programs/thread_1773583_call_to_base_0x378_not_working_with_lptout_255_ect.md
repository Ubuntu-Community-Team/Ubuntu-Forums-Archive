---
title: "call to base 0x378 not working with lptout 255 ect."
date: 2011-06-02
forum: Packaging and Compiling Programs
---

### Post by 1885 on 2011-06-02
lptout 255 is not recognized by Ubuntu 11.?

$lptout 255 works but will not send signal to parallel port

?  Could be a permissions problem?
any ideas?


I've run the following code via Gentoo and FC12 .
We just installed Ubuntu 11 (very nice !) and we are trying to control some electronics via the parallel port.  I compile the following code with 
$gcc lptout.c -o lptout
I then move lptout to /usr/bin and change permissions
#chmod x+s /usr/bin/lptout
lptout is called via Java, python ect: with
$lptout 255 (example)



#include <stdio.h> //start of code
#include <stdlib.h>
#include <unistd.h>
#include <sys/io.h>

#define *base 0x378 *          /* printer port base address */

main(int argc, char **argv)
{
    int value;

if (argc!=2)
fprintf(stderr, "Error: Wrong number of arguments. This program needs one argument which is number between 0 and 255.\n"), exit(1);
if (sscanf(argv[1],"%i",&value)!=1)
fprintf(stderr, "Error: Parameter is not a number.\n"), exit(1);
if ((value<0) || (value>255))
fprintf(stderr, "Error: Invalid numeric value. The parameter number must be between 0 and 255\n"), exit(1);
if (ioperm(base,1,1))
fprintf(stderr, "Error: Couldn't get the port at %x\n", base), exit(1);

outb((unsigned char)value, base);
}

---

