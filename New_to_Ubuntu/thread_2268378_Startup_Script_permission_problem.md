---
title: "Startup Script permission problem"
date: 2015-03-08
forum: New to Ubuntu
---

### Post by joska3 on 2015-03-08
I would like to set my PC to start up automatically and run a script. Then, at the end of the script, schedule the next startup time and power off.

I have the following command at the end of my script.sh file:

```
rtcwake -m off -t $(date +%s -d 'tomorrow 18:50')
```

I have also added this script to my Startup Applications Preferences, with the Command field set to: sh script.sh

The script executes as I intended at startup, except for the above command, which, if I were to run it in a Terminal, would require a sudo prefix and me entering my password.

So far, I have tried running sudo visudo, and I entered this in the last line: ```
myname ALL = NOPASSWD: /home/myname/script.sh
```

I also tried entering the following in the Terminal: 
```
sudo chown myname /dev/rtc0
sudo chown myname /sys/power/state

```

---

### Post by ian-weisser on 2015-03-09
'Startup Applications' does not refer to boot time. 
That 'startup' refers to the desktop session starting after a human logs in. If a human does not log in after boot, those jobs don't run.

To run a job at boot time, make it an Upstart job (12.04/14.04/14.10) in /etc/init/, or systemd job (15.04) in /etc/init/, or sysvinit job in /etc/init.d/
Boot-time jobs should be owned by root (nobody is logged in yet), and must not require a display (nobody is logged in to see it, so no consoles are assigned yet).

---

