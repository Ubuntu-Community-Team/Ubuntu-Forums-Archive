---
title: "cron issue"
date: 2017-10-15
forum: New to Ubuntu
---

### Post by 0N3 on 2017-10-15
[COLOR=#000000]1) My laptop when plugged in charges to 90% or greater I want unity to notify me of this (Works)[/COLOR]
[COLOR=#000000]2)When it reaches 90% or greater after I've plugged the laptop out it keeps reminding me to unplug the laptop until it drops below 90%(I don't want this) Ideally I'd like to check on_ac_power to detect I've plugged out the laptop and stop the notification! Is this possible?[/COLOR]

[COLOR=#000000]3) My laptop when unplugged and has a charge below 20% I want unity to notify me of this (Works)[/COLOR]
[COLOR=#000000]4)My laptop when plugged in and is below 20% keeps asking me to plug it in (I don't want this) Ideally I'd like to check on_ac_power to detect the laptop is plugged in charging and stop the notification? Is this possible?[/COLOR]
battery.sh:
```

#! /bin/bash


# read battery percentage value
OUT=`upower -i /org/freedesktop/UPower/devices/battery_BAT0 | grep percentage`


# select only the int value
IFS=':' read -ra P <<< "$OUT"
PERCENTAGE="%"
BATTERY_VALUE=${P[1]%$PERCENTAGE}


# send a notification if battery level is under 20%
if (($BATTERY_VALUE  < "20")); then


    eval "export $(egrep -z DBUS_SESSION_BUS_ADDRESS /proc/$(pgrep -u $LOGNAME gnome-session)/environ)";
    DISPLAY=:0 notify-send "Battery charged! You can now unplug your laptop!"

#sleep and retry again in 30 seconds if battery discharging
elif ((on_ac_power == 1 && $BATTERY_VALUE  >= "90")); then

    sleep 30


# send a notification if battery level is greater than or equal to 90%
elif ((on_ac_power == 0 && $BATTERY_VALUE  >= "90")); then


    eval "export $(egrep -z DBUS_SESSION_BUS_ADDRESS /proc/$(pgrep -u $LOGNAME gnome-session)/environ)";
    DISPLAY=:0 notify-send "Battery charged! You can now unplug your laptop!"
fi

```

crontab -e
```

*/1 * * * * /usr/local/bin/battery.sh

```

Any help appreciated!

---

### Post by 0N3 on 2017-10-16
Got it!

```

#!/bin/bash


OUT=`upower -i /org/freedesktop/UPower/devices/battery_BAT0 | grep percentage`
IFS=':' read -ra P <<< "$OUT"
PERCENTAGE="%"
BATTERY_VALUE=${P[1]%$PERCENTAGE}


if on_ac_power; then 
    


	if (( $BATTERY_VALUE  >= "90")); then
	eval "export $(egrep -z DBUS_SESSION_BUS_ADDRESS /proc/$(pgrep -u $LOGNAME gnome-session)/environ)";
	notify-send "Battery charged! You can now unplug your laptop!"
	paplay /usr/share/sounds/freedesktop/stereo/complete.oga
	fi
fi


if ! on_ac_power; then 
	
	if (( $BATTERY_VALUE  < "25")); then
	eval "export $(egrep -z DBUS_SESSION_BUS_ADDRESS /proc/$(pgrep -u $LOGNAME gnome-session)/environ)";
	notify-send "Battery low! You can now plug in your laptop!"
	paplay /usr/share/sounds/freedesktop/stereo/complete.oga
	fi
fi

```

---

