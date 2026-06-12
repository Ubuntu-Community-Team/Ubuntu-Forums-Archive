---
title: "Bash script, redirect output of kill command"
date: 2008-04-10
forum: Programming Talk
---

### Post by artesvida on 2008-04-10
I have a bash script that spawns another process, lets it run for a predetermined amount of time, then kills it.  I'm logging everything that happens, and I find that I can't redirect the output of the kill command.  For example, this line of code:

kill -s SIGTERM $pid >> $LOGFILE

generates nothing in the log file.  However, on the terminal where I started the script, I see that the process was killed.  I thought maybe I need to redirect STDERR as well as STDOUT, so I changed the line to:

kill -s SIGTERM $pid >> $LOGFILE 2>&1

still nothing in the log.  And yes, I still see the output of the kill command on the terminal where I started the script.

Any thoughts?  This isn't a big deal, but it's a bit annoying, and I want to be sure that if the "kill" fails that I see it in the log.

Thank you!!!

---

### Post by ghostdog74 on 2008-04-10
you might want to try an alternative, like checking for the return status equals 0 and if its 0, print your own message to the log.

---

### Post by stroyan on 2008-04-10
The kill command does not report that a process was killed.
I expect you are seeing a message from the shell parent process
of the process that you used kill to send a signal to.
When the process exits its parent process is notified.
A shell process will output a message when a child process
exits because of a fatal signal.  To hide that you need to redirect
the parent shell's stderr.
```

$ sleep 33 &
[1] 7588
$ kill $!
$ 
[1]+  Terminated              sleep 33
$ sleep 34 &
[1] 7594
$ kill -s SIGILL $!
$ 
[1]+  Illegal instruction     sleep 34
$ 

```

---

### Post by dwhitney67 on 2008-04-10
Is there any output?  Or are you perhaps confusing the output from the process that is being killed?

Here's a simple test, where I was _not_ able to generate output:
```
#!/bin/sh

./nonEnding.sh &

pid=`pidof -x ./nonEnding.sh`

`/bin/kill -s SIGTERM $pid`

exit 0
```

For nonEnding.sh (which permissions were set to 744):
```
#!/bin/sh

while [ true ]
do
        sleep 1;
done
```

Anyhow, if you want to dump all output to a file, try:
```
$ cmd 1> file 2> file
```

---

