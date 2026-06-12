---
title: "Scheduled Tas don't run"
date: 2015-03-05
forum: New to Ubuntu
---

### Post by jwn-2 on 2015-03-05
Ubuntu 14.04 LTS

I have installed Task Scheduler and entered a task to run once a day, but for some reason the task does not start at the specified time. The specified script does run okay when starting it manually, and I have checked, the task does appear in my crontab file. Is there anything else that should be activated somewhere for the task to start automatically?

---

### Post by ajgreeny on 2015-03-05
Cron is limited in what it can do so let's see the command or script that you can run manually but not using cron.

Does the task need a GUI application?  If so you need to "export to display" in order for it to work in cron with a command such as
 ```
(export DISPLAY=:0 &&) command to be executed
```

---

### Post by jwn-2 on 2015-03-05
No, it is only a couple of simple rsync commands to mak a daily backup:

sudo rsync --perms --delete -t -a --modify-window=1 --exclude=/home/jonnie/VirtualBox\ VMs/WinXP --exclude=/home/jonnie/.cache /home /media/jonnie/Shared/000-JEK/BACKUP/Ubuntu/Backups/Folders/
sudo rsync --perms --delete -t -a --modify-window=1 /etc /media/jonnie/Shared/000-JEK/BACKUP/Ubuntu/Backups/Folders/
sudo rsync --perms --delete -t -a --modify-window=1 /usr/bin /media/jonnie/Shared/000-JEK/BACKUP/Ubuntu/Backups/Folders/usr/

---

### Post by nerdtron on 2015-03-05
which crontab did you put it? if the script needs to use sudo, better to put it on the root crontab.

"sudo crontab -e"

---

### Post by jwn-2 on 2015-03-05
Okay, I have found the solution from other sources. You have to add yourself to the crontab group. Open /etc/groups, find the entry called "crontab" and add your user name to the end of it. That solved it for me.

---

