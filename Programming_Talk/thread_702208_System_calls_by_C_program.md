---
title: "System calls by C program"
date: 2008-02-20
forum: Programming Talk
---

### Post by pt_lam on 2008-02-20
Just got a school assignment. I have to write a C program to perform 2 system calls.
1. get the date and time
2. send the date and time data to printer and print it

I have no experience on Unix/Linux programming. Can anyone help?

Thanks!

---

### Post by ruy_lopez on 2008-02-20
To get the date and time, you type 'date' at the command line. You'll have to work out the rest.

---

### Post by lnostdal on 2008-02-20
man 2 time
man 3 ctime

..and you can use *fopen* etc. on */dev/lp**

---

### Post by ruy_lopez on 2008-02-20
> **lnostdal said:**
> man 2 time
man 3 ctime

I was going to suggest time & ctime. But then I thought, "only 2 syscalls". Also, I don't think a high-school would expect you to use pointers. 

I may be wrong. But I was thinking along the lines of 'system()'. Are you sure the school want a C program?

---

### Post by pt_lam on 2008-02-20
> **ruy_lopez said:**
> I was going to suggest time & ctime. But then I thought, "only 2 syscalls". Also, I don't think a high-school would expect you to use pointers. 

I may be wrong. But I was thinking along the lines of 'system()'. Are you sure the school want a C program?

Yes, a C program is needed in the assignment.
So can you tell more in details how to do the things using C? 
Thanks!

---

### Post by lnostdal on 2008-02-20
well, how far have you got now? -- or where are you stuck now?

---

### Post by ruy_lopez on 2008-02-20
Did they teach you C? Or did your lecturer just, out of the blue, tell you to write a C program?

---

### Post by pt_lam on 2008-02-20
> **ruy_lopez said:**
> Did they teach you C? Or did your lecturer just, out of the blue, tell you to write a C program?

I'm sorry that I just don't know how to begin

---

### Post by ruy_lopez on 2008-02-20
This will give you the basics:

[http://www.physics.drexel.edu/courses/Comp_Phys/General/C_basics/]("http://www.physics.drexel.edu/courses/Comp_Phys/General/C_basics/")

You should probably install this:

```
sudo apt-get install build-essential
```

To get the manpages for C functions:

```
sudo apt-get install manpages-dev
```

---

### Post by pedro_orange on 2008-02-20
Do what ruy_lopez said then;

Step 1:

Make a hello world in C.

Step 2: 

Make that hello world echo through system().

Step 3:

Change the system() to a Bash/Shell command.

Step 4:

Capture the output of said command in an appropriate container.

Step 5:

Run a second system() passing the captured output in as a parameter. 

[Hint: use the man pages of the shell commands you're going to be executing so you get what you want. Also you will need to include libraries for certain functions, for example system()]

---

### Post by LaRoza on 2008-02-20
Using system() is not a system call.

---

### Post by pedro_orange on 2008-02-20
> **LaRoza said:**
> Using system() is not a system call.

No but it allows you to run shell commands, which is effectively accomplishing what he needs?

---

### Post by ruy_lopez on 2008-02-20
> **LaRoza said:**
> Using system() is not a system call.

You are right. However, the OP's comments suggests his lecturer doesn't know the difference between a system call and a function. To achieve his aim using only two "system calls" would require something simple, like system().

If he uses real system calls, it'll take more than two to get the job done.

---

### Post by pt_lam on 2008-02-21
So what about dealing with the printer?
I know there's a lp command, but how can I do the similar in C?
Thanks

---

### Post by ruy_lopez on 2008-02-21
> **lnostdal said:**
> and you can use *fopen* etc. on */dev/lp**

See Lars' tip above.

---

### Post by slavik on 2008-02-21
how about system("date | lpr"); ??? did I give problem away? one call to the shell ...

if this class is about workstations programming, the assignment is meant to teach fork/exec and pipes ... if this is an intro class, something is wrong ...

---

### Post by pt_lam on 2008-02-21
> **slavik said:**
> how about system("date | lpr"); ??? did I give problem away? one call to the shell ...

if this class is about workstations programming, the assignment is meant to teach fork/exec and pipes ... if this is an intro class, something is wrong ...

The problem is... I have to do the "date | lpr" stuff in C program.
The assignment specifies that system calls by C program should be used instead of shell commands.

---

### Post by slavik on 2008-02-22
my question remains: what is the course name, description, and what is it supposed to teach you how to do?

---

### Post by pedro_orange on 2008-02-22
> **pt_lam said:**
> The problem is... I have to do the "date | lpr" stuff in C program.
The assignment specifies that system calls by C program should be used instead of shell commands.

Your teacher should have told you -how- to do a system call then, if he's expecting you to write a program to do this.
Or at least told you the libraries to use. Which would then just be a reading assignment ^^
I found that pretty much every programming assignment up to last year at university is usually explained and/or done for you in the course notes.

---

### Post by pt_lam on 2008-02-22
The course is called Operating Systems. So far the lecturer taught the general stuff about process management, scheduling, etc, and taught nothing about the details about shell commands system calls, or even C program.

Now he gives us this assignment:
"In UNIX / LINUX environment, write a short ‘C’ program using any TWO system calls, (Suggestion: to
request system data such as date and time, and to print a file to printer) then submit,
(i) the program listing and,
(ii) the results from the program execution (on using the system calls)."

---

### Post by dwhitney67 on 2008-02-22
You need to confirm with your professor if it is acceptable to use the system() C-library function.  If you can, then the assignment is cake.  Otherwise, you will need to call the appropriate C-library functions to get the system time, convert it to a date with the canonical format (e.g. YYY-MM-DD HH-MM-SS), and somehow send this data to the printer.

Someone earlier suggested opening /dev/lp* and then writing data to it.  That won't work for every system; for example, on my system I do not have an lp device node; my printer is networked.

The easiest way, and you need to verify if this is acceptable, is to do the following:
[PHP]#include <stdlib.h>

int main()
{
  system( "date | lp" );
  return 0;
}[/PHP]

Alternatively, the harder way is:
[PHP]#include <time.h>      // for time()
#include <stdio.h>     // for fopen(), fwrite()
#include <unistd.h>    // for ctime(), unlink()
#include <string.h>    // for strlen()
#include <stdlib.h>    // for system()

int main()
{
  const time_t systemTime = time( 0 );

  const char *canonicalTime = ctime( &systemTime );

  FILE *outFile = fopen( "/tmp/dateFile", "w" );

  if ( outFile )
  {
    fwrite( canonicalTime, strlen( canonicalTime ), 1, outFile );

    fclose( outFile );

    system( "lp /tmp/dateFile" );

    unlink( "/tmp/dateFile" );
  }

  return 0;
}[/PHP]

---

### Post by slavik on 2008-02-22
> **dwhitney67 said:**
> Someone earlier suggested opening /dev/lp* and then writing data to it.  That won't work for every system; for example, on my system I do not have an lp device node; my printer is networked.

If you use CUPS, then lpr can be made to print to the networked printer :)

---

### Post by dwhitney67 on 2008-02-22
Do you care to elaborate?  Maybe this could help the OP.

---

### Post by davehedge on 2011-02-22
> **dwhitney67 said:**
> You need to confirm with your professor if it is acceptable to use the system() C-library function.  If you can, then the assignment is cake.  Otherwise, you will need to call the appropriate C-library functions to get the system time, convert it to a date with the canonical format (e.g. YYY-MM-DD HH-MM-SS), and somehow send this data to the printer.

Someone earlier suggested opening /dev/lp* and then writing data to it.  That won't work for every system; for example, on my system I do not have an lp device node; my printer is networked.

The easiest way, and you need to verify if this is acceptable, is to do the following:
[PHP]#include <stdlib.h>

int main()
{
  system( "date | lp" );
  return 0;
}[/PHP]Alternatively, the harder way is:
[PHP]#include <time.h>      // for time()
#include <stdio.h>     // for fopen(), fwrite()
#include <unistd.h>    // for ctime(), unlink()
#include <string.h>    // for strlen()
#include <stdlib.h>    // for system()

int main()
{
  const time_t systemTime = time( 0 );

  const char *canonicalTime = ctime( &systemTime );

  FILE *outFile = fopen( "/tmp/dateFile", "w" );

  if ( outFile )
  {
    fwrite( canonicalTime, strlen( canonicalTime ), 1, outFile );

    fclose( outFile );

    system( "lp /tmp/dateFile" );

    unlink( "/tmp/dateFile" );
  }

  return 0;
}[/PHP]


hey i have to do a system call using ubuntu 10.10 in a virtual box and ive tried ur methods above with no success i also gotta do a interrupt function simular to this 1 in MS-DOS 

please help as ive tired i duno how many methods now lol

---

### Post by howefield on 2011-02-22
To increase your chances of getting help, please start a fresh thread rather than tag on to this 2 year old one. You can reference this thread if need be.

---

