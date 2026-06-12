---
title: "Switching between laptop &amp; external monitor issues"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by Rob Sayer on 2012-06-28
Day 9 of Linux ...

Ubuntu 12.04, machine is intel i3 with Intel Integrated HD graphics, just installed this morning.

If I connect my 1080p external monitor to my laptop, I get a perfectly good display on both monitors.  I can move the cursor between them just fine.

However, while this is what a lot of people want, it isn't what I want. 

I would like to just be able to switch from the internal to the external display, just one or the other.  As it is if I want to watch a video I have to drag the player's window from the internal to the external display.

This works but it's obviously compromising performance.  I just want to switch and have the same desktop on one or the the other monitor.

I tried switching off monitors from the Displays section of Settings.  This caused a total loss of cursor display and control and I had to do a hard shutdown ... though I must say the system handles that well ...

Somehow I can't help but feel I'm missing something simple, but I can't seem to find anything in the support stuff.

---

### Post by SEWilco on 2012-06-28
I think what you want is "Mirror Displays".  In upper right corner, click the On-Gear then click on Displays.  Or maybe you want to click the "Laptop ON" to turn off your laptop display.

---

### Post by Rob Sayer on 2012-06-29
Thanks, but that didn't work so well ... cursor control is not preserved very well.  Dual monitor support seems to be a well known weak link in Ubuntu, and frankly I was expecting worse.

---

### Post by Rob Sayer on 2012-06-30
Found out last night that if I'm in dual monitor mode and I close the laptop lid to suspend it doesn't suspend.

Also loses cursor control again, necessitating a hard shutdown.

Frankly, I expected better support for Intel Integrated HD graphics.  It's not exactly obscure.

Any ideas out there?

---

### Post by jbowen7 on 2012-10-15
Hey Rob,

Your Desktop Manager should have an application to do this easily.
Since I don't know what DM you're using, I'll assume it's Unity, which I don't much about. However I can provide a command line fix for you.

1) Open up a terminal
   Note: copy and paste the code in your terminal.

2)The following will display which output screens you have available, note the ones that are connected```
xrandr -q
```

3) Now activate all connected screens
```
xrandr --auto
```

4) NOTE: the following will turn off the LVDS1.. if you change LVDS1 to VGA1 then it'll turn off VGA1, so on and so forth.
```
xrandr --output LVDS1 --off
```

---

### Post by jbowen7 on 2012-10-16
Here's a script I just wrote for you. If you copy the code below into a file, then give it executable permissions then it should switch screens for you.. 

```

!/bin/bash
#
# To cycle through multiple screens for my laptop
# A bit hackish... 
# john bowen



declare -A screensOn
inc=0
screens=$(xrandr -q | grep "[^dis]connected")
while read line
do
    screenNames[$inc]=$(echo $line | cut -d" " -f1 )
    if [[ $(grep '+' <<< $line) ]] # The "+" indicates a viewport
        then
        screensOn[${screenNames[$inc]}]=1
    else
        screensOn[${screenNames[$inc]}]=0
    fi
    inc=$(expr $inc + 1)

done <<< "$screens"


inc=0
for i in ${screenNames[*]}
do
    if [[ ${screensOn[$i]} == 0 ]]
    then
        echo "$i is Off, so we'll use this."
        turnOn[$inc]=$i
    else
        echo "$i is On, we'll shut this off."
        turnOff[$inc]=$i
    fi
    inc=$(expr $inc + 1)
done

# Let's make sure both screens aren't on, and that we leave at least one screen on.
if [ -z $turnOn ]
then
    echo "we're going to be leaving ${turnOff[1]} turned on"
    turnOn[0]=${turnOff[1]}
    turnOff[1]=" "
fi



### we've gathered info, now let's use it.
xrandr --auto
for i in ${turnOff[*]}
do
    xrandr --output $i --off
done

```

---

### Post by Rob Sayer on 2012-11-09
Thanks for all the responses, especially the script writing, but I found a good solution.

I'm using xubuntu with arandr installed instead.  Xfce handles dual monitors just fine.  Plus it suspends properly ... ie. comes out of sleep mode ... with an external monitor.

Also it's *much* faster than unity or gnome classic.  I'm a happy camper now.

---

### Post by meantux on 2012-11-15
I found a fix for a similar problem:

The monitor connected to my docking station frustratingly stopped working with Ubuntu's regular kernel upgrade to 3.2.0-32-generic-pae

Sadly there was no point using xrandr, removing the xorg.conf, using the System settings. 

In none of those solutions there was any shadow of any clue that the system detected that second monitor, for the system only the laptop's screen existed.

I desperately did a few shots in the dark and I got lucky when I removed the "i915.modeset=0" in /boot/grub/grub.cfg (and in /etc/default/grub), rebooted and suddenly it all started to work normally again, finally. 

I have a laptop Dell Latitude 

(lspci output):
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0  VGA compatible controller: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)

---

