---
title: "How do you NOT take over the console?"
date: 2008-08-19
forum: Programming Talk
---

### Post by Kenchu on 2008-08-19
Just curious. Usually when you start a program in the console, that program will sort of "take over" the console and print its output (if it has any). However some programs seem to have the ability to let the user go back to typing commands, though the program is still running. An example of this is lampp. When you start lampp, it will indeed print some output. But then the user will come back to ":~$ " and can type new commands, though lampp is still running?

I've seen this in windows also. The majority of graphical apps don't even take over the console at all. How does that work?

---

### Post by LaRoza on 2008-08-19
Try this:

```

~$ firefox &

```

---

### Post by lordhaworth on 2008-08-19
If 

```
~$ firefox &
```

Doesnt work, try

```
]~$ ! firefox &
```

If i remember correctly that works - let me know if I'm wrong, I cant test it at the mo

---

### Post by lordhaworth on 2008-08-19
Sorry, that should be

```
~$ ! firefox &
```

without the extra "]" parenthesis

---

### Post by Kadrus on 2008-08-19
It doesn't work with **!firefox &**..well at least in my terminal.
and you can always edit your post.

---

### Post by ByteJuggler on 2008-08-19
To add:

When you've started an application in the foreground, then pressing ctrl-z will pause it and return you to the shell.  Then, the command "fg" will restart it again, bringing it to the "ForeGround", and the command "bg" will put it in the BackGround, as though you started it with an ampersand (&) on the end.  There's several other job control commands but those are the main ones to remember. :)

---

### Post by dwhitney67 on 2008-08-19
Just run your program in the "background", as LaRoza pointed out, using the &.  For instance from your terminal prompt (where the $ is your prompt):
```
$ app &
```
If you happen to run a program from your terminal and forget to run it in the background, then follow this sequence to place it in the background:
```
$ app
ctrl-z
$ bg
```

---

### Post by lordhaworth on 2008-08-19
It may be with a space between the ! and the program, I've used it before when running IRAF but that may have been in a different shell

---

### Post by finer recliner on 2008-08-19
> **lordhaworth said:**
> 

```
~$ ! firefox &
```



in bash, the exclamation point (!) just means to use the most recent command (in your history) that starts with "firefox &".

i dont know if this works the same way in dash (the default shell that ubuntu uses), but if it does, then i dont think it will help here :-/

---

### Post by lordhaworth on 2008-08-19
Ahhh ok, Im sure it must be a variation for another shell then... but which one lol

I might have to have a delve into my old work and see what I can find

---

### Post by Zugzwang on 2008-08-19
Could it be that the OP wants to know how to modify his/her program in order to "give back the console" at some point in his program? Like, for example:

[PHP]
...

int main() {
   initServer(); // User has to wait until server has been started
   giveBackConsole(); // The program switches to background mode here
   while (!gotQuitSignal) doServing();
   return 0;
}
[/PHP]

How would he/she do this let's say in C or Python?

---

### Post by finer recliner on 2008-08-19
> **Zugzwang said:**
> Could it be that the OP wants to know how to modify his/her program in order to "give back the console" at some point in his program? Like, for example:

[PHP]
...

int main() {
   initServer(); // User has to wait until server has been started
   giveBackConsole(); // The program switches to background mode here
   while (!gotQuitSignal) doServing();
   return 0;
}
[/PHP]

How would he/she do this let's say in C or Python?


this functionality is built into the shell already, by using ctrl+z to put the current process in the background and 'fg' to bring it back to the foreground as dwhitney67 stated earlier.

---

### Post by Zugzwang on 2008-08-19
> **finer recliner said:**
> this functionality is built into the shell already, by using ctrl+z to put the current process in the background and 'fg' to bring it back to the foreground as dwhitney67 stated earlier.

Well, this is how the *user* can do this. But how would the *program* make itself going into background mode at some point (not necessarily at the beginning)?

---

### Post by finer recliner on 2008-08-19
> **Zugzwang said:**
> Well, this is how the *user* can do this. But how would the *program* make itself going into background mode at some point (not necessarily at the beginning)?

this doesnt make sense. the only thing you gain from putting a process in the background is freeing up the shell so you (the user) can execute more processes. how is your process going to know when the user needs the terminal back? thats for the user to decide, not the process, hence why you can use ctrl+z and 'fg' at your own convenience.

---

### Post by ByteJuggler on 2008-08-19
> **Zugzwang said:**
> Well, this is how the *user* can do this. But how would the *program* make itself going into background mode at some point (not necessarily at the beginning)?

The program can't, it's the shell/OS responsibility to manage to process state (foreground/background.)

---

### Post by Zugzwang on 2008-08-19
> **ByteJuggler said:**
> The program can't, it's the shell/OS responsibility to manage to process state (foreground/background.)

Why not? Btw, I found it out. Example:
[PHP]
#include <sys/types.h>
#include <unistd.h>
#include <iostream>

int main() {
    std::cout << "Process init" << std::endl;
    sleep(2);
    int id = fork(); // <----------- [ How it works. ]
    if (id!=0) return 0; // <------- [ How it works. ]
    for (int i=0;i<10;i++) {
        sleep(2);    
        std::cout << "Doing work..." << std::endl;
    }
    std::cout << "Done!" << std::endl;
}
[/PHP]
Certainly the program shouldn't pollute the terminal with its output if run that way, but it *can* be done. More details: [http://http://forums.devshed.com/c-programming-42/fork-and-send-child-to-background-58441.html]("http://http://forums.devshed.com/c-programming-42/fork-and-send-child-to-background-58441.html")

EDIT: And looking at the original post, one might get the impression that this is actually what the OP wanted.

---

### Post by Kenchu on 2008-08-19
> **Zugzwang said:**
> Why not? Btw, I found it out. Example:
[PHP]
#include <sys/types.h>
#include <unistd.h>
#include <iostream>

int main() {
    std::cout << "Process init" << std::endl;
    sleep(2);
    int id = fork(); // <----------- [ How it works. ]
    if (id!=0) return 0; // <------- [ How it works. ]
    for (int i=0;i<10;i++) {
        sleep(2);    
        std::cout << "Doing work..." << std::endl;
    }
    std::cout << "Done!" << std::endl;
}
[/PHP]
Certainly the program shouldn't pollute the terminal with its output if run that way, but it *can* be done. More details: [http://http://forums.devshed.com/c-programming-42/fork-and-send-child-to-background-58441.html]("http://http://forums.devshed.com/c-programming-42/fork-and-send-child-to-background-58441.html")

EDIT: And looking at the original post, one might get the impression that this is actually what the OP wanted.


Yes this was what I was wondering about. Not how the USER does it, but rather a program itself. I know that you in visual studio can choose whether your app should be a console app or a frame app. If console (in windows), itll "take over" the console when it runs. If frame, youll get back to the console. And I noticed lampp seems to work in the same manner in linux.

---

### Post by dwhitney67 on 2008-08-19
> **Zugzwang said:**
> Why not? Btw, I found it out. Example:
[PHP]
#include <sys/types.h>
#include <unistd.h>
#include <iostream>

int main() {
    std::cout << "Process init" << std::endl;
    sleep(2);
    int id = fork(); // <----------- [ How it works. ]
    if (id!=0) return 0; // <------- [ How it works. ]
    for (int i=0;i<10;i++) {
        sleep(2);    
        std::cout << "Doing work..." << std::endl;
    }
    std::cout << "Done!" << std::endl;
}
[/PHP]
Certainly the program shouldn't pollute the terminal with its output if run that way, but it *can* be done. More details: [http://http://forums.devshed.com/c-programming-42/fork-and-send-child-to-background-58441.html]("http://http://forums.devshed.com/c-programming-42/fork-and-send-child-to-background-58441.html")

EDIT: And looking at the original post, one might get the impression that this is actually what the OP wanted.
Although this solution seems nifty, it does not work the same as placing an application in the background.  Sure the user will be able to regain control of the terminal used to launch the application, however "full" control will not be achieved.  For instance, if the user were to end the shell session on the terminal, then the application will also terminate.

As I mentioned before, the best way to place an application in the background it to run it with the with the '&', or by first suspending the application (using ctrl-z) and then issuing a 'bg' command to place it in the background.

---

### Post by ByteJuggler on 2008-08-19
> **Zugzwang said:**
> Why not? Btw, I found it out. 

Well yes you can fork your process into 2 of course as you've shown and then terminate the primary to achieve the effect you're after.  (But of course that's not exactly the same as "giving back the console" (as you put it) **in the same process** which is what you seemed to be asking in your original pseudocode, obviously you're more interested in achieving the illusion in whatever way is possible. :) )

---

### Post by kpatz on 2008-08-19
Like others have posted, "not taking over the console" simply means the shell isn't waiting for your program to finish.  The & is one way to do it, but if you want your program to go "background" automatically, the fork() and exit trick works.

If you want to go into "100% daemon mode", where the process becomes completely disassociated with the terminal, use this code:

[php]
#include <sys/ioctl.h>
#include <unistd.h>

...
int pid;
if ((pid = fork()) == 0) // is the child
{
  setpgrp();  // new process group
  fclose(stdin);  // Close stdin, stdout, stderr
  fclose(stdout);
  fclose(stderr);

  // Make child process have no controlling terminal
  // Now there will be no tty associated with the process
  // when you view it with ps
  int fd = open("/dev/tty", O_RDWR);
  if (fd >= 0) {
    ioctl(fd, TIOCNOTTY, 0);
    close(fd);
  }
}
else
{
   cout << "I'm the parent, the child is detached and has PID " << pid << ", I'm exiting now" << endl;
   exit(0);
}
[/php]

---

### Post by imdano on 2008-08-19
Here's how you would become a daemon in Python[php]# Fork the first time to disconnect from the parent terminal and
    # exit the parent process.
    try:
        pid = os.fork()
        if pid > 0:
            sys.exit(0)
    except OSError, e:
        print >> sys.stderr, "Fork #1 failed: %d (%s)" % (e.errno, e.strerror)
        sys.exit(1)

    # Decouple from parent environment to stop us from being a zombie.
    os.setsid()
    os.umask(0)

    # Fork the second time to prevent us from opening a file that will
    # become our controlling terminal.
    try:
        pid = os.fork()
        if pid > 0:
            sys.exit(0)
    except OSError, e:
        print >> sys.stderr, "Fork #2 failed: %d (%s)" % (e.errno, e.strerror)
        sys.exit(1)[/php]

---

### Post by mssever on 2008-08-19
> **finer recliner said:**
> i dont know if this works the same way in dash (the default shell that ubuntu uses), but if it does, then i dont think it will help here :-/Um, Ubuntu's default shell is bash, not dash. dash is merely what you get when you run /bin/sh.

> **Zugzwang said:**
> Well, this is how the *user* can do this. But how would the *program* make itself going into background mode at some point (not necessarily at the beginning)?A program that detaches from the controlling terminal is called a daemon. I don't know if Python has a simple way to safely create a daemon (there's a little more to it then simply calling [FONT=Courier New]fork and exit[/FONT]). In Ruby, you can do something like (assuming you've installed libdaemons-ruby): ```
require 'daemonize'
Daemonize::daemonize
```and presto, you have a daemon. Perhaps Python has something similar.

---

### Post by imdano on 2008-08-19
> **mssever said:**
> In Ruby, you can do something like (assuming you've installed libdaemons-ruby): ```
require 'daemonize'
Daemonize::daemonize
```and presto, you have a daemon. Perhaps Python has something similar.It doesn't.  There are some third-party modules written that do it, though.  [Here is a well-documented example](http://code.activestate.com/recipes/278731/).  I'm not exactly sure why Python doesn't include a way to do it, I vaguely remember googling it and seeing a comment from Guido about it being best done externally.

The only step missing from my example above is redirecting file descriptors, I pulled the snippet from a project I work on and forgot that the file descriptors get redirected in a different method.

---

