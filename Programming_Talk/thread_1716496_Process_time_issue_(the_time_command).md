---
title: "Process time issue (the time command)"
date: 2011-03-28
forum: Programming Talk
---

### Post by paxxus on 2011-03-28
Hi,

I'm relying on the time command to measure CPU time for some scripts I'm executing.

The script calls a lot of other commands (make, recursive make etc. etc.) and somewhere in this command tree it ends up calling the primary job - a compute intensive EDA program.

What I see is that sometimes the time command reports almost no CPU usage even though that is not the case - the job may have run for hours on an otherwise unloaded machine. It's as if the EDA program sometimes becomes detached. I suspect that it is the EDA program which manages to do something odd which triggers this, specifically I suspect that a wait for license - even for just a brief period - causes the job CPU time to not be reported back to the encapsulating time command.

Any suggestions on a more reliable method of obtaining CPU utilization information (bash scripting)?

---

### Post by paxxus on 2011-03-31
I guess that if I could use a time command which included all the spawned forks, then it would work. I just don't know how to do this :(

---

### Post by MadCow108 on 2011-03-31
you could try systat/pidstat
the -T option should allow tracing children

---

### Post by paxxus on 2011-03-31
Neither the systat nor the pidstat command is available on my system (I can't install stuff) :(

---

### Post by paxxus on 2011-05-16
I found a more reliable approach. While the job(s) are running I at regular intervals do a ps command as follows:

ps --no-headers -e -o user,ppid,pid,pcpu

The output is then fed to a perl script which traces the process tree by following the process IDs (pid) and parent process IDs (ppid). Along the way the CPU usage (pcpu) for the individual sub-jobs in the tree are summed and the final sum gives me the overall current CPU usage. When the job complete I take the average of all samples and multiples by the wall time thereby finally giving me an estimate of the overall CPU time.

This is hardly super accurate but it seems quite reliable. As a bonus I can now monitor CPU usage while the job is running.

Edit: The pcpu option for ps actually already returns the accumulated CPU utilization (and not current CPU utilization as shown by top). So, I don't have to perform the averaging I talked about.

---

