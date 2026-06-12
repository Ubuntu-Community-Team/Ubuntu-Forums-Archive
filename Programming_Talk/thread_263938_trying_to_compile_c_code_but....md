---
title: "trying to compile c code but..."
date: 2006-09-23
forum: Programming Talk
---

### Post by sannin on 2006-09-23
Hi,

I've currently migrated from the land of Windows to this new country called UBUNTU, and so far, i'm liking it.  Anyways on with the question.  I'm trying to compile c codes for my class.  Our instructor gave us a script file that we should use to compile the code, it's called rcc(it looks liek a makefile of some sort??).  This is the contents of rcc file:

#!/bin/zsh -f
foreach i ($argv)
	echo Compiling $i
	gcc -D_REENTRANT -D__USE_POSIX199309 -D_GNU_SOURCE -o `basename $i '.c'` $i -lrt -lpthread -lm
end
echo Done.


We are using this instead of gcc for the POSIX(pthreads), RE-ENTRANT and GNU compatibility.  Although I'm not sure if gcc can do this as well.  

we were also told to:

Add the "bin" directory to your search path, i.e.

	export PATH=~/bin:$PATH

once it is done, we can just use:   $ rcc hello.c
and the hello.c will compile and we can execute the hello file

my questions are as follows:

1) For some reason, this doesn't seem to want to work for ubuntu.  The place where I use this has Fedora 5 installed and it works perfectly.  I was wondering if I need to install additional libraries or am I missing a step? 

thanks,

---

### Post by tht00 on 2006-09-23
First off, you're probably missing the compilers --

Either 1) run this from the terminal:
sudo apt-get install build-essential
or 2) Go to System -> Admin -> Synaptic and install the 'build-essential' package from there.

If that doesn't solve the problem, what are the exact errors are you getting?

---

### Post by sannin on 2006-09-23
yup, I installed the build-essential so the gcc works.  

However, when I use this file:  rcc hello.c 

this is what I get: $ command not found

when I try to run:  ./rcc hello.c  

I get this error message:

bash: ./rcc: /bin/zsh: bad interpreter: No such file or directory

The place where I use this (fedora), I just type rcc hello.c and it compiles everything. :confused:

---

### Post by Buffalo Soldier on 2006-09-23
```
#!/bin/**zsh** -f
```

I'm no expert, but i think that line refers to the zsh command interpreter (shell). While Ubuntu uses the bash shell. I think you can install zsh from the repository.

---

### Post by tht00 on 2006-09-23
> **sannin said:**
> yup, I installed the build-essential so the gcc works.  

However, when I use this file:  rcc hello.c 

this is what I get: $ command not found

when I try to run:  ./rcc hello.c  

I get this error message:

bash: ./rcc: /bin/zsh: bad interpreter: No such file or directory

The place where I use this (fedora), I just type rcc hello.c and it compiles everything. :confused:

Yeah, I think Buffalo is right.  Install zsh (sudo apt-get install zsh), and it should work (or at least be one step closer).

---

### Post by sannin on 2006-09-24
Thanks buffalo and thx for the support.  I installed zsh and the rcc command works now.

I just have a quick follow up question:

when i have a c file that has different header files i.e.,

### EDITED, please see my next post #### sorry for the confusion.

---

### Post by theturtlemoves on 2006-09-24
> **sannin said:**
> Thanks buffalo and thx for the support.  I installed zsh and the rcc command works now.

I just have a quick follow up question:

when i have a c file that has different header files i.e.,

#include<time.h>

for this code:

#include <stdio.h>
#include <sys/time.h>
#include <time.h>
#include <unistd.h>

void print_time ()
{
 struct timeval tv;
 struct tm* ptm;
 char time_string[40];
 long milliseconds;

 /* Obtain the time of day, and convert it to a tm struct. */
 gettimeofday (&tv, NULL);
 ptm = localtime (&tv.tv_sec);
 /* Format the date and time, down to a single second. */
 strftime (time_string, sizeof (time_string), "%Y-%m-%d %H:%M:%S", ptm);
 /* Compute milliseconds from microseconds. */
 milliseconds = tv.tv_usec / 1000;
 /* Print the formatted time, in seconds, followed by a decimal point
   and the milliseconds. */
 printf ("%s.%03ld\n", time_string, milliseconds);
}

I get this error:

$ gcc -o time time.c
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o: In function `_start':../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status

thanks again!

Are you sure that's a system problem? Seems to me you need a main() function in your program.

---

### Post by sannin on 2006-09-24
Sorry I was half-awake last night when I was typing the last message.  
I meant to put this one:  

gcc -o test test2.c
/tmp/cc2SQZEF.o: In function `func':lab2.c:(.text+0x97): undefined reference to `clock_gettime'
:lab2.c:(.text+0xbe): undefined reference to `clock_gettime'
/tmp/cc2SQZEF.o: In function `main':lab2.c:(.text+0x181): undefined reference to `pthread_create'
:lab2.c:(.text+0x1b0): undefined reference to `pthread_join'
collect2: ld returned 1 exit status

and this is the c code:

#include <stdio.h>
#include <time.h>
#include <stdlib.h>
#include <pthread.h>

struct thread_info {
   long long maxitr;
   double exec_time;
};

typedef struct thread_info thread_info_t;

thread_info_t info1;

void test_func(long long maxitr)
{
   long long i;
   double a, b, c;

   b = 2.0; c = 3.0;

   for (i = 0; i < maxitr ; i++) {
         a = b*b + b*c + c*c;
   }

}

void *func(thread_info_t *info)
{
   struct timespec time_1, time_2;
   double exec_time;

   exec_time = 0.0;

   clock_gettime(CLOCK_REALTIME, &time_1);

   test_func((*info).maxitr);
         
   clock_gettime(CLOCK_REALTIME, &time_2);

   exec_time = (time_2.tv_sec - time_1.tv_sec);
   exec_time = exec_time + (time_2.tv_nsec - time_1.tv_nsec)/1.0e9;

   (*info).exec_time = exec_time;

   pthread_exit(NULL);
   
}


int main(void)
{
   pthread_t thread1;
   double maxitr;

   maxitr = 1.0e7;

   info1.maxitr = (long long)maxitr;

   if (pthread_create(&thread1, NULL, (void *)func, &info1) ) {
           printf("Error in creating thread 1\n");
           exit(1);
   }

   pthread_join(thread1, NULL);
   printf("Exec time for thread1 = %f sec\n", info1.exec_time);

   exit(0);
}

thx.

---

### Post by sannin on 2006-09-24
any takers?

---

### Post by po0f on 2006-09-25
If you would have looked in your shell script, you would have found the answer.  You weren't linking your executable to the pthread or rt libraries, so the linker couldn't find those functions.

[quote=sannin]gcc -D_REENTRANT -D__USE_POSIX199309 -D_GNU_SOURCE -o `basename $i '.c'` $i -lrt -lpthread -lm[/quote]

And why are you using shell scripts instead of makefiles?  Zsh shell scripts at that!

---

### Post by maubp on 2006-09-25
> **po0f said:**
> And why are you using shell scripts instead of makefiles?  Zsh shell scripts at that!
Its not his fault, he was told to (see first post):
[quote=sannin]Our instructor gave us a script file that we should use to compile the code[/quote]

---

### Post by po0f on 2006-09-25
maubp,

It was more of a rhetorical question, I did see that his instructor gave them the shell script to use.

---

### Post by Lord Illidan on 2006-09-25
> **po0f said:**
> maubp,

It was more of a rhetorical question, I did see that his instructor gave them the shell script to use.

Perhaps the instructor is living in the stone age? Why don't you take it up with your instructor, **sannin** and ask him to use makefiles...

---

### Post by sannin on 2006-09-25
Thx for the replies, let me see if I can answer some of the comments.

> **Lord Illidan said:**
> Perhaps the instructor is living in the stone age? Why don't you take it up with your instructor, **sannin** and ask him to use makefiles...

I was quite surprised too why i'm using this 'rcc' thing.  I assumed it was some sort of a makefile. Anyways, I believe the reason he was using this rcc is to make sure, i. it's a RE-ENTRANT (for Real Time Control application ii) POSIX (follows posix standards) iii) GNU ( compatible).  I'll gladly mention this to the instructor tomorrow cuz i'm having a hard time compiling the programs at home.

@ po0F:

"If you would have looked in your shell script, you would have found the answer. You weren't linking your executable to the pthread or rt libraries, so the linker couldn't find those functions."

-- I am quite new to the linux world, specially UBUNTU.  So when you mentioned to look into my shell script, I wouldn't know where or what to look.  So if I wasn't linking my exec. to the pthread or rt libs, how do I link it properly?  Perhaps, it would've been nicer if you would've mentione d how to properly proceed.  Regarding the pthread or rt libs, i did a quick man pthread.h and it's not showing properly, so it seems that ubuntu didn't install it... 


BTW, most of my c experience comes from the windows world.  Usually i just compile with Quincy and everything is done.  To be quite honest, I would've gladly stayed with windows but since they want us to use c in linux, i got no choice.

In summary, I believe my original question is still open.  If there's a way for me to use gcc with the appropriate ' -something ' to make it RE-ENTRANT, POSIX, GNU compatible, then I'd gladly appreciate it if somebody lets me know.

thanks and have a good day.

---

### Post by po0f on 2006-09-25
sannin,

[quote=sannin]
#!/bin/zsh -f
foreach i ($argv)
echo Compiling $i
gcc -D_REENTRANT -D__USE_POSIX199309 -D_GNU_SOURCE -o `basename $i '.c'` $i -lrt -lpthread -lm
end
echo Done.[/quote]

The command in that script that you're most interested in is the line with gcc on it (the actual compiler command).  If you're more familiar with Windows, think of it*[EDIT2: I meant to say shell script here, edited for calrification.] as a .bat file.  It shows you all the flags that you need to pass to the preprocessor/compiler/linker to get the executable that you need.  I'll break it down for you:

[list]gcc:
  The command to call the compiler.[/list]
[list]-D_REENTRANT -D__USE_POSIX199309 -D_GNU_SOURCE:
  These are flags passed to the preprocessor to let it know what you want to include into your executable, based on certain conditions.  The REENTRANT one basically means prepare this executable to handle threads.  I looked through time.h and saw that __USE_POSIX199309 needed to be defined to get one of the functions that was failing to link, clock_gettime().  GNU_SOURCE is a common flag needed to get GNU extensions to the standard POSIX libraries.[/list]
[list]-o:
  The -o flag tells gcc where to put the final executable after preprocessing, compilation, and linking are all done.[/list]
[list]`basename $i '.c'`
  The command in backticks (`) is one that is to be run before the command surrounding it.  basename strips off the leading directories, leaving you with the filename.  The optional argument to basename indicates the suffix that is to be stripped off the end.  Basically, given a file '/home/foo/bar.c', it returns 'bar'.[/list]
[list]$i:
  I actually skipped explaining the for loop.  $i is just one of the passes through the loop.  You could have called this script with multiple arguments, and they would all be compiled like this.[/list]
[list]-lrt -lpthread -lm:
  Any argument given to gcc that is preceded by '-l' is the name of a library to link with, in this case the pthread, rt (real time), and m (math, I don't know why this is here) libraries.  The reason you couldn't get the program to compile is because you weren't linking it against the pthread and rt libraries.[/list]

You can't look up the man page for a header file, but you can look up the man page(s) for functions in the header file.  For example, not `man time.h`, but `man clock_gettime`.

Sorry if I didn't explain it to you good enough the first time, I assumed you had some knowledge of Linux programming.

Anyway, I hope this helps.  If not, post again!

And tell your instructor he's a dummy-head (yes, I said dummy-head) for using Zsh scripts and not makefiles.  Every Linux programmer has make installed, but most likely not Zsh.

[EDIT]

Here's an example Makefile (actually save it to a file called Makefile, with a capital M, in the directory with your source files):
```
CC=gcc
DEFINES=-D_REENTRANT -D__USE_POSIX199309 -D_GNU_SOURCE
LIBS=-lpthread -lrt -lm
PROGRAMS=test

all: $(PROGRAMS)

test: test.c
    $(CC) $(DEFINES) -o test test.c $(LIBS)
```

I haven't tested this, but if it doesn't work, let me know and I'll fix it.  BTW, that should be a tab after the line with 'test: test.c' instead of spaces.

---

### Post by sannin on 2006-09-26
thanks for the insight po0F!

---

