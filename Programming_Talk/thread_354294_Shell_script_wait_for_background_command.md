---
title: "Shell script wait for background command"
date: 2007-02-05
forum: Programming Talk
---

### Post by rogeriovinhal on 2007-02-05
Hello, I am writing a script, but there is something I need that I can't find a way to do it...

I need to make a command in background "command1 &" and then somewhere in the script I need to wait for it to finish before I do command2.  Basically, I need this:


```

start script
...
command1 &
...
more commands to run parallel to command1
...
wait for command1 to finish
command2
end of the script

```

I've looked a lot of pages, but I couldn't make this simple task to be done. I've seen something about a 'wait' command with the pid process number, but that didn't work also (or I couldn't make it work).

Can anybody help me?

EDIT

Nevermind, I solved it.

To those that may be interested, the problem was that the command1 was a wine call, but it seems that wine calls returns a exit signal even before it stops working, so "wait" didn't wait for it to finish properly. I solved this by executing the 'wine blablabla' command inside a subshell that should return a value at background "$( wine blabla ) &", so now wait really worked.

---

### Post by tonybaqain on 2007-10-19
1. when you run a command in the BG using the **&** notation, it is now in the jobs daemon. so **jobs -l** will display the jobs with information about them, as follows: 

```

jobs -l
[2]-  9647 Running                 ping 192.168.11.27 >&status &
[3]+  9656 Exit 1                  df -hs &>/dev/null

```

2. the **"wait"** command usage is as follows
```
wait [n]
```
where **n** is the PID to wait for

this example clearifies the usage:

```

.
.
.
*[command]* &
wait_command_pid=`jobs -l | awk '{print $2}'`
.
.
.
wait $wait_command_pid
.
.
.

```

**jobs -l | awk '{print $2}** will print out the pid number only, which is the second delimitted word at the output of the job itself.

---

### Post by tonybaqain on 2007-10-19
futhur more, to be more specific, and to let you use more than one bg command
do the following :

instead of **jobs -l | awk '{print $2}'** use **jobs -l | grep *criteria* | awk '{print $2}'**, but you have to be aware that not to use the same command twice, or even similer commands that cann't be grepped.

---

### Post by tkharris on 2007-10-19
You could do that, or you could do this:

```

tribeca:~ harris$ bash foo.sh ; cat foo.sh 
Pid = 372
#!/bin/bash

echo "Foobar" >/dev/null & EPID=$!
wait $EPID
echo "Pid = $EPID" 
tribeca:~ harris$ 

```

=D
$! contains the PID of the last called process.  :)

---

### Post by komputes on 2008-02-29
```

wait for command1 to finish

```You can also hard-code how long you want the script to wait before going onto the next process by doing

```
command1
sleep 5
command2
```

In this example script, command1 will run, wait 5 seconds, and run command2

---

### Post by ghostdog74 on 2008-02-29
> **tonybaqain said:**
> instead of **jobs -l | awk '{print $2}'** use **jobs -l | grep *criteria* | awk '{print $2}'**, but you have to be aware that not to use the same command twice, or even similer commands that cann't be grepped.

just FYI, grep is redundant
```

jobs -l | awk '/criteria/{print $2}'

```

---

