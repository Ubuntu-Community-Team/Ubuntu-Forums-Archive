---
title: "Running script from Launcher asks for password"
date: 2014-01-09
forum: New to Ubuntu
---

### Post by steveearle86 on 2014-01-09
I have a script that sends the PC to sleep and wakes on the 1st of the month:

```
#!/bin/bash

#current system time and waketime
old=`date '+%H:%M'`
new=11:55


THISYEAR=`date +'%Y' -d 'now'`
NEXTMONTH=`date +'%m' -d 'next month'`


#if next month is January, increment the year by 1
if [ $NEXTMONTH == 01 ]
then
    THISYEAR=`date +'%Y' -d '1 year'`
fi


#current system date and wake date(1st of next month)
olddate=`date +%Y-%m-%d`
newdate=$THISYEAR"-"$NEXTMONTH"-01"


IFS=: read old_hour old_min <<< "$old"
IFS=: read hour min <<< "$new"


# convert the date in seconds from Unix EPOCH time
sec_old=$(date -d "$olddate $old_hour:$old_min:00" +%s)
sec_new=$(date -d "$newdate $hour:$min:00" +%s)


DIFFERENCE=$(( (sec_new - sec_old) )) 


#lock the screen
#gnome-screensaver-command -l


#suspend the system and wake in this many seconds
sudo rtcwake -m mem  -s $DIFFERENCE



```

This is saved as /home/steve/SuspendWake.sh

From the terminal, if I type

```
 /home/steve/SuspendWake.sh

```

the script runs as expected.

I have created a desktop launcher to run the script above but it asks me for a password. If I change the desktop launcher command to ```
sudo /home/steve/SuspendWake.sh
``` it still asks for a password, as does: ```
gksudo /home/steve/SuspendWake.sh
```

I have tried adding to visudo as follows:

```
Steve ALL= NOPASSWD: /home/Steve/SuspendWake.sh

```

but still no luck!

Can anyone help getting the launcher to run without asking for a password?
Thanks

---

### Post by mc4man on 2014-01-09
Post your orig. .desktop, the one without (gk)sudo
Do you care if it runs in a terminal and or does it have to run in a terminal?

> from the terminal, if I type

 /home/steve/SuspendWake.sh

the script runs as expected.

Is that in a new terminal? (never used to auth in.

---

### Post by steveearle86 on 2014-01-11
Hi,
Config file from home/steve/desktop/Standby.desktop:

```
[Desktop Entry]Name=Standby
Exec=/home/steve/SuspendWake.sh
Terminal=true
Type=Application
Name[en_GB]=Standby
Icon=/home/steve/Pictures/Icons/Shutdown.png

```

I have also tried the above with ```
Exec=sudo /home/steve/SuspendWake.sh
``` which also asks for a password

> [COLOR=#000000]Is that in a new terminal? (never used to auth in.[/COLOR]
If I open a new terminal, and type ```
[COLOR=#000000]*/home/steve/SuspendWake.sh*[/COLOR]
```it asks for the password. If the terminal is still running, it doesn't

---

### Post by mc4man on 2014-01-11
It seems that you're using sudo on rtcwake, not your script (SuspendWake.sh
Does rtcwake need to be run as root?

Does this need to be run in a terminal?, if so the add a line  to .desktop
Terminal=true

---

### Post by steveearle86 on 2014-01-11
I see what you mean, its the RTCwake in the script asking for the password. If I change the last lines of the script to
```
[COLOR=#000000][FONT=Ubuntu Mono]#suspend the system and wake in this many seconds
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]rtcwake -m mem  -s $DIFFERENCE[/FONT][/COLOR]
```

(removing the sudo) and run the script from a terminal, I get > open failed: /dev/rtc0: Permission denied

The launcher with the command 
```
[COLOR=#000000][FONT=Ubuntu Mono]Exec=/home/steve/SuspendWake.sh[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Ubuntu Mono]
now just pops open a terminal window and shuts it immediately, I assume it is showing the same message[/FONT][/COLOR]

---

### Post by steveearle86 on 2014-01-12
Sorted!
Run the following two commands from Terminal:

```
sudo chown steve /dev/rtc0
```

```
sudo chown steve /sys/power/state
```

---

