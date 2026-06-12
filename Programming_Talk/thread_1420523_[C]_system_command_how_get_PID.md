---
title: "[C] system command: how get PID"
date: 2010-03-03
forum: Programming Talk
---

### Post by erotavlas on 2010-03-03
Hi all,

I would like to know  how can I get the PID of the program executed by the system command. For example the command system("VLC"). I can't find feasible solution.

Thank you very much

---

### Post by alexandari on 2010-03-03
```
 ps cux 
```

Edit (later) : sorry didn't understand exactly what you were asking...

---

### Post by MadCow108 on 2010-03-03
I don't think its possible with the system command (at not least without using a second system command which calls ps)
also it would make little sense because system does not return until the called process ended (I think)

consider using fork and exec family function (man 3 exec)
fork returns the pid of the child process
```

#include <sys/types.h>
#include <unistd.h>
#include <stdio.h>


int main(int argc, const char *argv[])
{
  pid_t pid;
  if ((pid = fork()) < 0) {
    puts("error");
  }
  else if (pid == 0) {
    puts("child");
    execv("someprogram", NULL);
  }
  else {
    printf("master, child pid: %d\n", pid);
    sleep(6);
    puts("killing child");
    char t[100];
    snprintf(t,100, "kill %d", pid);
    system(t); //sending sigterm would be better
    puts("ending master");
  }
  return 0;
}

```

---

### Post by psusi on 2010-03-03
Aye, the system **function** does not return until it has finished, so by the time you get control again, there IS no other process to get the pid of.

---

### Post by erotavlas on 2010-03-03
> **psusi said:**
> Aye, the system function does not return until it has finished, so by the time you get control again, there IS no other process to get the pid of.

The system function returns the control if it is terminated & with parameter. system("vlc &")


I have written this code to terminate vlc. But it doesn't work. I get segmentation fault

```
#include <stdio.h>   /* printf, stderr, fprintf */
#include <unistd.h>  /* _exit, fork */
#include <stdlib.h>  /* exit */
#include <errno.h>   /* errno */

#include <signal.h>
#include <string.h>



// getPID:
void getPID(char* processName, char* processID)
{
    char* args[2];
    char str[100];

    args[0] = "pidof ";
    args[1] = processName;
    
        strcpy (str,args[0]);
        strcat (str,args[1]);
    
     FILE* cmdresults = popen(str, "r");
    fscanf (cmdresults, "%s", processID);
        printf("pid = %s\n", processID);
    
    pclose(cmdresults);
            
    int a = system(str);
    printf("system call: %s \nstatus: %d\n", str, a);    
          
}


// killProcess: kill VLC process to permit dynamic update
void killProcess(char* processID)
{
    char* args[2];
    char str[50];

    args[0] = "/bin/kill -9 ";
    args[1] = processID;
    
        strcpy (str,args[0]);
        strcat (str,args[1]);
            
    int a = system(str);
    printf("system call: %s \nstatus: %d\n", str, a);    
      
}


 
int main(void)
{

    char* processID = "0";
    
    system("/usr/bin/vlc &");

    sleep(3);
    
    // get PID of vlc
    getPID("vlc", processID);

    if (strcmp(processID, "0") != 0)    
    //    killProcess(processID);

    return 0;
 
}
```where is the problem?

PS I used the same code with killall and process name. It work well. Now I have more than one vlc instance and so I need the process ID

---

### Post by MadCow108 on 2010-03-03
processId is a string literal which are read only ( the type should be const char* btw)
so you can"t use it as a buffer for your fscanf

also you could use the kill(pid, SIGTERM) instead of the system("kill")

I hope this is just a private program
system function calls are dangerous to computer security in certain cases

---

### Post by erotavlas on 2010-03-03
> **MadCow108 said:**
> processId is a string literal which are read only ( the type should be const char* btw)
so you can"t use it as a buffer for your fscanf

also you could use the kill(pid, SIGTERM) instead of the system("kill")

I hope this is just a private program
system function calls are dangerous to computer security in certain cases

This is a prototype code...

I couldn't understand how to change the code...

---

### Post by psusi on 2010-03-03
> **erotavlas said:**
> The system function returns the control if it is terminated & with parameter. system("vlc &")


Not quite.  system() executes the system shell and passes it the command line you specify.  The shell interprets & to mean that it should background the job and continue.  With no further commands to process, the shell exits and so system() returns.

You should be using fork(), exec(), and kill() instead of making all the shell call outs.  fork() returns the pid of the new child process which you can later just pass to kill() without needing to dork about with all of the string formatting.  Also you should not use SIGKILL unless the process will not respond to SIGTERM.

---

### Post by johnl on 2010-03-03
I've written a sample program that does what you want using fork, exec, and kill.  Hopefully you can see how much easier it would be than dealing with the system() call :)

```

#define _POSIX_SOURCE  /* for kill() */

#include <stdlib.h>
#include <stdio.h>

#include <unistd.h>    /* for fork, exec, kill */
#include <sys/types.h> /* for pid_t            */
#include <sys/wait.h>  /* for waitpid          */
#include <signal.h>    /* for SIGTERM, SIGKILL */

/*
 * fork a child process, execute vlc, and return it's pid.
 * returns -1 if fork failed.
 */
pid_t spawn_vlc(void)
{
    pid_t pid = fork();
    if (pid == -1) {
        perror("fork");
        return -1;
    }

    /* when you call fork(), it creates two copies of your program:
     * a parent, and a child. you can tell them apart by the return
     * value from fork().  If fork() returns 0, this is is the child
     * process.  If fork() returns non-zero, we are the parent and the
     * return value is the PID of the child process. */
    if (pid == 0) {
        /* this is the child process.  now we can call one of the exec
         * family of functions to execute VLC.  when you call exec,
         * it replaces the currently running process (the child process)
         * with whatever we pass to exec.  So our child process will now
         * be running VLC.  exec() will never return except in an error
         * case, since it is now running the VLC code and not our code. */
        execlp("vlc", "vlc", (char*)NULL);
        perror("vlc");
        abort();

    } else {
        /* parent, return the child's PID back to main. */
        return pid;
    }
}


int main(int argc, char* argv[])
{
    pid_t vlc = spawn_vlc();

    if (vlc == -1) {
        fprintf(stderr, "failed to fork child process\n");
        return 0;
    }

    printf("spawned vlc with pid %d\n", vlc);

    sleep(3);

    /* kill will send the specified signal to the specified process.
     * in this case, we send a TERM signal to VLC, requesting that it
     * terminate.  If that doesn't work, we send a KILL signal.
     * If that doesn't work, we give up. */
    if (kill(vlc, SIGTERM) < 0) {
        perror("kill with SIGTERM");
        if (kill(vlc, SIGKILL) < 0) {
            perror("kill with SIGKILL");
        }
    }

    /* this shows how we can get the exit status of our child process.
     * it will wait for the the VLC process to exit, then grab it's return
     * value. */
    int status = 0;
    waitpid(vlc, &status, 0);
    printf("VLC exited with status %d\n", WEXITSTATUS(status));

    return 0;
}

```

---

### Post by whirlwind on 2010-03-03
+1 for not using system().  that was a great example btw, john very similar to how I was taught it in my intro systems class.

ww

---

### Post by MadCow108 on 2010-03-03
> **erotavlas said:**
> This is a prototype code...

I couldn't understand how to change the code...

stuff in double quotes are so called string literals or string constants in C
they get placed in some global read only memory section.
What is important is that you cannot change that memory.
Example:
```

const char * str = "tt"
str[0] = 'b'

```
this will segfault. It is the same problem in your code just that your declaration is in another function than the write.

Just give your fscanf a new writable buffer:
```

char str[100];
fscanf(filestream,"%s", str);

```

---

### Post by psusi on 2010-03-03
You need to leave some time after sending SIGTERM before giving up and sending SIGKILL.  It can take the program a second or two to shut down properly when it gets the SIGTERM.

---

### Post by johnl on 2010-03-03
> **psusi said:**
> You need to leave some time after sending SIGTERM before giving up and sending SIGKILL.  It can take the program a second or two to shut down properly when it gets the SIGTERM.

Yeah, the way I wrote that turns out to be incorrect.  kill() will return failure only if the process doesn't exist or we don't have permission to send that signal to it.  So the code should be more like:

```

if (kill(vlc, SIGTERM) < 0) {
    if (errno == ESRCH) {
         printf("process does not exist (already exited?)\n");
    } else {
         perror("kill");
    }
} 

// sleep or wait for a bit, then try again with SIGKILL.

```

Thanks for pointing that out.

---

### Post by erotavlas on 2010-04-01
> **johnl said:**
> I've written a sample program that does what you want using fork, exec, and kill.  Hopefully you can see how much easier it would be than dealing with the system() call :)

```

#define _POSIX_SOURCE  /* for kill() */

#include <stdlib.h>
#include <stdio.h>

#include <unistd.h>    /* for fork, exec, kill */
#include <sys/types.h> /* for pid_t            */
#include <sys/wait.h>  /* for waitpid          */
#include <signal.h>    /* for SIGTERM, SIGKILL */

/*
 * fork a child process, execute vlc, and return it's pid.
 * returns -1 if fork failed.
 */
pid_t spawn_vlc(void)
{
    pid_t pid = fork();
    if (pid == -1) {
        perror("fork");
        return -1;
    }

    /* when you call fork(), it creates two copies of your program:
     * a parent, and a child. you can tell them apart by the return
     * value from fork().  If fork() returns 0, this is is the child
     * process.  If fork() returns non-zero, we are the parent and the
     * return value is the PID of the child process. */
    if (pid == 0) {
        /* this is the child process.  now we can call one of the exec
         * family of functions to execute VLC.  when you call exec,
         * it replaces the currently running process (the child process)
         * with whatever we pass to exec.  So our child process will now
         * be running VLC.  exec() will never return except in an error
         * case, since it is now running the VLC code and not our code. */
        execlp("vlc", "vlc", (char*)NULL);
        perror("vlc");
        abort();

    } else {
        /* parent, return the child's PID back to main. */
        return pid;
    }
}


int main(int argc, char* argv[])
{
    pid_t vlc = spawn_vlc();

    if (vlc == -1) {
        fprintf(stderr, "failed to fork child process\n");
        return 0;
    }

    printf("spawned vlc with pid %d\n", vlc);

    sleep(3);

    /* kill will send the specified signal to the specified process.
     * in this case, we send a TERM signal to VLC, requesting that it
     * terminate.  If that doesn't work, we send a KILL signal.
     * If that doesn't work, we give up. */
    if (kill(vlc, SIGTERM) < 0) {
        perror("kill with SIGTERM");
        if (kill(vlc, SIGKILL) < 0) {
            perror("kill with SIGKILL");
        }
    }

    /* this shows how we can get the exit status of our child process.
     * it will wait for the the VLC process to exit, then grab it's return
     * value. */
    int status = 0;
    waitpid(vlc, &status, 0);
    printf("VLC exited with status %d\n", WEXITSTATUS(status));

    return 0;
}

```

Hi, 

I appreciate a lot your help. I haven't had a free time in the last mounth. Now I'm trying to follow your suggestion...I have two questions:
1)How can I call vlc and passing to it the parameters with the execl or execv functions ?

Like vlc -I rc image.jpg --fake-duration 7200000 --sout '#transcode{vcodec=H263p,width=352,height=288,acodec=none}:duplicate{dst=rtp{dst=192.168.0.4,port-audio=12280,port-video=15158}}' 

I have tried with 

    ```
char* args[9];
    char str[500];

    args[0] = "/usr/bin/vlc -I rc ";
    args[1] = outputImage;
    strcpy (str,args[0]);
        strcat (str,args[1]);
        
              execl(str, "vlc", (char*) NULL)
        execv("/usr/bin/vlc", args);


```
It doesn't work.
              

2)With your example can I have more than one instance of VLC running in the system? I need to call fork() for every instance?

---

### Post by johnl on 2010-04-01
Hi,

1. With execlp() you pass the arguments like so

```

/* execlp(program, arg0, arg1, arg2, ... (char*)NULL); */
   execlp("vlc", "vlc", "-I", "rc", "image.jpg" 
          "--fake-duration", "7200000", /* ... etc ...*/
          (char*)NULL);

```

If you use a different member of the exec family, like execvp, you can pass the arguments as null-terminated an array:

```

char** args = malloc(sizeof(char*) * (NUM_ARGS + 1));
args[0] = "vlc";
args[1] = "-I";
args[2] = "rc"
args[3] = "image.jpg"
/* etc */
args[NUM_ARGS] = NULL;
execvp("vlc", args);

```

The manpage for 'exec' describes the different members of the exec family. 
exec**l*** functions all take a variable number of arguments for parameters to pass to the program.
exec**v*** functions expect the parameters as a null-terminated array of strings.
exec***p** functions search the $PATH environmental variable for the program you want to call, instead of requiring a full path to be passed as the first argument (this is why we can just call "vlc" above instead of "/usr/bin/vlc").


2.  Yes, you can fork as many children as you like.  In the case of the example I gave above, this would be as simple as calling spawn_vlc() again.  You would need to remember to waitpid() for all your children's PIDs as well.

Hope this helps!

---

### Post by erotavlas on 2010-04-03
I have a new question ;)


I  need to use the code as root user. So I must use vlc-wrapper instead of vlc. The function execv("usr/bin/vlc", args) works well while doesn't work with execv("usr/bin/vlc-wrapper", args). How can I solve the problem?

Thank you

---

### Post by dwhitney67 on 2010-04-03
> **erotavlas said:**
> I have a new question ;)


I  need to use the code as root user. So I must use vlc-wrapper instead of vlc. The function execv("usr/bin/vlc", args) works well while doesn't work with execv("usr/bin/vlc-wrapper", args). How can I solve the problem?

Thank you

It works fine for me.  Thus I have to conclude that you have a programming mistake.  Did you read the man-page for execv() carefully?

Examine this code and compare with whatever you are trying to accomplish:
```

#include <unistd.h>
#include <string.h>
#include <errno.h>
#include <stdio.h>

int main(int argc, char** argv)
{
   char* cmd      = "/usr/bin/vlc-wrapper";
   char* myArgs[] = { cmd, "/tmp/KingdomCome.mp3", (char*) 0 };

   execv(cmd, myArgs);

   // should not reach here unless error occurs
   printf("Error occurred: %s (%d)\n", strerror(errno), errno);

   return -1;
}

```

---

### Post by erotavlas on 2010-04-04
> **dwhitney67 said:**
> It works fine for me.  Thus I have to conclude that you have a programming mistake.  Did you read the man-page for execv() carefully?

Examine this code and compare with whatever you are trying to accomplish:
```

#include <unistd.h>
#include <string.h>
#include <errno.h>
#include <stdio.h>

int main(int argc, char** argv)
{
   char* cmd      = "/usr/bin/vlc-wrapper";
   char* myArgs[] = { cmd, "/tmp/KingdomCome.mp3", (char*) 0 };

   execv(cmd, myArgs);

   // should not reach here unless error occurs
   printf("Error occurred: %s (%d)\n", strerror(errno), errno);

   return -1;
}

```

Your solution works only with one parameter. If I try with this

```
    char* args[10];
    
    args[0] = " -I rc ";    
    args[1] = outputImage;
    args[2] = " --fake-duration 7200000 --sout '#transcode{vcodec=H263p,width=352,height=288,acodec=none}:duplicate{dst=rtp{dst=";
    args[3] = IP;
    args[4] = ",port-audio=";
    args[5] = ports[0];
    args[6] = ",port-video=";
    args[7] = ports[1];
    args[8] = "}}' ";
    
    char * cmd = "/usr/bin/vlc-wrapper";
    char* myArgs[] = { cmd, args[1], args[2], args[3], args[4], args[5], args[6], args[7], args[8], (char*) NULL };

    execv(cmd, myArgs);


```I get open error from vlc.

My older version with system function is the following 

```
char* args[9];
    char str[500];

    args[0] = "/usr/bin/vlc-wrapper -I rc ";
    args[1] = outputImage;
    args[2] = " --fake-duration 7200000 --sout '#transcode{vcodec=H263p,width=352,height=288,acodec=none}:duplicate{dst=rtp{dst=";
    args[3] = IP;
    args[4] = ",port-audio=";
    args[5] = ports[0];
    args[6] = ",port-video=";
    args[7] = ports[1];
    args[8] = "}}' &";
    strcpy (str,args[0]);
    strcat (str,args[1]);
    strcat (str,args[2]);
    strcat (str,args[3]);
    strcat (str,args[4]);
    strcat (str,args[5]);
    strcat (str,args[6]);
    strcat (str,args[7]);
    strcat (str,args[8]);
    
    int a = system(str);
    printf("system call: %s \nstatus: %d\n", str, a);    
    
```[B]
[B]It works well

How can I resolve the problem?


Thank[/B]
[/B]

---

### Post by dwhitney67 on 2010-04-04
Sorry, the following code, with multiple args, works for me:
```

#include <unistd.h>
#include <string.h>
#include <errno.h>
#include <stdio.h>

int main(int argc, char** argv)
{
   char* cmd      = "/usr/bin/vlc-wrapper";

   char* myArgs[] = { cmd,
                      "/tmp/KingdomCome.mp3",
                      "--volume",
                      "80",
                      (char*) 0 };

   execv(cmd, myArgs);

   // should not reach here unless error occurs
   printf("Error occurred: %s (%d)\n", strerror(errno), errno);

   return -1;
}

```
Check your options; make sure they are valid.  In fact, I would recommend that you start with a minimal set of args so that you can test your app as you go along.


P.S.  In case you have failed thus far to see the issue with your app, it is the joining of the option-args and associated values with such.  You need to specify option-arg and each value using a separate entry in your args[] array; this is only applicable if there is white-space between the option-arg and value.

Perhaps you should write a small app that tests getopt() and/or getopt_long() to get a feel for how the vlc-wrapper is interpreting your command line args.  You can read about these functions at "man 3 getopt".

---

### Post by erotavlas on 2010-04-04
> P.S. In case you have failed thus far to see the issue with your app, it is  the joining of the option-args and associated values with such.  You  need to specify option-arg and each value using a separate entry in your  args[] array; this is only applicable if there is white-space between  the option-arg and value.How can I specify the option-arg?

---

### Post by dwhitney67 on 2010-04-04
```

char* args[] = {
                  cmd,
                  "-I", "rc",    
                  outputImage,
                  "--fake-duration", "7200000",
                  ...
               };

```

P.S.  I'm not sure what exactly "-I rc" is meant to do; if it is merely to hide the VLC player, then consider running "cvlc" instead.

---

### Post by erotavlas on 2010-04-04
Thank, with your suggestion works well. Is there a more elegant way to pass the  parameters?How can I overcome the problem of white spaces?

The option cvlc can't be used with vlc-wrapper :(

---

### Post by dwhitney67 on 2010-04-04
> **erotavlas said:**
> Thank, with your suggestion works well. Is there a more elegant way to pass the  parameters?How can I overcome the problem of white spaces?

Don't use them!  :-)

> 
The option cvlc can't be used with vlc-wrapper :(
cvlc is not an option; it is a wrapper for vlc, similar to vlc-wrapper.  When running clvc, the VLC GUI is not displayed.

---

### Post by erotavlas on 2010-04-04
I still have the same problem...

The command exec take only some arguments ](*,)


```
char * cmd = "/usr/bin/vlc-wrapper";
    char * myArgs[] = { cmd, outputImage, "--fake-duration", "7200000", "--sout", "'#transcode{vcodec=H263p,width=352,height=288,acodec=none}:duplicate{dst=rtp{dst=", IP, ",port-audio=", ports[0], ",port-video=", ports[1], "}}' ", (char*) NULL } ;
```



This is the error ](*,)

```

 main stream output error: stream chain failed for `standard{mux="",access="'#transcode{vcodec=H263p,width=352,height=288,acodec=none}",dst="duplicate{dst=rtp{dst="}


```

---

### Post by dwhitney67 on 2010-04-04
Take this "monster":
```

'#transcode{vcodec=H263p,width=352,height=288,acodec=none}:duplicate{dst=rtp{dst=", IP, ",port-audio=", ports[0], ",port-video=", ports[1], "}}

```
and build a string out of it, since it appears that VLC wants to interpret it as one value.

I can't guarantee the following is correct (ie there might be syntax errors):
```

...

char buf[1024] = {0};

snprintf(buf, sizeof(buf),
         "#transcode{vcodec=H263p,width=352,height=288,acodec=none}"
         ":duplicate{dst=rtp{dst=%s,port-audio=%s,port-video=%s}}",
         IP, ports[0], ports[1]);

char* vlc    = "/usr/bin/vlc-wrapper";
char* args[] = { vlc,
                 outputImage,
                 "--fake-duration", "7200000",
                 "--sout", buf,
                 (char*) NULL
               };

execv(vlc, args);

// check for error here!!!

```

---

### Post by erotavlas on 2010-04-05
Thank you very much. You are very powerful programmer :)


I have three last questions:

1) Now my program works as with the system() function but now is better. There is the last detail: how can I launch vlc as vlc-wrapper with -I rc parameters? I prefer to use it without interface, but it isn't a problem. [U]**SOLVED**
[/U] 
2) What is the purpose of the following code? What I can do with the return value?

```

/* this shows how we can get the exit status of our child process.
     * it will wait for the the VLC process to exit, then grab it's return
     * value. */
    int status = 0;
    waitpid(vlc, &status, 0);
    printf("VLC exited with status %d\n", WEXITSTATUS(status));


```3) What is the best of the two following pieces of codes?

```
 if (kill(vlc, SIGTERM) < 0) {
        perror("kill with SIGTERM");
        if (kill(vlc, SIGKILL) < 0) {
            perror("kill with SIGKILL");
        }
    }

```or this

```
if (kill(vlc, SIGTERM) < 0) {
    if (errno == ESRCH) {
         printf("process does not exist (already exited?)\n");
    } else {
         perror("kill");
    }
}

// sleep or wait for a bit, then try again with SIGKILL.
```

---

