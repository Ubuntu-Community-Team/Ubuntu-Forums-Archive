---
title: "Finding who (what) killed my process."
date: 2009-11-18
forum: Programming Talk
---

### Post by Gary13579 on 2009-11-18
I have a rather simple script that restarts a process everytime it exits, because the process is designed to exit and restart using the shell script.


```
#!/bin/bash
while true
do
        echo "Starting."
        ./program params
done
```

Typically, when it crashes, it exits with this:

```
terminate called after throwing an instance of 'exception'
./program.sh: line 6: 16453 Aborted                 ./program params
```

Which is completely expected, the program is throwing an exception and my script restarts it. Now, I managed to catch something weird...

```

// Program is generating output like normal, nothing weird.
./program.sh: line 6: 16445 Killed                  ./program params

```

Killed? How? Why? To be specific, bash is telling me the program executed by program.sh is being killed. I know the kernel will kill a program which is being memory intensive, but this is a simple 200kb program which is not memory intensive in any way, and even restarts every ~hour to eliminate any possible memleaks.

I've tried looking through the log files that should contain info, but nothings there.

```
gary@snuggles:/var/log$ sudo grep 16445 *
[sudo] password for gary: 
gary@snuggles:/var/log$ 

```

No one else has access to this PC, either directly or remotely. Any ideas on how to track down why/how it was killed?

---

### Post by Gary13579 on 2009-11-18
Bump!

---

### Post by lensman3 on 2009-11-20
My guess is the "./programs params" is crashing or returning with the wrong value and shell script isn't catching the return code and handling it correctly.  According to the bash "man" page ./programs should/must return with an exit status of zero for success.  You might print the exit status of ./programs using "?".

You might try running ./programs using the full path to the program.  Also try running the script using:

sh -xv "name of the script"

The -xv expand  what the shell reads and then executes.  That might tell  you which statement is actually failing.


Hope this might help.

---

### Post by mamthor on 2010-03-12
I am having a somewhat similar problem, so I'll post here instead of starting a new thread.  I'm running an analysis program multiple times in succession.  There is no problem with going over memory.  

I find if I don't reboot the machine for a couple days then any new instances of the program don't even try to start they just immediately return 

Killed

Once the problem starts it will continue until I reboot, then the program will run fine.

I also checked in /var/log using 

```
grep "killed" /var/log/*
```

but this didn't find the killings I was looking for.  Any ideas?

I'm on Jaunty Jacalope (9.04) if that helps.

---

### Post by Agent ME on 2010-03-12
It seems in Ubuntu, when memory is low, a random/arbitrary process is killed - often not the one taking the most memory. Are you running a program that's taking up too much memory?

---

### Post by lisati on 2010-03-12
> **Gary13579 said:**
> I have a rather simple script that restarts a process everytime it exits, because the process is designed to exit and restart using the shell script.


```
#!/bin/bash
while true
do
        echo "Starting."
        ./program params
done
```

Typically, when it crashes, it exits with this:

```
terminate called after throwing an instance of 'exception'
./program.sh: line 6: 16453 Aborted                 ./program params
```

Which is completely expected, the program is throwing an exception and my script restarts it. Now, I managed to catch something weird...

```

// Program is generating output like normal, nothing weird.
./program.sh: line 6: 16445 Killed                  ./program params

```

Killed? How? Why? To be specific, bash is telling me the program executed by program.sh is being killed. I know the kernel will kill a program which is being memory intensive, but this is a simple 200kb program which is not memory intensive in any way, and even restarts every ~hour to eliminate any possible memleaks.

I've tried looking through the log files that should contain info, but nothings there.

```
gary@snuggles:/var/log$ sudo grep 16445 *
[sudo] password for gary: 
gary@snuggles:/var/log$ 

```

No one else has access to this PC, either directly or remotely. Any ideas on how to track down why/how it was killed?

Perhaps I'm missing something here: what's the "while true" bit for? My instincts are telling me that you have the potential for multiple copies of the program starting.

---

### Post by Agent ME on 2010-03-12
"while true" means that it repeats the next block forever.

I just thought of a possible problem - what if ./program crashed immediately, and did so for at least its next several thousand runs? The script would quickly tie up a lot of processor usage relaunching ./program so much. A delay would help a bit in the script:
```
#!/bin/bash
while true
do
        echo "Starting."
        ./program params
        sleep 10
done
```

However, if you're trying to run a program as a system service, and it's not just a one-off thing you want to run constantly for a few times, you should set it up as a service properly with upstart. Here's a helpful link: [http://dustin.github.com/2010/02/28/running-processes.html](http://dustin.github.com/2010/02/28/running-processes.html)

---

### Post by cariboo on 2010-03-13
Not a security question. Moved to Programming talk.

---

### Post by soltanis on 2010-03-13
Have you checked memory usage using top or something similar to verify that it is not leaking memory?

Also, if your program forks (I don't know if it does, I need to take a closer look) you should be aware that even if it exits its resources might not be collected (it will be a zombie until the parent does wait()) which also might be a cause.

---

### Post by mamthor on 2010-03-13
Of course I cannot speak to Gary13579's original issue, but my particular case has nothing to do with memory.  The issue does not occur during a period of high memory usage.  I do regularly keep tabs on my resources using top.  It is not a memory leak, because the process is not being killed while it is actually running, but after one instance has completed and before the next one is allowed to even start (also there is no forking).

I might also comment that for this reason I rather object to this thread being moved to programming talk, since it has little to do with the program and everything to do with the fact that Ubuntu is killing new instances without letting them start.  The only thing I can think of is that there is some program policeman sitting somewhere paying attention to how many times a program is executed and if it gets executed too many times then it is considered a possible nuisance and killed.  This is just my naive theory.  If anyone can credibly dismiss it, that would be some progress.  For now I'll just be rebooting when it happens, but it's very strange for programs to be killed with no log entry or anything and no explanation to be found.  If rebooting didn't fix it, then what would I do?  Since this code is integral to my work I'd have to install another Linux distro just to run it, ouch.

---

### Post by dwhitney67 on 2010-03-13
> **mamthor said:**
> 
I might also comment that for this reason I rather object to this thread being moved to programming talk, since it has little to do with the program and everything to do with the fact that Ubuntu is killing new instances without letting them start.  The only thing I can think of is that there is some program policeman sitting somewhere paying attention to how many times a program is executed and if it gets executed too many times then it is considered a possible nuisance and killed.  This is just my naive theory.  If anyone can credibly dismiss it, that would be some progress.  For now I'll just be rebooting when it happens, but it's very strange for programs to be killed with no log entry or anything and no explanation to be found.  If rebooting didn't fix it, then what would I do?  Since this code is integral to my work I'd have to install another Linux distro just to run it, ouch.

I enjoyed your assumptions; they are quite entertaining.

Are you you stating that if a compiled/linked C program, which is no more than the following, would not be executed after N tries???

Let's see...
```

#include <stdio.h>

int main(void)
{
   printf("I'm running.\n");
   return 0;
}

```
To compile:
```

gcc fun.c

```

Then to execute indefinitely:
```

#!/bin/bash

while [ true ]
do
   ./a.out
done

```

---

### Post by mamthor on 2010-03-15
I suppose I deserved a good swat for my silliness.  I'm just frustrated.  It seems that, as a matter of principle, automatic killing should at least produce a log message somewhere.  I don't suppose it would help to say that the code is actually fortran 77.  Certainly it's unlikely to help my reputation in a programming forum ;)  I guess this will just be one of those mysteries that goes away inexplicably at some point.

---

