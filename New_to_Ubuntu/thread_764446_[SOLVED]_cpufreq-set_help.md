---
title: "[SOLVED] cpufreq-set help"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by drewster1829 on 2008-04-23
When I use cpufreq-set to change my CPU scaling setting on my Toshiba Satellite M55, it saves the governor setting I use (ondemand) and the maximum speed (1.73 GHz), but resets the minimum speed on reboot to 1.73 GHz.  I have to manually type in:

sudo cpufreq-set -d 800M

Every time I start the system to reset the minimum CPU speed.  Is there a way I can do this automatically somehow?  Thanks.

---

### Post by Tatty on 2008-04-23
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

the last step shows you how to do that.

---

### Post by drewster1829 on 2008-04-24
> **Tatty said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

the last step shows you how to do that.

Thanks...I think that guide is a bit out of date (I'm using Gutsy..sorry I didn't mention it before), as the filed I was looking for is /etc/init.d/cpufrequtils.

The valid section is:

```

ENABLE="true"
GOVERNOR="ondemand"
MAX_SPEED="0"
MIN_SPEED="0"

```

Notice that Enable is already set to true, but I edited the max and min speeds to "1730" and "800" respectively.  I'll test it and see if that fixed it.

---

### Post by spiderbatdad on 2008-04-24
You may need to manually add the module to /etc/modules file. For example if yours is the powernow-k7 module, add that to the list.

---

### Post by drewster1829 on 2008-04-24
I didn't read this part in /etc/init.d/cpufrequtils:

```
# Both MIN_SPEED and MAX_SPEED must be values
# listed in:
#   cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
# a value of 0 for any of the two variables will disabling the use of 
# that limit variable.
```

The output of cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies is:

```
drew@drew-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
1733000 1333000 1067000 800000
```

By editing the appropriate part of the file to this:

```
ENABLE="true"
GOVERNOR="ondemand"
MAX_SPEED="1733000"
MIN_SPEED="800000"
```

It is fixed.  Now the minimum speed is at 800 MHz at boot.

For others having this problem, [here]("http://ubuntuforums.org/showthread.php?t=762610&highlight=cpufreq-set")'s another possible solution (esp. if using xubuntu).

---

### Post by drewster1829 on 2008-06-23
It would still change sometimes, mainly when switching from AC to battery (and back) or recovering from restore.  Here's another useful fix I've found:

[http://ubuntuforums.org/archive/index.php/t-762610.html]("http://ubuntuforums.org/archive/index.php/t-762610.html")

---

