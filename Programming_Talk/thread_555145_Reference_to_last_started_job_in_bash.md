---
title: "Reference to last *started* job in bash"
date: 2007-09-19
forum: Programming Talk
---

### Post by olejorgen on 2007-09-19
> 
       [...] The symbols
       %% and %+ refer to the shell&#8217;s notion of the current job, which is the
       last  job  stopped  while  it  was in the foreground or started in the
       background.  The previous job may be referenced using %-.   In  output
       pertaining to jobs (e.g., the output of the jobs command), the current
       job is always flagged with a +, and the previous job with a -.  A sin&#8208;
       gle % (with no accompanying job specification) also refers to the cur&#8208;
       rent job.


```
ole@tabole:~$ jobs
ole@tabole:~$ man bash
Reformatting bash(1), please wait...

[1]+  Stopped                 man bash
ole@tabole:~$ jobs
[1]+  Stopped                 man bash
ole@tabole:~$ gconf-editor &
[2] 2724
ole@tabole:~$ jobs
[1]+  Stopped                 man bash
[2]-  Running                 gconf-editor &
ole@tabole:~$ vim

[3]+  Stopped                 vim
ole@tabole:~$ jobs
[1]-  Stopped                 man bash
[2]   Running                 gconf-editor &
[3]+  Stopped                 vim
ole@tabole:~$ gconf-editor &
[4] 2750
ole@tabole:~$ jobs
[1]-  Stopped                 man bash
[2]   Running                 gconf-editor &
[3]+  Stopped                 vim
[4]   Running                 gconf-editor &
ole@tabole:~$ 

```
How to reference [4]?

EDIT: not using %4

---

### Post by mssever on 2007-09-20
```
fg 4
```

---

### Post by olejorgen on 2007-09-20
Well, I want to reference the last started job, not a specific last started job. (ie. without using the actually number) (clearified in the op)

I could of course do something like jobs | tail -1 | sed -e "something" but it seems like this functionality should be builtin? (Maybe I just suck reading documentation)

---

### Post by mssever on 2007-09-20
Hmmm... Don't know that...

---

### Post by olejorgen on 2007-09-28
*Bump* ?

---

