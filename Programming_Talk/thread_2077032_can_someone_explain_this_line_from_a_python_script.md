---
title: "can someone explain this line from a python script"
date: 2012-10-27
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2012-10-27
```
ratio = min([25, 50, 75, 100], key=lambda x: abs(x - (float(freq) / fmax * 100)))
```
this is from the gnome cpu frequency monitor applet, i am re writing it for the xfce4-genmon-plugin
i noticed it does not round the the nearest 25%
i need to know the way it rounds it

---

### Post by Vaphell on 2012-10-27
it finds the value for which abs(percentage-threshold) is the lowest

```
$ python -c 'freq=200; fmax=1000; print [ abs(x - (float(freq) / fmax * 100)) for x in [25,50,75,100] ]; print min([25, 50, 75, 100], key=lambda x: abs(x - (float(freq) / fmax * 100))) '
[**5.0**, 30.0, 55.0, 80.0]
25
$ python -c 'freq=600; fmax=1000; print [ abs(x - (float(freq) / fmax * 100)) for x in [25,50,75,100] ]; print min([25, 50, 75, 100], key=lambda x: abs(x - (float(freq) / fmax * 100))) '
[35.0, **10.0**, 15.0, 40.0]
50
```

---

### Post by Bachstelze on 2012-10-27
See this: [http://docs.python.org/library/functions.html#min](http://docs.python.org/library/functions.html#min)

And lambda x: f(x) is a shortcut to define a function that takes x as argument without really defining it. The code is equivalent to

```

def f(x):
    global freq, fmax
    return abs(x - (float(freq) / fmax * 100))

ratio = min([25, 50, 75, 100], key=f)

```

---

### Post by pqwoerituytrueiwoq on 2012-10-27
odd this behaves the same as the way i assumed it would, but the applet acts different
```
python -c 'freq=2200000; fmax=3400000; print [ abs(x - (float(freq) / fmax * 100)) for x in [25,50,75,100] ]; print min([25, 50, 75, 100], key=lambda x: abs(x - (float(freq) / fmax * 100))) '
```
that simulates the second speed on my system, on my 10.04 install 2200000 is displayed as the 50% icon not the 75% icon as that line says it should

---

### Post by Vaphell on 2012-10-27
maybe the code selecting the icon is wrong or the icon itself?

---

### Post by pqwoerituytrueiwoq on 2012-10-27
i know the icon is there and is usable 
my 64% usage used the 50% icon on 10.04 (even thought that line just said 75% icon)
my laptop's 50% usage used the 50% icon so i know that worked
anyway here is my script for my genmon applet (icons are attached)
```
#!/bin/bash
ICONS="/usr/local/share/pixmaps/cpufreq-applet"
if [ -z "$1" ];then
    echo "<img>$ICONS/cpufreq-na.png</img><txt>Which Core?</txt>"
    echo -e "<tool>$(basename $0) [Core Number]\n$(basename $0) 0</tool>"
    exit
fi
LOC="/sys/devices/system/cpu/cpu$1/cpufreq"
GOV=$(cat $LOC/scaling_governor)
if [ "$2" == "--set" ];then
    GOVS=$(cat $LOC/scaling_available_governors)
    LIST=$(echo ${GOVS:0:-1} | sed 's/.*/\L&/;s/[a-z]*/\u&/g;s/ / FALSE /g')
    NewGOV=$(zenity --list --title 'Choose a Governor' --text 'Select one' --radiolist --column 'Pick' --column 'Opinion' TRUE $LIST)
    if [ -n "$NewGOV" ];then
        if [ "$NewGOV" == "Userspace" ];then
            SPD=$(cat $LOC/scaling_available_frequencies)
            LIST=$(echo ${SPD:0:-1} | sed 's/ / FALSE /g')
            NewSPD=$(zenity --list --title 'Choose a Governor' --text 'Select one' --radiolist --column 'Pick' --column 'Opinion' TRUE $LIST)
            if [ -z "$NewSPD" ];then
                exit
            fi
        fi
        echo ${NewGOV,} > $LOC/scaling_governor
        if [ -n "$NewSPD" ];then
            echo $NewSPD > $LOC/scaling_setspeed
        fi
    fi
    exit
fi
CUR=$(cat $LOC/scaling_cur_freq)
MAX=$(cat $LOC/scaling_max_freq)
USE=$(perl -e "print int($CUR/$MAX*1000)")
GHz=$(perl -e "print $CUR/1000000")
if [ "$2" == "--bar" ];then
    echo "<img>$ICONS/cpufreq-na.png</img>"
    echo "<bar>$(($USE/10))</bar>"
elif [ $USE -lt 125 ];then
    echo "<img>$ICONS/cpufreq-0.png</img>"
elif [ $USE -lt 325 ];then
    echo "<img>$ICONS/cpufreq-25.png</img>"
elif [ $USE -lt 625 ];then
    echo "<img>$ICONS/cpufreq-50.png</img>"
elif [ $USE -lt 825 ];then
    echo "<img>$ICONS/cpufreq-75.png</img>"
else
    echo "<img>$ICONS/cpufreq-100.png</img>"
fi
if [ ${GHz:0:1} -gt 0 ];then
    Spd="$GHz GHz"
else
    MHz=$(perl -e "print $GHz*1000")
    Spd="$MHz MHz"
fi
USE="$(($USE/10))"
# if [ $USE -lt 100 ];then
#     echo "<txt>$USE%<span fgcolor=\"#18191A\">0</span></txt>" # make applet use same width at all times using extra 0 same color as background
# else
     echo "<txt>$USE%</txt>"
# fi
echo -e "<tool>Core $1 is at $Spd\nGovernor is ${GOV^}</tool>"
echo "<click>$(basename $0) $1 --set</click>"
exit
```i have this in my /etc/rc.local so it can change the cpu governor ```
bash -c "chmod 777 /sys/devices/system/cpu/cpu{0..3}/cpufreq/{scaling_setspeed,scaling_governor}"
```

---

