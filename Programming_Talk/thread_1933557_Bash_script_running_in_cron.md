---
title: "Bash script running in cron"
date: 2012-02-29
forum: Programming Talk
---

### Post by powertower on 2012-02-29
I have a script with the following lines
current_temp=70
date=`date`
echo $date,$current_temp >> log.csv

Its running in my crontab every 15 minutes along with some other code but I cannot get the above lines to append data to log.csv. Do I have a syntax error? If I run it manually everything is fine....

---

### Post by Khayyam on 2012-02-29
> **powertower said:**
> I have a script with the following lines
current_temp=70
date=`date`
echo $date,$current_temp >> log.csv

Its running in my crontab every 15 minutes along with some other code but I cannot get the above lines to append data to log.csv. Do I have a syntax error? If I run it manually everything is fine.

I can't say exactly but you should make it a habit of 'bracing' your variables, and not using (depreciated) backticks. Also, where is crons ${PWD}? .... use a path to a log.csv

```
#!/bin/bash

CURRENT_TEMP="70"
DATE=$(date)
echo ${DATE},${CURRENT_TEMP} >> /path/to/log.csv
```HTH ... khay

---

### Post by powertower on 2012-02-29
> **Khayyam said:**
> I can't say exactly but you should make it a habit of 'bracing' your variables, and not using (depreciated) backticks. Also, where is crons ${PWD}? .... use a path to a log.csv

```
#!/bin/bash

CURRENT_TEMP="70"
DATE=$(date)
echo ${DATE},${CURRENT_TEMP} >> /path/to/log.csv
```HTH ... khay

Reading your comment made everything come together. It was not storing the log.csv in my working directory, I need to specify the full log path...Thanks for the help.

---

### Post by Khayyam on 2012-02-29
> **powertower said:**
> Reading your comment made everything come together. It was not storing the log.csv in my working directory, I need to specify the full log path...Thanks for the help.

Your welcome, I imagined it was the path (or lack thereof) to the logfile that was at issue. You should take the comments re bracing and backticks as a bonus .. heh

You should now [mark this thread as [SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

best ... khay

---

