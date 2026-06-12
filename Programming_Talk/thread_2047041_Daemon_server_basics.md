---
title: "Daemon server basics"
date: 2012-08-24
forum: Programming Talk
---

### Post by IAMTubby on 2012-08-24
I have a few doubts regarding Daemon server. These questions were posted in another thread. Sorry for the spam, but I marked it as solved(as it solved the original problem) and now there are no replies for the same reason.

1)What advantage does a daemon provide over a normal server program running on the terminal. 

2)How long does a daemon run ? Does a daemon server run forever ?

3)After running the daemon server, when I do a ps, why doesn't it show me the daemon running ? I still get only bash and ps.

Thanks

---

### Post by sanderj on 2012-08-24
Use "ps -ef" to see all processes.

---

### Post by dwhitney67 on 2012-08-24
> **IAMTubby said:**
> 
1)What advantage does a daemon provide over a normal server program running on the terminal. 

2)How long does a daemon run ? Does a daemon server run forever ?

3)After running the daemon server, when I do a ps, why doesn't it show me the daemon running ? I still get only bash and ps.

Thanks

1) A daemon process is not associated with a terminal, thus it can be left running even after one exits a terminal, and even their desktop session.

2) A daemon process, similar to other "regular" processes, will run until an anomaly occurs or the system is shutdown.  You should be able to control your daemon process so that it responds, at a minimum, to the SIGTERM and SIGHUP signals.  The latter is typically used to restart the daemon (e.g. to re-read a config file).

3) This question has previously been answered; however to expand on that answer, use:
```

ps -ef | grep <daemon-name> | grep -v grep

```
where <daemon-name> is the name of your daemon process.

Typically, a daemon process will also insert a "token" file containing its process ID (PID) into a file located in /var/run.  Not all daemon processes do this, for it is not required.

---

### Post by IAMTubby on 2012-08-24
Thanks sanderj, dwhitney67.
But I still have some clarifications.

a. Can you explain to me what ps -ef | grep <daemon-name> | grep -v grep does ?
I can understand that it does a ps and searches for the daemon program. But what does grep -v grep do ?

b.I don't seem to have the token files in the /var/run folder. But you have already mentioned that not all daemon processes do this.

Otherwise things are clear.

---

### Post by IAMTubby on 2012-08-24
Ohh does it omit out the grep from the ps ?

---

### Post by IAMTubby on 2012-08-24
dwhitney, I just checked the man pages. It says, ""

-v, --invert-match
Invert the sense of matching,to select nonmatching lines.

Thanks. Shall mark the thread as solved after you reply.

---

