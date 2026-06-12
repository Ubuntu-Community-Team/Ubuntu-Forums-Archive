---
title: "Logger for postfix"
date: 2009-10-11
forum: Programming Talk
---

### Post by januzi on 2009-10-11
Hi

I'm looking for the logging script (python, perl, php, etc) that would grep mail.log and put data into the mysql database. I checked all links at the postfix addons in the "log" section and I didn't found anything that would fit my needs. I need something that would work like the authsmpt log viewer:
> 
Emails: sent

Date | Email id | From | To | Reply
xxx | xxx | xxx | xxx | x.x.x OK

Page: 1 2 3 4 5
> 
Emails: error

Date | Email id | From | To | Reply
xxx | xxx | xxx | xxx | x.x.x Connection timeout
xxx | xxx | xxx | xxx | x.x.x No such mailbox

Page: 1 2 3 4 5

I could write my own, but I don't want to reinvent the wheel.

Well, if I have to write my own then which language will be useful ?

---

### Post by kidders on 2009-10-17
Hi there,

You wouldn't have to do too much work to get some *basic* logs into your database. For example, you could use sed or awk to transform log lines into SQL and execute them.```
tail -n0 -f /path/to/mail.log | grep --line-buffered <SOMETHING> | sed -u 's/<SOMETHING>/INSERT INTO tablename etc etc;\x00/' | xargs -0L1 mysql -e
```

Just in case that needs some explanation ...[LIST]
[*]You could start by using tail to monitor for changes to your flat mail log.
[*]Filter out garbage you're not interested in with grep (in line buffering mode). I don't have a copy of Postfix running at the moment, so I wasn't able to construct any useful suggestions for what <SOMETHING> (a regular expression) might be.
[*]Transform grep's output into a sequence of null-terminated INSERT statements. This <SOMETHING> might take a bit of trial and error to get right. (NB: The "\x00" is important.)
[*]Use xargs to spawn MySQL client processes & execute the generated SQL. If you handle a lot of mail, this will be _very_ inefficient, but there are a few easy ways of streamlining it, if you turn out to like the general idea.
[/LIST]

Anyhow, assuming the information you want to store in MySQL is readily extractable from your logs (ie it doesn't require much post-processing), hooking Postfix up to MySQL should be a matter of a single command.

There are alternative approaches though. For instance, you could set up the MySQL interaction at syslog level, so instead of (or as well as) writing log lines to flat files, you system logger could send them to a MySQL database.

I hope that helps.

---

### Post by januzi on 2009-10-22
Thanks for Your reply. I found [howto](http://chaos.untouchable.net/index.php/HOWTO_setup_syslog-ng_to_log_to_mysql) (that pipe part is obsolete) and I set up the logger for the smtp$. The bad news is that I have to post-process records. The good news is that there are only 100-200 mails per day.

---

