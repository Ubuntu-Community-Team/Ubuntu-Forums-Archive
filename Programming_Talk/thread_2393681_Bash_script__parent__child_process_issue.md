---
title: "Bash script : parent / child process issue ?"
date: 2018-06-06
forum: Programming Talk
---

### Post by mohicann on 2018-06-06
Hello there,

I managed to write a bash script that, among other functionalities, launches another sub-process which is not another bash script but a binary (which is supposed to be run only by bash). When I launch directly my "parent" script, everything works perfectly, subprocess included. But once it starts automatically through cron, the binary subprocess doesn't work anymore. 

My crontab command was the following, in order to check and restart only if necessary my script:

```
crontab -l | { cat; echo "*/1 * * * * /bin/bash pgrep -f ~/Documents/Linux/checker > /dev/null || ~/Documents/Linux/checker"; } | crontab -
```

Is there anything (or a lot of things) I've done incorrectly? Thanks in advance!

---

### Post by TheFu on 2018-06-06
~/ doesn't work in cron.   Most environment variables aren't set.

---

### Post by mohicann on 2018-06-06
Thank you for your reply. Actually, I tried to write and run some small test loop scripts with the same crontab command in order to figure out where the issue was coming from, and nonetheless it worked. But they didn't have child processes. That's why I was focusing on this possibility.

PS: I probably got your idea. I need to check a few more things indeed, for instance the relative paths in my "parent" script.

---

### Post by TheFu on 2018-06-06
Compare the output of 
```
env > /home/mohicann/env.interactive
```
to running it from a crontab
```
env > /home/mohicann/env.cron
```

You'll see what is and isn't set that way.

---

### Post by mohicann on 2018-06-06
Thank for you reply. There are exactly the same. I assume it doesn't come from relative and absolute paths?

---

### Post by papibe on 2018-06-06
Hi mohicann.

You don't need to use /bin/bash on your crontab line. This should work:
```
*/1 * * * * pgrep -f ~/Documents/Linux/ch...
```
~ works depending on the shell used by the distribution. crontab uses /bin/sh. In Ubuntu /bin/sh is a link to /bin/dash. dash expands the ~ to your home directory

Thus, in Ubuntu ~ works in crontab. However, if you want portability, use absolute paths instead.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by TheFu on 2018-06-06
> **mohicann said:**
> Thank for you reply. There are exactly the same. I assume it doesn't come from relative and absolute paths?

I suspect you aren't doing it correct then. Let me check mine.  Ok ... that ran.
```
$ wc -l  env*
  16 env.cron
  74 env.int
```

The interactive env is VERY DIFFERENT from the env under cron.
Oddly, HOME and PWD are set - those are both new to me in a crontab.  Very unexpected.  It wasn't that way 10 yrs ago.

```
SHELL=/bin/sh
PATH=/usr/bin:/bin
PWD=/home/thefu

```
But a bunch of other variables are missing and the PATH is certainly tiny under cron.  USER is not set, but LOGNAME is.  Interesting.

Much of my cron knowledge comes from UNIX systems, so some things are a little different.

---

### Post by mohicann on 2018-06-07
Thank you for your replies and information.

I've checked with this crontab command line:

```
crontab -l | { cat; echo "30 * * * * /home/mohicann/Documents/Linux/checker"; } | crontab -
```

It starts but my subprocess still doesn't work.

I've checked my script with bash -x and it runs perfectly, and when it is started manually, everything works fine. There really should be a trick somewhere between cron and bash or cron and my subprocess that I still don't get. Moreover, if I fill in the crontab command with my script command line (absolute path)) that starts my subprocess, it doenst' work either while it works perfectly from a bash console. It seems it can only work through my script alone or a bash console.

---

### Post by TheFu on 2018-06-07
Simplify and test.
What, exactly, is the line in the crontab?  I know what you think it is, but what is it really?
Which crontab, exactly, is being used?
What are the file permissions for the script?  
Does the script depend on any interactive environment variables? I bet it does.

---

### Post by mohicann on 2018-06-07
I've added absolute paths in my script and a chmod 777 to my subprocess (as my script was already).

I'm using my user crontab but I've noticed something: when my script is launched manually (double click), its parent is dolphin, and when it's launched by crontab, its parent is sh. My subprocess (when it works) always has my script as parent. However, when my subprocess is directly started from a console as a main process, it has bash as parent. Indeed, there could be something set that doesn't work, such as an absolute path of bash command inside my script, that was supposed to start my subprocess. Moreover, if I start my script from a bash console, its parent is still bash but the subprocess works.

PS: if I specify /bin/bash to run my subprocess in my script, it doesn't work either.

---

### Post by TheFu on 2018-06-07
Perhaps if I ask for information a different way?  Descriptions show what you think  is happening, not necessarily what actually is happening.

What do you think we need to see to help you?

---

### Post by mohicann on 2018-06-07
I don't know. I will try something else indeed: isolating a minimal script and post it with all command used on bash and cron. My script is probably too complex to explore line by line what could play up.

---

### Post by mohicann on 2018-06-07
Here is my crontab:

```
crontab -l | { cat; echo "*/1 * * * * pgrep -f test6 > /dev/null || ~/Documents/Linux/test6"; } | crontab -
```

which works partially. Started this way, only the "cp" command of the following script works, "bin1 test" doesn't start.

My test script is now this (for test purpose):

```
#!/bin/bash

# to check if script works
cp /etc/os-release /home/mohicann/os-release

# to start test
/home/mohicann/bin1 test >> ~/data.txt
```


- If "bin1 test" is launched from console alone, it works.

Parent is "bash".


-  If my script "test6" is launched from console, everything works.

"test6": parent is "bash".
"bin1 test": parent is "test6".


- If my script "test6" is launched from double-click, everything works as well.

"test6": parent is "dolphin".
"bin1 test": parent is "test6".


If all cases, everything works: os-release is copied and/or "bin1 test" sends its data to data.txt.

  When I shut down my script test6, bin1 is still running, but no longer provides data to data.txt. Moreover it's parent becomes systemd.

---

### Post by mohicann on 2018-06-07
PS: even with this crontab, it doesn't work:

```
crontab -l | { cat; echo "*/1 * * * * /home/user/bin1 test >> /home/user/data.txt"; } | crontab -
```

But if I remove "bin1 test" from my script, even this crontab works (it copies os-release each minute):

```
crontab -l | { cat; echo "*/1 * * * * ~/test6"; } | crontab -
```

---

### Post by mohicann on 2018-06-07
Even when correcting my script, it still doesn't work :

```
#!/bin/bash

# to check if script works
cp /etc/os-release /home/mohicann/os-release

# to start test
/home/mohicann/bin1 test >> /home/mohicann/data.txt
```

---

### Post by spjackson on 2018-06-07
Maybe bin1 is seg-faulting or something like that. Try:
```

#!/bin/bash

# to check if script works
cp /etc/os-release /home/mohicann/os-release

# to start test
**ulimit -c unlimited**
/home/mohicann/bin1 test >> /home/mohicann/data.txt
```
If it is seg-faulting you should get a core in your home directory, which you can then debug with gdb and get a backtrace.

---

### Post by papibe on 2018-06-07
It looks like 'bin1' might need environment vars to run. These are usually given by an interactive shell, or the desktop.

Try this:
```
#!/bin/bash

**source ~/.profile**

# to check if script works
cp /etc/os-release /home/mohicann/os-release

# to start test
/home/mohicann/bin1 test >> /home/mohicann/data.txt
```
This would force the execution of ~/.bashrc too.

If 'bin1' needs a graphical environment, you need an extra variable at the crontab level:
```
crontab -l | { cat; echo "*/1 * * * *  pgrep -f test6 > /dev/null || **env DISPLAY=:0** ~/Documents/Linux/test6"; } | crontab -
```
You may want to use DISPLAY=:0.0 if you have a multiple monitor setup.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by mohicann on 2018-06-07
Thank you very much for your replies.

> **spjackson said:**
> Maybe bin1 is seg-faulting or something like that. Try:
```
**ulimit -c unlimited**
```
If it is seg-faulting you should get a core in your home directory, which you can then debug with gdb and get a backtrace.

I keep this as I've already had a seg-faulting message on another setup, I may need it to solve that one day or another.


> **papibe said:**
> It looks like 'bin1' might need environment vars  to run. These are usually given by an interactive shell, or the desktop.

Try this:
```
#!/bin/bash

**source ~/.profile**

# to check if script works
cp /etc/os-release /home/mohicann/os-release

# to start test
/home/mohicann/bin1 test >> /home/mohicann/data.txt
```
This would force the execution of ~/.bashrc too.

It worked! Well done! I'll check everything to ensure there is nothing left, but at least the stubborn process eventually gave up... Now its starts and provides its data when launched from cron!

Thank you very much all for your help!

---

