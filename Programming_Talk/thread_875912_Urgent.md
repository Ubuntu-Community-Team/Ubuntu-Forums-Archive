---
title: "Urgent"
date: 2008-07-31
forum: Programming Talk
---

### Post by hosseinyounesi on 2008-07-31
Hi, Please help me. I asked this question in a lot of forums but nothing answered :(
Any way that I can understand user log in/off ? ( Please do not say to use who command every second :mad: )
You know that in windows we can use registry, win api and a dll to do this, but how in linux ?
Thanks for ur answer

---

### Post by Smygis on 2008-07-31
Your question makes no sense. How do you want to understand user log in/off? And what does who have to do with it. And what can you do with the windows registry, winapi and a dll?

---

### Post by WW on 2008-07-31
Hi hosseinyounesi, welcome to the forums.

In the future, please chooses titles for your threads that have something to do with the question. "Urgent" is basically useless.

---

### Post by Zugzwang on 2008-07-31
Do I see it correctly that you want some code to be executed each time some user logs in or off?

---

### Post by pmasiar on 2008-07-31
OP: you did not get answers because your question does not make any sense. Read "How to ask questions" in my sig (and read sticky FAQ for more advice)

---

### Post by mssever on 2008-07-31
> **hosseinyounesi said:**
> Any way that I can understand user log in/off ?
What do you want to understand about login and logout? Your question is too vague to answer.

---

### Post by hosseinyounesi on 2008-07-31
First thank you ww to remind me choose a well topic then Maybe I have to apologize to ask my question ambiguously !!! I have a program that runs as a service (when system comes up) and it should understand when a user logs in/off and calculate some thing like time that he has been logged in what he has done and ... In windows we can use WM_USERCHANGED or ... and control log in/off by callong a dll when event happens. What to in Linux ?
Sorry for my bad english (If I had mistakes in english, please notify me)

---

### Post by LaRoza on 2008-07-31
> **hosseinyounesi said:**
> First thank you ww to remind me choose a well topic then Maybe I have to apologize to ask my question ambiguously !!! I have a program that runs as a service (when system comes up) and it should understand when a user logs in/off and calculate some thing like time that he has been logged in what he has done and ... In windows we can use WM_USERCHANGED or ... and control log in/off by callong a dll when event happens. What to in Linux ?
Sorry for my bad english (If I had mistakes in english, please notify me)

Programs that run in the background as the system starts are called "daemons": [http://en.wikipedia.org/wiki/Daemon_(computer_software)](http://en.wikipedia.org/wiki/Daemon_(computer_software))

You could write one, but I am not sure what you want it to do.

---

### Post by ib.lundgren on 2008-07-31
Sounds like you would like to create something like an internet café style of monitoring the time every user sits on the computer.

I do not know exactly how to implement this but I am sure someone else can answer. I think you can do something like this.

- Computer starts and loads your daemon.
- A user loggs in, which will most likely trigger an event of some kind that you could capture.
- Your daemon logs the login time
- After some time, the user logs out, triggering another event
- Your daemon computes the total time logged in and reports it in someway.

The only difficult thing I can see would be difficult is to get the daemon to capture the login / logout event.

---

### Post by mssever on 2008-07-31
> **hosseinyounesi said:**
> First thank you ww to remind me choose a well topic then Maybe I have to apologize to ask my question ambiguously !!! I have a program that runs as a service (when system comes up) and it should understand when a user logs in/off and calculate some thing like time that he has been logged in what he has done and ... In windows we can use WM_USERCHANGED or ... and control log in/off by callong a dll when event happens. What to in Linux ?
Sorry for my bad english (If I had mistakes in english, please notify me)
UNIX has had process accounting for years. I'm positive software for this exists, though I don't know how to write it. Here are some thoughts:

[LIST]
[*]Check and see if libpam has any hooks you can use for this.
[*]Monitor a process that must be running as long as a user is logged in. For example, for a terminal login, there will likely be a shell that stays running (though I don't know if an attacker can work around that). For a GDM-based login, you can set GDM to kill X between logins, then you can monitor that specific X process.
[*]The best way: Find a stable, well-written program that does this already, and see what it does.
[/LIST]

---

### Post by Martin Witte on 2008-07-31
> **hosseinyounesi said:**
>  I have a program that runs as a service (when system comes up) and it should understand when a user logs in/off and calculate some thing like time that he has been logged in what he has done and ... In windows we can use WM_USERCHANGED or ... and control log in/off by callong a dll when event happens. What to in Linux ?
Sorry for my bad english (If I had mistakes in english, please notify me)

This kind of information gets written to /var/log/auth.log on Ubuntu, the location for this log file is specified in  /etc/syslog.conf. You could write a process which checks this file on a regular interval, and then look for the 'session opened' en 'session closed' lines. Timestamps are printed, so the total time for a session can be calculated.

---

### Post by mssever on 2008-07-31
> **Martin Witte said:**
> This kind of information gets written to /var/log/auth.log on Ubuntu, the location for this log file is specified in  /etc/syslog.conf. You could write a process which checks this file on a regular interval, and then look for the 'session opened' en 'session closed' lines. Timestamps are printed, so the total time for a session can be calculated.
On my system, auth.log only contains entries for cron jobs. Oh, I just checked more and discovered that it was due to log rotation.

---

### Post by dribeas on 2008-07-31
+1 (mssever) on searching for prebuilt software.
+1 (Martin Witte) check the logs, that can even be configured to

If you really really want to do your own software you must know how logins/logouts are treated.

In a console the shell defined in /etc/passwd for the user is launched, whenever that process dies, logout is detected.

In a graphical environment there is an equivalent 'command for the session'. For failsafe logins is the xterm that is launched, while for common logins is usually x-session-manager. You can find what is being launched with:
```

$ ps auxfwww 
... a whole lot of other processes
root      6157  0.0  0.1  14060  1588 ?        Ss   16:48   0:00 /usr/sbin/gdm
root      6158  0.0  0.2  14516  2996 ?        S    16:48   0:00  \_ /usr/sbin/gdm
root      6164  1.2  5.0  77372 65680 tty7     Ss+  16:48   3:12      \_ /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      6300  0.0  5.0  77372 65680 tty7     S+   16:48   0:00      |   \_ /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
dibeas    6651  0.0  0.5  28872  7544 ?        Ssl  16:51   0:00      \_ x-session-manager
dibeas    6811  0.0  0.4  22648  6264 ?        Ss   16:51   0:00          \_ /usr/bin/seahorse-agent --execute x-session-manager
... a whole lot of other processes
```

As you see in my system x-session-manager is the root of all my programs for the session (gdm is the login manager, and X is the graphic environment, both run as root). Now, if you write a program and configure gdm (or kdm, xdm, whichever) to launch your program. And then you make your program fork, exec x-session-manager and wait for the process completion then your process lasts exactly the same as the user's session.

I don't think this helps much, as it is much easier going for pre-built software or writting a periodic script that reads through auth.log, but it's one of those pieces of information you don't need and still know...

   David

---

### Post by mssever on 2008-07-31
> **dribeas said:**
> In a console the shell defined in /etc/passwd for the user is launched, whenever that process dies, logout is detected.That's what I assumed, but I just tested it, and it isn't necessarily true.

Try this:

[LIST=1]
[*]Login on the console.
[*]Assuming bash is the default shell, run ```
exec htop -u youruser
```
[*]Bash is no longer running, but you're still logged in until you exit htop.
[*]Presumably, you could exec any other process, including another bash instance, and get around any login monitor that relies on a particular process.
[/LIST]

---

### Post by dribeas on 2008-07-31
> **mssever said:**
> That's what I assumed, but I just tested it, and it isn't necessarily true.


After you have 'exec'ed you are still running the same process, even though the code being run is not the same. The process that init created for bash

```

# From a console, after login
$ ps
  PID TTY          TIME CMD
32447 tty2     00:00:00 bash
32489 tty2     00:00:00 ps
$ exec htop -u dibeas

# From another console
$ ps a | grep htop
32447 tty2     R+     0:00 htop -u dibeas
32614 pts/1    S+     0:00 grep htop

```

As you see, you have loaded a different executable but the process is still the same. In consoles /bin/login is the OS process that gets called and creates your shell:

```

$ ps auxfwww 
...
root     32439  0.0  0.0   2568  1208 tty2     Ss+  00:30   0:00 /bin/login --       
dibeas   32447  0.8  0.0   2364  1208 tty2     S+   00:30   0:01  \_ htop -u dibeas
...
$ sudo gdb /bin/login 32439
...
(gdb) bt
#0  0xb7ef8410 in __kernel_vsyscall ()
#1  0xb7de442d in wait () from /lib/tls/i686/cmov/libc.so.6
#2  0x0804ba16 in ?? ()
#3  0xb7d65450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#4  0x08049d71 in ?? ()
(gdb) 

```

As you see, /bin/login is waiting for its child process (initially bash, after exec htop) to die. Then it will complete and login will be shown for the next user.

   David

---

### Post by hosseinyounesi on 2008-08-01
We found that "Getty" checks out the log in/off events in linux :)
But how to use it ?!!!

---

### Post by hosseinyounesi on 2008-08-01
Really thanks for your answers, but I don't want to sleep for a while (say 0.1 second or ...). I just want to handle an event in a separate thread or process. As I said in last post "Getty" handles the log in/off events, but I don't know how to use it :( Thanks for helping me in this way
Any Event ?

---

### Post by mssever on 2008-08-01
> **hosseinyounesi said:**
> Really thanks for your answers, but I don't want to sleep for a while (say 0.1 second or ...). I just want to handle an event in a separate thread or process. As I said in last post "Getty" handles the log in/off events, but I don't know how to use it :( Thanks for helping me in this way
Any Event ?
Have you read the documentation? I've never used getty, so I know less about it than you do.

---

### Post by hosseinyounesi on 2008-08-02
Hi, No I haven't. Reading documentation of sth is different than you can programming with it !!!

---

### Post by mssever on 2008-08-02
> **hosseinyounesi said:**
> Hi, No I haven't. Reading documentation of sth is different than you can programming with it !!!
You basically have two options: Read documentation, or read code. If someone tells you how to use something, that's the same category as reading documentation. And if you aren't willing to read the docs, it's less likely that people who can help you will.

---

### Post by hosseinyounesi on 2008-08-02
Ok, I'll report here if I could fine something useful :KS

---

