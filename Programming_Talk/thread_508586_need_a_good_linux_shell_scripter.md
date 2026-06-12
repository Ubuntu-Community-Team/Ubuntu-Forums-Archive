---
title: "need a good linux shell scripter"
date: 2007-07-24
forum: Programming Talk
---

### Post by Wall86 on 2007-07-24
this is for a WoW mangos server.

```
#!/bin/bash
monitorMangos () {
if test "$mangosIntCpu" -gt "98"
then
        sleep 10s
        mangosCpu=`top -b -n 1 -p $mangosPid | awk '($12 ~ /americas-worldd /) { print $9 }'`
        mangosIntCpu=${mangosCpu%.*}
        if test "$mangosIntCpu" == ""
        then
                mangosIntCpu="0"
        fi
        if test "$mangosIntCpu" -gt "98"
        then
                sudo kill -9 $mangosPid
                echo "Killed MaNGOS for exceeding it's cpu limit."
                echo `date` ", Killed MaNGOS for $mangosIntCpu% CPU Usage for more then 10s." >> /opt/mangos/run/americas/logs/crash.log
        else
                echo `date` ", MaNGOS CPU Usage warning." >> /opt/mangos/run/americas/logs/crash.log
        fi
elif test "$mangosIntCpu" -eq "0"
then
        mangosTelnet=`(sleep 2; echo 'USER lskdn2j8enjoi23en0'; sleep 2 ) | telnet localhost 3444 2>&1 | grep "No such user"`
        if test "$mangosTelnet" != "-No such user."
        then
                mangosTelnet=`(sleep 2; echo 'USER lskdn2j8enjoi23en0'; sleep 2 ) | telnet localhost 3444 2>&1 | grep "No such user"`
                if test "$mangosTelnet" != "-No such user."
                then
#                       sudo kill -9 $mangosPid
                        echo `date` ", Warned MaNGOS for locking up - failing user login test" >> /opt/mangos/run/americas/logs/crash.log
                        echo `date` ", Warned MaNGOS for locking up - failing user login test"
                        sleep 15s
                fi
        else
                echo `date` ", MaNGOS Passes the cpu test."
                sleep 10s
        fi
else
        echo `date` ", MaNGOS Passes the cpu test."
        sleep 10s

fi
}
monitorMangosPid=$$
while :
do
mangosTelnet="no"
mangosPassed="no"
mangosPid=`ps ax | awk '($5 ~ /americas-worldd /) { print $1 }'`
if test "$mangosPid" == ""
then
        mangosPid="0"
fi
mangosCpu=`top b -n 1 -p $mangosPid | awk '($12 ~ /americas-worldd /) { print $9 }'`
mangosIntCpu=${mangosCpu%.*}
if test "$mangosIntCpu" == ""
then
        mangosIntCpu="0"
fi
monitorMangos ; wait
done


```

This script needs to be updated so that it will actually terminate the process if it is using 100% CPU for more than 60 seconds. Can someone help?

---

### Post by Mr. C. on 2007-07-24
There are no statistics in a process structure that you can use to do what you want.

By definition, on a single processor system, your script will be running at the very moment you are collecting your statistics, which implies that some other program cannot be running.

Are you trying to automatically kill the process when it appears hung ?

MrC

---

### Post by Wall86 on 2007-07-24
ya, i need the logon server to auto restart itself once the process hangs so it does not need to be manually restarted

---

### Post by Mr. C. on 2007-07-24
I'm afraid you'll have to find some other hang indicator.

You can approximate some notion of hung by exaxmining the proc info for the process.  In /proc/PID/stat, there are statistics, defined in man proc.  These are used by ps and top to provide output, so you can grab them directly by just cat'ing the pseudofile /proc/PID/stat (where PID is the process ID of your program).

You would have to essentially use the values for utime, stime, cutime, and cstime and construct a heuristic that would indicate the process has spent too much time relative to how much time was available by the system.  But this would be very crude at best, as the scheduler tries to give as much time as possible to the process, so long as there isn't anything else to run with a higher priority.  The scheduler will also reduce the priority of an intensive job, so that other jobs will get a chance to run.  This makes determining your "stuck" process difficult.  

This is why the program itself should be responsible for producing some output, or responding to some request.  The distinction between running hard, and running hard doing nothing is difficult.  Windows fails on this miserablly with the Not Responding messages.

Is there some file, or log entries that the game could produce periodically that you could use?  Eg. no log entry after 60 seconds...

MrC

---

