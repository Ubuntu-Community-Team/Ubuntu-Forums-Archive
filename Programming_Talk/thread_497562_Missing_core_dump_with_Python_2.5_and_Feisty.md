---
title: "Missing core dump with Python 2.5 and Feisty"
date: 2007-07-10
forum: Programming Talk
---

### Post by abierbaum on 2007-07-10
I recently switched over to Ubuntu from Fedora and everything has been going very well except for a few small development related issues where I haven't quite found the Ubuntu way yet.  The current issue that is causing me problems is that I can't seem to get a core dump from a python extension model that I am currently debugging.

When I run python, it loads the extension module successfully, and then somewhere internal to the code there is a seg fault.  I am 99% sure the seg fault is caused by some of my code in the extension module so now I would like to debug the problem.  The application exits with "Segmentation fault (core dumped)".  My core size limit is set to "unlimited" so I would expect a "core" file in the local directory where I executed the command.  Unfortunately no core file is showing up.

To verify that I can create core files, I created a simple C++ application that seg faults and that works as expected.  It seems that there is something about python that is keeping this from working.  I know it works with Fedora because I have used core dumps to debug this module many times in the past.

Is there something I am missing about how either python or Ubuntu is working that may be preventing the system from writing the core file?

Additional details:
- python 2.5.1 (r251:54863)
- Ubuntu 7.04
- kernel 2.6.20-16-generic SMP
- shell: tcsh
- limits: all limits set to unlimited
- g++ 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

Thanks,
Allen

---

### Post by Mr. C. on 2007-07-10
Perhaps python is changing its working directory while loading the module.  Search your system with 

```
find / -name core"*" -ls
```

MrC

---

### Post by abierbaum on 2007-07-11
> **Mr. C. said:**
> Perhaps python is changing its working directory while loading the module.  Search your system with 

```
find / -name core"*" -ls
```

MrC

No such luck.  I tried this when I first had the problem and the only core files on the system are in the linux-headers, the /dev directory, and one header in boost.  :(

Any other ideas?

-Allen

---

### Post by Mr. C. on 2007-07-11
Try starting python with the debugger.

```
gdb /path/to/python
```

and then running :

```
run
```

and see where it crashes.

MrC

---

### Post by abierbaum on 2007-07-13
> **Mr. C. said:**
> Try starting python with the debugger.

```
gdb /path/to/python
```

and then running :

```
run
```

and see where it crashes.

MrC

Thanks for the additional idea.  

This doesn't give me any problems.  But it doesn't provide a good solution because what I really want to track down is "random" crashes in a production application.  In other words running it in a debugger all the time isn't a great option.  I want a way to analyze a crash after the fact.

For now I will just use the debugger, but if anyone has any other ideas please let me know.

-Allen

---

### Post by Mr. C. on 2007-07-13
I see.

Try changing the core directory, as discussed here:

[http://aplawrence.com/Linux/limit_core_files.html](http://aplawrence.com/Linux/limit_core_files.html)

The typical ways of preventing core are via ulimit, an unwritable core file, or a core directory.  If you're sure the later are not the problem, i'm out of answers.

MrC

---

### Post by abierbaum on 2007-07-17
I tracked down the problem.  Based on Mr C's last response I looked at /proc/sys/kernel/core_pattern and found:

```
cat /proc/sys/kernel/core_pattern 
|/usr/share/apport/apport
```

It seems that the apport package was causing problems.  As soon as I removed the apport package, things are working as I would expect.

Thanks for all the help.

-Allen

---

### Post by Mr. C. on 2007-07-17
Ah!  I had not heard of this software.  Thanks for the update.

MrC

---

### Post by kazik on 2007-07-24
Indeed, this is a "feature" of Apport (automated crash reporting). Read more about this "patch" at:

[Crash interception]("https://wiki.ubuntu.com/Apport#head-07a01cd17513789f2389e89c33413100789448ef")

---

