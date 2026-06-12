---
title: "Can someone please explain this output?"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by vasa1 on 2012-06-17
If I run "ps aux | grep compiz" in a terminal, I see:
```
user_name   2213  0.0  0.0   4368   840 pts/1    S+   12:17   0:00 grep --color=auto compiz

```
Does that mean I'm running compiz? To my mind, I'm running a basic Xfce 4.10 session.

---

### Post by bab1 on 2012-06-17
> **vasa1 said:**
> If I run "ps aux | [COLOR="Red"]**grep**[/COLOR] [COLOR="RoyalBlue"]**compiz**[/COLOR]" in a terminal, I see:
```
user_name   2213  0.0  0.0   4368   840 pts/1    S+   12:17   0:00 **[COLOR="Red"]grep[/COLOR]** --color=auto [COLOR="RoyalBlue"]**compiz**[/COLOR]

```
Does that mean I'm running compiz? To my mind, I'm running a basic Xfce 4.10 session.

Nope.  It shows you are running grep (see red above) looking for compiz (see blue above).

---

### Post by codemaniac on 2012-06-17
As told by bab1 there is no compiz process running now , still ps returns grep's pid with other attributes .

ps aux output explained below .

> USER       PID  %CPU %MEM  VSZ RSS     TTY   STAT START   TIME COMMAND

USER = user owning the process
PID = process ID of the process
%CPU = It is the CPU time used divided by the time the process has been running.
%MEM = ratio of the process&#8217;s resident set size to the physical memory on the machine
VSZ = virtual memory usage of entire process
RSS = resident set size, the non-swapped physical memory that a task has used
TTY = controlling tty (terminal)
STAT = multi-character process state
START = starting time or date of the process
TIME = cumulative CPU time
COMMAND = command with all its arguments

---

### Post by vasa1 on 2012-06-17
Thank you both :)

Marking thread **solved**.

---

### Post by firekage on 2012-06-17
> **bab1 said:**
> Nope.  It shows you are running grep (see red above) looking for compiz (see blue above).

Can You check this:

```
firekage@deusex:~$ ps aux | grep compiz
firekage  2640  0.0  0.0   2040   504 ?        Ss   00:57   0:00 /bin/sh -c /usr/bin/compiz-decorator
firekage  2662  1.8  3.6 337596 151072 ?       Sl   00:57  12:26 compiz
firekage 28322  0.0  0.0   5688   800 pts/0    S+   12:13   0:00 grep --color=auto compiz
firekage@deusex:~$ 
```

I use it, right?

---

### Post by Carborundum on 2012-06-17
> **firekage said:**
> Can You check this:

```
firekage@deusex:~$ ps aux | grep compiz
firekage  2640  0.0  0.0   2040   504 ?        Ss   00:57   0:00 /bin/sh -c /usr/bin/compiz-decorator
firekage  2662  1.8  3.6 337596 151072 ?       Sl   00:57  12:26 compiz
firekage 28322  0.0  0.0   5688   800 pts/0    S+   12:13   0:00 grep --color=auto compiz
firekage@deusex:~$ 
```I use it, right?

Use 'ps -e | grep compiz' instead. If you are using Compiz, the output will look something like this:
```
 1613 ?        00:09:00 compiz
```
Otherwise, you won't get any output.

---

### Post by vasa1 on 2012-06-17
Yes,
```

USER		PID	%CPU	%MEM
firekage	2662	1.8	3.6
```

---

### Post by vasa1 on 2012-06-17
> **Carborundum said:**
> Use 'ps -e | grep compiz' instead. If you are using Compiz, the output will look something like this:
```
 1613 ?        00:09:00 compiz
```
Otherwise, you won't get any output.

Neat!

---

### Post by firekage on 2012-06-17
Thank You very much ;)

---

