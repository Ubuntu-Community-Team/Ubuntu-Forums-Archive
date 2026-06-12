---
title: "get process ID in C"
date: 2010-03-14
forum: Programming Talk
---

### Post by bourne-sc2 on 2010-03-14
Hey,

I have a program that I want running in the background.  What I want it to do, amongst other things, is log the process ID of the current foreground process.

I have seen the function tcgetpgrp(int fd); but I do not know how to properly use this given my problem.  For instance, fd should be the terminal associated with the calling process.  I do not know how to easily get this, nor do I know if this will get me what I want.  Most of the processes I see when I run 'ps -e' in the terminal have '?' under TTY, which leads me to believe this might be in vain?

Anyone have any idea how to go about getting the process ID of the current foreground process/process group from a background process?  And if so, will this let a C/C++ background program log when I switch from, say, Firefox to a text editor?

Thanks in advance

P.S. running Ubuntu Linux 9.04 if that makes a difference

---

### Post by dwhitney67 on 2010-03-14
Will the following meet your needs?
```

#include <unistd.h>
#include <stdio.h>

int main(void)
{
   printf("My process ID : %d\n", getpid());
   printf("My parent's ID: %d\n", getppid());

   return 0;
}

```

---

### Post by soltanis on 2010-03-15
What are you going to do with this program?

First of all, in Linux there is no such thing as the "foreground" process in the general case; as it is a multi-user, multi-process OS, what process is in the foreground really depends on what foreground you're talking about.

I don't think dwhitney's code will help here since that only tells you about your own PID and the parent process PID which would be the shell as opposed to the current foreground process in the shell.

If you're talking about the currently active window as in your example, then this would have to deal with the current window manager to find out the currently active window.

If you're talking about just the program that is using the most CPU time/memory/other resource then checking out the manpage for top(1) might point you in the right direction.

---

### Post by bourne-sc2 on 2010-03-15
Thanks for the replies!

I am doing research about malware for a professor and need to modify a keylogger to get the current active window/process that is using the input.  From there we can determine if input we logged was actually inputted tithe process recorded or not.  From what I understand it will be enough to get the current active window process id. For instance, if some one is typing in firefox, I want to know the pid along withthe input.  If they switch to gedit then I again want to log the pid of gedit  and input they type.

Let me know if I need to clarify. I am exhausted and typing on my iPod touch so it might come out weird

---

