---
title: "An equivalent to Windows' custom performance counters?"
date: 2008-04-03
forum: Programming Talk
---

### Post by joblessjunkie on 2008-04-03
I'm trying to create some custom monitoring for our server farm.

One thing I am missing is something equivalent to Windows' custom performance counters: system-wide integers that can be quickly and thread-safely incremented or queried from any process. I'd like to create counters for various application-specific events like jobs completed, errors encountered, etc.

Does Linux/Ubuntu have a standard way to implement such a thing? Forgive me if this is a silly question -- I'm coming from a long Windows history :-(

A naive solution might be just to simply store integers in a small file somewhere, but this ability seemed so core to the system that I suspect there is probably some existing way to do this....

Thanks!

---

### Post by pseudo-random on 2008-04-03
I'd say there's more ways to go about this on a unix-type system than windows.
Take grep or tail for example. Both those commands can be called on by a script making use of variables such as time. I haven't an example to hand but I'd say grep: "Grep".

---

### Post by ghostdog74 on 2008-04-03
> **joblessjunkie said:**
> 
Does Linux/Ubuntu have a standard way to implement such a thing? Forgive me if this is a silly question -- I'm coming from a long Windows history :-(

If i get you correct:  some tools that could help
vmstat, sar, mpstat , ps, iostat, process accouting (acct)...etc

---

### Post by lnostdal on 2008-04-03
not sure what you're after, but /proc has a lot of stuff ..

try it:
cat /proc/cpuinfo
cat /proc/meminfo

..etc..

..all the directories with numbers for names in /proc represent PIDs (process IDs) .. you can examine processes .. i'm running a process SBCL and i know its PID is 19737 (ps -A | grep sbcl) .. so i do:

cat /proc/19737/status

..to get some info about that process ... lots of stuff here

edit:
see man 5 proc

---

### Post by slavik on 2008-04-04
you can use semaphores as counters ...

---

