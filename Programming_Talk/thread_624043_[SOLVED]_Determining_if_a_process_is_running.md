---
title: "[SOLVED] Determining if a process is running"
date: 2007-11-26
forum: Programming Talk
---

### Post by dwhitney67 on 2007-11-26
Is there an easier way to determine if a process is running, other than using the "ps" (process status) command?

A co-worker insists the following script is inefficient and not because of the "sleep" call, but because of the repeated calls to "ps".  I agree with him, thus I am looking for a way to perform the "ps" only once, and use this result through each iteration of the loop.

```
#!/bin/sh

isProcessRunning()
{
  # $1 is process-name to verify if running
  #
  ps -ef | cut -b 49- | grep -e ^.*/$1$ >/dev/null 2>/dev/null
  retval=$?
}


# Main program
#
while true
do
        # DATABASE
        isProcessRunning database
        if [ $retval -ne 0 ]
        then
                /usr/bin/database > /dev/null 2> /dev/null &
        fi

        # ARCHIVER
        #isProcessRunning archiver
        #if [ $retval -ne 0 ]
        #then
        #       /usr/bin/archiver > /dev/null 2> /dev/null &
        #fi

        # HISTOGRAM
        isProcessRunning histogram
        if [ $retval -ne 0 ]
        then
                /usr/bin/histogram > /dev/null 2> /dev/null &
        fi

        # HARDWARED
        isProcessRunning hardwared
        if [ $retval -ne 0 ]
        then
                /usr/bin/hardwared > /dev/null 2> /dev/null &
        fi

        sleep 2
done
```

---

### Post by scorp123 on 2007-11-26
You may want to look into the **pidof** command ...  It returns the PID of a process. Let's suppose I wanted to check if Firefox is running: ```
$ pidof firefox-bin
13549 
``` ... The number there is the PID of my firefox instance. If nothing is returned then the program in question isn't running. This can be also incorporated into a script, e.g. this command: ```
echo $?
``` ... returns the exit code of the last command that was run. So my example with "pidof firefox-bin" gives me a return code of  "0" which means "all OK" whereas e.g. "pidof blahblahcatchme" will give me a return code of "1" which means "not OK".

And of course you could put this into a nice "if ... then" loop, e.g. ```
if [ "$?" -ne "0" ]; then
  echo "Sorry, program xyz is not running it seems!"
  exit 1
fi
``` 

So I suppose your script up there could be shortened and made to look more elegant?

---

### Post by dwhitney67 on 2007-11-26
Thanks for the tidbit.  I will look into whether my non-Ubuntu system supports this.  This command is definitely much more efficient than doing the "ps", followed by a "cut", and then a "grep".

---

### Post by scorp123 on 2007-11-26
> **dwhitney67 said:**
>  I will look into whether my non-Ubuntu system supports this.  This command is definitely much more efficient than doing the "ps", followed by a "cut", and then a "grep". The "pidof" command is pretty much standard on Linux .... but not on commercial UNIX, e.g. Solaris, HP-UX, and so on. So if your script is running on one of those OS'es you'd have to do it the way you did it now with all those tools.

---

### Post by tyoc on 2007-11-26
IIRC, you can do some like *kill -0* or some like that.

---

### Post by scorp123 on 2007-11-26
> **tyoc said:**
> IIRC, you can do some like *kill -0* or some like that.  Taken from the "kill" manual: ```
**SIGNALS**
       The signals listed below may be available for use with kill. 
        When known constant, numbers and  default  behavior are shown.

       Name     Num   Action    Description
       0          0   n/a       exit code indicates if a signal may be sent
....

```

So this would check if a task is still responding (= accepting signals via "kill") .... that's kinda not exactly the same.

---

### Post by PaulFr on 2007-11-27
Just my 0.02: In POSIX systems, > ps -eo comm|grep <command_name>is reasonable (i.e. look at the -o option to ps). On Solaris, **pgrep** has some useful arguments.

---

### Post by dwhitney67 on 2007-11-27
Everyone, thank you for your replies.  I think I will rely on scorp123's suggestion and use the pidof command.  The system I am using, CLFS (cross-compiled linux from scratch) has support for this command.

My script should end up looking something like:

```
#!/bin/sh

while true
do
        # DATABASE
        pidof database >& /dev/null
        if [ $? -ne 0 ]
        then
                /usr/bin/database >& /dev/null &
        fi

        # ARCHIVER
        #pidof archiver >& /dev/null
        #if [ $? -ne 0 ]
        #then
        #       /usr/bin/archiver >& /dev/null &
        #fi

        # HISTOGRAM
        pidof histogram >& /dev/null
        if [ $? -ne 0 ]
        then
                /some/path/not/usr/bin/histogram >& /dev/null &
        fi

        # HARDWARED
        pidof hardwared >& /dev/null
        if [ $? -ne 0 ]
        then
                /usr/bin/hardwared >& /dev/null &
        fi

        sleep 2
done
```

---

### Post by geirha on 2007-11-27
Instead of 
```
pidof database >& /dev/null
if [ $? -ne 0 ]
```
You can simply do
```
if ! pidof database >& /dev/null
```
And since you only run one command in each if, you can make it quite compact with
```
pidof database >& /dev/null || /usr/bin/database >& /dev/null &
``` The command after || will only run if the first command fails (returns non-zero)

---

### Post by scorp123 on 2007-11-27
> **geirha said:**
>  ```
pidof database >& /dev/null || /usr/bin/database >& /dev/null &
``` The command after || will only run if the first command fails (returns non-zero) ... Which is the opposite of ```
command1 && command2
``` So command2 will only execute if command1 before it was successful.

(Just for the sake of completeness)

---

