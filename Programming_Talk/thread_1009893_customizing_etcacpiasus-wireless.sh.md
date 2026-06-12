---
title: "customizing /etc/acpi/asus-wireless.sh"
date: 2008-12-13
forum: Programming Talk
---

### Post by nightfrost on 2008-12-13
On my new and shiny laptop (an Asus N20A), I have two ways of controlling wireless and bluetooth. One is a hardware switch that turns everything on and off, another is Fn+F2. In Vista, as well as Express Gate, Fn+F2 basically browses through different combinations of wlan+bt.

Furthermore, as far as I understand, the radio transmitters are controlled like this:

/sys/devices/platform/asus-laptop/bluetooth -> controls bt-device & wlan-led
/sys/devices/platform/asus-laptop/wlan -> controls wlan-led
/sys/class/net/wlan1/device/rfkill/rfkill0/state -> controls wlan-device

The default events and scripts that are included in the acpid package aren't very well adapted for this laptop. I guess they might be for other models of asus, but on mine the wireless-toggle, for example, behaves seemingly random, with no indication of what it did. So I created a script that checks whether what's active is wlan, bt, wlan+bt, or none. If wlan is active, it switches to bt, if bt is active, it switches to wlan+bt, and so on. In this script I'm also using notify-send, in order to notify the user what actually is active at the moment. I've also paired Fn+space (which is detected as lockbtn, whatever that is), to this script giving a notification of the current status.

I've edited /etc/events/asus-wireless, asus-wireless-on, asus-wireless-off, and asus-lock, to call this script instead, with the appropriate argument where applicable.

Also, since NetworkManager doesn't seem to get that the wlan device is down, when it is down, I'm using cnetworkmanager, which is a command line frontend to NM, to deactivate and re-activate the wlan interface.

There are still some issues with it, and I'm no programmer, so I would love any help. For example, using notify-send from an acpi script is really suboptimal. When gnome has started up I need to open a terminal and run /etc/init.d/acpid restart for the notification bubbles to show up. If the same could be achieved with dbus-send, I'm sure that would be much better. But I don't know how to do it.

Maybe with the help of some real coders, we could make useful additions to the acpid scripts, and have them included in a future release of Ubuntu :-)

Anyway, here's the script, if it proves useful for anyone else:
```

#!/bin/sh
# Find and toggle wireless/bluetooth devices on Asus laptops

WLAN="`cat /sys/class/net/wlan1/device/rfkill/rfkill0/state`"
BT="`cat /sys/devices/platform/asus-laptop/bluetooth`"

if [ "$WLAN" -eq "1" ] && [ "$BT" -eq "0" ]; then STATE="ONLY_WLAN"; fi
if [ "$WLAN" -eq "0" ] && [ "$BT" -eq "1" ]; then STATE="ONLY_BT"; fi
if [ "$WLAN" -eq "1" ] && [ "$BT" -eq "1" ]; then STATE="BOTH"; fi
if [ "$WLAN" -eq "0" ] && [ "$BT" -eq "0" ]; then STATE="NONE"; fi

arg="$1"
echo $STATE
echo "$arg"
case "$arg" in
	"on")
		# Hardware switch is turned ON
		echo 1 > /sys/devices/platform/asus-laptop/wlan
		cnetworkmanager -w 1
		DISPLAY=:0 notify-send -i /usr/share/icons/gnome/32x32/emblem-default.png "Hardware switch: ON"
		exit 0
	;;
	"off")
		# Hardware switch is turned OFF
		echo 0 > /sys/devices/platform/asus-laptop/wlan
		cnetworkmanager -w 0
		DISPLAY=:0 notify-send -i /usr/share/icons/gnome/32x32/actions/gtk-cancel.png "Hardware switch: OFF"
		exit 0
	;;
	"status")
		# Return the current status without changing anything
		case "$STATE" in
			"ONLY_WLAN")
			DISPLAY=:0 notify-send -i /usr/share/app-install/icons/nm-device-wireless.png "WLAN: active"
			;;
			"ONLY_BT")
			DISPLAY=:0 notify-send -i /usr/share/app-install/icons/bluetooth.png "Bluetooth: active"
			;;
			"BOTH")
			DISPLAY=:0 notify-send -i /usr/share/app-install/icons/bluetooth.png "Bluetooth: active"
			DISPLAY=:0 notify-send -i /usr/share/app-install/icons/nm-device-wireless.png "WLAN: active"
			;;
			"NONE")
			DISPLAY=:0 notify-send -i /usr/share/icons/gnome/32x32/actions/gtk-cancel.png "No radio devices active"
			;;
		esac
		exit 0

	;;
esac

case "$STATE" in
	# No argment was passed to this script, start the toggling!
	"ONLY_WLAN")
	# New status: Only Bluetooth active
	echo "new state: only bluetooth"
	echo 1 > /sys/devices/platform/asus-laptop/bluetooth
	echo 0 > /sys/devices/platform/asus-laptop/wlan
	echo 0 > /sys/class/net/wlan1/device/rfkill/rfkill0/state
	cnetworkmanager -w 0
	DISPLAY=:0 notify-send -i /usr/share/app-install/icons/bluetooth.png "Bluetooth is now active"
	;;
	"ONLY_BT")
	# New status: Both WLAN and Bluetooth active
	echo "new state: activate both radio devices"
	echo 1 > /sys/devices/platform/asus-laptop/bluetooth
	echo 1 > /sys/devices/platform/asus-laptop/wlan
	echo 1 > /sys/class/net/wlan1/device/rfkill/rfkill0/state
	cnetworkmanager -w 1
	DISPLAY=:0 notify-send -i /usr/share/app-install/icons/bluetooth.png "Bluetooth is now active"
	DISPLAY=:0 notify-send -i /usr/share/app-install/icons/nm-device-wireless.png "WLAN is now active"
	;;
	"BOTH")
	# New status: Neither WLAN nor Bluetooth active
	echo "new state: disable both radio devices"
	echo 0 > /sys/devices/platform/asus-laptop/bluetooth
	echo 0 > /sys/devices/platform/asus-laptop/wlan
	echo 0 > /sys/class/net/wlan1/device/rfkill/rfkill0/state
	cnetworkmanager -w 0
	DISPLAY=:0 notify-send -i /usr/share/icons/gnome/32x32/actions/gtk-cancel.png "No radio devices active"
	;;
	"NONE")
	# New status: Only WLAN active
	echo "new state: only wlan"
	echo 0 > /sys/devices/platform/asus-laptop/bluetooth
	echo 1 > /sys/devices/platform/asus-laptop/wlan
	echo 1 > /sys/class/net/wlan1/device/rfkill/rfkill0/state
	cnetworkmanager -w 1
	DISPLAY=:0 notify-send -i /usr/share/app-install/icons/nm-device-wireless.png "WLAN is now active"
	;;
esac

```

EDIT: I have now solved one of the issues by using the netcat tool. Basically, I have a script running with non-root privileges listening to a port on localhost. The acpi script sends the message, and the user-run script, instead, uses notify-send to inform the user of what's going on.

---

### Post by Eckdar on 2008-12-14
Hey nice work there! :D I've been working and googling for some time on the same problem on my new Asus F80S. For now I'm trying to identify how to control wlan & bt. Looks like it behaves a little bit different on my system.
Bluetooth (and its led) is controlled with the same file as yours - "/sys/devices/platform/asus-laptop/bluetooth", but wlan is different:

/sys/devices/platform/asus-laptop/wlan -> controls only wlan led (2 states: 1 - led constantly on, 0 - led blinking)
/sys/class/net/wlan1/device/rfkill/rfkill0/state -> I don't have any "rfkill" directories at all :-k

So far I managed to completely shutdown wlan only by removing the module with "modprobe -r ath9k", but I'm looking around if there's any more elegant way to do it. Then if I find some time I'll write some scripts as well. I'm sure your script will be helplful so thanks for sharing!

---

### Post by nightfrost on 2008-12-14
> **Eckdar said:**
> Hey nice work there! :D I've been working and googling for some time on the same problem on my new Asus F80S. For now I'm trying to identify how to control wlan & bt. Looks like it behaves a little bit different on my system.
Bluetooth (and its led) is controlled with the same file as yours - "/sys/devices/platform/asus-laptop/bluetooth", but wlan is different:

/sys/devices/platform/asus-laptop/wlan -> controls only wlan led (2 states: 1 - led constantly on, 0 - led blinking)
/sys/class/net/wlan1/device/rfkill/rfkill0/state -> I don't have any "rfkill" directories at all :-k

So far I managed to completely shutdown wlan only by removing the module with "modprobe -r ath9k", but I'm looking around if there's any more elegant way to do it. Then if I find some time I'll write some scripts as well. I'm sure your script will be helplful so thanks for sharing!

Which kernel are you using? I'm actually on an 2.6.28rc kernel. I used the jaunty deb sources to recompile one for intrepid. Maybe that kernel will give you your rfkill interface?

---

### Post by nightfrost on 2008-12-21
Alright, considering that I don't know how to code, I've made a lot of improvements here.

There are now three scripts. 1) asus-functions.sh. This script contains the functions that the main acpi script calls. The reason I've put the functions in a seperate script is because this way, it can be made more generic in the future. 2) asus-script.sh. This is the main script that gets called from the event files. Basically, the event files call this script with one argument, that argument indicating which function key was pressed. Finally there is 3), the asus-userdaemon.sh. This script runs with no root privileges and just does things that the acpi script asks it to. It's pretty ugly, and that's simply because I don't know python. If I did, I would use python and dbus, but now I'm using netcat instead :-p

If anyone wants to help me to move this over to python and dbus, I'd be really happy. I hope that would get me started learning some python for real :-)

You'll notice that I've made the functions key sometimes do things they're not meant for. That's because I don't know what they're for (I'm not a dual booter), and I just put them to good use.

Anyway, here are the scripts, for what it's worth:

asus-functions.sh
```
# Functions used by asus-script.sh
# This file is supposed to be sourced


check_state()
{
	# Check the state of radio devices, return a string in the variable STATE
	if [ "`cat /sys/class/net/wlan1/device/rfkill/rfkill0/state`" -eq "1" ] && \
		[ "`cat /sys/devices/platform/asus-laptop/bluetooth`" -eq "1" ]; then STATE="BOTH"; fi
	if [ "`cat /sys/class/net/wlan1/device/rfkill/rfkill0/state`" -eq "1" ] && \
		[ "`cat /sys/devices/platform/asus-laptop/bluetooth`" -eq "0" ]; then STATE="ONLY_WLAN"; fi
	if [ "`cat /sys/class/net/wlan1/device/rfkill/rfkill0/state`" -eq "0" ] && \
		[ "`cat /sys/devices/platform/asus-laptop/bluetooth`" -eq "1" ]; then STATE="ONLY_BT"; fi
	if [ "`cat /sys/class/net/wlan1/device/rfkill/rfkill0/state`" -eq "0" ] && \
		[ "`cat /sys/devices/platform/asus-laptop/bluetooth`" -eq "0" ]; then STATE="NONE"; fi
	if [ "`cat /sys/class/net/wlan1/device/rfkill/rfkill0/state`" -eq "2" ]; then STATE="SWITCH_OFF"; fi
echo "function script says: $STATE"
}

switch()
{
	# Takes two arguments, 1) wlan/bluetooth and 2) on/off
	case "$1" in
		"bluetooth")
			case "$2" in
				"on")
					echo 1 > /sys/devices/platform/asus-laptop/bluetooth
				;;
				"off")
					echo 0 > /sys/devices/platform/asus-laptop/bluetooth
				;;
				*)
					return 1
				;;
			esac
		;;
		"wlan")
			case "$2" in
				"on")
					echo 1 > /sys/devices/platform/asus-laptop/wlan
					echo 1 > /sys/class/net/wlan1/device/rfkill/rfkill0/state
				;;
				"off")
					echo 0 > /sys/devices/platform/asus-laptop/wlan
					echo 0 > /sys/class/net/wlan1/device/rfkill/rfkill0/state
				;;
				*)
					return 1
				;;
			esac
		;;
	esac
}

communicate()
{
	# This function is responsible for communication with the user daemon.
	# We are using netcat at the moment, but that's just because I don't know how to code :-(
	# I'm sure dbus is the way to go
	PORT=12345
	case "$1" in
		"notify")
			# This should have the format "notify|icon|message".
			echo "$1|$2|$3" | nc localhost $PORT -q 10
			;;
		"popup")
			# This should have the format "popup|$STATE"
			# This function will also wait for a reply, and then act accordingly
			echo "$1|$2|$3" | nc localhost $PORT -q 10
			REPLY="`nc -l -p $PORT`"
			if [ "$REPLY" = "NO_CHANGE" ]; then
				# The user cancelled, and so will we
				return 1
			fi
			if [ "`echo $REPLY | grep Bluetooth | wc -l`" -eq "1" ]; then
				switch bluetooth on
			else
				switch bluetooth off
			fi
			if [ "`echo $REPLY | grep WLAN | wc -l`" -eq "1" ]; then
				switch wlan on
			else
				switch wlan off
			fi
			;;
		*)
			# In other cases, just pass along the first argument
			echo "$1" | nc localhost $PORT -q 10
			;;
		esac
}

```

asus-script.sh
```
#!/bin/sh

. /etc/acpi/asus-functions.sh

case "$1" in
	"radio")
		check_state
		case "$STATE" in
			"ONLY_WLAN")
				# New status: Only Bluetooth active
				echo "new state: only bluetooth"
				switch wlan off
				switch bluetooth on
				communicate notify bluetooth.png "Bluetooth is now activated"
			;;
			"ONLY_BT")
				# New status: Both active
				echo "Both radio devices activated"
				switch wlan on
				switch bluetooth on
				communicate notify both.png "Both radio devices are now activated"
			;;
			"BOTH")
				# New status: None activated
				echo "new state: turn off both radio devices"
				switch wlan off
				switch bluetooth off
				communicate notify gtk-cancel.png "None of the radio devices are now activated"
			;;
			"NONE")
				# New status: Only WLAN active
				switch wlan on
				switch bluetooth off
				communicate notify nm-device-wireless.png "WLAN is now activated"
			;;
		esac

	;;
	"hw_switch")
		case "$2" in
			"on")
				echo 1 > /sys/devices/platform/asus-laptop/wlan
				ifconfig wlan1 up
				communicate notify emblem-default.png "Hardware switch is on"
			;;
			"off")
				echo 0 > /sys/devices/platform/asus-laptop/wlan
				communicate notify gtk-cancel.png "Hardware switch is off"
			;;
		esac
	;;
	"display")
		check_state
		case "$STATE" in
			"ONLY_WLAN")
			communicate notify nm-device-wireless.png "WLAN is active"
			;;
			"ONLY_BT")
			communicate notify bluetooth.png "Bluetooth is active"
			;;
			"BOTH")
			communicate notify both.png "WLAN and Bluetooth are active"
			;;
			"NONE")
			communicate notify gtk-cancel.png "No radio devices active"
			;;
			"SWITCH_OFF")
			communicate notify gtk-cancel.png "Hardware switch is currently OFF" 
			;;			
		esac

	;;
	"lock")
		communicate lock
	;;
	"camera")
		check_state
		communicate popup $STATE
	;;
	"vga")
		communicate display
	;;
	*)
	;;
esac

```

```
#!/bin/bash
PORT=12345
message="`mktemp`"
data="$HOME/.local/share/asus-icons"
until [ 0 -eq 1 ]; do
	nc -l -p $PORT > "$message"
	ARG1=`cat $message | cut -d"|" -f1`
	ARG2=`cat $message | cut -d"|" -f2`
	ARG3=`cat $message | cut -d"|" -f3`
	case "$ARG1" in
		"notify")
			notify-send -i "$data"/"$ARG2" "$ARG3"
			;;
		"popup")
			case "$ARG2" in
				"BOTH")
					BTBOOL=TRUE
					WLANBOOL=TRUE
				;;
				"ONLY_WLAN")
					BTBOOL=FALSE
					WLANBOOL=TRUE
				;;
				"ONLY_BT")
					BTBOOL=TRUE
					WLANBOOL=FALSE
				;;
				"NONE")
					BTBOOL=FALSE
					WLANBOOL=FALSE
				;;
			esac
			echo $BTBOOL
			echo $WLANBOOL
			zenity --list --checklist --column "På/Av" --column "Funktion" "$BTBOOL" "Bluetooth aktiv" "$WLANBOOL" "WLAN aktiv" > "$message"
			if [ $? -eq 1 ]; then
				echo "NO_CHANGE" | nc localhost $PORT -q 10
			else
				echo "`cat $message`"
				echo "`cat $message`" | nc localhost $PORT -q 10
				echo "done"
			fi
			;;
		"display")
			gnome-display-properties
			;;
		"lock")
			gnome-screensaver-command --lock
			;;
		*)
			exit 1
			;;
	esac
done

```

---

