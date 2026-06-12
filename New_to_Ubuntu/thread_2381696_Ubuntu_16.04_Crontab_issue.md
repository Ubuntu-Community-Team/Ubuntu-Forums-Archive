---
title: "Ubuntu 16.04 Crontab issue"
date: 2018-01-04
forum: New to Ubuntu
---

### Post by 0N3 on 2018-01-04
[COLOR=#111111][FONT=Ubuntu]I followed a tutorial here on crontab checking your battery status to alert you when it was low and high. I want it to alert me when it is less than or equal to 10% and not on ac power and greater than or equal to 90% when on ac power.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I followed this link here:[/FONT][/COLOR]
[https://askubuntu.com/questions/754609/laptop-battery-high-low-alarm](https://askubuntu.com/questions/754609/laptop-battery-high-low-alarm)

[COLOR=#111111][FONT=Ubuntu]Here is my customized version of the code this did work for me before but I am on a new fresh install and it isn't working now.

```
[/FONT][/COLOR]#!/bin/bash


OUT=`upower -i /org/freedesktop/UPower/devices/battery_BAT0 | grep percentage`
IFS=':' read -ra P <<< "$OUT"
PERCENTAGE="%"
BATTERY_VALUE=${P[1]%$PERCENTAGE}


if on_ac_power; then 
    


	if (( $BATTERY_VALUE  > "90")); then
	eval "export $(egrep -z DBUS_SESSION_BUS_ADDRESS /proc/$(pgrep -u $LOGNAME gnome-session)/environ)";
	notify-send "Battery charged! You can now unplug your laptop!"
	paplay /usr/share/sounds/freedesktop/stereo/complete.oga
	fi
fi


if ! on_ac_power; then 
	
	if (( $BATTERY_VALUE  < "10")); then
	eval "export $(egrep -z DBUS_SESSION_BUS_ADDRESS /proc/$(pgrep -u $LOGNAME gnome-session)/environ)";
	notify-send "Battery low! You can now plug in your laptop!"
	paplay /usr/share/sounds/freedesktop/stereo/complete.oga
	fi
fi[COLOR=#111111][FONT=Ubuntu]
```

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Any help greatly appreciated![/FONT][/COLOR]

---

### Post by 0N3 on 2018-01-04
Solved it changed my code around.
Changed:
```
OUT=`upower -i /org/freedesktop/UPower/devices/battery_BAT0 | grep percentage`
```

To:

```
OUT=`upower -i /org/freedesktop/UPower/devices/battery_BAT1 | grep percentage`
```

```
#! /bin/bash



# read battery percentage value
OUT=`upower -i /org/freedesktop/UPower/devices/battery_BAT1 | grep percentage`




# select only the int value
IFS=':' read -ra P <<< "$OUT"
PERCENTAGE="%"
BATTERY_VALUE=${P[1]%$PERCENTAGE}




# send a notification if battery level is under 20%
if ! on_ac_power; then 


if (($BATTERY_VALUE  < "10")); then


    eval "export $(egrep -z DBUS_SESSION_BUS_ADDRESS /proc/$(pgrep -u $LOGNAME gnome-session)/environ)";
    notify-send "Battery charged! You can now unplug your laptop!"
    paplay /usr/share/sounds/freedesktop/stereo/complete.oga
fi


fi


#sleep and retry again in 30 seconds if battery discharging


if on_ac_power; then


if (($BATTERY_VALUE  >= "90")); then




    eval "export $(egrep -z DBUS_SESSION_BUS_ADDRESS /proc/$(pgrep -u $LOGNAME gnome-session)/environ)";
    notify-send "Battery charged! You can now unplug your laptop!"
    paplay /usr/share/sounds/freedesktop/stereo/complete.oga
fi


fi
```

---

