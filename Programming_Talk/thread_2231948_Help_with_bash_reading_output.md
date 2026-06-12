---
title: "Help with bash reading output?"
date: 2014-06-29
forum: Programming Talk
---

### Post by r_avital on 2014-06-29
Hi all,

In a terminal, I issue: xrandr -q | grep "*"  - I get exactly what I expected:  the line "   1600x1200      60.0*+" is output on screen.  It tells me what the current resolution is.

In a bash script, I can enter:
```
echo "xrandr -q | grep \"*\"" 
```-- which is nicely output to the screen, but of course, not executed.  I need to:
1. Execute that command
2. capture the output
3. find out what it contains.

My plan is to follow with something similar to this (I know this syntax is wrong, this is just to explain what I need to do):

```
if [ output contains "1600x1200" ] ; then
do something
fi

if [output contains "1920x1080"] ; then
do something else
fi
```

This will execute when the greeter is started, right after X starts.

Any ideas?  TIA :)

---

### Post by Mouldy_19 on 2014-06-29
personally id get the string down to only the data i want and do a direct comparison
```
RES=`xrandr -q | grep "*" | awk '{print $1}'`
if [ $RES == "1920x1080" ] ; then
    echo "big";
fi
```

---

### Post by Habitual on 2014-06-29
backticks are deprecated in favor of $()
```
RES=$(xrandr -q | grep "*" | awk '{print $1}')
```

---

### Post by r_avital on 2014-06-30
Thanks so much, both of you!
I found additional material elsewhere, and extrapolated from that and what you've offered here.

Here's what I ended up with:

in /etc/lightdm/lightdm.conf.d I have a file simply named "my.conf" which has the following:```
[SeatDefaults]
greeter-setup-script=/etc/lightdm/lightdmxrandr.sh
```This executes when the lightdm (or other) greeter starts, and after X started.

One directory up from than, in /etc/lightdm, I have the script named lightdmxrandr.sh:```
#!/bin/sh
set $(xrandr -q|grep "*")
case $1 in
  1600x1200) xrandr -o left ;;
  *) ;;
esac
```So, when the laptop boots up, xrandr -q knows which resolution it is running with (Connected to external monitor = 1600x1200, not connected = 1920x1080).  My external monitor is rotated vertically, so lightdm knows whether or not to rotate itself left, thanks to this script.

Tested, works beautifully.  if you see anything in my bash code that is wrong, I'd appreciate the feedback (I'm more of an OO programmer -- java, PowerBuilder -- and SQL programmer) -- I obviously have a lot to learn about bash scripting, and awk.

Either way, thanks so much both of you! :)

---

