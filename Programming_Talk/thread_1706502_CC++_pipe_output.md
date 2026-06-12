---
title: "C/C++ pipe output"
date: 2011-03-13
forum: Programming Talk
---

### Post by scu-ba-de-buntu on 2011-03-13
Hi, I need to plot data and I would like to use gnuplot. I would like to send (gnuplot formated) instructions to gnuplot and have it render the changes in real-time. To do this I was thinking I could just send a new 'plot' command, but that means I need to create and maintain a writable pipe between my program and gnuplot.

This is a stripped down example. How could I make this work?
```
solved. needed \n
[CODE]#include <sys/wait.h>
#include <assert.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>
#include <iostream>
int main(int argc, char *argv[])
{
    int pfd[2];
    pid_t cpid;
    char buf;
   FILE *fp;

   fp = popen("gnuplot", "w"); 
   if (fp == NULL){/*ERROR*/_exit(0);}
   char buffer[] = {"\nplot sin(x)/x\n"};
	fwrite (buffer , 1 , sizeof(buffer) , fp );
   fflush(fp);
	
   getchar();   
   pclose(fp);

   getchar();
}

```
[/CODE]

Please and Thanks!

---

### Post by scu-ba-de-buntu on 2011-03-13
I can only make gnuplot execute one exchange. using something like 
```
"\nplot sin(x)/x \n plot cos(x)/x\n"
```
*seems* to work, but not twice, as in 
```
char buffer[] = {"\nplot sin(x)/x\n"};
	fwrite (buffer , 1 , sizeof(buffer) , fp );
   fflush(fp);
	sleep(3);
     
   char buffer2[] = {"\n\nplot cos(x)/x\n"};
	fwrite (buffer2 , 1 , sizeof(buffer2) , fp );
   fflush(fp);
```

---

### Post by rnerwein on 2011-03-14
high
i'am only working with read and write ( because i know what i'am doing).
habe you tried the sequence: 
popen --> fwirte --> pclose .. --> popen --> fwrite --> pclose.
normaly i think must your "pclose" must work too.
but try "plcose".
by the side - i don't believe in functions - only in system calls.
oh i forgot: if you are really talkink at real-time have a look at:
sched_setscheduler
sched_getscheduler
getpriority
setpriority
ciao

---

