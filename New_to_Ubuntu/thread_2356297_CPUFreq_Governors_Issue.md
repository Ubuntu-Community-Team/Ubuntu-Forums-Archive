---
title: "CPUFreq Governors Issue"
date: 2017-03-22
forum: New to Ubuntu
---

### Post by sara8 on 2017-03-22
Hi,

I'm using Ubuntu Mate 16.04. I like to set stable CPU speed in my PC. 

client@client:~$ sudo cpufreq-set -c 0 -f 2200Mhz

  Error setting new values. Common errors:
- Do you have proper administration rights? (super-user?)
- Is the governor you requested available and modprobed?
- Trying to set an invalid policy?
- Trying to set a specific frequency, but userspace governor is not available,
   for example because of hardware which cannot be set to a specific frequency
   or because the userspace governor isn't loaded?

Pls help me.

---

### Post by Doug S on 2017-03-23
To be able to help we would need to know which CPU frequency scaling driver and governor you are using. Example:```
doug@s15:~/c$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
doug@s15:~/c$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/COLOR]
powersave
powersave
powersave
powersave
powersave
powersave
powersave
powersave

```

---

### Post by sara8 on 2017-04-11
Thank you for your support. I solved the problem.

client@client:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
intel_pstate
intel_pstate
client@client:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
powersave
powersave

# sudo vi /etc/default/grub
Change the line like below 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_pstate=disable"

Run
# sudo update-grub
# sudo init 6

Then set the governor & frequency.

---

