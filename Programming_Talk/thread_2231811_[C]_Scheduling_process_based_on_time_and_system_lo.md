---
title: "[C] Scheduling process based on time and system load"
date: 2014-06-28
forum: Programming Talk
---

### Post by erotavlas on 2014-06-28
Hi,

I have a question for you. I would like to write a program in C similar to crontab [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto), but that offer the further possibility to monitor the system load.  In practice, it should control both the time to start a process and the system load to launch or suspend a process. In a few words the program algorithm should be something similar to:
1) check if actual time meets the set time for process A
2) check if actual system load meets the load threshold for which to run process A
3) If 1) and 2) are ok, check if process A is already running: if yes don't do anything otherwise run process A. Otherwise if process A is already running pause it or don't do anything.

If think I can do this in C by making some system calls to bash. I can retrieve the system load from top command and I can launch process by using ps. Can I do this in C? Does already exists such program? 
Thank you

---

### Post by TheFu on 2014-06-28
It is more complicated than your outline, but that is a good start.  Checking for prior completions will be needed too.
Between anacron and taskspooler, you should find all the code needed.  Use system library calls, not system() calls ... please!

I find that using **task spooler** to manage the queue depth and number of concurrent processes works great.

BTW, sendmail shuts itself down when system load is over 90%. That code might be useful to look at.

---

### Post by erotavlas on 2014-07-15
Thank you, task spooler is very good to manage the queue of concurrent processes.

---

