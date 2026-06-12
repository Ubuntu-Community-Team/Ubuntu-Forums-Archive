---
title: "bash script logging"
date: 2006-08-03
forum: Programming Talk
---

### Post by kook44 on 2006-08-03
So I have this bash script that does a bunch of nice things and I've put in a lot of nice verbose logging with echo statements, but I need to capture the stdout & stderr in a logfile.  Now it's a bit more complicated than redirecting the output with a >. Since it will be run periodically with crontab, i need to specify a unique filename for the log each time.  The script creates a directory based on the time & some other things, and i'd like to be able to put the log for each run in there.  can anyone think of a better way to do this than adding a > to every statement in the script?

thx

---

### Post by sirlancelot on 2006-08-08
In the crontab you can direct output to a log file and an error log like so...
```
00 00 * * * /usr/bin/cmd > ~/log/cron-myscript.out.log 2> ~/log/cron-myscript.err.log
```
Hope this helps! I'm new to bash and crontab too, just started experimenting with them tonight, be sure to do searches on your question before you post, there's a  [crontab tutorial]("http://www.ubuntuforums.org/showthread.php?t=102625") that I learned quite a bit from.

---

