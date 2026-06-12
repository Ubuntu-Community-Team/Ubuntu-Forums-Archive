---
title: "cron + notify send"
date: 2011-04-12
forum: Programming Talk
---

### Post by l3ecl on 2011-04-12
I can't get cron to work out a notify send. 

```
[jk@Ubuntu /]$ sudo crontab -l
* * * * * env DISPLAY=:0.0 /home/jk/Scripts/Alarm.sh >> /home/jk/check.log 2>&1
* * * * *  DISPLAY=:0.0 /home/jk/Scripts/Alarm.sh >> /home/jk/check.log 2>&1

```

Cron creates an empty 'check.log' in my home directory but still doesn't display notify-send.

I've checked the 'notify-send script' manually and it works.

```
[jk@Ubuntu /]$ cat /home/jk/Scripts/Alarm.sh 
#!/bin/bash
DISPLAY=:0.0 /usr/bin/notify-send Blink "Blink 5x" -t 7000

```

---

### Post by Rushyang on 2011-04-12
I had the same problem before.. and then I enabled X ACL for localhost to connect to GUI applications. 

>  ~$ xhost +local:
non-network local connections being added to access control list
 ~$ xhost
access control enabled, only authorized clients can connect
LOCAL:
...Reference:
[https://help.ubuntu.com/community/CronHowto#GUI%20Applications]("https://help.ubuntu.com/community/CronHowto#GUI%20Applications")

---

### Post by Rushyang on 2011-04-12
Also, there is no need of "DISPLAY=0.0" in your Alarm.sh, as you'll be giving it from cron.

& with notify-send "expire time" doesn't work yet. No Matter what you do, that notification will stay on your screen ~10 seconds.

PS: if you're getting work expire-time somehow.. please let me know.

---

### Post by DaithiF on 2011-04-12
also, any reason why you're running this from roots crontab (sudo crontab) rather than your own user's crontab?  As root you won't have the correct DBUS_SESSION_BUS_ADDRESS set that you would need to send the notification to your users gnome session, so I don't think your notify-send command will work.

---

### Post by l3ecl on 2011-04-12
> **DaithiF said:**
> also, any reason why you're running this from roots crontab (sudo crontab) rather than your own user's crontab?  As root you won't have the correct DBUS_SESSION_BUS_ADDRESS set that you would need to send the notification to your users gnome session, so I don't think your notify-send command will work. 

i disabled the 'sudo' command and got it working perfectly, awesome. thanks!

---

### Post by l3ecl on 2011-04-12
> **Rushyang said:**
> Also, there is no need of "DISPLAY=0.0" in your Alarm.sh, as you'll be giving it from cron.

& with notify-send "expire time" doesn't work yet. No Matter what you do, that notification will stay on your screen ~10 seconds.

PS: if you're getting work expire-time somehow.. please let me know.

no wonder it stayed a little too long

---

### Post by BkkBonanza on 2011-04-12
It is possible to enable the timeout (-t) option but it requires replacing notify-send with a ppa package that a user rebuilt with the fix. I did that and it works. The ppa is [leolik]("https://launchpad.net/~leolik/+archive/leolik")

The all-knowing Ubuntu devs have decided that they don't want to support -t so other than this you'll not see it supported any time soon.

---

### Post by Rushyang on 2011-04-14
> **DaithiF said:**
> also, any reason why you're running this from roots crontab (sudo crontab) rather than your own user's crontab?  As root you won't have the correct DBUS_SESSION_BUS_ADDRESS set that you would need to send the notification to your users gnome session, so I don't think your notify-send command will work.

yes, you're right DBUS_SESSION_BUS_ADDRESS variable is unavailable in root environments. But, I wonder notify-send with my root cron is working perfectly... I know this because, This is because I run some cron for regular data backup & kill processes at specific time as root & to notify that task successfully completed, I use notify-send.

---

### Post by Rushyang on 2011-04-14
I also wonder, is there any way to work with zenity via crons??

EDIT: 
well, I just simply figured out if we add "DISPLAY=:0.0" line as prefix before calling any GTK+ dialogs  (through zenity) even in scripts. They works just fine.

---

### Post by DaithiF on 2011-04-14
the dbus session variable problem can be gotten around ... ie. even if you are root you can figure out the right value for a logged in user and set that value in your own environment such that notify-send appears on the user's desktop.

you pgrep for the users nautilus session, or gnome-panel, etc, ie. some process that is sure to running if that user is logged in, then from the pid grab the variable from the /proc/<pid>/environ 

so something like:
```
pid=$(pgrep -u username nautilus)
dbus=$(grep -z DBUS_SESSION_BUS_ADDRESS /proc/$pid/environ | sed 's/DBUS_SESSION_BUS_ADDRESS=//' )
DBUS_SESSION_BUS_ADDRESS=$dbus
```

---

### Post by kja999 on 2011-08-22
Just came across this thread.
Notify-send works fine with cron, just add :
export DISPLAY=:0
at the start of the script

---

### Post by spaceli on 2013-02-06
> **kja999 said:**
> Just came across this thread.
Notify-send works fine with cron, just add :
export DISPLAY=:0
at the start of the script

Marvelous!!
This works on my Ubuntu 12.04!!
Thanks!!

---

### Post by codemaniac on 2013-02-06
Old thread is closed now.

As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

Thanks!

---

