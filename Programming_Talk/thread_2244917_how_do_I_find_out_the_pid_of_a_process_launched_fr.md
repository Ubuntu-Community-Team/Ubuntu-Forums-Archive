---
title: "how do I find out the pid of a process launched from a script?"
date: 2014-09-19
forum: Programming Talk
---

### Post by IAMTubby on 2014-09-19
Hello,
 Assuming I have a line in a script which launches [http://ubuntuforums.org/](http://ubuntuforums.org/) using chrome's command-line tool, chromium-browser using _chromium-browser [http://ubuntuforums.org/](http://ubuntuforums.org/)_. How do I find out the process id of that particular instance. I tried doing the naive way of recording all the process ids of chromium-browser before and after using the command line tool and then finding the diff between the two(this can be seen in the script below), but even that doesn't seem to work. Is there a better way? 

```
ps -aux | grep 'chromium-browser' > log1.txt
**chromium-browser http://ubuntuforums.org/**
ps -aux | grep 'chromium-browser' > log2.txt
diff log1.txt log2.txt

```

Thanks.

---

### Post by Vaphell on 2014-09-19
if you run stuff in the background you get pid for free with $!

that said i don't think it's a viable approach in case of chromium. It seems to spawn and manage processes on its own and the pid returned has no reflection in actual ps output.

---

### Post by IAMTubby on 2014-09-20
> **Vaphell said:**
> if you run stuff in the background you get pid for free with $!

that said i don't think it's a viable approach in case of chromium. It seems to spawn and manage processes on its own and the pid returned has no reflection in actual ps output.
Thanks vaphell.

No, I'm not running in the background this time. I want to store the pid of the process launched from a shell script in a variable inside the script, so I can kill it from the script at a later point in time, maybe after a time interval or something. How do I go about this?

---

### Post by tgalati4 on 2014-09-20
Because *google-chrome* spins off threads for each tab, I don't know of an easy way to kill a specific tab.  You would have to use the *killall* command:

```
sudo killall google-chrome
```

There may be some switches on *killall* that you can use to tailor its behavior, but otherwise it seems to be an all-or-nothing process.

Your Use Case seems to point to *chroot* with a specific user or group.  That way you can simply kill all processes running in that *chroot*.  You can set limits for that user based on CPU, time, etc and when reached, boom.

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

Using pam_time to limit time for a specific user:

[http://askubuntu.com/questions/68918/how-do-i-restrict-my-kids-computing-time](http://askubuntu.com/questions/68918/how-do-i-restrict-my-kids-computing-time)

[http://askubuntu.com/questions/183530/how-to-lock-yourself-out-of-the-primary-account-temporarily](http://askubuntu.com/questions/183530/how-to-lock-yourself-out-of-the-primary-account-temporarily)

```
man time.conf
```

---

### Post by Vaphell on 2014-09-20
> No, I'm not running in the background this time. I want to store the pid of the process launched from a shell script in a variable inside the script, so I can kill it from the script at a later point in time, maybe after a time interval or something. How do I go about this? 


you may think so but in practice depending on the circumstances you often do.
- if chromium doesnt run, your process will be the chromium process and it will block the flow of the script, so you'll never reach ps #2 as long as your process exists. Pid is irrelevant because you never get to use it in time.
- if chromium exists already, your process passes relevant info to the master process and dies asap without blocking the script which is pretty much 'in the background' and the pid of your process is again useless.

like tgalati4 said, chromium doesn't work in a unixy way that exposes pids and stuff. The master process manages stuff on its own. You never get direct access to processes.
Chromium shows all processes in its Tools > Task manager but i don't think that information is exposed via cli.

your 'hack' could be replaced by this
```
pgrep -n chromium
```
it should return pid of the newest process


if the thing is supposed to be rock solid, i'd look at that chroot approach

---

