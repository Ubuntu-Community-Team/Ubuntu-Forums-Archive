---
title: "Elapsed process time in bash script"
date: 2009-08-19
forum: Programming Talk
---

### Post by DBQ on 2009-08-19
Hi everybody. I am trying to write a bash script which does the following: retrieves the time that has elapsed since the process named xxx was launched, if the process was running for longer then the specified time, terminate it.  My problem is that I cannot seem to find a way to get the elapsed time in a script. I tried ps, but its timing information does not seem to be updated - every-time I run it , it shows the same time. It changes only after a while.

Help is much appreciated!

---

### Post by DaithiF on 2009-08-19
I think you're looking for the etime output parameter:
ps -p yourprocessid -o etime=

```
ps -p 5846 -o etime=
```
   08:13:12

after 24 hours elapses, it rolls over into a format like:
1-00:23:51

where 1- indicates the # of days.

so you'll have some work to do to parse these into seconds, or minutes, or whatever you want to use to compare elapsed time with your threshold

---

### Post by DBQ on 2009-08-19
What if I only know the process name and not ID?

---

### Post by DaithiF on 2009-08-19
You could grep for the process by name first, and extract the id from that

for example:
```
myid=$(ps -ef | grep myprocessname | awk '{print $2}')
echo $myid
```

then
```
ps -p $myid etc...
```

[ just a caveat -- i'm @ work using cygwin ps which is different to the one in Ubuntu, so I can't say for sure that the process id will be in field 2 for you -- adjust $2 in the awk statement if you need ]

---

