---
title: "How To: Toshiba R200 Bluetooth, Brightness &amp; Touchpad Set-up Guide"
date: 2007-09-26
forum: Outdated Tutorials &amp; Tips
---

### Post by hotweiss on 2007-09-26
Everything works out of the box in Ubuntu 7.04, except for the Bluetooth, brightness control and the touch pad click & drag feature.

[U][B]
Touch Pad Set-up[/B][/U]

Thanks to this thread here, I got my touch pad properly working:

[http://ubuntuforums.org/showthread.php?t=236683](http://ubuntuforums.org/showthread.php?t=236683)


**Step 1:** Edit xorg.conf.

> sudo gedit /etc/X11/xorg.conf

**Step 2:** Add this in there after your mouse settings.

> Section "InputDevice"
Identifier "ALPS"
Driver "synaptics"
Option "AlwaysCore"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "LeftEdge" "120"
Option "RightEdge" "830"
Option "TopEdge" "120"
Option "BottomEdge" "650"
Option "FingerLow" "14"
Option "FingerHigh" "15"
#set MaxTapTime to 0 to disable tap-to-click
Option "MaxTapTime" "180"
Option "MaxTapMove" "110"
Option "ClickTime" "0"
Option "EmulateMidButtonTime" "75"
Option "VertScrollDelta" "10"
Option "HorizScrollDelta" "0"
Option "MinSpeed" "0.45"
Option "MaxSpeed" "0.75"
Option "AccelFactor" "0.020"
Option "EdgeMotionMinSpeed" "200"
Option "EdgeMotionMaxSpeed" "200"
Option "UpDownScrolling" "1"
Option "CircularScrolling" "0"
Option "CircScrollDelta" "0.1"
Option "CircScrollTrigger" "2"
Option "SHMConfig" "true"
EndSection

**Step 3:** Scroll to the bottom and add.

> InputDevice "ALPS" to ServerLayout.

[B]
Step 4:[/B] Reboot.

Your touch pad now should be working as expected.


[B][U]
Bluetooth & Brightness Control[/U][/B]

Thanks to Tim Anderson's blog I was able to get my Bluetooth and brightness controls working:

[http://www.itwriting.com/blog/?p=333#comment-35858](http://www.itwriting.com/blog/?p=333#comment-35858)

You see, the driver that enables your Bluetooth also enables your brightness control. This is done by creating a script file that turns it on  at start-up.


**Step 1:** Change to the directory where we are going to have the script file.

> 
cd /etc/init.d

**Step 2:** Creat the script file.

> sudo nano tosh-bluetooth

**Step 3:** Paste this script.

> 
#! /bin/bash

# script to start/stop Toshiba Bluetooth adapter
# requires toshset

case "$1" in
 start)
 /usr/bin/toshset -bluetooth on
 ;;
 stop)
 /usr/bin/toshset -bluetooth off
 ;;
 *)
 echo "Usage: /etc/init.d/tosh-bluetooth {start|stop}" >&2
 exit 1
 ;;

esac

exit 0



Make sure that there is an empty line after exit 0.

**Step 4:** Save and exit Nano.

Type Ctrl-O to exit and Ctrl-X to exit.

**Step 5:** Make the script executable.

> 
sudo chmod 755 tosh-bluetooth

**Step 6:** Add it to the startup scripts.

> sudo update-rc.d tosh-bluetooth defaults

**Step 7:** Reboot.

Your Bluetooth should now be working as expected.


**_Bluetooth Mouse Set-up_**

I'll use the settings that got my Logitech V270 going as an example.


**Step 1:** Get the address of your mouse.

> hcitool scan

The address label on the bottom of my mouse was incorrect, lol.

**Step 2:** Connect your mouse.

> sudo hidd --connect XX:XX:XX:XX:XX:XX

You have to do this manually once or it won't connect it automatically at start-up.

**Step 3:** Edit the file /etc/default/bluetooth.

> sudo gedit /etc/default/bluetooth

[B]
Step 4:[/B] Turn on HIDD.

Set the variable HIDD_ENABLED=1.

**Step 5:** Add this line below HIDD_ENABLED=1

HIDD_OPTIONS="--connect XX:XX:XX:XX:XX:XX --server"

**Step 6:** Reboot.

Your mouse now should be working as expected, but if your mouse does not work following all these steps, please repeat step 1&2 after your reboot (the last time you'll need to do this).


Hopefully this guide saves you a few hours of searching.

---

