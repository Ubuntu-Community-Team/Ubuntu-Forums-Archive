---
title: "TIP: Controlling priorities with ionice, nice"
date: 2006-12-22
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2006-12-22
This might be really old news to our seasoned veterans, but for the newer users, this information can be very useful to maintaining a responsive system, particularly with older and single-core hardware:

**Introduction**
The schedulers are responsible for deciding what programs get to use system resources at what time, a critical task for multitasking. For the most part, the Linux scheduling algorithms work superbly with no manual interaction. However, there are some extreme circumstances where your system responsiveness can benefit from some human control :)

**CPU nice**
niceness is the UNIX term for what you may know as priorities. A niceness value is an integer ranging from -20 to 19. -20 is the highest scheduling priority, while 0 is default and 19 is the lowest. (If this is difficult to remember, think of the number as a measure of how 'nice' the process will be to the rest of the system. A high-priority process is less 'nice' than a low-priority process)

Now, a quick talk of permissions: You may lower the priority (increase the niceness) of any processes you own, but once you do that you may **NOT** bring the priority back up again. The root (sudo) user is allowed to change priorities in any way he wants.

To start a process with very low priority, use a command like:
```

nice -n 19 ridiculous_video_encode_job

```

If you want to increase priority instead, it's better to first launch the command THEN re-nice it, since you probably dont' want to be running the command as root.

Your first task is to find the Process ID (PID) of the process you want to change. This can be done using GNOME System Monitor, *ps aux*, *top*, and other tools too.

Then, issue something like:
```

renice  -10 12345

```

Note the difference in syntax between nice and renice! In case you get confused, you can always refer to the man pages.

*For more info about nice/renice, see:* [http://www.linux.com/article.pl?sid=06/11/22/1823236](http://www.linux.com/article.pl?sid=06/11/22/1823236)


**IO Nice**
*NOTE*: **Edgy users only!**

Note that the above niceness only controls how CPU time is allotted. It doesn't influence disk (IO) resources, so something that uses low CPU and high disk (i.e. copying a bunch of files) can still make your system feel laggy.

Fortunately, since Edgy and the CFQ IO scheduler, it's now possible to set IO niceness. You need **schedutils** installed from universe.

IO niceness is done a bit differently. There are 3 classes:
  * **IDLE**: Only give disk time to this class if nothing else wants disk time.
  * **Best Effort**: (default). Serve these tasks in a fair, round-robin manner.
  * **Realtime**: Give these all the disk access they want before serving anything else.

Both Best Effort and Realtime take an additional optional priority from 0 to 7, 0 being highest priority.

**WARNING**: Read the description for realtime carefully. Realtime IO nice processes will starve the system completely until they are done using the disk. **You can easily make your system nonresponsive for long periods of time!** For example, if you give a 10GB copying job realtime IO nice, NOTHING else will have any disk access time until that job is completely done. **Don't use realtime unless you know what you're doing!**

See: [http://www.die.net/doc/linux/man/man1/ionice.1.html](http://www.die.net/doc/linux/man/man1/ionice.1.html) for info on using ionice. That manpage describes it so well I'd rather not paraphrase it :)

Note that IO niceness only has effect if you are using the CFQ io scheduler (default in Edgy). If you have an elevator= (as, deadline,noop) line in your menu.lst, IO niceness will have no effect.


So, armed with this information, you can do a full system backup, extract a large 10GB archive, search your hard drive for that long-lost document, all while watching a high-bitrate high-def movie without missing a frame :)

enjoy!

---

### Post by charles_elwood on 2007-12-01
Is there a way to allow a regular user to run a command as IDLEPRIO, eg 
```

ionice -c3 mv some/big/file somewhere/else/
```

---

### Post by jdong on 2007-12-01
No, there isn't. Someone once tried to explain to me why giving a regular user IDLEPRIO ability would be a security flaw, but I couldn't  comprehend the argument due to my lack of technical knowledge in this field.

---

