---
title: "Parallel processes in Bash"
date: 2005-05-02
forum: Programming Talk
---

### Post by Leif on 2005-05-02
Sorry for asking womething which I am sure is quite well documented, but my googling skills keep on returning the same things over and over again. I'm trying to learn how to run about 50 jobs in the most efficient way on a dual-cpu setup. I know you & a process to background it, and wait when you need to synchronize things. My first question is : Is there a way of setting a maximum number of processes a bash script can spawn, so instead of having 10 threads at a time running around, I have two, and when one finishes another one fires up ?

My second question is, how do you create blocks of code and then run them as a single sub-process ? Just ()'s around it ?

---

### Post by mendicant on 2005-05-05
You could do the parallel thing by storing the PIDs you get back, and use wait <PID0> && wait <PID1>.  The gives you at most two semantics.  If you also want at least one (if possible) semantics, then replacing && with || will get you that sometimes (if PID0 finishes first)--this will work fairly well if all the processes take the same amount of time.  You could also poll to see if the processes are done.

For your second question, I believe so. At least the environment variables will think so:
```

% (export BLAH=hello; echo $BLAH; echo $BLAH)
hello
hello
% echo $BLAH

```

---

### Post by Leif on 2005-05-05
Thanks for the help. The ()s work, as you noted. Wait PID wasn't really what I wanted because of the delatys it still causes, so I wrote a little function to check for the spawned processes and run the next when one exits. Bash is fun !

---

### Post by mendicant on 2005-05-05
Yeah--that's the polling solution.  The nice thing about wait is that it 'knows' when the process ends.  One thing you can do is trap SIGCHLD:

```

#!/bin/bash

set -bm

childfinished() {
  echo "childfinished in $0"
}

trap 'childfinished' SIGCHLD

sleep 10 &
sleep 5 &

while [ 1 ]; do
  echo -n ""
done

```

Obviously, the while changes to waiting until you have no more jobs to run, and the childfinished() function starts another job.  Note that you can't start any other processes (just use bash built-ins) in childfinished(), or it'll call childfinished() when it exits, going into an infinite loop.  This will also take all your CPU doing the echo.

A more sensible solution might be to wrap other processes in a script which traps SIGEXIT and notifies some master process (via kill -s SIGHUP, say) and have the master process trap SIGHUP, upon which it starts another process via the wrapper script.

---

### Post by Paru on 2005-11-17
Can you please suggest how you check for the spawned processes and run the next when one exits.
I tried doing wait <PID0> && wait <PID1> but it just looks at the first PID0 and not at the second one

Thanks

---

### Post by Leif on 2005-11-20
the "solution" I found is not very good, but here you go.

you need these two functions :

```

READY=0

function waitproc {
    stat1=$( ps ax | grep $PID1 | grep -v "grep" )
    stat2=$( ps ax | grep $PID2 | grep -v "grep" )
    if [ -z "$stat1" ] # if process1 finished
    then
	READY=1
    elif [ -z "$stat2" ] # if process2 finished
    then
	READY=1
    else
	sleep 1
    fi
}

function newproc {
    stat1=$( ps ax | grep $PID1 | grep -v "grep" )
    if [ -z "$stat1" ] # if process1 finished
    then
	PID1=$!
	READY=0
    else
	PID2=$!
	READY=0
    fi
}

```

initialize PID1 and PID2 with some processes first :

```

echo "Bla" &
PID1=$!
echo "Bla" &
PID2=$!

```

then :

```

  while [ $READY -eq 0 ]; do
    waitproc
  done
 your-proc &
  newproc

```

for each process

---

### Post by Parallel on 2007-09-15
Just got myself a quad-core, and ran into this problem trying to parallelize normalization and encoding from .flac, here is my solution:
```

#!/bin/bash

NUM=0
QUEUE=""

function echoqueue {
	for PID in $QUEUE
	do
		echo -n "$PID "
	done
	echo
}

function queue {
	QUEUE="$QUEUE
$1"
	NUM=$(($NUM+1))
	echo -n "QUEUE ";echoqueue
}

function dequeue {
	OLDDEQUEUE=$QUEUE
	QUEUE=""
	for PID in $OLDDEQUEUE
	do
		if [ ! "$PID" = "$1" ] ; then
			QUEUE="$QUEUE
$PID"
		fi
	done
	NUM=$(($NUM-1))
	echo -n "DEQUEUE ";echoqueue
}

function checkqueue {
	OLDCHQUEUE=$QUEUE
	for PID in $OLDCHQUEUE
	do
		if [ ! -d /proc/$PID ] ; then
			dequeue $PID
		fi
	done
	echo -n "CHECKQUEUE ";echoqueue
}

IFS="
"
for INS in $*
do
	#sleep $(($RANDOM/2000)) &
	
	#COMMAND TO SPAWN
	RF=`echo "$INS" | sed -e 's/.flac$//'`
	sh -c "flac -s -d \"$RF.flac\"
		   ssrc_hp --quiet --normalize \"$RF.wav\" \"$RF-norm.wav\"
		   lame --quiet -b 192 \"$RF-norm.wav\" \"$RF.mp3\"
		   rm \"$RF.wav\" \"$RF-norm.wav\" " &
	#COMMAND TO SPAWN STOP
	
	PID=$!
	queue $PID
	
	while [ $NUM -ge 6 ] # MAX PROCESSES
	do
		checkqueue
		sleep 1
	done
done

```
It spews debug-output right now, feel free to comment those lines.

It would probably be cleaner to use make or something, but i never got it to work correctly.

---

