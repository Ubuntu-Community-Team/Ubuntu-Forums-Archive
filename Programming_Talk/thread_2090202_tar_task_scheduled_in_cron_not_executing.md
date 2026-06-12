---
title: "tar task scheduled in cron not executing"
date: 2012-12-01
forum: Programming Talk
---

### Post by dwlamb on 2012-12-01
I am attempting to create a cron task to backup an ImapMail folder in Thunderbird without success.
This is my code:
```

tar -cvzf  /home/daniel/Desktop/`date +%Y-%m-%d`.tgz /home/daniel/.thunderbird/p2bjx6va.default/ImapMail/
```At the terminal prompt, the command works as it should, the archive creating with the day's date.  In the crontab, this is My syntax:
```

* * * * *  tar -cvzf  /home/daniel/Desktop/`date +%Y-%m-%d`.tgz /home/daniel/.thunderbird/p2bjx6va.default/ImapMail/

```For now, it is set to execute that way simply to debug.  Once I get it working, I will want to change it to run at 5 a.m. on the 1 and 15 every month.  I will most likely change the path of where to save the archive as well.

Researching this, I have found that bash scripts are a pain to schedule in cron so I have kept it simple with the above code.  Is there a PATH I need to set for tar or some other setting missing?

To edit the crontab, I am simply entering crontab -e at a terminal prompt.  The system does not have /etc/cron.allow or /etc/cron.deny.  As well, I set a cron task of 
```

* * * * *  touch /home/daniel/Desktop/test.txt

``` and that ran without a hitch at the top of the next minute. So I know it is not a permissions issue.

---

### Post by spjackson on 2012-12-01
The % symbol has special meaning in a crontab entry. It needs to be escaped. See [here]("http://ubuntuforums.org/showthread.php?p=12321688").

---

### Post by dwlamb on 2012-12-01
Thanks!  That is all I was missing.

---

