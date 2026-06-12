---
title: "CPU Frequency Scaleing Indicator"
date: 2014-12-14
forum: New to Ubuntu
---

### Post by Glkanter on 2014-12-14
Hi,

I recently, and reluctantly, ugraded to 14.04. Just not a Unity fan, I'm afraid.

Under 11.04 I used four instances of CPU Frequency Scaler Indicator to set each of the four CPUs to the highest speed. Each was configurable so each instance controlled a different processor, 0 -  3.

Under 14.04, I don't have any configuration options. So while I'm setting "it" to the highest speed, there may be three other processors that haven't been set. I'm really not sure.

I'd appreciate any help, work-arounds, or substitute programs.

Thanks!

Garry

---

### Post by Yellow Pasque on 2014-12-15
Note: I don't use Unity
Do you have different physical CPU's or are you just talking about one quad core CPU? 

I think the easiest way to check is using cpufreq-info. See what the governor is set to for each core when you start the system. Then, set "it" to highest speed and check cpufreq-info again. Hopefully, they'll all be using the performance governor.
```
cpufreq-info
```




sudo cpufreq-set -g perfromance

---

### Post by Glkanter on 2014-12-15
It's a quad core cpu.
I just installed "cpufreq" but can't find it on any menu.

---

### Post by Yellow Pasque on 2014-12-15
> I just installed "cpufreq" but can't find it on any menu. 
So the cpufreq-info command doesn't work? Not sure what you mean by 'menu' because it's not a GUI program.

---

### Post by sandyd on 2014-12-15
> **Glkanter said:**
> It's a quad core cpu.
I just installed "cpufreq" but can't find it on any menu.

Open a terminal (Unity Dash -> Type in 'Terminal')
Post the output of the following command. The command will show your current cpu frequency scaling settings.
```

cpufreq-info
```

---

### Post by Glkanter on 2014-12-15
That did it, thanks!
All 4 are ove 99% at maximum.

---

