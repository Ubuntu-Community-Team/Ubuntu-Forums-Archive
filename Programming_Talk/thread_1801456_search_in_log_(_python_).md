---
title: "search in log ( python )"
date: 2011-07-10
forum: Programming Talk
---

### Post by kyosa on 2011-07-10
I is making a script that's do a search for a string in a log file. This help me to see when often my application is restarted. 
---------System information-------
Python=2.7.1
Ubuntu
----------------------------------------
I have made this:
[PHP]
for line in open("NannyStatus.log"):
 if "User operation - start all services" in line:
   print line
[/PHP]the problem now is that I want to do a check for the last 7 days and count it (if it's been restarted 5 times the last week) and print it out.
the log file is showing this informations:
[PHP]
2009-03-06 18:20:26,423  User operation - start all services 
2009-03-06 18:20:26,470  message_broker           STOPPED 
2009-03-06 18:20:26,470  message_broker           LAUNCHED 
2009-03-06 18:20:41,861  message_broker           STARTING 
2009-03-06 18:20:46,861  message_broker           STARTED 
2009-03-06 18:20:51,471  mercuryAS                STOPPED 
2009-03-06 18:20:51,471  mercuryAS                LAUNCHED 
2009-03-06 18:20:58,658  mercuryAS                STARTING 
2009-03-06 18:23:38,773  mercuryAS                STARTED 
2009-03-06 18:23:41,492  tmu                      STOPPED 
2009-03-06 18:23:41,492  tmu                      LAUNCHED 
2009-03-06 18:23:48,726  tmu                      STARTING 
2009-03-06 18:23:53,726  tmu                      STARTED 
2009-03-06 18:23:56,492  db_loader                STOPPED 
2009-03-06 18:23:56,492  db_loader                LAUNCHED 
2009-03-06 18:24:03,727  db_loader                STARTING 
2009-03-06 18:24:08,727  db_loader                STARTED 
2009-03-06 18:24:11,493  wde                      STOPPED 
2009-03-06 18:24:11,493  wde                      LAUNCHED 
2009-03-06 18:24:18,727  wde                      STARTING 
2009-03-06 18:24:23,727  wde                      STARTED 
2009-03-06 18:24:26,493  schedulergw              STOPPED 
2009-03-06 18:24:26,493  schedulergw              LAUNCHED 
2009-03-06 18:24:33,743  schedulergw              STARTING 
2009-03-06 18:24:38,743  schedulergw              STARTED 
2009-03-06 18:24:41,494  ldap                     STOPPED 
2009-03-06 18:24:41,509  ldap                     LAUNCHED 
2009-03-06 18:24:48,759  ldap                     STARTING 
2009-03-06 18:24:53,760  ldap                     STARTED 
2009-03-06 18:24:56,510  webserverGuard           STOPPED 
2009-03-06 18:24:56,510  webserverGuard           LAUNCHED 
2009-03-06 18:25:03,760  webserverGuard           STARTING 
2009-03-06 18:25:08,760  webserverGuard           STARTED 
2009-03-07 12:04:28,897  User operation - stop nanny 
2009-03-07 12:04:34,491  webserverGuard           STOPPING 
2009-03-07 12:04:34,553  webserverGuard           STOPPED 
2009-03-07 12:04:39,491  ldap                     STOPPING 
2009-03-07 12:04:39,553  ldap                     STOPPED 
2009-03-07 12:04:44,460  wde                      STOPPING 
2009-03-07 12:04:48,507  wde                      STOPPED 
2009-03-07 12:04:49,476  schedulergw              STOPPING 
2009-03-07 12:04:49,522  schedulergw              STOPPED 
2009-03-07 12:04:54,460  db_loader                STOPPING 
2009-03-07 12:04:55,351  db_loader                STOPPED 
2009-03-07 12:04:59,460  tmu                      STOPPING 
2009-03-07 12:04:59,507  tmu                      STOPPED 
2009-03-07 12:04:59,554  mercuryAS                STOPPING 
2009-03-07 12:05:18,055  mercuryAS                STOPPED 
2009-03-07 12:05:22,633  message_broker           STOPPING 
2009-03-07 12:05:27,555  message_broker           STOPPED 
2009-03-07 12:06:39,698  User operation - start nanny 
2009-03-07 12:06:39,698  User operation - start all services
[/PHP]

---

### Post by MadCow108 on 2011-07-10
have a look at the time functions:
[http://docs.python.org/library/datetime.html](http://docs.python.org/library/datetime.html)
e.g.
```

import datetime, dateutil.parser
count = 0
time = datetime.datetime.now() - datetime.timedelta(7)
for line in open("NannyStatus.log"):
  if dateutil.parser.parse(line.split()[0]) > time
     count += 1

```

---

### Post by TwoEars on 2011-07-10
Here's what you got to do, assuming the same file format as you've given-

```
GET TODAY'S DATE AND STORE IN date_today
INITIALIZE count AS 0 
FOR line IN REVERSED(file):
    EXTRACT DATE FROM line AND STORE IN line_date
    IF line_date < date_today - 7 DAYS:
        break
    ELSE IF "User operation - start all services" IN line:
        INCREMENT count
        PRINT line


        
PRINT 'TIMES RESTARTED: ' + count
```


Modules for you to look into - 
re (not needed, but good to use)
datetime

---

### Post by slavik on 2011-07-10
gnu binutils are a wonderful thing.

```

#!/bin/sh

OLD=$(date --date="-7 days" +%Y-%m-%d)

cat $@ | while read date rest; do
  if [[ $date -le $OLD ]]; then
    echo $rest;
  fi
done | grep -c 'User operation - start all services'

```

---

