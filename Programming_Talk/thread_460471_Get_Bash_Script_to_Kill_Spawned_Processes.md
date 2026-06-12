---
title: "Get Bash Script to Kill Spawned Processes"
date: 2007-05-31
forum: Programming Talk
---

### Post by ruscoe on 2007-05-31
Is there any way I can get a bash script to spawn a process, sleep for x amount of time, then kill the process?

I want to use a script to spawn a process that would normally run indefinitely until I Ctrl+C it and have the script kill it, but so far I cannot get anything to happen past the process starting.

---

### Post by seamless on 2007-05-31
$! will has the pid of the last spawned process. Start your process in the backgroud using & if necessary. Then save $! somewhere. Use sleep <time> to sleep for a bit. Then use kill -15 <pid of spawned process>.

---

### Post by thomasaaron on 2007-05-31
pkill offers some possibilities.

If your process is named myProcess, you might use:
pkill -f myProcess
to find and kill it.

For more info, check out:
man pkill

---

### Post by ruscoe on 2007-05-31
Brilliant, guys. I started the process with an & and used pkill to kill it after 3 seconds.

It works great. Thank you.

---

### Post by youarefunny on 2010-03-09
When opening a terminal with this process i get error
"No such process"

It appears that the terminal changes its pid or something

---

### Post by derrick81787 on 2010-03-11
> **ruscoe said:**
> Is there any way I can get a bash script to spawn a process, sleep for x amount of time, then kill the process?

I want to use a script to spawn a process that would normally run indefinitely until I Ctrl+C it and have the script kill it, but so far I cannot get anything to happen past the process starting.

This sounds almost exactly like another question I answered the other day.  Take a look at [this post]("http://ubuntuforums.org/showpost.php?p=8886146&postcount=5").

Just change **thunar /media/local** to whatever your command is, but keep the &.  Obviously, don't run the mount command either.

- Derrick

---

### Post by youarefunny on 2010-03-11
> **derrick81787 said:**
> This sounds almost exactly like another question I answered the other day.  Take a look at [this post]("http://ubuntuforums.org/showpost.php?p=8886146&postcount=5").

Just change **thunar /media/local** to whatever your command is, but keep the &.  Obviously, don't run the mount command either.

- Derrick

But sometimes you get a "No such process" error.

as if the terminal changed it's PID

---

### Post by soltanis on 2010-03-12
Are you saving the variable somewhere else so that it has the right PID even if the $! variable changes?

If you are but it's still not working I would use pkill or this method:
```

ps -e | grep <process name> | awk '{print $1;}' | xargs kill -INT

```

Works every time for me when Firefox get's cranky. Just kill -9 it and everything's good.

---

