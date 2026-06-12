---
title: "Bash scripting.. Disable KDE screensaver while flash is running, cleanup.."
date: 2010-06-13
forum: Programming Talk
---

### Post by James78 on 2010-06-13
Hi, I copied and modified a shell script from [here]("http://ubuntuforums.org/showthread.php?t=1090393") and [here]("http://ubuntuforums.org/showpost.php?p=7838821&postcount=21"), and I just need to make sure it is functionally correct. It *appears* to work for me, however I'm NOT sure, especially since it's acting a little strange..

What it's supposed to do, is when flash player is running, it disables the KDE screensaver, blanking, and powersaving, then when flash player is no longer running, it re-enables it. And it also enables it at startup just to ensure it's fixed if the script was cut short or anything.

I actually know no shell scripting, so I was just going off of my best guess. Can anyone fix this..? It should be relatively easy for anyone who knows bash scripting..

kde-disable-screensaver-flash-disable.sh
(I also need the :TODO: to be done...)
[PHP]#!/bin/bash

# Cleanup any bad state we left behind if the user exited while flash was
# running
# Resume X blanking, Monitor blanking
xset s on; xset +dpms
# Resume screensaver
pkill suspend-dbus
echo " + Enabled screen blanking and powersaving, and screensaver"

# Create suspend screensaver program and give SUID and executable bit
echo '#!/bin/bash'  >  /tmp/suspend-dbus-screensaver
echo 'while :'      >> /tmp/suspend-dbus-screensaver
echo 'do'           >> /tmp/suspend-dbus-screensaver
echo 'qdbus org.freedesktop.ScreenSaver /ScreenSaver SimulateUserActivity' \
                    >> /tmp/suspend-dbus-screensaver
echo 'sleep 119'    >> /tmp/suspend-dbus-screensaver
echo 'done'         >> /tmp/suspend-dbus-screensaver
chmod u+x /tmp/suspend-dbus-screensaver

we_turned_it_off=0

while true; do
    sleep 60
    flash_on=0

    for pid in `pgrep firefox` ; do
        if grep libflashplayer /proc/$pid/maps > /dev/null ; then
            flash_on=1
        fi

        # Tests for X server blanking / Monitor blanking
        # A.k.a. screensaver is enabled
        xblanktest=$(xset -q | grep timeout | awk '{printf $2}')
        dpmstest=$(xset -q | grep "  DPMS is Enabled")

        # if flash is on, and screensaver is on, disable screensaver
        if [ "$flash_on" = "1" ] && [ "$xblanktest" -gt 0 ] || [ -n "$dpmstest" ]; then
            # Turn off X blanking, Monitor blanking
            xset s off; xset -dpms
            # Supend screensaver
            nohup "/tmp/suspend-dbus-screensaver" &> /dev/null &
            echo " - Disabled screen blanking, powersaving, and screensaver";
            we_turned_it_off=1
        # :TODO:
        # check for negation of [[ "$xblanktest" -gt 0 ]] || [[ -n "$dpmstest" ]]...
        elif [ "$flash_on" = "0" ] && [ "$we_turned_it_off" = "1" ]; then
            # Resume X blanking, Monitor blanking
            xset s on; xset +dpms
            # Resume screensaver
            pkill suspend-dbus
            echo " + Enabled screen blanking and powersaving, and screensaver"
            we_turned_it_off=0
        fi

    done
done

# Limitations:
#  Unable to tell if screensaver is active
#   qdbus org.freedesktop.ScreenSaver /ScreenSaver GetActive  always returns
#   false
#  Enables both X server blanking and DPMS even if one is orginally turned off[/PHP]

---

