---
title: "C language - ptrace() and memory reading | help"
date: 2010-06-02
forum: Programming Talk
---

### Post by Rany Albeg on 2010-06-02
Hi all , 

I wrote a simple shell program called my_shell.c
I want to build another program called tracer.c which will trace the process my_shell , take every command typed in it and use exec to run it.

I used ptrace(PTRACE_ATTACH...) in order to attach tracer to my_shell.
I used ptrace(PTRACE_GETREGS...) in order to get registers contents of my_shell.

The problem is - How do i know where the process my_shell stores the command line typed by the user?
In which address?
Is it somewhere in /proc/$pid/...?

This is my code until now :
```

/*tracer.c - father process*/
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/ptrace.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <sys/user.h>
#include <sys/syscall.h>
#include <unistd.h>

int main(int argc, char *argv[])
{   
    pid_t traced_process;
    struct user_regs_struct regs;
    int status;

    char backup[100];
    
    if(argc != 2) 
    {
        printf("Usage: %s <pid to be traced>\n",
               argv[0]);
        exit(1);
    }

    traced_process = atoi(argv[1]);

    if (ptrace(PTRACE_ATTACH,traced_process,NULL,NULL))
           perror("attach");

    waitpid(traced_process,NULL,0);

    if(ptrace(PTRACE_GETREGS,traced_process,&regs,&regs))
           perror("getregs");

     printf("%%esp : 0x%.8lx\n",regs.esp);

    //...STUCK HERE...

    ptrace(PTRACE_DETACH, traced_process,NULL, NULL);
    return EXIT_SUCCESS;
}
``` 

Any idea/help will be appreciated.
Thank you.

---

### Post by Rany Albeg on 2010-06-05
Hello again. I did some work but still i cant get it done.
I'll explain again what is the main purpose of this project and what are the errors:

I wrote a simple shell program named my_shell.c
my_shell needs to be traced by THIS program, which will print every line typed in my_shell.
As you can see below in the if(sc == SYS_read) block, I check for the read system call and then read
all the data stored in ECX register using 'getdata' function below.
It is working fine but i sometimes the output is printed twice and sometimes the output is being connected with previous one.
for example if i typed 'echo "hello world"' in my_shell , here i'll see
echo "hello world"
echo "hello world"

In addition it becomes really messy afterwards, as i said and you can see here -> [http://img59.imageshack.us/img59/5387/screenshotws.png](http://img59.imageshack.us/img59/5387/screenshotws.png)
 
At the right terminal - the traced process , my_shell.
At the left terminal  - the program that will traced my_shell. 

In the above screen shot you see:
1.) I execute my_shell
2.) I run ps to take PID of 'my_shell'
3.) I run 'tracer' at the left terminal, with the PID i got from ps.
4.) 'tracer' prints the output, the ps command.
5.) I run echo hello world at 'my_shell'
6.) Output is being printed twice at 'tracer'
7.) I run 'echo and it becomds messy'
8.) Output is messed at 'tracer'

And so on...

Any idea why is this happening?
Thanks in advance.

The code : 
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/time.h>
#include <time.h>
#include <sys/ptrace.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <sys/user.h>
#include <sys/syscall.h>
#include <unistd.h>

const int long_size   = sizeof(long);
const int BUFFER_SIZE = 100; 
const int TIME_BUFFER = 30;

void 
getdata(pid_t child, long addr,char *str, int len);

char* 
gettime();

void 
error_exit(char* msg);

int main(int argc, char *argv[])
{   
    pid_t traced_process;
    struct user_regs_struct regs;

    int status,
	sc;

    long addr;
    char child_cmdline[BUFFER_SIZE];
    char final_line[BUFFER_SIZE+TIME_BUFFER];
    char* time;

    if(argc != 2)
    {
        printf("Usage: %s <pid to be traced> <log file>\n",argv[0]);
        exit(1);
    }

    traced_process = atoi(argv[1]);

    /* Attaching to 'traced_process'. */
    if(ptrace(PTRACE_ATTACH, traced_process,NULL, NULL) == -1)
		error_exit("PTRACE_ATTACH failed.");

    /* Waiting for signal from 'traced_process'. */
    wait(&status);


    while(1)
    {
	/* Restart 'traced_process' and arrange it to be stopped at the next ENTRY-to
         * or EXIT-from a system call.
         */
	if(ptrace(PTRACE_SYSCALL,traced_process,NULL,NULL) == -1)
		error_exit("PTRACE_SYSCALL failed.");

	/* Wait for signal from 'traced_process'.*/
	wait(&status);

	if(WIFEXITED(status))
		break;
	else if(WIFSTOPPED(status))
	{
		/* Extracting registers contents to 'regs' struct after receiving signal from 'traced_process'. */
		if(ptrace(PTRACE_GETREGS,traced_process,NULL,&regs) == -1)
			error_exit("PTRACE_GETREGS failed.");

		/* Getting the number of the system call stored in orig_eax. */
		sc = regs.orig_eax;

		if(sc == SYS_read )
		{
			/* ecx register holds the wanted data so we will take its address. */
			addr = regs.ecx;
		
			/* Copy 'addr' contents into 'child_cmdline' from process 'traced_process'. */
			getdata(traced_process,addr,child_cmdline,BUFFER_SIZE);

			time = gettime();	        
			/* Printing command typed in 'traced_process' ex: (00:00:00) -> ls -l */
			sprintf(final_line,"(%s) -> %s",time,child_cmdline);
			printf("%s",final_line);
	
			free(time);
		 }
	}
     }

    /* Detaching from process 'traced_process'. */
    ptrace(PTRACE_DETACH, traced_process,NULL, NULL);

    return EXIT_SUCCESS;
}


void
getdata(pid_t child, long addr,char *str, int len)
{   
    char *laddr;
    int i, j;

    union u
    {
            long val;
            char chars[long_size];
    }data;

    i = 0;
    j = len / long_size;
    laddr = str;

    while(i < j)
    {
        if((data.val = ptrace(PTRACE_PEEKDATA, child, addr + i * 4, NULL)) == -1)
		error_exit("PTRACE_PEEKDATA failed.");
        memcpy(laddr, data.chars, long_size);
        ++i;
        laddr += long_size;
    }

    j = len % long_size;

    if(j != 0)
    {
        if((data.val = ptrace(PTRACE_PEEKDATA, child, addr + i * 4, NULL)) == -1)
		error_exit("PTRACE_PEEKDATA failed.");
        memcpy(laddr, data.chars, j);
    }

    str[len] = '\0';
}
char*
gettime()
{
        char* buff = malloc( TIME_BUFFER + 1 );

        if(buff == NULL)
		perror("malloc failed.");

        buff[TIME_BUFFER]  ='\0';
	struct timeval tv;

	time_t curtime;

        gettimeofday(&tv, NULL); 
        curtime=tv.tv_sec;

        strftime(buff,TIME_BUFFER,"%T",localtime(&curtime));

	return buff;
        
}
void 
error_exit(char* msg)
{
	perror(msg);
	exit(1);
}
```

---

### Post by Rany Albeg on 2010-06-06
*bump*

---

### Post by dwhitney67 on 2010-06-06
Can you please explain what "my_shell" is doing?

As for the messy output you have, it could possibly be explained by this:
```

char child_cmdline[BUFFER_SIZE];
...
getdata(traced_process,addr,child_cmdline,BUFFER_SIZE);

```
In getdata(), you are inserting a null-character into "str" (aka child_cmdline) at position BUFFER_SIZE. That's beyond the range of your buffer, which is addressable via an index ranging from 0 through BUFFER_SIZE - 1.

By inserting a null at str[len], where len = BUFFER_SIZE, you are corrupting final_line.

---

### Post by dwhitney67 on 2010-06-06
EDIT:  I compensated for the double-peeking; now only one command is printed.

---------------------------------------------

Out of interest, I took a more careful look at your tracer application, and refined it so that I got better results.

Look at getdata() to see the mods I placed there (which btw, could probably be done better).

tracer.c:
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/time.h>
#include <time.h>
#include <sys/ptrace.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <sys/user.h>
#include <sys/syscall.h>
#include <unistd.h>

#define SIZEOF_LONG sizeof(long)
#define BUFFER_SIZE 1024
#define TIME_BUFFER 30


void  getdata(pid_t child, long addr, char *str, const int len);
char* gettime();
void  error_exit(const char* msg);


int main(int argc, char** argv)
{   
   if (argc != 2)
   {
      printf("Usage: %s <pid to be traced> <log file>\n", argv[0]);
      exit(1);
   }

   pid_t traced_process = atoi(argv[1]);

   /* Attaching to 'traced_process'. */
   if (ptrace(PTRACE_ATTACH, traced_process, NULL, NULL) == -1)
   {
      error_exit("PTRACE_ATTACH failed.");
   }

   /* Waiting for signal from 'traced_process'. */
   int status;
   wait(&status);

   while (1)
   {
      /* Restart 'traced_process' and arrange it to be stopped at the next ENTRY-to
       * or EXIT-from a system call.
       */
      if (ptrace(PTRACE_SYSCALL, traced_process, NULL, NULL) == -1)
      {
         error_exit("PTRACE_SYSCALL failed.");
      }

      /* Wait for signal from 'traced_process'.*/
      wait(&status);

      if (WIFEXITED(status))
      {
         break;
      }
      else if (WIFSTOPPED(status))
      {
         struct user_regs_struct regs;

         memset(&regs, 0, sizeof(regs));

         /* Extracting registers contents to 'regs' struct after receiving signal from 'traced_process'. */
         if (ptrace(PTRACE_GETREGS, traced_process, NULL, &regs) == -1)
         {
            error_exit("PTRACE_GETREGS failed.");
         }

         /* Getting the number of the system call stored in orig_eax. */
         int sc = regs.orig_eax;

         if (sc == SYS_read)
         {
            char child_cmdline[BUFFER_SIZE] = {0};

            /* ecx register holds the wanted data so we will take its address. */
            long addr = regs.ecx;
		
            /* Copy 'addr' contents into 'child_cmdline' from process 'traced_process'. */
            getdata(traced_process, addr, child_cmdline, sizeof(child_cmdline) - 1);

            char* time = gettime();

            /* Printing command typed in 'traced_process' ex: (00:00:00) -> ls -l */
            fprintf(stdout, "(%s) -> %s\n", time, child_cmdline);

            free(time);
         }
      }
   }

   /* Detaching from process 'traced_process'. */
   ptrace(PTRACE_DETACH, traced_process, NULL, NULL);

   return EXIT_SUCCESS;
}


void getdata(pid_t child, long addr, char* str, const int len)
{
   typedef union _data
   {
      long val;
      char chars[SIZEOF_LONG];
   } Data;

   static int ping_pong = 0;

   if ((ping_pong ^= 1) == 1)
   {
      Data data;
      int i = 0;

      while (strlen(str) < len)
      {
         if ((data.val = ptrace(PTRACE_PEEKDATA, child, addr + i * SIZEOF_LONG, NULL)) == -1)
         {
            error_exit("PTRACE_PEEKDATA failed.");
         }

         int j = 0;
         for (; j < SIZEOF_LONG && data.chars[j] != '\n'; ++j, ++str)
         {
           *str = data.chars[j];
         }

         if (data.chars[j] == '\n') break;

         ++i;
      }
   }

   *str = 0;
}


char* gettime()
{
   char* buff = malloc(TIME_BUFFER + 1);

   if (!buff)
   {
      perror("malloc failed.");
   }

   buff[TIME_BUFFER] = '\0';
   struct timeval tv;

   time_t curtime;

   gettimeofday(&tv, NULL); 
   curtime = tv.tv_sec;

   strftime(buff, TIME_BUFFER, "%T", localtime(&curtime));

   return buff;
}


void error_exit(const char* msg)
{
   perror(msg);
   exit(1);
}

```

---

### Post by Rany Albeg on 2010-06-07
Hello dwhitney67,

Thank you very much for your help.
As for your question about 'my_shell' : it actually parses a given input from the user and uses execvp function to run the requested command line.

I understand the problems that are in 'getdata' so I modified 'getdata' according to your changes - but I'm using the XOR operation outside 'getdata'.
Maybe later I'll try to write it better as you said.
I like your idea of using ping_pong but don't really understand why you should use it?
In other words - where in the code am i calling 'getdata' twice? my guess is - when exiting a system call and entering one.
but which system call? There are few system calls.

Also why did you decide to use 'memset' here? :

```
      else if (WIFSTOPPED(status))
      {
         struct user_regs_struct regs;

         memset(&regs, 0, sizeof(regs));
         ...
       }

```

ptrace(PTRACE_GETREGS,...) will overwrite the existing data in newly created 'regs'.


I appreciate your effort in reading , understanding and modifying the code.
Thank you.

---

### Post by dwhitney67 on 2010-06-07
> **Rany Albeg said:**
> Hello dwhitney67,

Thank you very much for your help.
As for your question about 'my_shell' : it actually parses a given input from the user and uses execvp function to run the requested command line.

I implemented my own 'my_shell' that reads stdin using fgets(), then issues the command using system().

> **Rany Albeg said:**
> 
I understand the problems that are in 'getdata' so I modified 'getdata' according to your changes - but I'm using the XOR operation outside 'getdata'.
Maybe later I'll try to write it better as you said.
I like your idea of using ping_pong but don't really understand why you should use it?
In other words - where in the code am i calling 'getdata' twice? my guess is - when exiting a system call and entering one.
but which system call? There are few system calls.

The ptrace(PTRACE_GETREGS, ...) is being called twice, and in each instance the regs.orig_eax is set to SYS_Read; this is why getdata() is called twice.  This was undesirable, thus the reason for placing the ping_pong in that function.  It could just as well be placed outside the function too.

> **Rany Albeg said:**
> 
Also why did you decide to use 'memset' here? :

```
      else if (WIFSTOPPED(status))
      {
         struct user_regs_struct regs;

         memset(&regs, 0, sizeof(regs));
         ...
       }

```

ptrace(PTRACE_GETREGS,...) will overwrite the existing data in newly created 'regs'.

It was my futile attempt to see if I could get ptrace(PTRACE_GETREGS, ...) from reporting the same status twice.

> **Rany Albeg said:**
> 
I appreciate your effort in reading , understanding and modifying the code.
Thank you.
You're welcome; I was merely monkeying around to see if I could get it to work and learn something in the process.

---

### Post by Rany Albeg on 2010-06-08
Hi dwhitney67,

So I understand now that ptrace(PTRACE_GETREGS...) is being called twice.
I still don't understand why is that happening.
Can you be more specific?

---

### Post by Rany Albeg on 2010-06-11
Hello all,

Thanks to dwhitney67 , I managed to solve my problem.
As you can see and as dwhitney67 said earlier I called ptrace(PTRACE_GETREGS,...) twice so i got a double output.
That was because of the call to ptrace(PTRACE_SYSCALL,...) function which restarts the child process and arranges it to be stopped at the next
entry-to OR exit-from a system call.
I only needed that the child process will stop at the next entry-to a system call.

So instead of using ptrace(PTRACE_SYSCALL,...) I used ptrace(PTRACE_SINGLESTEP,...) and now I don't have to use
this :

```
   if ((ping_pong ^= 1) == 1)
   {
	...
   }

```
'ping pong block' ( see 'getdata' function) because the child process stops only once per system call.

I would like to thank dwhitney67 and I hope that this solution will serve the community at the future.

Have a nice day.

---

