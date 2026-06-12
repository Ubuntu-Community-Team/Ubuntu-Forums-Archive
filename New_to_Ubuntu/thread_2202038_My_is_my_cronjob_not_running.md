---
title: "My is my cronjob not running?"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by frogwarrior on 2014-01-27
So I added this line to the crontab file:
```
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command
**15 * * * * /home/horse/ss/cronhandler.sh**

```
The way I understand it, this should make crontab run cronhandler.sh every 15 minutes. Heres whats in the cronhandler.sh file:
```
#!/usr/bin/bash
echo "It works" > cronlog.txt

```

so I've been looking out for this cronlog.txt file, but its not appearing. If I run crontab -l, I can still see my entry in there:
```
# 
# For more information see the manual pages of crontab(5) and cron(8)
# 
# m h  dom mon dow   command
15 * * * * /home/horse/ss/cronhandler.sh

```

but it doesn't seem to be doing anything. What am I doing wrong here?

---

### Post by ajgreeny on 2014-01-27
[LIST=1]
[*]It needs to be **#!/bin/bash** in the first line not **#!/usr/bin/bash**, ie, remove the /usr in the pathway.
[*]your crontab would make the cron job run at 15 minutes past every hour, not every 15 minutes.
[*]Is the script executable?
[*]If you want the cronlog.txt to be added to every time the cron job is run, ie add a line each time it runs, you need to use >> for "append to file", not > for "write to file", which will overwrite it each time.
[/LIST]

---

### Post by Dave_L on 2014-01-27
In addition to what ajgreeny said:

It's best to use full paths in a crontab, so specify the full path for cronlog.txt. For example:
```
#!/bin/bash
echo "It works" >>/tmp/cronlog.txt
```

To run the task every 15 minutes:
```
*/15 * * * * /home/horse/ss/cronhandler.sh
```
or
```
0,15,30,45 * * * * /home/horse/ss/cronhandler.sh
```

---

### Post by frogwarrior on 2014-01-28
Thanks for the answers. I changed it to **#!/bin/bash **and I'd forgotten to make the script executable. I only used > cuz I wasnt sure if >> appending would create a new file, but I tested it out there and it does. I still haven't seen this cronlog.txt file created but I changed it to an absolute directory path lave Dave_L suggested. Also, thanks for telling me how to make it run every 15 minutes, that will make testing a whole lot easier. I see there are cron.hourly and cron.daily folders too, so I added a script to each of those to test it out.

EDIT: Changed it to 3 minutes, and just saw the cronlog.txt file with a couple of lines in it. Thanks a lot for the help. This cron thing will definitely make life easier for me.

---

