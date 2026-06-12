---
title: "help: bash script to start a process and stop it (not another instance)"
date: 2007-08-20
forum: Programming Talk
---

### Post by frafu on 2007-08-20
Hello, 

I want to write a script that starts a process and later kills it again. In other words, I call a script to start the process; later I call it again to stop the process. 

How can I make sure to kill the process that I started and not another instance of that process?

I thought about getting the pid of the started process and storing it into a file. When the script is called again, it reads the file to get the pid of the process to kill. 

Or is there a better standard way to do it and that does not involve creating a file? 

Thanks in advance.

---

### Post by duff on 2007-08-20
You've got the right idea.  That's what all those *.pid files in /var/run are for.

---

### Post by frafu on 2007-08-20
Thanks for the confirmation. 

I did not know about the /var/run directory. But the process that I am starting is not listed in that directory. Is it because it is a program written in python?

Francesco

---

### Post by Mr. C. on 2007-08-20
It won't be there unless you put it there.  Your program needs to get its own PID, and create a file in /var/run so that it can later interrogate that file.  The file is up to you to create.

If you want only one instance of your program running, your program should refuse to run when another instance is running.  There are various techniques for doing this.

If you want multiple instances to run, you'll have to specify to your start/stop script the PID or some unique instance ID you create and use.

MrC

---

### Post by frafu on 2007-08-22
Thanks for your reply. 

In fact, there might be other instances of the program I am starting; but later, I want to kill the instance that I created. 

Could you please tell me how I can get the pid of the instance of the program that I started from a script? I tried the following in the script, but it did not work: 

myProgramInstance=`/usr/bin/program&`

Could you also tell me how to start the program so that the script can end, but program keeps on running? The & after the programcall does not seem to work. 

Thanks in advance for any additional help. 

Francesco

---

### Post by cwaldbieser on 2007-08-22
> **frafu said:**
> Thanks for your reply. 

In fact, there might be other instances of the program I am starting; but later, I want to kill the instance that I created. 

Could you please tell me how I can get the pid of the instance of the program that I started from a script? I tried the following in the script, but it did not work: 

myProgramInstance=`/usr/bin/program&`

Could you also tell me how to start the program so that the script can end, but program keeps on running? The & after the programcall does not seem to work. 

Thanks in advance for any additional help. 

Francesco

The variable "$!" has the PID of the last background process you started.  So:
```

#!/bin/bash

PROGRAM=/path/to/myprog
$PROGRAM &
PID=$!
echo $PID > /path/to/pid/file.pid

```
The pid of the background process is now stored in "/path/to/pid/file.pid".  You can later retrieve the PID from this file and kill your process.

The only complication is that if you allow multiple instances of your program to run, you need a way to save all the PIDs in different files and then determine which process you actually mean to kill.

You might want to explain how you plan on running your program a second time decides to kill a particular process.  It seems to me, that without more information (e.g. the sessions are named by the user, only one instance per user) it would be hard to do this.

---

### Post by frafu on 2007-08-26
@ cwaldbieser

Thanks for your help. In fact, it is the script that starts the command and that kills it. 

In order to know what instance of the program to kill,  I also add the display number to the filename. But I don't manage to get the pidfile written.

```
 
#!/bin/sh

fixPartOfFilename="onboard-at-gdmlogin-display-"
displayPartOfFilename=$DISPLAY
extensionOfFilename=".pid"
pathOfFile="/tmp/"

filenameWithPath=$pathOfFile$fixPartOfFilename$displayPartOfFilename$extensionOfFilename

PROGRAM="/usr/bin/onboard --size 400x150 -x 10 -y 10"
$PROGRAM &
PID=$!
echo $PID > $filenameWithPath

``` 

Could anybody please tell me where the mistake is? 
Why does it not create the file? 
I suppose that it is only a problem of syntax. 

Thanks in advance. 

Francesco

---

### Post by Mr. C. on 2007-08-26
It might be creating the file, but not with a name you are expecting.  Try instead:
```

echo $PID > "$filenameWithPath"
```

If this doesn't help, echo the output of each variable as a debugging aid.

I'd also suggest for readability, reducing to something like:

```
basedir="/tmp/"
pidfile="$basedir/onboard-at-gdmlogin-display-${DISPLAY}.pid"

...

echo $PID > "$pidfile"
```

MrC

---

### Post by frafu on 2007-08-26
Thanks, it works now. 

However, there remains one detail: the name of the pidfile ends with a "?" when using the command ls, and "^M", when I do a tab for the autocompletion. 

Could anybody please tell me how I can get rid of the question mark character at the end of the name? 

I am using the following to create the filename: 

```
 
basedir="/tmp"
pidfile="$basedir/onboard-at-gdmlogin-display-${DISPLAY}.pid"

``` 

Thanks 

Francesco

---

### Post by Mr. C. on 2007-08-26
I'm not following you.  Are you saying your script is incorrectly adding the ? character at the end of the file name ?  The script you showed earlier would not be doing that.

Please show your completed script, and the output of ls.

MrC

---

### Post by frafu on 2007-08-26
Here the script:

```

#!/bin/sh


# build the filename and path of the pidfile 
# The pidfile is a file to store pid of onboard started
# during gdmlogin

# basedir="/tmp"
# pidfile="$basedir/onboard-at-gdmlogin-display-${DISPLAY}.pid"
pidfile=/tmp/onboard-at-gdmlogin-display-${DISPLAY}.pid


# if the pidfile does not exists, we start onboard and create the pidfile
# otherwise we kill onboard and remove the pidfile
if [ ! -e "$pidfile" ]
then
	PROGRAM="/usr/bin/onboard --layout /home/frafu/.sok/layouts/deMod.sok --size 400x150 -x 10 -y 10"
	$PROGRAM &
	PID=$!
	echo $PID > "$pidfile"
else
	pid2kill=`cat $pidfile`
	kill -9 $pid2kill
	rm $pidfile
fi


exit 0


```


And here the relevant part of the output of ls -l

```

srwxr-xr-x 1 frafu frafu    0 2007-08-26 21:46 mapping-frafu
srwxr-xr-x 1 root  root     0 2007-08-26 21:51 mapping-root
-rw-r--r-- 1 frafu frafu    5 2007-08-26 22:04 onboard-at-gdmlogin-display-127.0.0.1:1159.0.pid?
drwx------ 2 frafu frafu 4096 2007-08-26 22:04 orbit-frafu


```


During an error it asked me to remove: 
onboard-at-gdmlogin-display-127.0.0.1:1159.0.pid\r

I am using gedit; should I use another editor that also shows formatting characters?

---

### Post by frafu on 2007-08-26
Problem solved; I replaced

pidfile=/tmp/onboard-at-gdmlogin-display-${DISPLAY}.pid

with 

pidfile="/tmp/onboard-at-gdmlogin-display-${DISPLAY}.pid"

Nevertheless, an editor that also shows formatting characters could be useful. 

Thanks for your help. 

Francesco

---

### Post by Mr. C. on 2007-08-26
vi, and then

```
:set list
```

Its not a formatting issue, but a difference between \n, \r, and some editors do not add a final \n character.

MrC

---

### Post by MustNotSleep on 2007-08-27
not completely sure if this is relevant, or if it's what you're looking for, but i use a similar script i found somewhere on the net while looking for Conky info..

it's basically a switch to start or stop a Conky instance.. it's pretty simple..

```
#!/bin/sh

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
exec killall conky
else
exec conky
fi
```
but it works superbly, all in 10 lines of code.. basically, it checks if Conky's running by making sure it's PID is greater than /dev/null, in which case it kills *all* instances of Conky (which is why i'm not sure this would work in your case), or else it starts it.. :D

hope this helps..

---

### Post by frafu on 2007-08-27
Hello, 

Thanks for your help and the script; unfortunately it does not exactly the same as the script that I posted: in fact, in my case it is important to only kill the instead of the process that was created in that session (for example multiple user environment). That is why I also append the $DISPLAY to the pidfile name... 

Have a nice day. 

Francesco

---

### Post by kvineeth on 2008-04-26
hi

i want something similar , but want to run 3 or 4 different process in background and then stop it.

plz could someone suggest

---

