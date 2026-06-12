---
title: "Kill Tasks from Shell"
date: 2011-06-02
forum: Programming Talk
---

### Post by McLeodUA on 2011-06-02
Hi, dear all!

I have a task to solve, I just don't getting how to implement this.:confused:

I need to:
1) List processes with a template like
```
ps ax | grep apache
```
2) Filter processes list to match any kind that works more than 1 hour
3) Kill result list

---

### Post by Lampi on 2011-06-02
check out the manpage of killall:

> 
killall - kill processes by name

       -o, --older-than
              Match only processes that are older (started before) the time specified.  The time is specified  as  a  float  then  a
              unit. The units are s,m,h,d,w,M,y for seconds, minutes, hours, days, weeks, Months and years respectively.

       -y, --younger-than
              Match only processes that are older (started after) the time specified.  The time is specified as a float then a unit.
              The units are s,m,h,d,w,M,y for seconds, minutes, hours, days, weeks, Months and years respectively.

---

### Post by Petrolea on 2011-06-02
I wrote a simple script for you. It greps apache processes, checks if they are running for more than 1 hour, and kills those by getting their PID. 
```

var=`ps ax | grep apache | awk '{print $1 " "  $4}' | tr -d ":" | awk '{if($2 / 100 >= 1) print $1}'`
echo $var
`kill $var`

```

Save this in a file and name it something.sh. Then chmod it ('chmod 777 something.sh') and run it with './something.sh'.

I hope my script is good, not sure if I've done it all correctly. I guess those numbers are time, I think the first number before ':' is hour, if that is correct the script should be fine. Also the first number (something like 1876) I think is process ID so that should be good too.

---

### Post by McLeodUA on 2011-06-22
Thanks a lot!

---

### Post by dwhitney67 on 2011-06-22
Never chmod a file to 777.  That's simply asking for trouble; you would opening the file for anyone on the system to edit, perhaps to replace your commands.

Also, when grepping the results from ps, exclude the grep.  For example:
```

ps ax | grep apache | grep -v grep

```
Also be aware that the command above will also list tomcat; I'm not sure if it is desirable to perform the similar action with tomcat as you are planning to do with apache.  It is perhaps better to grep for **apache2** or **/usr/sbin/apache2**.

---

