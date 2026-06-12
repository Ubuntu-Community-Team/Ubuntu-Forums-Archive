---
title: "compiling with gcc and &quot;undefined reference to xxx&quot;"
date: 2011-02-14
forum: Programming Talk
---

### Post by NeillHog on 2011-02-14
I have run up against a wall. I really appreciate any and all help because I am so out of my depth.

I have installed gcc on a NSLU2.
Running gcc -o test test.c brings no error and afterwards I can run the program test with ./test.

test.c
[I]#include <stdio.h>
main()
{
  printf("Linuxquestions.org\n");
}
[/I]

so it seems I did something correct.

But when I try to compile the file that I really want to use "vclient.c" I get an error message 
/tmp/ccuuPxtN.o(.text+0x3bc): In function `main': vclient.c: undefined reference to `initLog'

Now as I may have mentioned I am a long way out of my depth but I looked in the source code and found
#include "common.h"

common.h is in the directory and is obviously being found because if I add another m to make it commmon.h then the compiler complains that it can not find it.

When I look in common.h I find
int initLog(int useSyslog, char *logfile,int debugSwitch);

and looking in common.c (also in the same directory) I find
int initLog(int useSyslog, char *logfile,int debugSwitch) {
	/* oeffnet bei Bedarf syslog oder log-Datei */
        xxxxxxxxxxxxxxxxxx
}

where xxxx is code.

So to me everything looks OK!
But obviously I am missing something fundamental.

As I wrote, I really would appreciate any help.
Thank you
Neill

---

### Post by Arndt on 2011-02-14
> **NeillHog said:**
> I have run up against a wall. I really appreciate any and all help because I am so out of my depth.

I have installed gcc on a NSLU2.
Running gcc -o test test.c brings no error and afterwards I can run the program test with ./test.

test.c
[I]#include <stdio.h>
main()
{
  printf("Linuxquestions.org\n");
}
[/I]

so it seems I did something correct.

But when I try to compile the file that I really want to use "vclient.c" I get an error message 
/tmp/ccuuPxtN.o(.text+0x3bc): In function `main': vclient.c: undefined reference to `initLog'

Now as I may have mentioned I am a long way out of my depth but I looked in the source code and found
#include "common.h"

common.h is in the directory and is obviously being found because if I add another m to make it commmon.h then the compiler complains that it can not find it.

When I look in common.h I find
int initLog(int useSyslog, char *logfile,int debugSwitch);

and looking in common.c (also in the same directory) I find
int initLog(int useSyslog, char *logfile,int debugSwitch) {
	/* oeffnet bei Bedarf syslog oder log-Datei */
        xxxxxxxxxxxxxxxxxx
}

where xxxx is code.

So to me everything looks OK!
But obviously I am missing something fundamental.

As I wrote, I really would appreciate any help.
Thank you
Neill

What are the compilation and linking commands you do to produce vclient?

---

### Post by MadCow108 on 2011-02-14
creating an executable is, simply speaking, a two stage process, compile the source code to object files and link the object files together to form an executable
*undefined reference error* is a linking error
the compiled vclient.c needs to be linked with the compiled symbols from common.c

gcc vclient.c common.c -o output
which is short for:
#compile
gcc -c vclient.c -o vclient.o
#compile
gcc -c common.c -o common.o
#link
gcc vclient.o common.o -o output

should solve this problem.

---

### Post by NeillHog on 2011-02-14
Thank you MadCow108.
I mess about for weeks and you solve the problem in 5 minutes.
If you are ever passing through the Alps I owe you a huge beer.
Thank you!

---

