---
title: "Kill several jobs in one command?"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by ferhtgoldaraz on 2012-04-07
Hi to every one there.

I'm trying to learn some GNU/Linux basic level command line stuff, and I've found myself used to Ctrol+Z a lot to exit man pages an less reads, instead of pressing q (trying to stop doing it... habits...).

That leaves some jobs stopped in the background that I see with the command "jobs", and I can terminate those jobs with "kill %N", N being the job number shown in "jobs" for a job.

**Researching how to kill several jobs in one command** (it got tedious), I found that I should be able to do:


```

~$: kill `jobs -p`

```  NOTE: I haven't reached explanation of this syntax

or at least:

```

~$: kill $(jobs -p)

```  NOTE: I haven't reached explanation of this syntax


**However**, it returns (for each job's process ID, I guess):


```

bash: kill: (17893) - No such process
bash: kill: (17897) - No such process
.
. etc
.

```


And if I look for the process, it doesn't show (only shows the grep process ID):


```

~$: ps aux | grep 17893
mish     19533  0.0  0.0   7624   936 pts/0    S+   16:08   0:00 grep --color=auto 17893

```


Evendough "jobs" shows it, and "kill %1" seems to work:


```

~$: jobs -p             # **1st command**
16772
.
. etc
.
17893
17897
.
. etc
.
17939
~$: kill %1             # **2nd command**

[1]   Stopped                 man grep  (wd: /etc/init)
(wd now: ~)
~$: jobs                # **3d command**
[1]   Terminated              man grep  (wd: /etc/init)
[2]   Stopped                 info bash  (wd: /etc/init)
.
. etc
.

```

If somebody knows what's happening, I'd very much apreciate any help or reference to help you might be able to give me (I've read what i've found in the man pages and I'v searched google as well as I know, that might be subject to further enhancement... :)

The shell is bash, version 4.1.5(1)-release (x86_64-pc-linux-gnu),
and this is an acer laptop (very general pieces and all), whith ubuntu 10.04 LTS for amd64. Any other information that might be valuable I can get you (hopefully).


**Thanks in advance!**

And please excuse my English if it sounds weird some times. Not my first language...


(if the post is too long or wrong in some way, please do tell me, it is my first one)

---

### Post by iponeverything on 2012-04-07
do  a:

```
pstree -up
```

you will see processes represented in tree format instead of flat.

Killing the process at the base of given branch will generally cause it to send a termination signal to its children.

This may explain the behavior that you are seeing.

---

### Post by ferhtgoldaraz on 2012-04-07
Thanks, I'm looking into it.

---

### Post by ferhtgoldaraz on 2012-04-07
The commands that are supposed to work actually work without problems, it was me.

the PIDs that where giving me trouble where weird things that I was doing with redirections to try n find out how they work, such as:


```

~$: jjj 2>&1 | less

```

less shows the sterr and then stops, but it's PID can keep being a mystery to me at this point, since I don't know if it's parent is the shell or the other command that doesn't exist because it failed, or something to do with the pipe or the redirection...

... and I'll worry about it when I advance further.

Thanks, the parent-child suggestion actually helped me!

And sorry for the inconvenience, didn't realise this was the case.

---

### Post by iponeverything on 2012-04-07
> And sorry for the inconvenience, didn't realise this was the case. 

no apologies necessary -- people are happy to help out.

---

### Post by dfreer on 2012-04-07
Is this what you are trying to accomplish?
```
killall jobs
```

---

### Post by ferhtgoldaraz on 2012-04-08
The idea that it suggests, yeah!

But it isn't working just like that:


```

:~$ jobs
[1]   Stopped                 info check
[2]   Stopped                 info autogen
[3]   Stopped                 man cat
[4]   Stopped                 man bash
[5]-  Stopped                 man jobs
[6]+  Stopped                 info jobs
:~$ killall jobs
jobs: no process found

```


The commands posted above (kill `jobs -p` and kill $(jobs -p)) are working in normal situations dough, but i'd apreciate any other way of doing it just for knowledge's sake. Or any reference to it too.

Thanks!

---

### Post by ferhtgoldaraz on 2012-04-08
EDIT: I find myself using:


```

:~$ kill  -9 `jobs -p`

```


or


```

:~$ kill  -9 $(jobs -p)

```


Because the normal SIGTERM doesn't seem to kill them.

---

### Post by dfreer on 2012-04-08
Actually I had to read your post a little better. You could do a:
```
killall info
killall man
```

And it should kill all processes of the name 'info' or 'man'.

---

### Post by ferhtgoldaraz on 2012-04-08
Haven't thought of that... It actually works better, so I wouldn't have to be worried about other jobs or anything.

Thanks, I'll use that!

---

