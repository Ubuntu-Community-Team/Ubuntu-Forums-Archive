---
title: "desktop going into hibernate mode"
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by seattle vic on 2011-09-28
I have 11.10 loaded on an old desktop that I use as a server.  For the last couple of days it's been going into some sort of hibernate or sleep mode after a short period of time (maybe an hour, haven't timed it).  It's not a laptop and the only power setting I see in the systems is power low, which should not be.

Is there a way to check after the fact if it, indeed went into hibernate mode, and is this something anybody else has seen?

Thanks in advance.

---

### Post by __lonewolf on 2011-09-28
I am seeing the same thing, although I do have 2 options under power, "Suspend when inactive for:" which is set to "don't suspend" and low power.  Hopefully someone has some ideas.

My bad, looks like it is this bug and in another thread on this forum.  [https://bugs.launchpad.net/ubuntu/on...on/+bug/860485](https://bugs.launchpad.net/ubuntu/on...on/+bug/860485)

---

### Post by effenberg0x0 on 2011-09-28
+1.. unusable as HTPC....

---

### Post by effenberg0x0 on 2011-09-28
```

sudo killall -s KILL upowerd

```Don't know what it is. Actually I know what it is but don't know how to set it up properly. Too sleepy to search today.
But it seems like life is good again. HTPC stopped shutting down monitor / suspending in the middle of "Through the Wormhole / Universe / Carl Sagan's Cosmos" sleep playlist.

Regards,
Effenberg

---

### Post by seattle vic on 2011-09-28
I checked my syslog and it's going into sleep mode; don't know why.

I tried the 'sudo killall -s KILL upowerd' and will now wait for a couple hours to see if it worked.

Thanks.

---

### Post by seattle vic on 2011-09-28
It didn't work.  I killed unpowerd but somehow it got running again and sent the machine into sleep mode...

---

### Post by effenberg0x0 on 2011-09-29
And the man pages for UPowerd are fantastic. I feel very confident on how to set it up lol. See the /etc/conf file. Definitely not very clear for me.

Seriously, someone will have to come with a workaround and find out how to fix it. So we better start trying.

if you kill and restart the daemon, you have a chance of seeing some files it reads. I caught the output to a file to study it and noticed it seems to use /usr/bin/pm-is-supported still. It seems to read the output to see if the machine is capable of suspending/hibernating. This is good because it's known territory. There is a known workaround: Move/Backup /usr/bin/pm-is-supported to /usr/bin/pm-is-supported.old and create a new /usr/bin/pm-is-supported with only "exit 1" inside it. chmod +x and reboot. If it really relies solely on pm-is-supported to see if the machine can  suspend/hibernate, pm-utils will exit with status 1. The machine, in  theory, can't suspend or hibernate, we'll be happy again. I'm trying it now in two PCs. Will post results later. 

I have a script that used to avoid dimming, blank, screensaver, sleep, hibernate, altogether. Its useless now against upowerd for suspend/hibernate. But still manages to keep the screen on.

**EDIT**: _As of Sep 29th, 2011 updates, this settings can't avoid the screen from going blank anymore. Useless for HTPC once again._
```

$ sudo cat no_sleep.sh 
[sudo] password for al: 
#!/bin/sh
#
# Attempts to disable sleep, suspend, hibernate, screensaver, blank screen
# and other stuff that is not necessary on a HTPC.
# 
# Alvaro "Effenberg" Leal <xxxxxxxxxxxxxxxxxxxxxxxxxxxx@GMail.com>

# ################ CHANGELOG #################  
# September, 29, 2011
# Still avoids monitor from going blank or screensaver, but is useless
# against upowerd suspend / hibernate.
#
# June, 05, 2011
# Added xset commands.
#
# May, 11, 2011
# Changed address / valur for dim_on_idle. Working again.
#
# March, 18, 2011
# Fixed Screensaver idle time (bool vs integer)
#
# Jan, 12, 2011
# Works, yey.

# ################ ToDo #####################
# I need to test settings independently, to find out
# which are the important / really working ones.

## SCREENSAVER
# Disable screensaver start
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t bool /apps/gnome_settings_daemon/screensaver/start_screensaver false

# Disable screensaver locking
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t bool /apps/gnome-screensaver/lock_enabled false

# Increase screensaver idle time (GUI maximum is 2h. The following cmd sets it to 10h)
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t integer /apps/gnome-screensaver/idle_delay 600

# Disable screensaver entirely
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t bool /apps/gnome-screensaver/idle_activation_enabled false

## DPMS
# Disable DPMS screen blank on AC and battery
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t string /apps/gnome-power-manager/ac_dpms_sleep_method off 
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t string /apps/gnome-power-manager/battery_dpms_sleep_method off

## NON-DPMS
# Disable Computer sleep when on AC and battery
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t integer /apps/gnome-power-manager/ac_sleep_computer 0 
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t integer /apps/gnome-power-manager/battery_sleep_computer 0

# Disable Display sleep when on AC and battery
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t integer /apps/gnome-power-manager/ac_sleep_display 0 
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t integer /apps/gnome-power-manager/battery_sleep_display 0

# Disable Dimming screen when idle
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t bool /apps/gnome-power-manager/dim_on_idle false

## SETTERM
setterm -powersave off -blank 0

## XSET
xset dpms 0 0 0
xset s noblank
xset s off

```**EDIT2: **As a workaround, I tried xdotool to simulate activity in  the HTPC. A single mouse-move or mouse-click every 20 to 30 minutes is  enough to keep the monitor on. So, one can create any script with it.  Something like this draft:
```

cat ./keep_awake.sh
#!/bin/bash
# Keep PC awake with a single mouse click (left button) every n minutes
# It is obviously a much more interesting idea to use ps, grep, sed, awk, pidof,
# whatever to only keep the PC awake if the media player (like XBMC) is
# running. 
# Then anything, like nohup keep_awake.sh & via SSH would do OK to start it.

KEEPAWAKE_CMD="xdotool click --repeat 1 --delay 10000 --window 0 1"
SLEEP_TIME=1200 # (20 minutes in seconds)

while  :
do 
`$KEEPAWAKE_CMD`
 sleep $SLEEP_TIME
done


```______________________________
OBS: I know nothing about upowerd. Documentation is zero. Try anything I post at your own risk. Ubuntu Oneiric is Beta software. It is expected to not work 100% and is not what I would personally recommend for anyone that just needs to get the job done. It's aimed at beta testers and people that can afford to have a broken PC right now. So PLEASE: DO NOT attempt any of the mentioned procedures if you're working on a server / production machine, if you don't have backup of your data or if you don't have the habit of performing fixes in Ubuntu / Linux distros. You can end up having to do a new install from scratch. I can't be held responsible for any damage, ok? :-)

Regards,
Effenberg

---

### Post by dino99 on 2011-09-29
devs are working on :)
[https://bugs.launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/+bug/860485](https://bugs.launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/+bug/860485)

---

### Post by effenberg0x0 on 2011-09-29
This is probably the first time ever I'm stuck with no viable documentation. Searched quite a bit, but still am unsure on how to work with upowerd.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2011-09-29
The workaround mentioned at [https://bugs.launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/+bug/860485/comments/15](https://bugs.launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/+bug/860485/comments/15) seems to be a winner.

Regards,
Effenberg

---

### Post by seattle vic on 2011-09-29
> **effenberg0x0 said:**
> The workaround mentioned at [https://bugs.launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/+bug/860485/comments/15](https://bugs.launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/+bug/860485/comments/15) seems to be a winner.

Regards,
Effenberg

Just tried it, so will check back in an hour...

---

### Post by seattle vic on 2011-09-29
Looks like that one does the trick :)

Thanks.

---

### Post by effenberg0x0 on 2011-09-29
Yes it did... Lets see how Oneiric evolve in the sense of having valid power settings in gnome-control-center. It's missing some important / working settings like:

```

**On AC-POWER**
Suspend                     <YES/NO/INACTIVITY_TIME>
Hibernate                   <YES/NO/INACTIVITY_TIME>
Turn of HDD                <YES/NO/INACTIVITY_TIME>
Turn of Monitor           <YES/NO/INACTIVITY_TIME>
Display Brightness      <%>

**On BATTERY**
Suspend                    <YES/NO/INACTIVITY_TIME/BATTERY_LEVEL>
Hibernate                  <YES/NO/INACTIVITY_TIME/BATTERY_LEVEL>
Turn off HDD              <YES/NO/INACTIVITY_TIME/BATTERY_LEVEL>
Turn off Monitor         <YES/NO/INACTIVITY_TIME/BATTERY_LEVEL>
Display Brightness     <%>

**On UPS**
Suspend                   <YES/NO/INACTIVITY_TIME/UPS_BATTERY_LEVEL>
Hibernate                 <YES/NO/INACTIVITY_TIME/UPS_BATTERY_LEVEL>
Turn off HDD             <YES/NO/INACTIVITY_TIME/UPS_BATTERY_LEVEL>
Turn off Monitor        <YES/NO/INACTIVITY_TIME/UPS_BATTERY_LEVEL>
Display Brightness    <%>

```And this are basic settings. Other OSs have conditions for when playing media, when sharing files, when there are pending updates to apply, etc. I'm worried about this move from gconf settings to UPower at this point of the game. Not sure it can all be done / tested / fixed, on time for release... There are many other more important bugs. 

Regards,
Effenberg

---

### Post by abarbaccia on 2011-10-03
I have been following this thread since my desktop suddenly started going to sleep after the upgrade.

Today it seems a patch was pushed that corrects this. I had to go into power settings and reset the settings (changed to sleep after 1 hour, then changed back) so they took effect. 

Thanks devs for committing a fix quickly!

---

