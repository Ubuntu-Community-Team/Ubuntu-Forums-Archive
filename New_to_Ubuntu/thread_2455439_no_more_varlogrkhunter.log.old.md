---
title: "no more /var/log/rkhunter.log.old"
date: 2020-12-19
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-12-19
i use this script to run rkhunter 
#!/bin/bash
echo xxxx | sudo -S sudo rkhunter -c --sk --display-logfile
everytime i run it it creates a new rkhunter.log and moves the older rkhunter log file to .log.old
how do i modify so all each new run replaces the log in /var/log/rkhunter and no /var/log/rkhunter.log.old is created  tks

---

### Post by rburkartjo on 2020-12-20
okay figured it out. made a separate script to delete the old log then tied it to the rkhunter script so it ran after and put in crontab.

---

