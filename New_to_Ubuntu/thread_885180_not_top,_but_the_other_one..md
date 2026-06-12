---
title: "not top, but the other one."
date: 2008-08-09
forum: New to Ubuntu
---

### Post by adamogardner on 2008-08-09
I have virtual box in full screen mode.  So i figure I would do this since I can't seem to escape it: List the running processes, find the process id (pid) and then type "kill pid"  Is this correct?  can I please have the command to list the processes.  there is no good way I know of to reverse lookup commands.  thanks/

---

### Post by hofa on 2008-08-09
There must be a key combination to get you out of fullscreen =/

If you can't find it directly, just go

```
killall virtualbox
```

---

### Post by z.s.tar.gz on 2008-08-09
you can find running processes by using the "top" command.
you should also be able to stop it by command name, such as:
"kill virtualmachinecommand"

edit: sorry, i just realized what the title was. :p

---

### Post by adamogardner on 2008-08-09
> **hofa said:**
> There must be a key combination to get you out of fullscreen =/

If you can't find it directly, just go

```
killall virtualbox
```

It's not called virtualbox but something else.  I tried to run it that way and just tried to shut down as described.  Nope.  Besides I know there is a way like I;m describing.

---

### Post by loell on 2008-08-09
how about?

```
ps ax
```

---

### Post by adamogardner on 2008-08-09
why didn't this work?  THe virtual box is still there:

10163 ?        Rl     0:55 /usr/lib/virtualbox/VirtualBox
10181 ?        S      0:00 /usr/lib/virtualbox/VBoxXPCOMIPCD
10193 ?        Sl     0:01 /usr/lib/virtualbox//VBoxSVC --automate
18397 ?        Sl     0:00 /usr/lib/virtualbox/VirtualBox
19081 pts/1    Ss+    0:00 bash
19455 pts/3    Ss     0:00 bash
19628 pts/3    R+     0:00 ps -ax
20933 ?        Ss     0:00 /bin/sh -c gnome-terminal
20934 ?        Rl     0:03 gnome-terminal
20950 ?        S      0:00 gnome-pty-helper
20951 pts/0    Ss+    0:00 bash
24819 pts/2    Ss+    0:00 bash
29724 ttyUSB0  Ss+    0:00 pppd 921600 -detach call kppp-options crtscts default
31931 ?        S      0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
adamogardner@CRONUS:~$ kill 10163
adamogardner@CRONUS:~$ kill 10181
adamogardner@CRONUS:~$ kill 10193
adamogardner@CRONUS:~$ kill 18397

---

### Post by yabbadabbadont on 2008-08-09
Try using "kill -9" on those process IDs instead.

Edit: You might need to use sudo with the kill command.

---

### Post by adamogardner on 2008-08-09
> **yabbadabbadont said:**
> Try using "kill -9" on those process IDs instead.

Edit: You might need to use sudo with the kill command.

can someone show me the format of doing this all at once?  Would it be:
  "sudo kill -9 pid1 pid2 pid3 pid4"      ???  hey might as well learn it as I go.

---

### Post by yabbadabbadont on 2008-08-09
> **adamogardner said:**
> can someone show me the format of doing this all at once?  Would it be:
  "sudo kill -9 pid1 pid2 pid3 pid4"      ???  hey might as well learn it as I go.

That should work.

---

### Post by Dougie187 on 2008-08-09
Not sure if your issue is resolved, but another way to get the pid for virtualbox is 
```

ps aux | grep virtual

```
just replace virtual box with what ever program you want too, and if you are curious what either of the commands do, you can just man it of course. You should not need the sudo command to kill virtual box, because virtual box as far as i know, doesn't run as root. you can check when you do ps aux though, it will tell you who owns the process.

---

### Post by adamogardner on 2008-08-09
this is odd.  It still doesn't work.  I'm also getting an error there for sudo but I've had that a long time and hasn't adversely affected me.  here;s what's going on:

adamogardner@CRONUS:~$ sudo kill -9 10163 10181 10193 18397
sudo: unable to resolve host CRONUS
[sudo] password for adamogardner: 
adamogardner@CRONUS:~$ hmmmm, still there!
bash: hmmmm,: command not found
adamogardner@CRONUS:~$ sudo kill 10163
sudo: unable to resolve host CRONUS
adamogardner@CRONUS:~$ sudo kill -9 10163
sudo: unable to resolve host CRONUS
adamogardner@CRONUS:~$

---

### Post by yabbadabbadont on 2008-08-09
Try running it without the sudo.  If your user started the program, then it should be able to kill it.

---

### Post by adamogardner on 2008-08-09
yes i did and it said no such process existed so I ran the ps -ax command and sure enough the processes are no longer listed.  the problem now is that I have that full screen and virtual box still captures my mouse and keypad.  huh?

---

### Post by Dougie187 on 2008-08-10
Try this thread.

[http://ubuntuforums.org/showthread.php?t=615579](http://ubuntuforums.org/showthread.php?t=615579)

For your sudo problem that is.

---

