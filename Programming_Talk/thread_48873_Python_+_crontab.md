---
title: "Python + crontab"
date: 2005-07-14
forum: Programming Talk
---

### Post by paulfox on 2005-07-14
Hi All,
I've written a program which is in /home/fox/log.py, and i want to execute it at 10:30 am.
The program checks some system statistics like uptime, and creates a log file called system.log, in the directory where the log.py file is.
in my crontab (crontab -e), i have:
```

30 10  * * * /home/fox/log.py

```
the python code is executed ok, but the log file isn't created. (it is if i execute it manually though).

Any ideas how to get it working? i've tried writing a bash script:
```

#!/usr/bin/python /home/fox/log.py

```
setting it executable, and running that from cron. but i get the same results.

help please! :)

thanks for reading.

---

### Post by badrinarayan on 2005-07-14
I think that the python code uses relative path for the log file and you are unable to locate it. It should work otherwise.

Regards
Badri

---

### Post by LordHunter317 on 2005-07-14
To clarify what he said, if you're using a relative path for the script output, it's not being output where you think it is.

---

