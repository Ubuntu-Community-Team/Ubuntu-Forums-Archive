---
title: "any command more powerful than kill PID?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by legolas_w on 2008-06-10
Hi
Thank you for reading my post
Is there any command more powerful than kill PID in order to kill a process that kill pid can not kill?
sometimes program hangs and kill pid can not kill them, they use alot of CPU and force me to restart the computer. for example totem movie player.

Thanks.

---

### Post by wootah on 2008-06-10
```
sudo kill -9 *pid*
```I think that's as hard core as it gets? From the man pages:
> 
       Name     Num   Action    Description
       0                 0        n/a       exit code indicates if a signal may be sent
       ALRM       14      exit
       HUP           1      exit
       INT            2       exit
       **KILL         9       exit      this signal may not be blocked**


---

### Post by the_doc on 2008-06-10
If a process still persists after using just KILL you can use KILL -s 9 PID.

This will get rid of even stubborn processes, but doesn't give them time to shut down in a graceful manner.

---

### Post by legolas_w on 2008-06-10
Hi
thank you for reply
but even KILL -s 9 PID. had no effect on the process and it is still eating cpu.
I tried to lower its priority using system monitor but it had no effect either.

thanks

---

### Post by timcredible on 2008-06-10
sudo kill -9 PID
that should stop any process.

---

### Post by legolas_w on 2008-06-10
You may say that this is crazy but even pressing ALT+CTRL+BackSpace did not kill that process.

So I switched to ALT+CTRL+F7 and tried to issue ```
sudo reboot
``` and it was not able to restart the computer :O

Finally I pressed the restart button and now I am free of that process :O

thank you all for your tips.

---

### Post by kaptengu on 2008-06-10
[http://gprime.net/video.php/kill9]("http://gprime.net/video.php/kill9")
:lolflag:

---

### Post by jimv on 2008-06-10
What is the process?

Seems like that could be an important piece of info.

---

### Post by markbuntu on 2008-06-10
It is probably not the process you think you are trying to kill. Many programs make calls to other processes and sometimes these can run amok even after the process that called them is killed. For example if Totem has called xine and xine is going crazy, killing totem may not kill xine and it will continuee to run after totem is killed.

firefox3b5 was doing that to me. It would crash and disappear from the desktop but keep running until it crashed the whole system.

System monitor can give you a comprehensive real time listing of which processes are running you out of resources and you can kill them from there.

---

### Post by miss.magenta on 2008-06-10
There may also be a parent process (noted by a number in the PPID column of ps -ef output) that is hindering you.  

Alternatively, you can use fuser to find processes that are eating up file/socket resources and kill them that way, or there is pkill, killall, etc - ultimately though, they all send the same set of signals that kill does...still, worth a read through the man pages if you're unfamiliar with them.

---

### Post by wolfen69 on 2008-06-10
do alt-F2 and type xkill. then just click on the offending application.

---

### Post by markbuntu on 2008-06-10
Having the force quit button in a panel is also helpful for getting rid of stalled apps.

---

### Post by legolas_w on 2008-06-11
If you are intrested it was totem playing a file located on a NTFS partition.

There was no totem window in the desktop and only totem process was present in  ```
ps -ef |grep totem
```.

---

