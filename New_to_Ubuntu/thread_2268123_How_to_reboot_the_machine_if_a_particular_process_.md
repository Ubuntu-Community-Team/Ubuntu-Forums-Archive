---
title: "How to reboot the machine if a particular process is killed"
date: 2015-03-06
forum: New to Ubuntu
---

### Post by sajeesh-cs on 2015-03-06
I want to make a process in such a way that ,if somebody inlcuding the root user, tries to kill that process,the system should reboot.

---

### Post by nerdtron on 2015-03-06
I think you need to have a script that will check the process list, crontab entry for repeated check like every minute, then perform the server reboot.

something like:
```
#!/bin/bash
ps -ef | grep process_name | grep -v grep
if [ "$?" -ne 0 ]
then
reboot
fi

```

If the script runs and doesn't find any process name process_name on the process list, it will issue the reboot command.

And the crontab entry can be:
```
* * * * * /bin/bash /path/to/script
```

remember to put the cron on root. "sudo crontab -e"

---

### Post by sajeesh-cs on 2015-03-06
Thanks for the reply.Actually my intention is to make an unkillable process. If somebody tries to kill it ,the system should reboot. If the cron script menitioned above is killed,our purpose is defeated.

---

### Post by nerdtron on 2015-03-06
Basically if you are root, you have complete control on the system? Even if you have installed/configured a "protection" on a process, the root user can disable that protection and kill the process. We can be stuck on this loop as long as we are talking to about the root user.

---

### Post by sajeesh-cs on 2015-03-06
Yes you are right. Thanks for the info

---

