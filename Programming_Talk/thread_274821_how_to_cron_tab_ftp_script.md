---
title: "how to cron tab ftp script"
date: 2006-10-10
forum: Programming Talk
---

### Post by dyol on 2006-10-10
**as newbie i read somthing about crontab-may u help me on how to crontab my ftp script-and direct the output to a file-so that i can graph it.thx **

---

### Post by William the Conquerer on 2006-10-10
here's a good site with info about crontab on ubuntu

[http://doc.gwos.org/index.php/Crontab](http://doc.gwos.org/index.php/Crontab)

if you need to pipe the output to a file you should be able to add >> to the end of the script execution followed by the file you want to pipe to for instance: ```
 01 04 * * * /usr/bin/somedirectory/somecommand >> logfile.txt
```

do you have any other specific questions?...

---

