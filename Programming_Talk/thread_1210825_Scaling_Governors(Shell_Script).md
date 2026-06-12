---
title: "Scaling Governors(Shell Script)"
date: 2009-07-11
forum: Programming Talk
---

### Post by Finalfantasykid on 2009-07-11
I have been trying to get my laptop to change the scaling governors from Performance to OnDemand when it changes from AC to Battery.  So far I have had no success(on older versions of Ubuntu I believe you could 8.04 and below, but I use 9.04).

So I figured I would make my own little shell script to do this.  I didn't know shell scripting more than 3 hours ago, so if I made some blatant syntax mistakes/poor programming practices forgive me.

```
if on_ac_power
then
    last=0
else
    last=1
fi

while true; do
    if on_ac_power
    then
        current=0
    else
        current=1
    fi
    if test $current -ne $last
    then
        if test 0 -eq $last
        then
            last=1
        else
            last=0
        fi
        if on_ac_power
        then
            cpufreq-selector -c 0 -g performance
            cpufreq-selector -c 1 -g performance 
        else
            cpufreq-selector -c 0 -g ondemand
            cpufreq-selector -c 1 -g ondemand 
        fi
    fi
    sleep 5;
done
exit 0
```

This only works if you have done "sudo dpkg-reconfigure gnome-applets" and selected yes.

There is a problem with this code though.  For some reason there is a massive delay between cpufreq-selector calls, like 10 seconds at least, which means that it the change doesn't happen immediatly.  And if I put "cpufreq-selector -c 0 -g ondemand &" with the ampersand for example, it will sometimes spit out a ton of warnings saying something like the system bus is full.

Anyways.  I'd like to use this as a startup application, that way it will properly scales the cpus depending on the situation.  Any advice on this would be greatly appreciated.

---

