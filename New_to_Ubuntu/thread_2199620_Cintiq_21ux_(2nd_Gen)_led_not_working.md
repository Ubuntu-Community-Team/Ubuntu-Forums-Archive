---
title: "Cintiq 21ux (2nd Gen) led not working"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by ryansftg on 2014-01-14
I am dual booting Ubuntu 12.04.2 x64 with Windows 7 and I have a Cintiq DTK-2100 (the generation with intuos 4 tech) and I cannot get my LED to change depending when I what touch strip mode is active. I have looked over the internet on how to get this to work, but all I can find is information regarding the Cintiq DTZ-2100(intuos 3 tech). All the information that I have come across is never relevant for what I have, is written for an intermediate Ubuntu user, or is so old that they break my system for being incompatible. In fact, my last attempt was through Synaptic Package Manager where I uninstalled the default xorg wacom driver and installed a newer one(couldn't install the most recent due do a dependency requirement that I was unable to install) which has now made it so my system display only black screen on boot -- I will most definitely need to reinstall ubuntu AGAIN. :-x 

Another Problem that I am getting is that the map buttons for the wacom driver doesn't accept ctrl, alt, or shift, which are the most essential commands needed for an efficient workflow while painting with the Cintiq. I'm trying to completely configure Ubuntu so that it matches my Windows environment.

I find that Ubuntu is nice for an average user who is mostly happy with out-of-box experience, but since I care about getting my system to be fully compatible with my hardware, I find Ubuntu is less than attractive for my needs since my desire to plug and play is impossible. However, I do want to get it working, and I am confident that when I do get it working how I want it, that I will enjoy it much more. Please help me get this working. I have been trying to find my way thought this operating system for several months now, but it seems that when I fix one thing something else becomes broken. For example the ATI driver would revert my over-scan settings in CCC on boot causing a black border around my main monitor, which I found a fix for online, which broke my ability to use Krita, which I fixed by installing kde-full (also found online), which broke my wacom driver, which I never really fixed because I noticed other glitches happening such as desktop freezing, crashes, and errors while trying to fix my wacom driver, of which I decided to reinstall Ubuntu. :|

If anyone posts help, please understand that I am a novice with Ubuntu and terminal. I have to google almost everything several times in order to understand how to do a specific task, such as compiling and installing drivers, dependencies, etc.

---

### Post by ryansftg on 2014-01-16
[FONT=arial]After much headache and trial an error, I have finally figure out how to get everything to work. I followed this guide by Favux here : [http://ubuntuforums.org/showthread.php?t=1380744&page=32](http://ubuntuforums.org/showthread.php?t=1380744&page=32)
His process can take about 2 minutes to implement in a fresh install of ubuntu or linix mint 16 once you fully understand what is going on. I tried it on both systems, and it works great. It actually works better in mint because in order to get the [/FONT]status_led0_select and status_led1_select file to change the leds in ubuntu, I had to change their permissions directly, completely negating the need for the modified rc.local file.[FONT=arial] In Mint, I was able to create the modded rc.local file with two "/bin/chmod paths" matching the two different "status_led#_select's." I then saved Favux's [/FONT]touchring-toggle.sh script in two different files, each containing only one status_led* path that were matched with keyoard shortcuts corresponding to my xsetwacom enteries. I wish I understood how to combine the two files together though. (any suggestions?)[FONT=arial] Anyways, I am very glad that my cintiq is now working correctly. I hope my noobness helps another noob.

[/FONT][FONT=arial][**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=699990")
[/FONT]
[FONT=arial] 						[/FONT]

---

### Post by ryansftg on 2014-01-17
It turns out that I did not configure things correctly. I had to reinstall again because I got into some wierd crashes from my previous attemps to try and install the wacom drivers.

Just to let anyone know, my specs are:
Asus p6x58d Premium motherboard.
i7 930 cpu.
Patriat Extreme 12gb ram.
HD 5850 xfx gpu.
Mx5500 keyboard/mouse combo.
WD 1tb hdd
Antec 900 case

---

### Post by ryansftg on 2014-01-18
Alright, I'm going to mark this as solved now. After doing a little sniffing around my system, I found out how to get my Cintiq working perfectly. It involved changing my xsetwacom values for the touch strip to the correct buttons. Here is my modified bash files for anyone with a cintiq 21ux 2nd gen to use. I have written a little bit of instructions in the file to help avoid the problems that I was having. Enjoy. And I thank Favux for his work.

```
#!/bin/bash

## Touch ring toggle script
##
## Bind Button 1 (button center of touch ring) to the script.
##
## This script is edited to from Favux's script located here : http://ubuntuforums.org/showthread.p...380744&page=32
##
## The first thing you need to do is map a command in your xsetwacom.sh to your led toggle buttons using this form:
## xsetwacom set "<put your device name pad>" Button 1 key <key assignment(s)> #this is for the left button replace "Button 1"  with "Button 14"
## once you are done, assign this file to startup applications and in the command section write bash path/to/file.
##
## To allow script to select mode status LEDs edit rc.local to change root
## only permissions on the sysfs status_led0_select file:
## gksudo gedit /etc/rc.local
## Add the following comment and command (before 'exit 0'):
## Change permissions on status_led0_select file so being root isn't
## required to switch Wacom touch ring mode status LEDs.
## /bin/chmod 666 /sys/bus/usb/devices/*/wacom_led/status_led0_select
##
## Once finished, enter terminal and use gksudo nautilus to locate the /etc/rc.local file and right click it and set permission
## to be executable and also ownership to being your username. You can also use chown <yourusername:<yourusername> path/to/file
##
## launch it in terminal by double clicking it.
## Add this file to startup as well
##
## You will need to create two files of this script with different extensions, so that you can map the toggle buttons to their ## matching counterpart. I used touch-toggle0.sh and touch toggle1.sh
## to corrispond to the "status_led1_select and status_led0_select" files
##
## You will also need to modify all the "mode_state" enteries below in one of your touch-toggle#.sh scripts so that they wont be ## working off the same mode_state file. I did "mode_state" and ## "mode_state2"
##
## You will also need to assign these bash files to keyboard shortcuts by using "bash path/to/file" and assigning them the same ## key assignments in your in your xsetwacom.sh file. when you ## click one button, it will execute the corrisponding 
## touch-toggle.sh file.
##
##
## Cintiq - status_led1_select = the left ring; status_led0_select =
## the right ring status LEDs.  Same for the touchstrips.
##
## For mode state notification use:
##   sudo apt-get install libnotify-bin
## Otherwise comment (#) out the notify-send lines.  If libnotify-bin
## installed see 'man notify-send' for details.

# check if mode_state file exists, if not create it and set to 0
if [ ! -f /tmp/mode_state2 ]; then
        echo 0 > /tmp/mode_state2
fi

# read mode state value from temporary file
MODE=`cat /tmp/mode_state2`

# select touch ring mode status LED for current mode state
echo $MODE > /sys/bus/usb/devices/*/wacom_led/status_led1_select

# for DEVICE use the pad "device name" from 'xinput list'
DEVICE="Wacom Cintiq 21UX2 pad"
#DEVICE="Wacom Cintiq 21UX2 pad"

# set touch ring function option and notification for the 4 toggled modes
if [ "$MODE" == 0 ]; then
        xsetwacom set  "$DEVICE" StripRightUp key 4  # scroll up
        xsetwacom set  "$DEVICE" StripRightDown key 5  # scroll down
    killall notify-osd
        notify-send -t 300 "Mode 1:  Scroll up or down."
elif [ "$MODE" == 1 ]; then
        xsetwacom set  "$DEVICE" StripRightUp key 9 # increase brush radius (must be mapped in GIMP)
        xsetwacom set  "$DEVICE" StripRightDown key 8  # decrease brush radius (must be mapped in GIMP)
    killall notify-osd
        notify-send -t 300 "Mode 2:  Increase or decrease brush size in Gimp"
    
elif [ "$MODE" == 2 ]; then
        xsetwacom set  "$DEVICE" StripRightUp key +  # zoom in
        xsetwacom set  "$DEVICE" StripRightDown key -  # zoom out
    killall notify-osd
        notify-send -t 300 "Mode 3:  Zoom in or out in Gimp."
elif [ "$MODE" == 3 ]; then
        xsetwacom set  "$DEVICE" StripRightUp key PgUp  # select previous layer
        xsetwacom set  "$DEVICE" StripRightDown key PgDn  # select next layer
    killall notify-osd
        notify-send -t 300 "Mode 4:  Select previous or next layer in Gimp"
fi

# toggle button increment counter
MODE=$((MODE += 1))

# set next mode state
if (( "$MODE" > 3 )); then  # roll over to 0, only 4 mode states available
        echo 0 > /tmp/mode_state2
else
        echo $MODE > /tmp/mode_state2
fi
```

---

