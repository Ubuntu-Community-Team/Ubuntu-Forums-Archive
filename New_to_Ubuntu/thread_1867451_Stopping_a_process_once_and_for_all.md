---
title: "Stopping a process once and for all"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by 29732 on 2011-10-23
Hi, 
I really would like to know how to kill some processes permanently, without it starting up again (i.e. gnome, NetworkManager, and many others).

Sure would be helpful.
Thanks, 
29732

---

### Post by zkriesse on 2011-10-23
I know this is a question not an answer but... Why would you want to kill a process permanently? And by permanently do you mean for good or for the current user(s)session?

---

### Post by 29732 on 2011-10-23
> **zkriesse said:**
> I know this is a question not an answer but... Why would you want to kill a process permanently? And by permanently do you mean for good of for per session?

Per session, or until I want it to run again.
And a couple of programs want me to kill off some processes to make them run at optimum quality, and also for the heck of it, you know? Just another addition to my knowledge :'P

---

### Post by zkriesse on 2011-10-23
Well what you can do is grep the process via terminal and then kill it that way... Probably then the process will not start until you either start it yourself or until another program/process requires it. So one thing you can do is try
```

ps -aux

```
That'll list most if not all of your system process(es) although it can be a tedious list to go through, obviously. [https://help.ubuntu.com/community/grep](https://help.ubuntu.com/community/grep) might have some more info...

---

### Post by dFlyer on 2011-10-23
just open a terminal and enter:

ps -aux

then when you find the  pid enter

kill (pid number)

---

### Post by 29732 on 2011-10-23
> **dFlyer said:**
> just open a terminal and enter:

ps -aux

then when you find the  pid enter

kill (pid number)
Like I said, that does not work.
I tried killing off NetworkManager, but it popped back up again.

---

### Post by 29732 on 2011-10-23
> **zkriesse said:**
> Well what you can do is grep the process via terminal and then kill it that way... Probably then the process will not start until you either start it yourself or until another program/process requires it. So one thing you can do is try
```

ps -aux

```
That'll list most if not all of your system process(es) although it can be a tedious list to go through, obviously. [https://help.ubuntu.com/community/grep](https://help.ubuntu.com/community/grep) might have some more info...
Wait, what?

---

### Post by dFlyer on 2011-10-23
Have you tried kill -9 (process number). Also you never said you tried anything so I gave you the easiest way to kill a command.

---

### Post by dFlyer on 2011-10-23
You might want to look under:

man kill

---

### Post by anewguy on 2011-10-23
Once you have the pid of network manager, try:

sudo kill -kill <process id>



Dave ;)

---

### Post by 3rdalbum on 2011-10-23
When a process "pops back up again", it's because there's another process whose job it is to restart the service again if it crashes. So, you need to kill that other process first before you can kill the main process.

In the case of Network Manager, if you really manage to find a reason to stop it mid-session, you don't kill it. You just use the 'service' command to stop it:

```
sudo service network-manager stop
```

To start it again, just replace 'stop' with 'start' and there you go.

---

