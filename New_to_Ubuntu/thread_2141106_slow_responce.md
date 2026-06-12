---
title: "slow responce"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by ghelp on 2013-05-01
I have been using Ubuntu for many months.
Since  a few days ago ( one to two weeks ) my computer is slow.
Could it be a virus?
My version is Ubuntu 12.04 LTS

The title should be [U][B]SLOW  RESPONCE
[/B][/U]
Ghelp

---

### Post by alphacrucis2 on 2013-05-01
More likely a runaway process. Open up a terminal and enter:

```
top
```


To see what is hogging your machine.

---

### Post by ghelp on 2013-05-01
I opened a terminal and entered " top ". The display showed much data that was changing. Some of the data at the top ( some of which did not change ) were --- Top 20:54:34 up 25 min 1 user load average:2.08, 2.28, 2.13 tasks 150 total 146 sleeping.

( Actually, I do not know what to look for. )

Ghelp

---

### Post by hnf a on 2013-05-02
maybe what alphacrucis2 want to tell you is look at the %CPU and see what process that consume high cpu resources 

CMIIW

---

### Post by prodigy_ on 2013-05-02
> **ghelp said:**
> Top 20:54:34 up 25 min 1 user load average:2.08, 2.28, 2.13 tasks 150 total 146 sleeping.
Wrong line. You want to look at Cpu(s) and at 5-10 processes on top (because they're sorted by how much CPU resources they eat). Example:

```
top - 14:00:39 up 4 days, 13:50,  2 users,  load average: 0.00, 0.01, 0.05
Tasks: 148 total,   1 running, 146 sleeping,   0 stopped,   1 zombie
**Cpu(s):  0.3%us,  0.5%sy,  0.0%ni, 97.3%id,  1.7%wa,  0.0%hi,  0.1%si,  0.0%st**
Mem:   2053428k total,  1128776k used,   924652k free,    57996k buffers
Swap:  2086908k total,        0k used,  2086908k free,   693184k cached

  PID USER      PR  NI  VIRT  RES  SHR S **%CPU** %MEM    TIME+  COMMAND                                                                                     
17288 prodigyd  20   0  2848 1136  872 R    **4**  0.1   0:00.02 top                                                                                         
    1 root      20   0  3528 1984 1316 S    **0**  0.1   0:00.82 init                                                                                        
    2 root      20   0     0    0    0 S    **0**  0.0   0:00.12 kthreadd                                                                                    
    3 root      20   0     0    0    0 S    **0**  0.0   2:44.13 ksoftirqd/0                                                                                 
    6 root      RT   0     0    0    0 S    **0**  0.0   0:00.03 migration/0                                                                                 
    7 root      RT   0     0    0    0 S    0  0.0   0:02.58 watchdog/0                                                                                  
    8 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/1
```

---

### Post by ghelp on 2013-05-02
Beautiful.
Thank you. 
That is just what I say on my computer - the %id around 95%id, and the others low.
Are these readings OK?

Also, in the mem line - about 160500k free,
  and in the swap line - about 261000k free.

Ghelp

---

### Post by prodigy_ on 2013-05-02
Should be fine. If your PC is slow to respond when CPU is 95% idle, it can be due to some change you made recently. Did you install any updates (particularly kernel or graphics drivers)? If so you mught want tor revert to a previous version.

Also try checking **~/.xsession-errors** log for errors.

---

### Post by ghelp on 2013-05-03
My reply seems to be lost - and replaced by the previous one.
I will try again here -
When I entered "  ~/.xsession-errors " in a terminal the response was " Permission denied ".

Ghelp

---

### Post by prodigy_ on 2013-05-03
Yeah, you need to open in with gedit or something. In terminal you should start with ```
ls -lh ~/.xsession-errors
``` to check the file size. If it's large, there may be something wrong with your DE. To see the most recent errors use something like ```
tail -1000 ~/.xsession-errors | less
``` Then you can use up/down or pagegup/pagedown keys to navigate the output.

Not sure if it'll be very helpful though. Pure performance issues (when you don't get any crashes or error messages) are usually the hardest to troubleshoot.

---

### Post by ghelp on 2013-05-03
I entered the two codes.
The first one  gave a one line response with " 18K " as the only relevant information.
I did it again and the it changed to " 23K ".

The second code gave a few pages of information.

Ghelp

---

