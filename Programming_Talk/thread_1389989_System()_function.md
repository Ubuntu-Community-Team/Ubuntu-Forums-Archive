---
title: "System() function"
date: 2010-01-25
forum: Programming Talk
---

### Post by erotavlas on 2010-01-25
Hi,

What type of code/command can substitute the following system call?


```
system("command... &");
```

Thank you very much

---

### Post by dwhitney67 on 2010-01-25
Look at the man-page for the execve() C library function.  On my Ubuntu 9.10 system, it includes a code example.

---

### Post by djurny on 2010-01-25
do not overlook the ampersand '&'.. :)
i think (s)he is looking for some kind of fork()-exec() solution.. that's the same as how bash or 'system("ls -laR &")' works.. fork the current process and execute some other stuff on the child (forked) copy of yourself..

[http://linux.die.net/man/2/fork](http://linux.die.net/man/2/fork)
[http://linux.die.net/man/2/execve](http://linux.die.net/man/2/execve)

[http://www.yolinux.com/TUTORIALS/ForkExecProcesses.html](http://www.yolinux.com/TUTORIALS/ForkExecProcesses.html)

---

### Post by Garratt on 2010-01-25
> What type of code/command can substitute the following system call?

I suggest don't do it, system commands are slow and create huge security gaps in your code. If your doing something that inherently talks to the system anyway such as a text editor or the like then it's plausable but otherwise i'd stay clear of them. Especially on windows. system("pause"); and system("clr"); is abused sooooo much, when you can achieve better results by using input stream or placing input stream in destructor.

---

### Post by dwhitney67 on 2010-01-25
> **djurny said:**
> do not overlook the ampersand '&'.. :)
i think (s)he is looking for some kind of fork()-exec() solution.. that's the same as how bash or 'system("ls -laR &")' works.. fork the current process and execute some other stuff on the child (forked) copy of yourself..

[http://linux.die.net/man/2/fork](http://linux.die.net/man/2/fork)
[http://linux.die.net/man/2/execve](http://linux.die.net/man/2/execve)

[http://www.yolinux.com/TUTORIALS/ForkExecProcesses.html](http://www.yolinux.com/TUTORIALS/ForkExecProcesses.html)

I believe the use of the '&' (ampersand) in a system() call is superfluous.  In other words, it doesn't buy anything to use it.

As for the system() implementation, I believe it uses execve(), exec(), or perhaps fork().

---

### Post by n00bi3 on 2010-01-25
I am using system() as well but I have a tiny problem..

when I do system("cd ..") it does not change the directory.

but when I type system("ls /root") it does its job perfectly so it is not about the blank character there.

I couldn't figure out the problem, any ideas ?

---

### Post by djurny on 2010-01-25
> **dwhitney67 said:**
> I believe the use of the '&' (ampersand) in a system() call is superfluous.  In other words, it doesn't buy anything to use it.

As for the system() implementation, I believe it uses execve(), exec(), or perhaps fork().

i'm pretty sure system() is implemented as a synchronous system call.. if system() is currently implemented using fork() it will be waiting on the child process before returning to its caller..

note: [http://linux.die.net/man/3/system](http://linux.die.net/man/3/system)

if you want the shell-like '&' functionality, you're stuck with fork() - exec() :)

did not use/test this myself, but;
use execl() if you want environment changes made by the system() call apparent in your own environment (like PWD/PATH/..etc)

---

### Post by djurny on 2010-01-25
> **n00bi3 said:**
> I am using system() as well but I have a tiny problem..

when I do system("cd ..") it does not change the directory.

but when I type system("ls /root") it does its job perfectly so it is not about the blank character there.

I couldn't figure out the problem, any ideas ?

use
```
chdir("..");
```
instead.. 

the ```
system("cd ..");
``` will just change the directory of the process started by 'system()'..

---

### Post by stim on 2010-01-25
The proper way to execute platform commands is by using system calls.
[http://en.wikipedia.org/wiki/System_call](http://en.wikipedia.org/wiki/System_call)

you should *never* use the system(), function!

---

### Post by Garratt on 2010-01-25
> **stim said:**
> The proper way to execute platform commands is by using system calls.
[http://en.wikipedia.org/wiki/System_call](http://en.wikipedia.org/wiki/System_call)

you should *never* use the system(), function!

damn straight, why do people always ignore this important FACT!
the amount of windows programmers I see using it drives me crazy. apart from making your exec EXTREMELY SLOW, it opens up your code to security issues. system commands should never ever ever make their way into release code EVER!

Unless for the above mentioned reasons ( paint apps etc... )

and people should also never clear the console (system("clr");).... if you want console manipulation there's a beautiful library called ncurses.(pdcurses on win32) Otherwise should never assume your code is going to be used as a stand alone product with no input output redirections !

---

### Post by djurny on 2010-01-25
> **Garratt said:**
> damn straight, why do people always ignore this important FACT!
the amount of windows programmers I see using it drives me crazy. apart from making your exec EXTREMELY SLOW, it opens up your code to security issues. system commands should never ever ever make their way into release code EVER!

Unless for the above mentioned reasons ( paint apps etc... )

and people should also never clear the console (system("clr");).... if you want console manipulation there's a beautiful library called ncurses.(pdcurses on win32) Otherwise should never assume your code is going to be used as a stand alone product with no input output redirections !

as much as i agree with the both of you, sometimes there is just no other (easy) way than to use the system() call..

to call 'synclient' from a c-app, for whatever reason, i am surely not going to copy/modify the synclient source code if its just an app i want to have handy very quickly..

another example, if i want to perform some function on another host with ssh from a c-app, without the hassle of setting up your own ports/sockets and stuff, a 'system("ssh somehost \"sensors\"");' will do just what i want, in less than a tenth of the time..

please note that i am not a big fan of putting a bunch of lines of bad code/mixed scripting together and rolling it out as it being an application, but sometimes you (also depending on the target audience) just cannot do it the correct way..
also, the examples like 'system("cd ..");' or 'system("ls -latr|sort -u")' are perfect candidates for using the appropriate (combinations of) (lib/)syscalls instead..

---

### Post by nvteighen on 2010-01-25
The system() function is there for cases in which you:
1. Don't have an API to interface with (rarely the case in GNU/Linux) and
2. Don't have a POSIX pipe to pipe from/to (rarely the case in GNU/Linux).

In other words, it's the way to execute something without being able to communicate with it, delegating all powers during its execution... therefore, something to be used as last resort and, of course, never letting user input determine what the system() call will do.

---

