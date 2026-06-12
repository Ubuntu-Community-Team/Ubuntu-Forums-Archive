---
title: "stopping a system() process in C"
date: 2010-07-17
forum: Programming Talk
---

### Post by J05HYYY on 2010-07-17
Hello, I am writing a C program and I need to know how to stop a system() process.

when I do:
```

system("play 1.wav &")

```
...sox plays the whole of 1.wav (unless I press control-c).

I want to be able to send a control-c message and stop the process from my code.

Any help, much appreciated.

---

### Post by Bachstelze on 2010-07-17
You can't do that because system() will block until the command has finished executing. Use fork().

---

### Post by J05HYYY on 2010-07-17
Could I get an example of this? Basically, I want to open the process, then close it again.

---

### Post by Bachstelze on 2010-07-17
Here's an example with an xterm:

```
#include <signal.h>
#include <stdio.h>
#include <unistd.h>

int main(void)
{
        int child_pid;
        printf("Starting xterm...\n");
        child_pid = fork();
        if(child_pid) {
                /* Parent */
                printf("Waiting 5 seconds before killing xterm...\n");
                sleep(5);
                kill(child_pid, 15); /* SIGTERM */
                printf("Exiting...\n");
        } else {
                /* Child */
                execve("/usr/X11/bin/xterm", NULL, NULL);
        }
        return 0;
}

```

I'll leave replacing the command and adding the argument as an exercise to the reader. ;)

---

### Post by J05HYYY on 2010-07-17
xterm did not open?

---

### Post by Bachstelze on 2010-07-17
Did you change the path? I did that on OS X, on Ubuntu it's /usr/bin/xterm.

---

### Post by Bachstelze on 2010-07-17
Hmm, that was a bad example, you need to set the DISPLAY environment variable for xterm to work.  You can replace it with any command.

---

### Post by J05HYYY on 2010-07-17
Now I get this:

```
Starting xterm...
Waiting 5 seconds before killing xterm...
(null) Xt error: Can't open display: 
(null):  DISPLAY is not set
Exiting...

```

---

### Post by soltanis on 2010-07-17
Yeah, you need to set the DISPLAY environment variable before running that program (it should be already set if you run it from an already-running xterm).

Also, I suggest you look into the **popen**(3) family of functions, they allow you to capture output from the process or direct input to it.

---

### Post by trent.josephsen on 2010-07-17
> **soltanis said:**
> Yeah, you need to set the DISPLAY environment variable before running that program (it should be already set if you run it from an already-running xterm).

Also, I suggest you look into the **popen**(3) family of functions, they allow you to capture output from the process or direct input to it.
I don't think that will help, because what the OP needs is a way to send a signal to the process, not feed it input.  Fortunately, kill(3) is available and in <signal.h>

---

### Post by J05HYYY on 2010-07-17
> **Bachstelze said:**
> Hmm, that was a bad example, you need to set the DISPLAY environment variable for xterm to work.  You can replace it with any command.

I tried replacing it with "play 1.wav" instead but it didn't work either... still no luck with this.

---

### Post by dwhitney67 on 2010-07-17
> **J05HYYY said:**
> Could I get an example of this? Basically, I want to open the process, then close it again.

Why you have elected to use C as opposed to bash is beyond me.

Anyhow, in C, as Bachstelze indicated, use fork() to spawn the child process.  Then use kill() to terminate the child whenever you desire (perhaps using ctrl-c).  Killing the child will also in turn, kill its child-process(es).

This is a simple (yet incomplete) example, which may or may not work to meet your needs:
```

#include <signal.h>
#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>

int killChild = 0;

void sigHandler(int signo)
{
   if (signo == SIGINT)
   {
      killChild = 1;
   }
}

int main(void)
{
   pid_t child = fork();

   if (child == 0)
   {
      system("/usr/bin/xeyes");
   }
   else
   {
      signal(SIGINT, sigHandler);

      while (1)
      {
         if (killChild == 1)
         {
            printf("\nKilling child...\n");
            kill(child, SIGTERM);
            break;
         }
         else
         {
            sleep(1);
         }
      }
   }

   return 0;
}

```

---

### Post by J05HYYY on 2010-07-17
It opened xeyes successfully but didn't close it again afterwards. This is what I need.

---

### Post by StephenF on 2010-07-17
> **J05HYYY said:**
> It opened xeyes successfully but didn't close it again afterwards. This is what I need.
Works fine for me.

Does the terminal you launched it from have keyboard focus when doing the Ctrl+C?

---

### Post by J05HYYY on 2010-07-17
Yes, when I press control-c it exits with the message "Killing child..." but the idea is that I would kill the child (or the equivalent of control-c) using some code.

---

### Post by StephenF on 2010-07-18
> **J05HYYY said:**
> I want to be able to send a control-c message and stop the process from my code.
So what you really want is for bash to kill the background process when you press Ctrl+C but to still have an interactive console?

This creates ambiguity. A Ctrl+C key press needs to affect only foreground process or by design necessity it would have to go to all processes launched from the terminal as to do otherwise would be confusing and in this form would make Ctrl+C into a very blunt instrument.

This line of reasoning leads me to believe there is a gap in your knowledge regarding Bash job control so here is a link for you.

[http://web.mit.edu/gnu/doc/html/features_5.html](http://web.mit.edu/gnu/doc/html/features_5.html)

Examples:
```

stephen@tmb ~ $ xeyes &
[1] 5950
stephen@tmb ~ $ jobs
[1]+  Running                 xeyes &
stephen@tmb ~ $ kill %1

```
```

stephen@tmb ~ $ xeyes &
[1] 5972
stephen@tmb ~ $ fg
xeyes
^C
stephen@tmb ~ $ 

```

---

### Post by Bachstelze on 2010-07-18
> **J05HYYY said:**
> I tried replacing it with "play 1.wav" instead but it didn't work either... still no luck with this.

The first argument to execve() is the command **only** (absolute path). The command arguments are given in an array as the second argument to execve(), which will become the argv of the new process (so the first element of the array must be the name of the command):

```
#include <signal.h>
#include <stdio.h>
#include <unistd.h>

int main(void)
{
        int child_pid;
        printf("Starting play...\n");
        child_pid = fork();
        if(child_pid) {
                /* Parent */
                printf("Waiting 5 seconds before killing play...\n");
                sleep(5);
                kill(child_pid, 15); /* SIGTERM */
                printf("Exiting...\n");
        } else {
                /* Child */
                char* args[] = {"play", "/path/to/1.wav", NULL};
                execve("/usr/bin/play", args, NULL);
        }
        return 0;
}
```

Of course, you can replace the code in the Parent block with whatever you want the parent to do after the child is fork()'edn just use kill() when you want to kill the child.  Also, you can also use system() instead of execve() in the child, but it's a bit more messy since you will fork a third process, that will actually run the command.

Worked for me. The commnd I tested is  [font=monospace]/usr/local/bin/idle3 /Users/firas/foo.py[/font] because I don't have play, but it should also work for you.

---

