---
title: "notify-send does not work inside a script called by cron"
date: 2010-07-18
forum: Programming Talk
---

### Post by GeoMX on 2010-07-18
I want to call a script that will show a notification message using notify-send (package libnotify-bin), this is my test script:

notify-script.sh
```

notify-send "Title" "Message"
echo "Script executed on $(date)" > /home/user/date.txt

```
I echo date so that I can check whether the script was executed.

I set cron to call the script every minute:

> $ crontab -l
* * * * * /home/jorge/checa-servidor.sh

I know cron is executing the script because cron log indicates it and date.txt gets updated every minute, but the notify-send message does never appear.

I've already checked the script by directly executing it, it works fine.

Thanks in advance for your help.

---

### Post by StephenF on 2010-07-18
It won't work because the cron launched script is not operating under the same environment and therefore has a different and much smaller set of environment variables.

The DBUS_SESSION_BUS_ADDRESS environment variable is the one to copy but there is a problem. This value will be different probably each time you log in, never mind boot so to get the script working again you would have to autostart something (another script) that saves this environment variable to a temporary file then have your crontabbed script pick it up.

That's assuming you are dead set on using cron.

---

### Post by cherva on 2010-07-18
You need to set the DISPLAY variable like this 
```
00 06 * * * env DISPLAY=:0 gui_appname
```
The env DISPLAY=:0 portion will tell cron to use the current display (desktop) for the program "gui_appname".And if you have multiple monitors, don't forget to specify on which one the program is to be run. For example, to run it on the first screen (default screen) use : 
```
00 06 * * * env DISPLAY=:0.0 gui_appname
```
The env DISPLAY=:0.0 portion will tell cron to use the first screen of the current display for the program "gui_appname".
Note: In Karmic(9.10), you have to enable X ACL for localhost to connect to for GUI applications to work. 
```
 ~$ xhost +local:
non-network local connections being added to access control list
 ~$ xhost
access control enabled, only authorized clients can connect
LOCAL:
...
``` Taken from the ubuntu wiki. [https://help.ubuntu.com/community/CronHowto#GUI%20Applications]("https://help.ubuntu.com/community/CronHowto#GUI%20Applications")

---

### Post by GeoMX on 2010-07-19
Thanks a lot for your answers, setting the DISPLAY variable did the trick, I tried with and without env instruction, it works great with both.

```

*/15 * * * * env DISPLAY=:0 /home/user/script.sh

```
```

*/15 * * * * DISPLAY=:0 /home/user/script.sh

```

> **StephenF said:**
> That's assuming you are dead set on using cron.
What I want is to run an online check for a remote server every X minutes and get notified of its results (mainly if the remote server does not respond), I thought a shell script + cron would be a simple and good solution, but would like to hear of other/better options :).

Thanks again for your help :).

---

