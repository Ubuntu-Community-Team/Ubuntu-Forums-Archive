---
title: "How to run lmbench on Ubuntu"
date: 2022-11-05
forum: New to Ubuntu
---

### Post by qishenliumass on 2022-11-05
I already run apt-get install lmbench lmbench-run lmbench-doc, When I type in lmbench, the command still not found.

lqs@lqsmachine:~$ lmbench
lmbench: command not found


Also, When I type sudo lmbench-run, it shows me:

lqs@lqsmachine:~$ sudo lmbench-run
/usr/bin/lmbench-run: 1: /var/lib/lmbench/config: Permission denied
No config file?
Benchmark run finished....
Remember you can find the results of the benchmark
under /var/lib/lmbench/results

I wanna know how to use lmbench in Ubuntu.

---

### Post by Dennis N on 2022-11-05
In terminal, try either:
**info lmbench**
or[B]
man lmbench[/B]
and you may find how to use the command.

---

### Post by ajgreeny on 2022-11-05
You have to run the command ```
sudo lmbench-run
```
This will run the utility and put the results in /var/lib/lmbench/results

Here's what I see when I run lmbench.
```
user@Xubuntu-2204:~$ sudo lmbench-run
[sudo] password for user: 
/usr/bin/lmbench-run: 1: /var/lib/lmbench/config: Permission denied
No config file?
Benchmark run finished....
Remember you can find the results of the benchmark 
under /var/lib/lmbench/results
```
The results file however is an empty file, presumably because there is no config file.

Unfortunately ***man lmbench*** isn't much help, or not to me, as it says nothing about the configuration needed.

So my question back to you is, why did you install lmbench and what did you hope it would show you? Maybe there are other things you could use.

---

### Post by ActionParsnip on 2022-11-06
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=296594](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=296594)

---

### Post by qishenliumass on 2022-11-07
I need lmbench is for kernel performance benchmark.
Do you have other recommendations other than phoronix-test-suite and hackbench?

---

### Post by borkowski22ai on 2023-04-20
It looks like this application package is at least incomplete or even broken. Why it is still in  the distribution in such form? 


[FONT=monospace]```
[COLOR=#54ff54]**wborkowski@w-borkowski-PC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo lmbench-run [/COLOR]
[sudo] password for wborkowski:  
/usr/bin/lmbench-run: 1: /var/lib/lmbench/config: Permission denied 
No config file? 
Benchmark run finished.... 
Remember you can find the results of the benchmark  
under /var/lib/lmbench/results 
[COLOR=#54ff54]**wborkowski@w-borkowski-PC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo ls -l  /var/lib/lmbench/config [/COLOR]
total 0 
[COLOR=#54ff54]**wborkowski@w-borkowski-PC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo ls -l  /var/lib/lmbench/ [/COLOR]
total 8 
drwxr-xr-x 2 root root 4096 maj 27  2021 config 
drwxr-xr-x 2 root root 4096 maj 27  2021 results
```

[/FONT]

---

### Post by borkowski22ai on 2023-04-20
So this bug is still unfixed???
> **ActionParsnip said:**
> [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=296594](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=296594):(

---

