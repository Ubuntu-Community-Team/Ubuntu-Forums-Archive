---
title: "Waiting for any one of a few processes to finish"
date: 2008-04-10
forum: Programming Talk
---

### Post by mvan83 on 2008-04-10
I'm writing a program that will be given a handful of process ids to monitor and when any one of them finishes, I want to know. Obviously a fork and waitpid will work for one process, but I will have potentially more than one. The first solution I can think of is to run a non-blocking waitpid over each process and then sleep for a short amount of time, and then repeat. This seems like a slightly ugly solution though. Is there a better way to do this? Thanks.

---

### Post by heikaman on 2008-04-10
when a child process finishes the parent receives a SIGCHLD, so install a signal handler.

man signal

---

### Post by themusicwave on 2008-04-10
Well I have 2 thoughts.

1)
You could capture the output of ps , and parse it for PIDs

2) If you know the pid you could see if os.path.exists(os.path.join("/proc/dev/",pid))

Every process gets a folder there and when it's done it's folder goes away.

Just 2 ideas, might not be optimal but I think it could work.

---

### Post by heikaman on 2008-04-10
> **themusicwave said:**
> 
2) If you know the pid you could see if os.path.exists(os.path.join("/proc/dev/",pid))

you mean "/proc/pid" ?


> **mvan83 said:**
> I'm writing a program that will be given a handful of process ids to monitor and when any one of them finishes, I want to know. Obviously a fork and waitpid will work for one process 

:confused: 
I'm confused i thought he wants to fork these processes, right ?

---

### Post by themusicwave on 2008-04-10
I forget the exact path and am not at my Linux box.  I think its dev/proc or proc/dev  somewhere every program gets a folder with it's pid.

Like I said it isn't optimal, but you can use it to check if a process is running.  I think the OP's original idea is better though.

---

### Post by Martin Witte on 2008-04-10
as an alternative you can examine the return code of command 'kill -o <pid>'
```

martin@toshibap200:~$ echo $(ps -u martin|awk '{print $1}')
PID 5492 5495 5531 5533 5537 5539 5545 5547 5549 5553 5560 5602 5637 5638 5640 5641 5646 5654 5660 5662 5664 5665 5668 5698 5712 5717 5738 5769 5847 5859 5863 6110 6648 6651 6652 6703 6704 6705
martin@toshibap200:~$ kill -0 1
bash: kill: (1) - Operation not permitted
martin@toshibap200:~$ echo $?
1
martin@toshibap200:~$ kill -0 9999
bash: kill: (9999) - No such process
martin@toshibap200:~$ kill -0 5533
martin@toshibap200:~$ echo $?
0

```

---

### Post by WW on 2008-04-10
> **mvan83 said:**
> I'm writing a program that will be given a handful of process ids to monitor and when any one of them finishes, I want to know. 
Who is giving you this "handful of process ids"?  If they are not children of your process id, I don't think waitpid will work; it expects a pid of child.

---

