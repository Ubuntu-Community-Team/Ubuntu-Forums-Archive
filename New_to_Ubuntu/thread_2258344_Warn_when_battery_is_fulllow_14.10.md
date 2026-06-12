---
title: "Warn when battery is full/low: 14.10"
date: 2014-12-26
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2014-12-26
Hello Ubuntu Forums community!

Previously, after running some upgrades in vanilla Ubuntu 14.04 LTS (no GNOME 3 Stable/Staging PPAs), HP 2000 Notebook PC, reboot to complete the update, LightDM failed to recognize my background. Logging in lead to an (almost) unusable experience. The Dock would take literally 30 seconds to unfold completely, networking was disabled and could not be re-enabled, a file in the desktop couldn't be moved into a folder, etc. So I decided it's time for an upgrade: Backed up important files to external HDD, installed Ubuntu GNOME 14.10, restored files. To ensure stability, even though I wanted GNOME 3.14, I decided once again to not enable GNOME 3 Stable/Staging PPAs. Also decided not to run update-manager, and disable Update Notifier from gnome-session-properties.

On another PC with vanilla Ubuntu 14.04 LTS, identical HP 2000 Notebook PC, although everything was running fine, I didn't want to risk it, so I installed Ubuntu GNOME 14.10, but did enable GNOME Stable/Staging PPA, as ultimate stability was not completely necessary, as well as I wanted GNOME 3.14.

This is the problem: on the "Stock" Ubuntu GNOME, I only know that the battery is low when it's dead, and it gets really annoying to check the battery status now an then.
On the "Modified" Ubuntu GNOME, I get a notification on the top (I moved all notifications to the top using a GNOME Shell extension from extensions.gnome.org) when the battery is at 20%.

The questions are:

1) (STOCK Only: Compatible with GNOME 3.12 + Ubuntu 14.10) Is there any program, be it in the ubuntu repos, a PPA, a deb/autopackage/rpm/whatever package, a GNOME SHELL extension, or an SH file, that can make an alert when battery is at 20%, 25%, 30%, 20 minutes, or a customizable amount of %/min/whatever?
-OR-
1) (STOCK Only: Compatible with GNOME 3.12 + Ubuntu 14.10) I'm somewhat knowledgeable with scripting, and I know how to use zenity and notify-send. Is there any piece of SH code that I can put in a script, so when battery is at 20%/25%/20min/whatever it calls something, like a zenity info dialog or an alert from notify-send?

2) STOCK and MODIFIED: Compatible with GNOME 3.12 + GNOME 3.14 + Ubuntu 14.10) Is there any program, be it in the ubuntu repos, a PPA, a deb/autopackage/rpm/whatever package, a GNOME SHELL extension, or an SH file, that can make an alert when battery is at 100%?
-OR-
2) STOCK and MODIFIED: Compatible with GNOME 3.12 + GNOME 3.14 + Ubuntu 14.10) I'm somewhat knowledgeable with scripting, and I know how to use zenity and notify-send. Is there any piece of SH code that I can put in a script, so when battery is at 100% it calls something, like a zenity info dialog or an alert from notify-send?

Thanks for your support.

-Jonathan

---

### Post by Jonathan Precise on 2014-12-27
Fixed the problem, found that acpi could do the job if I would set a cron to run this script every minute: [http://unix.stackexchange.com/questions/60778/how-can-i-get-an-alert-when-my-battery-is-about-to-die-in-linux-mint?answertab=oldest#tab-top]("http://unix.stackexchange.com/questions/60778/how-can-i-get-an-alert-when-my-battery-is-about-to-die-in-linux-mint?answertab=oldest#tab-top")

Adapted it ever so slightly, just for the fun of it and to make it easier to debug when something went wrong... (added a --simulate-battery-percent PERCENTAGE argument, as well as others, like if to output all (or most) text to /a/path/where/the.log file resides (obviously user-defined with an argument), and added unimplemented options, like --raw-acpi-output, which is hidden there until I decide to add it.

*This thread is now marked as solved.*

EDIT: I have subscribed again to this thread, and I will post the script. Improvements are welcome.

---

### Post by Jonathan Precise on 2014-12-28
Here is the script:

```
#!/bin/bash
# Running every minute via cron

#variables, will be used later on
ARGS=$@
INLOGDEFARG=false
LOGout=/dev/stdout
LOGerr=/dev/stderr
INSIMBATLVLARG=false
RAWNOGREP=false
RAWWGREP=false

#detect args
for i in ${ARGS} nullopt ; do
	if env [ "$INLOGDEFARG" = "true" ]; then
		LOGout=$i
		LOGerr=$i
		INLOGDEFARG=false
	elif env [ "$INSIMBATLVLARG" = "true" ]; then
		SIMBATLVL=$i
		INSIMBATLVLARG=false
	else
		case $i in
			--help|-h)
				echo "
"				"Usage: `basename $0` [-h|--help] [-l|--log /path/to/log/file] [-s|--simulate-battery-level PERCENTAGE]
" #"[-r|--raw-acpi-output] [-n|--np-acpi-percentage-output]"
				exit 0 ;;
			--log|-l)
				INLOGDEFARG=true
				;;
			--simulate-battery-level|-s)
				INSIMBATLVLARG=true
				;;
#			--raw-acpi-output|-r)
#				RAWNOGREP=true
#				if env [ "$RAWWGREP" = "true" ]; then echo "Conflicting opts, fatal error w/o GUI, exiting"; exit 2; fi
#				;;
#			--np-acpi-percentage-output|-n)
#				RAWWGREP=true
#				if env [ "$RAWNOGREP" = "true" ]; then echo "Conflicting opts, fatal error w/o GUI, exiting"; exit 3; fi
#				;;
			nullopt) ;;
			*)
				echo "Unknown opt ${i}, fatal error w/o GUI, exiting" >$LOGerr
				exit 4
				;;
		esac
	fi
done

#acpi not installed function
error_no_acpi() {
	echo "The package \"acpi\" is not installed, notifying user..." >$LOGerr
	notify-send --urgency=critical "Not all required packages are installed" "The package \"acpi\" is not installed. Please install to continue. Note: This will pop-up every minute until it is installed." ;
	exit 1 ;
}

#grep not installed function
error_no_grep() {
	echo "The package \"grep\" is not installed, notifying user..." >$LOGerr
	zenity --error --title="Not all required packages are installed" --text=$'The package "grep" is not installed. Please install to continue.\nNote: This will pop-up every minute until it is installed.' ;
	exit 1 ;
}

if ! env [ -z $SIMBATLVL ]; then
	bat_lvl=$SIMBATLVL
else
	bat_lvl=`acpi -b | grep -P -o '[0-9]+(?=%)'`
fi

if env [ $bat_lvl -le **_[COLOR="#FF0000"]25[/COLOR]_** ]
then
	echo -e "\a"
	notify-send --urgency=critical --icon="/usr/share/icons/gnome/scalable/status/battery-caution-symbolic.svg" "Battery is extremely low." "Consider plugging in, only ${bat_lvl}% left."
fi
exit 0
```

Improvements are more than welcome.

EDIT: To change the percentage when you are notified, change the number in **BOLD**, **_UNDERLINE_**, and **_[COLOR="#FF0000"]RED[/COLOR]_**.

-Jonathan

---

