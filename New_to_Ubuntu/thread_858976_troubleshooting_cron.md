---
title: "troubleshooting cron"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by ziphyre on 2008-07-14
Hi,

I try to schedule tasks using cron, but fail. So to test it, I have the following configuration which runs firefox every minute. But nothing happens?? Here is the result of crontab -l:

```
ziphyre@neptune:~$ crontab -l
* * * * * firefox
```

Am I missing something?

---

### Post by hyper_ch on 2008-07-14
I don't think cron can work like this.

---

### Post by ziphyre on 2008-07-14
> **hyper_ch said:**
> I don't think cron can work like this.

Why? And if so, can you give me a working example to test it?

PS: additional info:
According to my syslog, to firefox command runs every minute:

```
Jul 14 11:51:01 neptune /USR/SBIN/CRON[9130]: (ziphyre) CMD (firefox)
Jul 14 11:52:01 neptune /USR/SBIN/CRON[9162]: (ziphyre) CMD (firefox)
Jul 14 11:53:01 neptune /USR/SBIN/CRON[9194]: (ziphyre) CMD (firefox)
Jul 14 11:54:01 neptune /USR/SBIN/CRON[9226]: (ziphyre) CMD (firefox)
Jul 14 11:55:01 neptune /USR/SBIN/CRON[9259]: (ziphyre) CMD (firefox)
Jul 14 11:56:01 neptune /USR/SBIN/CRON[9292]: (ziphyre) CMD (firefox)
```

---

### Post by hyper_ch on 2008-07-14
(1) make a little bash script
test.sh
```

#!/bin/bash
ls -al ~/ > ~/Desktop/output.txt

```

(2) make it executable
```

chmod 0755 test.sh

```

(3) add it to (user) cron
```

* * * * * ~/test.sh

```

---

### Post by ziphyre on 2008-07-14
Thanks, it actually works.
So what is the problem with firefox?

---

### Post by hyper_ch on 2008-07-14
it's a gui application

it might have started ff in the backgroun. Run
```

ps aux | grep firefox

```

---

### Post by ziphyre on 2008-07-14
Nope,

```
~$ ps aux | grep firefox
ziphyre  10933  0.0  0.0   2976   768 pts/1    S+   13:29   0:00 grep firefox
```

---

### Post by hyper_ch on 2008-07-14
then cron just can't run gui stuff (probably)

---

### Post by ziphyre on 2008-07-14
Ok, I see

I switched to a console using Ctrl+Alt+F1, logged in and tried firefox, It gives me a:

 GTK warning: Cannot open display

So, I assume this is the same case with cron.
But there must be a way to start a gui app with cron?

---

### Post by fatality_uk on 2008-07-14
Maybe this will help!
[http://kyle.mathews2000.com/blog/2007/05/01/ubuntu-tutorial-how-to-launch-an-gui-from-cron-i](http://kyle.mathews2000.com/blog/2007/05/01/ubuntu-tutorial-how-to-launch-an-gui-from-cron-i)

Run: > whereis firefox
in a terminal to locate the GUI app you want. Then add that path.

edit. duh! it's /usr/bin/firefox ;)

So your cronjob will look like this:

> 45 11 * * * export DISPLAY=:0 && /usr/bin/firefox

to work at 11:45am

---

### Post by ziphyre on 2008-07-14
Resolved,

I should add export DISPLAY=:0 && before every gui command.

```
* * * * * export DISPLAY=:0 && firefox
```

Thanks

---

### Post by hyper_ch on 2008-07-14
there we go :)

---

