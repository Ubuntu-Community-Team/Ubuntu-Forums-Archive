---
title: "Auto restart @ certain hour + launch 2 tasks"
date: 2014-01-19
forum: New to Ubuntu
---

### Post by ardoniceksvk on 2014-01-19
Hello, i want to reboot my server at a certain hour (9:00 AM)

and make it start with those two commands:



```
screen -AmdS csko ./hlds_run -game cstrike +port 7431 +maxplayers 18 +sys_ticrate 1000 -pingboost 2 +map de_dust2 -master -secure


screen -AmdS public ./hlds_run -game cstrike +port 7430 +maxplayers 16 +sys_ticrate 1000 -pingboost 2 +map de_dust2 -master -secure

```

The hlds_run file is in those two folders:
/home/csko/
/home/public/

How to do it? :)
(I'm on a VPS with Ubuntu Server)

Thanks!

---

### Post by fosterD on 2014-01-19
1- Make a script with these commands (let say "my-script.sh")
```
#!/bin/bash
screen -AmdS csko ./hlds_run -game cstrike +port 7431 +maxplayers 18 +sys_ticrate 1000 -pingboost 2 +map de_dust2 -master -secure 
screen -AmdS public ./hlds_run -game cstrike +port 7430 +maxplayers 16 +sys_ticrate 1000 -pingboost 2 +map de_dust2 -master -secure
```
#Note: Please use absolute path for 'screen', 'csko', 'public', './'hlds'

2- Make the script executable
```
sudo chmod u+x my-script.sh
```

3- Copy the script to /etc/init.d/ ,which will make it start on boot

4- To schedule reboot your system on 9.00am everyday, you can use crontab
```
sudo crontab -e
```
with
```
0 9 * * * /sbin/shutdown -r now
```

.... then hope this would work :)

---

### Post by ardoniceksvk on 2014-01-20
Should this script work?

> 
[COLOR=#000000][FONT=Ubuntu Mono]#!/bin/bash[/FONT][/COLOR]screen -AmdS csko /home/csko/hlds_run -game cstrike +port 7431 +maxplayers 18 +sys_ticrate 1000 -pingboost 2 +map de_dust2 -master -secure  [COLOR=#000000][FONT=Ubuntu Mono]screen -AmdS public /home/public/hlds_run -game cstrike +port 7430 +maxplayers 16 +sys_ticrate 1000 -pingboost 2 +map de_dust2 -master -secure[/FONT][/COLOR]

---

