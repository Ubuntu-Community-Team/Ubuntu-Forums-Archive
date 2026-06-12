---
title: "Need to log KILL's - BASH"
date: 2008-04-11
forum: Programming Talk
---

### Post by RudolfMDLT on 2008-04-11
HI there!

I'm damn desperate! :)

I've written a project for varsity, and now, as a bonus, I want to say how successful it is. I've set the application to output 3 comma separated values, and written a BASH script to log them by running the application in a for loop. 

My app however sometimes goes into an infinite loop(which is okay :) ), and then I need to kill it, in order to continue the logging of data. The killing part also works fine. 

I just can't log the kills or the "not-kills".

The code looks like this:

> for i in $(seq 1 1000000); do ./exampleRover >> MasterLog.txt & pid= ps -ef | grep "exampleRover" | awk '{print $2}' ;sleep 2; kill -0 $! && kill $!|grep such >> killlog.txt ; done



I just have NO idea how to output the result of the kill. I have searched google! ;) thats how I got this thing written in the first place, but no where do I find(something I can remotely understand), a way to capture the output of kill.


My current output looks like this:

> 18986
./stat1.sh: line 3: kill: (18984) - No such process
18992
18994
./stat1.sh: line 3: kill: (18992) - No such process
19001
./stat1.sh: line 3: kill: (18999) - No such process
19006
19008
./stat1.sh: line 3: kill: (19006) - No such process
19012
./stat1.sh: line 3: kill: (19012) - No such process
19021
./stat1.sh: line 3: kill: (19021) - No such process
19027



even if I could just log the "No such process", I could still count them later. But no matter what I try, I can't do it! I've tried different variations of tee and grep, but no results!

I would REALLY be greatful if anybody could help me! 

Thanks,

Rudolf

---

### Post by ghostdog74 on 2008-04-11
a successful kill will result in 0. you can catch this 0 and log to file using $? with you own message, eg echo  "Process $pid killed "  >> logfile.txt
you can redirect kill errors using 2>logfile.txt .

A recent [thread]("http://ubuntuforums.org/showthread.php?t=751648") on this

---

### Post by RudolfMDLT on 2008-04-11
Thanks man! :)

---

