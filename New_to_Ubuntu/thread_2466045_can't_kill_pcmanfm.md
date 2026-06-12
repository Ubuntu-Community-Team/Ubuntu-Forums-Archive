---
title: "can't kill pcmanfm"
date: 2021-08-18
forum: New to Ubuntu
---

### Post by maketopsite on 2021-08-18
```
#kill [FONT=courier new]*PID*[/FONT]
```

does not work.

(PID is number which ```
ps aux | grep pcman
``` returns).

Is there please other way than  restart of Ubuntu 20.04 ?

---

### Post by Impavidus on 2021-08-18
What's that # at the start of your command? Do you mean you type the command at a root prompt (no need for that if running pcmanfm as your normal user) or did you actually type it at the command line (that would turn it into a comment)?

I don't really know pcmanfm. kill by default sends SIGTERM, the termination signal, which pcmanfm can ignore or handle in some other way than terminating, but normally an application should handle it with clean termination. Or your system could be configured to restart pcmanfm whenever it gets closed, but then the PID will change.

---

### Post by maketopsite on 2021-08-18
> **Impavidus said:**
> What's that # at the start of your command? Do you mean you type the command at a root prompt (no need for that if running pcmanfm as your normal user) or did you actually type it at the command line (that would turn it into a comment)?

I don't really know pcmanfm. kill by default sends SIGTERM, the termination signal, which pcmanfm can ignore or handle in some other way than terminating, but normally an application should handle it with clean termination. Or your system could be configured to restart pcmanfm whenever it gets closed, but then the PID will change.

I typed the command at a root prompt (and at user prompt too).

PID is always the same.

---

### Post by &amp;KyT$0P# on 2021-08-18
Why are you trying to kill pcmanfm?  What specific steps/circumstances led to this situation where you want to kill it?

---

### Post by maketopsite on 2021-08-18
> **halogen2 said:**
> Why are you trying to kill pcmanfm?  What specific steps/circumstances led to this situation where you want to kill it?

It's unresponsive. I can't launch another instance of it. Probably OOM.

---

### Post by TheFu on 2021-08-18
The kill command send the process a signal. There are lots and lots of different signals.  -15 is the default (sigterm).  -9 is the nasty "kill it no matter what", sigterm.
To see all the signals on your system, start in this file: /usr/include/signal.h and follow the #includes until you get to the list.  For me, that led to /usr/include/asm-generic/signal.h.
I'm seeing 31 signals available.

So ... try **kill -9 {PID}**
That can create a zombie process - meaning it isn't running, not using any resources, but it is still in the process table.  I think top will actually label is "zombie".

---

### Post by maketopsite on 2021-08-18
> **TheFu said:**
> The kill command send the process a signal. There are lots and lots of different signals.  -15 is the default (sigterm).  -9 is the nasty "kill it no matter what", sigterm.
To see all the signals on your system, start in this file: /usr/include/signal.h and follow the #includes until you get to the list.  For me, that led to /usr/include/asm-generic/signal.h.
I'm seeing 31 signals available.

So ... try **kill -9 {PID}**
That can create a zombie process - meaning it isn't running, not using any resources, but it is still in the process table.  I think top will actually label is "zombie".

Thank you, this has solved the problem.

---

### Post by TheFu on 2021-08-18
> **maketopsite said:**
> Thank you, this has solved the problem.

Beware that using -9 does nasty things to running processes. I might use it 3 times a year.

---

### Post by maketopsite on 2021-08-18
> **TheFu said:**
> Beware that using -9 does nasty things to running processes. I might use it 3 times a year.

Wel thank you. Do you mean "to other processes" than killed process itself ?

---

### Post by Holger_Gehrke on 2021-08-18
No, he means it can't be ignored. SIGKILL ends a process. Period. If the process was writing or changing a file, that file will in all probability be damaged beyond repair. If that process was a game running in a lower resolution graphics mode, it won't reset the screen to the normal desktop resolution. If it was reconfiguring some hardware (think about avrdude or something similar ...), that hardware will be stuck in a half-configured state.

Holger

---

