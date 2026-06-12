---
title: "HOWTO: Fn-F8 to cycle between LCD/external display on ATI cards (fglrx)"
date: 2008-07-15
forum: Outdated Tutorials &amp; Tips
---

### Post by tramir on 2008-07-15
During the dreaded days I was still using Windows, I could attach a projector and then press Fn-F8 to cycle between using only the LCD display, the LCD and the projector, or only the projector. This tutorial will allow you to do the same in Ubuntu. It was tested on Hardy and a Dell Inspiron 6000, with the proprietary ATI drivers, but should work on any laptop with the proprietary ATI drivers. These instructions are based on [this set of instructions]("http://www.thinkwiki.org/wiki/Script_for_Dynamic_Display_Management_with_fglrx") and on [this thread]("http://ubuntuforums.org/showthread.php?t=634675").

**Step 1:** Check that you have the proprietary ATI drivers: go to System - Administration - Hardware drivers and make sure that "ATI accelerated graphics driver" is enabled and in use. If it's not, you can find many posts about how to enable it.

**Step 2:** Create the script that handles the on-th-fly cycling between displays. For that, open a terminal window (Applications - Accessories - Terminal) and type:
```
gksu gedit /etc/acpi/ati-toggle.sh
```
(if you're using Kubuntu, replace gedit with kate; if you're using xubuntu, with mousepad)

Copy and paste the following code in the text editor:
```
#!/bin/bash
#
# Script to switch displays, e.g. by pressing Fn-F7 on Thinkpad Laptops.
# Uses aticonfig from the ATI fglrx driver for dynamic switching, and
# xrandr for resolution changing. OSD done with xosd.sh, which uses
# osd_cat from Xosd.
#
# Author: Armin Hornung  --  www.arminhornung.de
# Date: 2008-05-01
#
# Partly based on a display switching script from SuSE 10.1
# 
 
# path to xosd.sh, change to "echo" if not installed
xosd="/usr/local/bin/xosd.sh"
 
# path to xrandr
xrandr="/usr/bin/xrandr"
 
INTERNAL="lvds" # internal LCD of Laptop
EXTERNAL="tv" # external monitor, CRT or TFT
 
 
# Determine X user, script usually runs as root:
 
getXuser() {
        user=`finger| grep -m1 ":$displaynum " | awk '{print $1}'`
 
        if [ x"$user" = x"" ]; then
                user=`finger| grep -m1 ":$displaynum" | awk '{print $1}'`
        fi
        if [ x"$user" != x"" ]; then
                userhome=`getent passwd $user | cut -d: -f6`
                export XAUTHORITY=$userhome/.Xauthority
        else
                export XAUTHORITY=""
        fi
}
 
for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser
    if [ x"$XAUTHORITY" != x"" ]; then
        # extract current state
	export DISPLAY=":$displaynum"
	_enabled_monitors=`aticonfig --query-monitor | grep Enabled`
	_connected_monitors=`aticonfig --query-monitor | grep Connected`
    fi
done
 
 
# determine if internal is active
echo "${_enabled_monitors}" | grep $INTERNAL > /dev/null 2>&1 
if [ $? -eq 0 ]; then
  _internal_enabled=yes
else
  _internal_enabled=no
fi
 
# determine if external is connected 
# (LVDS always assumed to be connected)
echo "${_connected_monitors}" | grep $EXTERNAL > /dev/null 2>&1 
if [ $? -eq 0 ]; then
  _external_connected=yes
else
  _external_connected=no
fi
 
# determine if external is active
_external_enabled=no
echo "${_enabled_monitors}" | grep $EXTERNAL > /dev/null 2>&1 
if [ $? -eq 0 ]; then
  _external_enabled=yes
fi
 

#### display switching part ####
 
if [ "${_internal_enabled}" = "yes" ]; then
  if [ "${_external_connected}" = "yes" ]; then
    if [ "${_external_enabled}" = "yes" ]; then
      # switch to external only, after both enabled:
      $xosd "Enabling $EXTERNAL" &
      aticonfig --enable-monitor=$EXTERNAL
      # adjust resolution back to standard:
      $xrandr -s 1280x800 -r 60
    else
      # switch to both enabled, after external only
      $xosd "Enabling $INTERNAL & $EXTERNAL" &
      aticonfig --enable-monitor=$INTERNAL,$EXTERNAL
      # adjust resolution:
      $xrandr -s 1024x768 -r 60
    fi
  else
    $xosd "No external display connected" &
    if [ "${_external_enabled}" = "yes" ]; then
      # switch back just if external display got disconnected
      aticonfig --enable-monitor=$INTERNAL
      $xrandr -s 1280x800 -r 60
    fi
  fi
else
  # switch back to internal only, after external enabled:
  $xosd "Enabling $INTERNAL" &
  aticonfig --enable-monitor=$INTERNAL
  # adjust resolution back to standard:
  $xrandr -s 1280x800 -r 60
fi
 
exit 0

```
Save and close.

**Step 3:** *(optional)* Create a script to display on the screen the display(s) that will be activated. In the terminal window, type:
```
sudo apt-get update && sudo apt-get install xosd-bin
gksu gedit /usr/local/bin/xosd.sh
```
Copy and paste the following text in the text editor:
```
#!/bin/bash
# 2006-03-09 <pille@struction.de>
#
# displays text in arguments on X screen using osd_cat (in some nicely preconfigured style)
 
OSD_CAT=`which osd_cat`
XOSD="${OSD_CAT} --delay=2 --age=0 --lines=2 --pos=bottom --align=right --font=-adobe-helvetica-bold-r-normal-*-*-180-*-*-p-*-*-* --colour=green --shadow=1 --offset=25 --indent=25"
 
echo $@ | ${XOSD}

```
Save and close.

**Step 4:** Associate the scripts with Fn-F8. In the terminal window, type:
```
gksu gedit /etc/acpi/events/videobtn
```
In the text editor, comment out (type a "#" at the beginning) the line starting with "action" and paste the following line:
```
action=/etc/acpi/ati-toggle.sh
```
So, the text should look like this:
```
# /etc/acpi/events/videobtn
event=video.* 00000080
#action=/etc/acpi/videobtn.sh
action=/etc/acpi/ati-toggle.sh

```
Save and close.

**Step 5:** Enjoy :) (you might need to restart for this to work)

---

