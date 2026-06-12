---
title: "How to I force another session to logout?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by JillSwift on 2008-08-21
Once in a while a game I play crashes. Sadly, said game takes over the keyboard and mouse, and when it crashes I can't do anything in the session.

I've taken to logging in to TTY1 and killing Xorg, but this seems a little harsh.

Is there a better way to force that session to logout?

Better still, anyone know how to grab they keyboard and mouse back?

---

### Post by neurostu on 2008-08-21
when the game crashes is it still running? Can you see it when you connect over the TTY?  You can try starting and stopping GDM...  look around for directions on how to do that...

What I would recommend is installing htop, then switch to a TTY run htop and see what process is using your resources and then kill that specific process... if that doesn't work then try killing gdm

---

### Post by damis648 on 2008-08-21
Press Ctrl+Alt+Backspace... that forces X to restart. Better, though, would be to eliminate the crash in the first place. Run the game from terminal and look at the output when it crashes (putting the game in windowed mode)

---

### Post by JillSwift on 2008-08-21
I should have mentioned, sorry:

The game crash is a freeze, but the game appears to still be running at the same CPU usage as before. I tried just killing the game, but the keyboard and mouse were still unresponsive afterward.

There is nothing written to the terminal when it freezes. :(

---

### Post by stmiller on 2008-08-21
Yeah Ctrl+Alt+Backspace will save you.

---

### Post by neurostu on 2008-08-21
Have you tried running top to see what processes are consuming system resources?

---

### Post by JillSwift on 2008-08-21
> **neurostu said:**
> Have you tried running top to see what processes are consuming system resources?Yes, that's how I know the game is still running, and with the same percentage cpu and memory as before the freeze.

---

### Post by robert shearer on 2008-08-21
Don't know if this works for Kubuntu but in Ubuntu this process un-freezes and reboots.Though I think you just want to free up without rebooting??.

Still better than a hard reboot to solve a lock-up.

Recovery - Type the phrase “REISUB” while
holding down Alt and SysRq (PrintScrn) with
about 1 second between each letter. Your system
will reboot.

---

### Post by damis648 on 2008-08-21
> **robert shearer said:**
> Don't know if this works for Kubuntu but in Ubuntu this process un-freezes and reboots.Though I think you just want to free up without rebooting??.

Still better than a hard reboot to solve a lock-up.

Recovery - Type the phrase “REISUB” while
holding down Alt and SysRq (PrintScrn) with
about 1 second between each letter. Your system
will reboot.

Actually, you are probably going to want to use "**RSEIUB**". That would be the order you would want to use.
Which would be Raising Skinny Elephants Is Utterly Boring.

---

### Post by robert shearer on 2008-08-22
> **damis648 said:**
> Actually, you are probably going to want to use "**RSEIUB**". That would be the order you would want to use.
Which would be Raising Skinny Elephants Is Utterly Boring.

Hey thanks, explains why I usually have to run it twice!
 Got the instruction as posted from the Ubuntu Reference from FOSSwire.
Just shows that not all info is good info.
Apologies to O/P for the misdirection.

---

### Post by JillSwift on 2008-08-22
Thank you for that, robert and damis648, but it's only the game that's frozen. I can get my machine back by restarting X.

Thing is I really hate having to do that, especially if I had something else running (like when I was torrenting a collection of short videos to friends).

---

### Post by unutbu on 2008-08-22
```

ps axuw
```
will list all processes running on the machine.

```

ps axuw | grep NAME
```

will list all processes running on the machine that contains the word NAME somewhere in the output line.

For firefox, for example, you might see something like
```

hairdryer@max:~/test% ps axuw | grep firefox
hairdryer    [COLOR="Red"]6129[/COLOR]  0.0  0.1   3852  1360 ?        S    08:02   0:00 /bin/sh /usr/bin/firefox
hairdryer    [COLOR="Red"]6143[/COLOR]  0.0  0.1   3892  1380 ?        S    08:02   0:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bi
hairdryer    [COLOR="Red"]6148[/COLOR]  3.3  4.3 156988 45204 ?        Sl   08:02   0:11 /usr/lib/firefox/firefox-bin
hairdryer    [COLOR="Red"]6307[/COLOR]  0.0  0.0   2976   772 pts/0    S+   08:08   0:00 grep firefox
```

The second column are process ID numbers (PIDs).

To kill process 6148:

```
kill 6148
```

You can then check that the process is gone (if it isn't obvious) by doing "ps axuw | grep NAME" again. Sometimes a process will refuse to die. In such cases, you can send a message to the linux kernel that you want something killed:

```
kill -9 6148
```

No process that you own can escape the wrath of the linux kernel. It is best to try to kill without the -9 flag first however, because it gives the process a chance to close itself down gracefully.

In the above example there are 3 firefox processes (PID=6129, 6143, 6148) and one process (PID=6307) related to the grep command. In the case of firefox, killing any of the three will do. In other cases, you might have to experiment.

---

### Post by JillSwift on 2008-08-22
Thanks, unutbu. As I said above, killing the game's process (it only has one) does not release the keyboard and mouse. I've never had to use a -9 on it.

---

### Post by neurostu on 2008-08-22
Have you tried starting and stopping GDM I'm not sure how to do it but I'm about 99% sure that it will work.

---

### Post by xeth_delta on 2008-08-22
> **JillSwift said:**
> Thanks, unutbu. As I said above, killing the game's process (it only has one) does not release the keyboard and mouse. I've never had to use a -9 on it.

Might have been mentioned before, but I did not find it. After killing the game main process, is the CPU still under heavy usage?

My guess would be that there is more than one process associated to the game, even though they don't share similar names.

Try
```
ps -ef
```
before and after starting the game (of course before any crash) and compare what processes are running.

Alternatively, try
```
pstree
```
Which will show you processes in a tree-like structure.

You could also have a look at the Xserver log /var/log/Xorg.0.log (EE lines show errors, WW warnings) and system log /var/log/syslog

---

### Post by damis648 on 2008-08-22
> **neurostu said:**
> Have you tried starting and stopping GDM I'm not sure how to do it but I'm about 99% sure that it will work.

The result would be the equvalent of restarting X (ctrl+alt+backspace), and that already works.

---

### Post by unutbu on 2008-08-22
JillSwift, perhaps try

System>Administration>Login Window

Uncheck the box that says "Disable multiple logins for a single user"

Click the icon in the upper right corner of your screen and select "Switch User".

Login again.

Run the game.

When you finish the game. Press Ctrl-Alt-Backspace to restart X. It will not affect your first login session.

You can also switch between the two sessions by pressing Ctrl-Alt-F7 (first login) and Ctrl-Alt-F8 (second login)

---

### Post by JillSwift on 2008-08-22
> **xeth_delta said:**
> Might have been mentioned before, but I did not find it. After killing the game main process, is the CPU still under heavy usage?

My guess would be that there is more than one process associated to the game, even though they don't share similar names.

Try
```
ps -ef
```before and after starting the game (of course before any crash) and compare what processes are running.

Alternatively, try
```
pstree
```Which will show you processes in a tree-like structure.

You could also have a look at the Xserver log /var/log/Xorg.0.log (EE lines show errors, WW warnings) and system log /var/log/syslog
Thanks, I didn't know about pstree.

The game has the one process.
After a crash the CPU is still being fully utilized by the game (which is normal for the game while running) and after killing the game the CPU usage is normal for my desktop, which is about 1-2% used.

There were no errors left behind in the logs by the game's freeze. I can see where I restarted X in Xorg.*.log, and the messages from the processes I start on login in syslog too, but not a thing from the game or errors of any sort.

Restarting down X recovers from the problem fine. I'd just prefer to recover the keyboard and mouse inputs without having to do that. :(

---

### Post by JillSwift on 2008-08-22
> **unutbu said:**
> <trim work-around>That's a nice work-around idea. Thanks!

---

### Post by JillSwift on 2008-08-22
> **neurostu said:**
> Have you tried starting and stopping GDM I'm not sure how to do it but I'm about 99% sure that it will work.It would be the same as restarting X.
Also, I'm using Kubuntu, so it's KDM :)

---

