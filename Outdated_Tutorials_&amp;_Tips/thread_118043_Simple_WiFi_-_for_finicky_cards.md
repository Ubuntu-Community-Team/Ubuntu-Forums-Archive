---
title: "Simple WiFi - for finicky cards"
date: 2006-01-16
forum: Outdated Tutorials &amp; Tips
---

### Post by benplaut on 2006-01-16
[COLOR="Red"]**Disclaimer**[/COLOR]
I'm not responible for any bodily or virtual injury or death caused by this script, however please report your death to me so i can fix the problem!

**What is this?**
This is a project to
 A) Make a simpler, one-click way to connect to WiFi networks
 B) Teach me how to shell script :rolleyes: 
 C) Provide integration for profile scripts (if [ -z `iwlist wlan0 | grep MyNetwork` ] then `simplewifi MyNetwork`)
Full support is provided in Gnome, and the command-line mode should work in any desktop environment (or from the command line, of course)

**How do i install it?**
The first step to download the script, and make it executable:

```

sudo -s
cd /usr/bin
wget http://box.net/public/benplaut/dfiles/simplewifi
chmod +x simplewifi
gedit /usr/bin/simplewifi
```

The seventh line of the file that opens looks like this:

```
INTERFACE=ath0 # Change this to your WiFi interface (wlan0, wifi0, eth1, and ath0 are common)
```

Change the 'ath0' to whatever your wifi card's interface is.

lines 39 and 44 look like this:

```
#				zenity --notification --text "Connected to $ESSID" --window-icon=/usr/share/icons/gnome/16x16/devices/gnome-dev-wavelan.png  ## Uncomment this line if you still want visual notification of connection
```

Remove the '#' in front of both lines if you want to have an icon pop up in your system tray when the WiFi is connected. If you're not in Gnome, do not want notification of when you are connected, or are running from the command line, then leave the line commented.

**How do i use it?**
If SimpleWiFi is run from the command line with no arguments, then it will open a dialog asking for the ESSID of the network you're trying to connect to, then ask for the WEP key (if any).

SimpleWiFi can also be run with arguments, so that it does not prompt for user input. The format for this is:

```
simplewifi NetworkName keykeykey
```

As with the graphical mode, leave the key blank if the network does not require one.

-----------------------------------

Features still coming:

*Auto-find network card
*KDE [graphical] support
*Saving output to a log file
*Check for errors, stop the script and display them (if any found)
*Less verbose by default, then -v flag to enable verbososity (sp?)

This is my first shell script, so if you know of a better way of doing these things, please let me know!

Have Fun! :D

---

