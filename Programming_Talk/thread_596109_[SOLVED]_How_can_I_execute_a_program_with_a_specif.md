---
title: "[SOLVED] How can I execute a program with a specified max. time (BASH)"
date: 2007-10-29
forum: Programming Talk
---

### Post by hod139 on 2007-10-29
Is there a way to provide a max execution time to a program when I launch it?  Here is what I am doing now
```

## c --> each students' name
## hw  --> name of executable
MAX_NUM_HOURS="2" ## arbitrary upper bound

## time a detached program
/usr/bin/time -f "%E real,%U user,%S sys"  --output="${c}_Time.txt" --append ./${hw} > {c}_output.txt & 
    
#Kill program after running for specified hours
DONE=0
while [ $DONE -eq 0 ]; do
   /bin/sleep 1s # sleep for a second
   elapsedTime=`ps -e | grep ${hw} | awk '{print $3}'`
   if [ -z $elapsedTime ]; then # finished before time limit
      DONE=1             
   else # kill if running too long
      hours=`echo $elapsedTime | cut -d":" -f1`
      if (("$hours" >= "$MAX_NUM_HOURS")); then
         echo "Killing program, running too long"
         /bin/kill `pidof ${hw}` &> /dev/null
         DONE=1 
      fi
   fi
done

```As you see, I run the students' code detached, and start a while loop monitoring the execution, killing their code if it is taking too long.  Is there a better way?

---

### Post by xtacocorex on 2007-10-29
My idea is similar to yours, but instead of using ps to get time, just keep calling /usr/bin/time to get the current time.
 
I have no code for it and this was a quick think in a short break at work.

---

### Post by cwaldbieser on 2007-10-29
How about:

```

/program/to/run/in/background &
CHILD_PID=$!
#Sleep 2 hours (for example).
sleep 2h 
kill -HUP $CHILD_PID

```

---

### Post by hod139 on 2007-10-29
> **cwaldbieser said:**
> How about:<snip>

This is a neat idea, but
1) The program may very well end before the time limit is up, in which case your script will be sleeping for a long time (most likely not a problem).

2) I did not show all the code in my script, but I have many student's submissions that I need to run.  The while loop condition allows me to block the execution of subsequent students while another's submission is running.

Catching the pid of the process is a really good idea though, and will clean up a lot of my while loop code.  Thanks for that.

---

### Post by cwaldbieser on 2007-10-29
> **hod139 said:**
> This is a neat idea, but
1) The program may very well end before the time limit is up, in which case your script will be sleeping for a long time (most likely not a problem).

2) I did not show all the code in my script, but I have many student's submissions that I need to run.  The while loop condition allows me to block the execution of subsequent students while another's submission is running.

Catching the pid of the process is a really good idea though, and will clean up a lot of my while loop code.  Thanks for that.

You could do something like:
```

#! /bin/bash

MAX_TIME=1m
for CHILD in list of progs to run; do
    $CHILD &
    CHILD_PID=$!
    bash -c "sleep $MAX_TIME; kill -HUP $CHILD_PID" &
    wait $CHILD_PID
done

```

Here you run the child in the background, but you'll wait for it (so you don't move onto the next program until it is done).  You also spawn another background process that will wait for some amount of time and then signal the child to quit.

You might end up with a bunch of processes waiting to kill non-existant other processes if all your student's programs run quickly, though.  There might also be some problems if your students are trapping signals.

---

### Post by hecato on 2007-10-29
also you can pass *kill -0 PID (for ask the state of the program)* or some like that , go to #bash XD, they will send you to the FAQ taht they have (a very nice source of info on bash). O ya, I have the link here: [http://wooledge.org/mywiki/BashFAQ](http://wooledge.org/mywiki/BashFAQ)

---

### Post by aks44 on 2007-10-29
> **hecato said:**
> [http://wooledge.org/mywiki/BashFAQ](http://wooledge.org/mywiki/BashFAQ)

This FAQ is a killer. Thanks for the link!

---

### Post by hod139 on 2007-10-29
> **hecato said:**
> also you can pass kill 0 or some like that, go to #bash XD, they will send you to the FAQ taht they have (a very nice source of info on bash). O ya, I have the link here: [http://wooledge.org/mywiki/BashFAQ](http://wooledge.org/mywiki/BashFAQ)
Awesome, thanks.  FAQ 68 answers my question!  That is a great link.

---

