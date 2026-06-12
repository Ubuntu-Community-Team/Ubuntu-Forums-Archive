---
title: "ubuntu 11.10 always crashes"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by kanodapogs on 2011-11-27
Hello, I'm new to ubuntu and love it at first use, Now I can finally be free from microsoft. Problem is, It always crashes, after about every 30 minutes to 1 hour. I don't know why, I first suspected firefox so I uninstalled it and used chromium. It was good for about a day and it is happening again though not as often as it did with firefox, could it be the clamav?

---

### Post by ajgreeny on 2011-11-27
Is the machine running hot?

---

### Post by azertyh on 2011-11-27
hello,
look in your logs, perhaps you would find there some information.
type in a terminal
```
tail -f /var/log/syslog
```
(ctrl+c to stop it).

---

### Post by kanodapogs on 2011-11-28
Hi azerith, here is my log info...


kano@kano-G31M-ES2C:~$ tail -f /var/log/syslog
Nov 28 18:07:44 kano-G31M-ES2C kernel: [   35.723880] Inbound IN=eth0 OUT= MAC=00:24:1d:e8:26:3d:00:26:18:d7:11:de:08:00 SRC=172.169.1.5 DST=172.169.0.141 LEN=396 TOS=0x00 PREC=0x00 TTL=1 ID=32746 PROTO=UDP SPT=1900 DPT=58640 LEN=376 
Nov 28 18:08:12 kano-G31M-ES2C blueman-mechanism: Exiting 
Nov 28 18:08:41 kano-G31M-ES2C dbus[785]: [system] Activating service name='org.debian.apt' (using servicehelper)
Nov 28 18:08:42 kano-G31M-ES2C AptDaemon: INFO: Initializing daemon
Nov 28 18:08:42 kano-G31M-ES2C dbus[785]: [system] Successfully activated service 'org.debian.apt'
Nov 28 18:08:42 kano-G31M-ES2C AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Nov 28 18:08:42 kano-G31M-ES2C AptDaemon.Trans: INFO: Simulate was called
Nov 28 18:08:42 kano-G31M-ES2C AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/19b287e28032466bbca202cdbc2bbe9b
Nov 28 18:08:45 kano-G31M-ES2C AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Nov 28 18:09:09 kano-G31M-ES2C kernel: [  120.608430] exe (2244): /proc/2244/oom_adj is deprecated, please use /proc/2244/oom_score_adj instead.

I hope it tells you something coz I don't comprehend what this info is telling me... thanks for the effort, I really appreciate it. 

I also tried jgreeny's suggestion, the boot log info script, I followed the instructions but terminal says no such command... sorry.

If nothing works then I will have to go with navaleshubham10's suggestion...:(

---

### Post by Paqman on 2011-11-28
> **kanodapogs said:**
> 
If nothing works then I will have to go with navaleshubham10's suggestion...:(

Before going that far I'd try booting up into your LiveCD and using it as your main system for a while. If the problem is hardware then it'll probably fail on the LiveCD as well, but if it doesn't then your problem is software and a reinstall might be the quicker fix.

---

### Post by kanodapogs on 2011-11-28
> **Paqman said:**
> Before going that far I'd try booting up into your LiveCD and using it as your main system for a while. If the problem is hardware then it'll probably fail on the LiveCD as well, but if it doesn't then your problem is software and a reinstall might be the quicker fix.

Just one question, I'm also using windows xp as an alternative, if it's hardware, xp will also crash right? or ubuntu is just sensitive to failing hardware?

---

### Post by Paqman on 2011-11-28
> **kanodapogs said:**
> if it's hardware, xp will also crash right?

Most likely, yes.

---

### Post by enjoijesus94 on 2011-11-28
Try installing ubuntu again 
and tell us what happens then;)

---

### Post by kanodapogs on 2011-11-28
well, it doesn't happen with my xp so ok, I'll reinstall and get back to you guys, thanks again, appreciate it! By the way, how do I make a clean install in my ubuntu partition? Do I reformat it as I do with xp? If so, how?

---

### Post by ajgreeny on 2011-11-28
> **kanodapogs said:**
> well, it doesn't happen with my xp so ok, I'll reinstall and get back to you guys, thanks again, appreciate it! By the way, how do I make a clean install in my ubuntu partition? Do I reformat it as I do with xp? If so, how?
Choose "Something else" on the disk preparation page, and you will se all the partitions in the list.  You can then choose to make the old sdx# as your **Mountpoint root** partition in the dropdown box, use as ext4, and click on the Format tick box if it isn't already selected.  Do a similar thing with a separate /home partition, choosing /home as mountpoint, but most importantly make sure the Format box is not selected.

---

