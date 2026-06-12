---
title: "Time Command"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Oddrey on 2008-06-10
I got curious and I typed help time, I guess it measures how long it took to run something. I wondered though what is PIPELINE? And what is the difference between real, user, and sys time?

---

### Post by Cypher on 2008-06-10
I don't know what PIPELINE is, in this context. The Real time indicates the total elasped time as you would percieve it. User and Sys times indicate how long the program ran in the User or System context. So doing something like
```

time ls -l

```
yields
```

real    0m0.047s
user    0m0.004s
sys     0m0.000s

```
This indicates that as far as I could perceive it, it took about 50 milliseconds to execute, of which the commands REALLY ran for about 4 milliseconds in user space. Since the "ls" command doesnt' need anything from the system(kernel) to complete, the "sys" time is zero.

Run the command on a task that might take a little longer and start counting the seconds, and you'll find that the "real" portion will be inline with what you think has elapsed while the "sys" and "user" will tell you where the command was spending tmie..

---

### Post by brian_p on 2008-06-10
> **Oddrey said:**
> I got curious and I typed help time, I guess it measures how long it took to run something. I wondered though what is PIPELINE? And what is the difference between real, user, and sys time?

In a pipeline the output of one command becomes the input of the next command. The output is fed to the input with '|'.

e.g.

```
time cat /etc/services | grep ftp

```

---

