---
title: "[SOLVED] Crontab doesn't run script correctly"
date: 2008-12-27
forum: Programming Talk
---

### Post by easybake on 2008-12-27
I have an alarm clock script to play music through rhythmbox, speak the weather and the date with festival. When I run the script in terminal it works perfectly however when I run it though a crontab, it does not run the rhythmbox portion correctly.

I have tried running mail and sudo mail but I don't have any messages. Here is the script.
```
#!/bin/sh

#put a "cd" command here if your gmail and wakeup scripts aren't in the same folder
#amixer -c 0 sset Master,0 100%  & #change the % here for starting Master volume
rhythmbox
rhythmbox-client --play 
rhythmbox-client --set-volume .2  #commout out from here to
sleep 3; rhythmbox-client --set-volume .3 
sleep 3; rhythmbox-client --set-volume .4 
sleep 3; rhythmbox-client --set-volume .5 
sleep 3; rhythmbox-client --set-volume .6 
sleep 3; rhythmbox-client --set-volume .7 
sleep 3; rhythmbox-client --set-volume .8 
sleep 3; rhythmbox-client --set-volume .9 
sleep 3; rhythmbox-client --set-volume 1.0  #here to disable escalating the volume slowly
sleep 15; rhythmbox-client --set-volume .8  #change the '65' in this line to reflect how long you want to play (after volume escalation)
sleep 1; rhythmbox-client --set-volume .6  #comment out from here to
sleep 1; rhythmbox-client --set-volume .4 
sleep 1; rhythmbox-client --set-volume .2 
sleep 1; rhythmbox-client --set-volume .1  #here to disable the volume from "fading" when festival starts speaking

#-----------------------------------------------------------------------

echo "Good Morning Jake." |  festival --tts;
sleep 1; echo "Today is $(date '+%A') $(date '+%-B') $(date '+%-e')" |  festival --tts;
#sleep 1; echo "$(date '+%-B') $(date '+%-e')" |  festival --tts;
sleep 1; echo "The time is $(date '+%-I') $(date '+%-M')" |  festival --tts;
echo "It is currently"|  festival --tts;
weather-util -i KMDW | grep Temperature | cut -c16-19 | festival --tts;
echo "degrees outside and" |  festival --tts;
weather-util -i KMDW | grep Sky | cut -c19-30 | festival --tts;
echo "You have $(./gmail.py) e-mails." |  festival --tts;
#weather-util -i KMDW | grep Sky | cut -c19-30 | festival --tts; #visit http://www.nws.noaa.gov/tg/siteloc.shtml to help find the ID or your METAR station nearest you, and replace that anywhere you see KMDW.
#weather-util -i KMDW | grep Temperature |  festival --tts; #visit http://weather.noaa.gov/pub/data/observations/metar/decoded/ to see the txt file that the stations provide, and you can include your own weather lines here using grep like below
#weather-util -i KMDW | grep Weather |  festival --tts;
#weather-util -i KMDW | grep Humidity |  festival --tts;

#-----------------------------------------------------------------------

sleep 1; rhythmbox-client --set-volume .2 & #comment out from here to
sleep 1; rhythmbox-client --set-volume .4 &
sleep 1; rhythmbox-client --set-volume .6 &
sleep 1; rhythmbox-client --set-volume .8 &
sleep 1; rhythmbox-client --set-volume 1.0 & #here to disable escalation back up from speaking
```

I believe the sleep commands work because there is a delay from the time i set with crontab till it begins speaking.

I think the problem is in "rhythmbox-client --set-volume..." but I don't know how to fix it.

---

### Post by pytheas22 on 2008-12-27
If the script runs fine when you call it manually from a terminal, then I would suspect that the problem lies with crontab, not with your script.

First of all, are you sure the script has execute permissions?

Otherwise, what does your crontab look like?  There may be a typo or other problem there that's preventing the script from actually running.

Finally, sometimes it's helpful to add something to the script to see whether or not it's actually being executed by crontab.  For example, if you added a line like this to the top:
```

date > /home/YOUR-USERNAME/Desktop/SCRIPT-RAN
```

then the script would create a file on your desktop containing the time that ran.  You can check to see whether this file exists in order to know if crontab tried to run the script at all.

---

### Post by Cracauer on 2008-12-28
Redirect the whole shebang into a logfile to diagnose

sh -x $HOME/myscript 2>&1 | tee $HOME/log

---

### Post by easybake on 2008-12-28
> **Cracauer said:**
> Redirect the whole shebang into a logfile to diagnose

sh -x $HOME/myscript 2>&1 | tee $HOME/log

Ok I got the error messages logged out and this is what I have currently```
Cannot open display: 
Run 'rhythmbox --help' to see a full list of available command line options.

(rhythmbox-client:8416): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8418): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8475): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8478): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8481): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8484): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8487): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8490): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8499): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8522): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8526): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8530): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8533): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8536): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8539): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8605): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8608): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8611): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8614): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.


(rhythmbox-client:8617): Rhythmbox-WARNING **: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.

```

so it looks to be a dbus problem. Googling the problem currently.

---

### Post by easybake on 2008-12-28
The problem was resolved by adding DISPLAY=:0.0 to the crontab entry.

Here is the end cron i ended up using.```
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root
SHELL=/bin/bash
37 * * * * DISPLAY=:0.0 $HOME/morningalarm.sh > $HOME/tempfile.txt 2>&1

```

---

### Post by Cracauer on 2008-12-28
Oh, so you are calling a GUI program from crontab?

I don't think that's a good idea. What happens if you aren't logged in on the console, or somebody else is logged in?

---

### Post by easybake on 2008-12-28
> **Cracauer said:**
> Oh, so you are calling a GUI program from crontab?

I don't think that's a good idea. What happens if you aren't logged in on the console, or somebody else is logged in?

I'm the sole user of this so I don't think that is going to be a problem. Do you have any ideas how I could go about doing this without a gui program?

---

### Post by pytheas22 on 2008-12-28
> Do you have any ideas how I could go about doing this without a gui program?

You could use mplayer instead of Rhythmbox to play your audio.  mplayer doesn't require a GUI.

---

### Post by Cracauer on 2008-12-28
> **pytheas22 said:**
> You could use mplayer instead of Rhythmbox to play your audio.  mplayer doesn't require a GUI.

But mplayer requires a terminal, which isn't available either inside a cronjob.

I would use some true commandline thing like mpg123, or pipe something to aplay.

---

### Post by dunno on 2009-01-09
After much bash-ing around, IT WORKS!  thanks.

my crontab -e looks like:
```

12 12 * * * export DISPLAY=:0 && $HOME/alarm.sh

```

i had to add a 
```

sleep 3;

```
after the initial starting call to rhythmbox to the alarm.sh script, which i think is key to allow time for the DBUS_SESSION_BUS_MESSAGE env var to be set.  i've attached the modified alarm.sh.

Also, i changed the alarm.sh to use espeak instead of festival because it was already installed (by default) on my machine.

check out [http://ubuntuforums.org/showthread.php?p=5899086]("http://ubuntuforums.org/showthread.php?p=5899086") for other options and more good info

also attached is gmail.py

---

