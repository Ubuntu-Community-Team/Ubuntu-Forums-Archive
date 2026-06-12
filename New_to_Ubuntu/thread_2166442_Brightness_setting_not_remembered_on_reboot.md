---
title: "Brightness setting not remembered on reboot"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by aks86 on 2013-08-09
Hello, I have a HP omni 120 1134 desktop PC. This PC doesn't seem to have any buttons hardwired or keyword shortcuts that can be used to change the brightness. Instead, I was told by tech support that the only way to reduce the brightness on windows 7 is to go to power options in control panel and then reduce it. On xubuntu I figured out how to do it with the brightness panel applet. But the problem is that Xubuntu doesn't seem to remember the brightness settings on reboot. This is the problem on linux distros in this PC, not just xubuntu to be honest. I have tried a bunch of solutions mentioned on these forums like changing my grub boot options:


GRUB_CMDLINE_LINUX="quiet splash acpi_osi=Linux acpi_backlight=vendor"




And then updating the grub. The thing is this remembers the last saved brightness setting but it destroyed the /sys/class/backlight/acpi_video0 folder which existed before and on reboot, I can't access the brightness applet anymore. It says "No device found" when I hover on the applet and shows a red icon on it. Then I tried editing the /etc/rc.local file and adding this statement:


echo 0 > /sys/class/backlight/acpi_video0/brightness 


(0 doesn't make it dark on my desktop)


I restart the computer and brightness is back to maximum. Could this be because rc.local does not run at boot ? 


So my question is what can I do to make sure that the brightness settings are remembered ? I really want to run linux on my computer and I feel this may be a problem that can be fixed.

---

### Post by aks86 on 2013-08-09
I just tried this again in windows 7 . I can reset the brightness and it remembers the setting after restart so why is this a problem in linux ? Do I need to run a script before booting ?

---

### Post by pqwoerituytrueiwoq on 2013-08-09
[FONT=courier new] acpi_osi=Linux acpi_backlight=vendor[/FONT]
if you take that out and you can control your back-light don't use that

This is how i restore my backlight settings (bold lines are what you will need)
```
~$ cat /etc/lightdm/lightdm.conf 
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
[B]greeter-setup-script = /usr/local/bin/greeter-setup-script
session-cleanup-script = /usr/local/bin/session-cleanup-script[/B]
session-setup-script = sh -c '/usr/local/bin/session-setup-script &'
#display-setup-script =
```

for me [FONT=courier new]backlightx --get current[/FONT] gives a number from 0 to 10 but [xbacklight](apt:xbaklight) assumes 0 to 100 due to this i multiple the value by 10 using [FONT=courier new]$((10*$val))[/FONT]
```
~$ cat /usr/local/bin/greeter-setup-script
#!/bin/bash
if [ -f /var/log/backlightx ];then
    val=$(cat /var/log/backlightx)
    if [ ${#val} -gt 0 ];then
        xbacklight -set $((10*$val))
    fi
fi
exit
```

```
~$ cat /usr/local/bin/session-cleanup-script
#!/bin/bash
backlightx --get current > /var/log/backlightx
```

```
~$ cat /usr/local/bin/backlightx 
#!/bin/bash
# Dependencies: coreutils sed grep

where="/sys/class/backlight/acpi_video0" # You may need to edit acpi_video0
max=`cat $where/max_brightness`
if [ -f "$where/actual_brightness" ];then
    current=`cat $where/actual_brightness`
else
    current=`cat $where/brightness`
fi
if [ "$1" == "--set" ] && [ -n "$2" ];then
    if [ ! "`echo $2 | sed 's/[a-Z]//g'`" == "$2" ];then
        `dirname $0`/`basename $0`
        exit
    elif [ 0`echo "$2" | sed 's/.//' | grep "^[0-9]*$"` -gt 0 ] && [ ! "`echo \"$2\" | grep \"^[0-9]*$\"`" == "$2" ];then
        if [ "`echo ${2:0:1}`" == "+" ];then
            X=$(($current+`echo ${2:1}`))
        elif [ "`echo ${2:0:1}`" == "-" ];then
            X=$(($current-`echo ${2:1}`))
        else
            echo "${2:0:1} is not a +/-"
            exit
        fi
        if [ $X -gt $max ];then
            echo $max > $where/brightness
        elif [ $X -lt 0 ];then
            echo 0 > $where/brightness
        else
            echo $X > $where/brightness
        fi
        exit
    fi
    if [ ! "`echo \"$2\" | grep \"^[0-9]*$\"`" == "$2" ];then
        echo "$2 is not a Intiger"
    elif [ "$2" -lt $(($max+1)) ] && [ "$2" -gt -1 ];then
        echo $2 > $where/brightness
    elif [ "$2" -lt 0 ];then
        echo 0 > $where/brightness
    else
        echo $max > $where/brightness
    fi
elif [ "$1" == "--get" ];then
    if [ "$2" == "current" ];then
        echo $current
    elif [ "$2" == "max" ];then
        echo $max
    else
        echo -e "Current: $current\nMaximum: $max"
    fi
else
    echo -e "Usage:\n\t`basename $0` --set Int | +Int | -Int"
    echo -e "\t`basename $0` --get current | max | NULL"
fi
exit
```

---

