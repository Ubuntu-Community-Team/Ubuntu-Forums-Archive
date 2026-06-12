---
title: "number of cores used by a user"
date: 2009-10-01
forum: Programming Talk
---

### Post by flylehe on 2009-10-01
Hi,

I am just wondering how I can find out in bash how many cpu cores a user is now using on a linux server (KUbuntu)?

I am submitting a fair amount of background jobs to the server, so I like to write a bash script to check before I submit a job if the running jobs(processes) submit by me are too many, because I have to let other users have enough cores to use for their jobs. So I like to know what bash command(s) can tell me how many cores my jobs are using now.

Thanks and regards!

---

### Post by MadCow108 on 2009-10-01
a quick solution would be to use *ps U username* to get the processes of a user (and count them with wc -l)
this should be a good estimate of the cores used if the user runs only single threaded programs
you can also get the cpu load with ps for a better estimate

---

### Post by flylehe on 2009-10-01
Thank you! But some jobs are multi-threading. 

Also some processes, like ssh connection to the server and screen from where the jobs are submitted, are also listed by "ps U username" but not shown as keeping using some core(s) in top, which perhaps can be not counted into the jobs submitted by the user?

---

### Post by flylehe on 2009-10-01
By the way, can someone care to share scripts that check the CPU and memory and dynamically submit jobs based on their usage? It also check the number of currently running jobs submit by myself?
Thanks!

---

### Post by hessiess on 2009-10-01
I doubt that you could find this without getting into the Kernel, Linux automatically distributes running processes across all the available cores/CPU's. ps -u won't work as this only lists running processes. For example I have 10 prosesses running currently on a quad core machine.

---

