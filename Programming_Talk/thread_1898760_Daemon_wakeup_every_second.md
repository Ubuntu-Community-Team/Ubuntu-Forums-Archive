---
title: "Daemon wakeup every second"
date: 2011-12-22
forum: Programming Talk
---

### Post by Cool Javelin on 2011-12-22
I am writing a daemon (my first) and it needs to wake up every second and check a special piece of hardware. I have it checking the hardware, but how do I make it sleep, then wake on a specific second.

I'd like to attach to the clock somehow and wake up using some kind of interrupt. Polling is out of the question as I don't want to spend the computer resources when idle.

Thanks, Mark

Pascal
Ubuntu Server 10.10
No OOP

---

### Post by slavik on 2011-12-22
sigalarm

---

### Post by Cool Javelin on 2012-01-05
Thanks, slavik:

I have been looking into the functions SigAlarm, Alarm, Pause and NanoSleep.

These are all functions in Pascal (Free Pascal) I assume there are similar counterparts in C as well.

All these functions seem to be relative meaning for Alarm, SigAlarm and Pause, the system will sleep for a second (or a number of seconds.)

The problem with that is there will be a cumulative error as some time will be taken up for the processing I need to do. 

So, sixty 1 second sleep periods will be longer then one minute.

Is there another method of handling this?
-----
I considered resetting this error by polling on the 59th second till I get 0 seconds and 0 milliseconds, but that is kind of a headache.

NanoSleep allows sleep periods less then 1 second, so I guess I could get the current time, then subtract out the distance till the next second and sleep for a few milliseconds

It would be easier if I could wake on second number n for example.

---

### Post by slavik on 2012-01-05
no ... read here: [http://www.gnu.org/software/libc/manual/html_node/Setting-an-Alarm.html](http://www.gnu.org/software/libc/manual/html_node/Setting-an-Alarm.html)

---

### Post by Cool Javelin on 2012-01-07
OK, well, here's the solution I came up with. A bit of a pain, but...

First, when I am ready to wait for the next second, I get the current MilliSecond. This is the finest resolution I can get from the system.

Then, I subtract that from 1000 (1000 Ms per second) minus the current Ms equals the number of Ms I need to wait.

Then multiply that by 1 million (to convert to NanoSeconds)

Then use NanoSleep(blah,blah).

This seems to work.

Thanks for you help.

Mark.

PS, I compared the CPU usage (with top) between this method and one that simply polls waiting for the next second to arrive, and the polling version uses 98% CPU, and this uses 0.3%. This is the way.

---

