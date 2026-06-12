---
title: "how to write to log from shellscript just before restart?"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by vikka on 2012-07-08
Hello,

I've setup some cronjobs(running sh scripts) on my ubuntu 12.04 server and one of them is a scheduled reboot, however if i try to write to a logfile in the same .sh file as my reboot script nothing seems to be written.

What i'd like to do is simply state uptime,date and then do the restart, something like: 

#!/bin/sh
sudo date >> reboot.log
sudo uptime >> reboot.log
sudo shutdown -r 1

If i run this script outside a cronjob , i.e just directly then it does write the reboot.log file, but if i run the script from the cronjob it only restarts and does not write the date,uptime to a file.

Any idea why?
Thanks.

---

### Post by Cheesemill on 2012-07-08
Try using the full paths for date, uptime and reboot.log

---

### Post by vikka on 2012-07-08
> **Cheesemill said:**
> Try using the full paths for date, uptime and reboot.log

Thanks, that solved my issue.

---

