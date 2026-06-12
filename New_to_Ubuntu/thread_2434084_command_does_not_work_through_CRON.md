---
title: "command does not work through CRON"
date: 2019-12-30
forum: New to Ubuntu
---

### Post by victorftp on 2019-12-30
I have this command:

```
/usr/bin/screen -d -m -S NAMEOFSCREEN bash -c "ssh -i /root/chave.pem USER@IPADDRES tail -f -n +1 /var/log/apache2/other_vhosts_access.log | /usr/local/bin/goaccess -p /usr/local/etc/goaccess/goaccess.conf -o /var/www/dashboard.html --real-time-html --fifo-in=/tmp/linuxclaro.in --fifo-out=/tmp/linuxclaro.out --port=7890"
```



It works fine from the shell, but when started from CRON it doesn't work, it doesn't give me any errors or anything.

this command creates a realtime access dashboard for my apache using goaccess

how can i run this command from crontab -e ?

10 such commands will be executed with different parameters


sorry for the bad english its translated from google tradutor


[B]explaining the context:
[/B]I type SCREEN and hit ENTER
I run this command:
```
ssh -i chave.pem USER@IP 'tail -f -n +1 /var/log/apache2/other_vhosts_access.log' | goaccess -p /usr/local/etc/goaccess/goaccess.conf -o /var/www/dashboard.html --real-time-html --fifo-in=/tmp/linuxclaro.in --fifo-out=/tmp/linuxclaro.out --port=7890
```
AND AFTER
CTRL+A AND CTRL + D
to detach the "dashboard".

I did it this way using the screen, because it was the only way I found to leave ssh active, already tried with nohup and etc but none worked.

---

### Post by yancek on 2019-12-30
Are you running that command from cron as you posted it, with a set time?  Better chance to get it working if you put the commands in a script and then create a cron entry with the complete/full path to the location of the script in the cron entry.

---

### Post by goaccess on 2019-12-30
Please try adding a single dash to read from the pipe. e.g., 

```
/usr/local/bin/goaccess - -p /usr/local/etc/goaccess/goaccess.conf -o /var/www/dashboard.html --real-time-html --fifo-in=/tmp/linuxclaro.in --fifo-out=/tmp/linuxclaro.out --port=7890
```

---

