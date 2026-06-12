---
title: "help to processing the text file content"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by jpjohnj on 2011-09-16
hi ..

i  need to analyse these content...

 PID TTY          TIME CMD
 5159 pts/1    00:00:00 bash
 5833 pts/1    00:00:00 ps


What i need is ... when i need to type "bash" then i need to get "5159"..

Give me some idea to write this in to script...

---

### Post by Lisiano on 2011-09-16
I think you should first read the manual page for ps
```
man ps
``` because usually just typing ps won't give much useful info (Only what is running in the current terminal). If you want everything on the system, including memory usage, cpu usage, where the process is running, what is it's status (Sleeping, I/O, running, etc, when it was started, how long it was running, under what username is it running and what is it's PID then you should use this instead of ps```
ps aux
```
ps aux
```
lisiano@Lisiano-Ubuntu:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  24140  2052 ?        Ss   Sep14   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    Sep14   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Sep14   0:44 [ksoftirqd/0]
root         6  0.0  0.0      0     0 ?        S    Sep14   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    Sep14   0:00 [migration/1]
root         9  0.0  0.0      0     0 ?        S    Sep14   0:19 [ksoftirqd/1]
root        11  0.0  0.0      0     0 ?        S<   Sep14   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S<   Sep14   0:00 [khelper]
... 236 more lines ...
lisiano@Lisiano-Ubuntu:~$ 
```ps ```
lisiano@Lisiano-Ubuntu:~$ ps
  PID TTY          TIME CMD
 3744 pts/0    00:00:00 bash
 3802 pts/0    00:00:00 ps
lisiano@Lisiano-Ubuntu:~$
```
You can also customize to however you want ps to show your data. For example I just want every process pid, I don't care bout the rest.
```
lisiano@Lisiano-Ubuntu:~$ ps ax -o pid=
    1
    2
    3
    6
    7
    9
   11
   12
... 236 more pids ...
lisiano@Lisiano-Ubuntu:~$
```
So instead of trying to parse the data, how about formating it to your needs?
Let's say I just want to find Compiz, I'll first tell ps to list every PID and name, then tell grep to find a line with the word compiz, and finaly, tell another grep to remove grep.
```
lisiano@Lisiano-Ubuntu:~$ ps ax -o pid,cmd | grep compiz | grep -v grep
26806 compiz --replace --sm-disable --ignore-desktop-hints ccp --indirect-rendering
lisiano@Lisiano-Ubuntu:~$ 
```
Okay. Guess I should explain.
ps - the PS command
ax - The A means not just yourself, the X means everything that is not running on a TTY/PTS.
-o - Custom formating
pid,cmd - Format as the following, show pid first then show the cmd.
grep - We use grep to find something in a piece of text. In our case ps
compiz - A cool program but in this case, a string we are looking by using grep.
grep -v grep - Grep again but telling it to look for everything that doesn't have the word grep in it.
And the vertical lines (pipes) | tell the terminal to send whatever the program says on the screen to a program.

Okay for your script... What language are you using? SH, Bash, LUA, etc? Depending on the language itself, different ways to find the data could be used. In LUA for example I can just make LUA trim whitespaces from the start of the string and on the end of the string, then tell LUA to search for any whitespace and on the first one it finds, show everything before the whitespace. Same could be done for SH, Bash but I don't know how to do that in those.

---

### Post by staticd on 2011-09-16
#!/bin/bash
#usage: myscript file processname
cat "$1"|grep "$2"|cut '-f1' '-d '


There must be more beautiful way to do this with awk but I dont know how.

---

### Post by jpjohnj on 2011-09-16
thanks for your help..

i made like this 

#!/bin/bash
echo "Enter the CMD" 
read CMD
ps -o pid,cmd | grep $CMD | grep -v grep | cut -c-5


thank you again...

---

### Post by Lisiano on 2011-09-16
```
#!/bin/bash
echo "Enter the CMD"
read CMD
ps_output=`ps ax -o pid,cmd | grep $CMD | grep -v grep`
echo $ps_output | cut '-f1' '-d '
```
This should work better since if you try looking for a process that was started a while ago, it might have a whitespace and cut will not show anything since you will have a space at the start. This way bash will trim the spaces at the start and let cut work it's magic.
Btw. Might I suggest ```
pidof
``` instead of the script? I understood you want to find the PID only so this could be a way cleaner solution
```
#!/bin/bash
echo "Enter the CMD"
read CMD
pidof $CMD
``` or even simpler
```
lisiano@Lisiano-Ubuntu:~$ pidof compiz
26806
lisiano@Lisiano-Ubuntu:~$ 
```

---

