---
title: "Could these bash script be more effcient?"
date: 2012-10-18
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2012-10-18
These scripts are being called from the xfce4-genmon-plugin
i don't care for the xfce4 sensors applet or the cpu frequency applets so i made some in genmon to look like there gnome2 couterpart
```
#!/bin/bash
ICONS="/usr/local/share/pixmaps/cpufreq-applet"
if [ -z "$1" ];then
    echo "<img>$ICONS/cpufreq-na.png</img><txt>Which Core?</txt>"
    echo -e "<tool>`basename $0` [Core Number]\n`basename $0` 0</tool>"
    exit
fi
LOC="/sys/devices/system/cpu/cpu$1/cpufreq"
CUR=`cat $LOC/scaling_cur_freq`
MAX=`cat $LOC/scaling_max_freq`
USE=`echo '' | awk "{print int($CUR/$MAX*1000)}"`
GHz=`echo '' | awk "{print $CUR/1000000}"`
GOV=`cat $LOC/scaling_governor`
if [ "$2" == "--bar" ];then
    echo "<img>$ICONS/cpufreq-na.png</img>"
    echo "<bar>`echo $USE/10 | bc`</bar>"
elif [ $USE -lt 375 ];then
    echo "<img>$ICONS/cpufreq-25.png</img>"
elif [ $USE -lt 625 ];then
    echo "<img>$ICONS/cpufreq-50.png</img>"
elif [ $USE -lt 875 ];then
    echo "<img>$ICONS/cpufreq-75.png</img>"
else
    echo "<img>$ICONS/cpufreq-100.png</img>"
fi
if [ `echo ${GHz:0:1}` -gt 0 ];then
    echo "<txt> $GHz GHz</txt>"
else
    MHz=`echo '' | awk "{print $GHz*1000}"`
    echo "<txt> $MHz MHz</txt>"
fi
echo -e "<tool>Core $1 is at `echo $USE/10 | bc`%\nGovernor is `echo ${GOV^}`</tool>"
exit

``````
#/bin/bash
temp="`cat /sys/class/thermal/thermal_zone0/temp | awk '{print $1/1000}'`"
echo "<img>/usr/local/share/icons/hicolor/22x22/devices/sensors-applet-cpu.png</img>"
if [ "$1" == "-f" ];then
    temp="`echo $temp | awk '{print $1*(9/5)+32}'`°F"
    echo "<txt>$temp</txt>"
    echo "<tool>CPU Temperature $temp</tool>"
else
    echo "<txt>$temp°C</txt>"
    echo "<tool>CPU Temperature $temp°C</tool>"
fi
exit
``````
#!/bin/bash
# Dependencies: nvidia-settings mawk grep coreutils
temp=`nvidia-smi -q -d temperature | grep Gpu | awk '{print $3}'`
if [ "$1" == "-f" ];then
    temp=`echo $temp | awk "{print $1*(9/5)+32}"`
    temp="$temp°F"
elif [ "$1" == "-k" ];then
    temp="$(($temp+273)).15"
else
    temp="$temp°C"
fi
#echo -e "\e[01;33m$temp\e[00m"
echo "<txt> $temp</txt><tool>GPU $temp</tool>"
echo "<img>/usr/local/share/icons/hicolor/22x22/devices/sensors-applet-gpu.png</img>"
exit
``````
#/bin/bash
if [ -n "$1" ];then
    HDD=$1
else
    HDD="sda"
fi
TEMP=`curl http://127.0.0.1:7634 | grep $HDD | sed 's/|/ /g' | awk '{print $4"°"$5}'`
echo "<txt>$TEMP</txt><tool>Hard Drive Temperature $TEMP</tool>"
echo "<img>/usr/local/share/icons/hicolor/22x22/devices/sensors-applet-drive-harddisk.png</img>"
exit
```

---

### Post by MadCow108 on 2012-10-18
nothing in these scripts looks particularly slow
some forks could probably be avoided but thats micro optimization.
how often are they run and how long do they take per execution?

---

### Post by Vaphell on 2012-10-18
first thing i see is that backticks suck and $() should be used instead. Code full of ",' and ` reeks of poor readability and it's easy to mistake the embedded commands for strings.
> ```
USE=`echo '' | awk "{print int($CUR/$MAX*1000)}"`
GHz=`echo '' | awk "{print $CUR/1000000}"`
```
piping nothing to awk just to do some math? o.O
```
use=$((cur/max*1000))
``` wouldn't work? (btw, all caps variable names also suck because by convention env variables are and bash won't protest when you override one)

---

### Post by pqwoerituytrueiwoq on 2012-10-18
> **Vaphell said:**
> first thing i see is that backticks suck and $() should be used instead. Code full of ",' and ` reeks of poor readability and it's easy to mistake the embedded commands for strings.

piping nothing to awk just to do some math? o.O
```
use=$((cur/max*1000))
``` wouldn't work? (btw, all caps variable names also suck because by convention env variables are and bash won't protest when you override one)
decimal support:
```
echo "$((30/60*120))" && gcalctool -s 30/60*120
```

---

### Post by pqwoerituytrueiwoq on 2012-10-18
> **MadCow108 said:**
> nothing in these scripts looks particularly slow
some forks could probably be avoided but thats micro optimization.
how often are they run and how long do they take per execution?
~0.3ms i think (edit: ~31197128 ns)
i want to run it every second (for the 1st one)
the others are less frequent (3 to 11 seconds)
my laptop has 2 cores
the applets are constantly using 0.7% of my CPU each
the CPU is a Athlon X2 2Ghz  ( 64bit )

---

