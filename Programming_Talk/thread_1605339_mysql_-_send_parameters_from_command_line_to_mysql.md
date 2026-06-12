---
title: "mysql - send parameters from command line to mysql routine"
date: 2010-10-25
forum: Programming Talk
---

### Post by ndefontenay on 2010-10-25
Hi.

I had this problem recently and I thought I should share it since it's useful.

The problem is as follow:

I got a routine that takes 2 dates to extract a bunch of data from mysql into a text file.

It can be called like this from mysql:
call myextract('2010/10/24','2010/10/25');

Problem is: Those dates will change every day and the command line mysql doesn't take variable. So how then?

I create a script that will generate my variables as such:

```
vim genparam.sh

rm -f /home/dw/scripts/param.sql

today=$(date '+%Y/%m/%d');
yesterday=$(date --date="1 days ago" '+%Y/%m/%d');
cd /home/dw/scripts
echo "set @startdate='$yesterday'; set @enddate='$today';" > param.sql;

exit
```

Another script got the command to call in a sql file:

```
vim callroutine.sql
call dwgetactivity(@startdate,@enddate);
```

Then all that's left to do is:
cat param.sql callroutine.sql | mysql -u[username] -p[password]

What mysql will see is the following:
set @startdate='2010/10/24';set@enddate='2010/10/25';call dwgetactivity(@startdate,@enddate);

Then it's easy to schedule it with a crontab and have data extracted daily.

---

### Post by DaithiF on 2010-10-25
why not:
```
today=$(date '+%Y/%m/%d');
yesterday=$(date --date="1 days ago" '+%Y/%m/%d');

mysql -u[username] -p[password] -e "call dwactivity('$yesterday', '$today')"
```

---

### Post by ndefontenay on 2010-10-25
Well that would avoid all the pain I've been through.
I've looked all around the web and the best solution I heard about was the way I've done it.

I'll try that tomorrow.

Thanks for the tip :)

---

