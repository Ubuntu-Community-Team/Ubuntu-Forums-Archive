---
title: "Howto: CPU Frequency Scaling on Celeron M and Pentium 4 processors"
date: 2006-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by krazykit on 2006-06-06
As you may have noticed, Pentium M processors support Speedstep.  For whatever reason, Intel left Speedstep out of the budget Celeron M processors.  But you're in luck!  You can get CPU frequency scaling on Celeron M and Pentium 4 processors.

First off, you need to insert the p4_clockmod module.  Open a terminal and do
```
sudo modprobe p4_clockmod
```
This shouldn't give any feedback.

To make this module load every boot, add it to /etc/modules with your favorite editor ...it should look something like this
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

p4_clockmod
```

Now, as for the actual scaling, you have a few choices.  As far as I know, the two more popular CPU scaling daemons are cpufreqd and powernowd.  cpufreqd is very configurable and I'm not going to go into it here.  I'm sure there are better guides for cpufreqd out there than what I can whip up.  The other option (and my preference) is powernowd.  Basically, powernowd will scale back your clockspeed when crunching is low, and if it needs more processign power, will scale the clockspeed back up.  Check out the man page for more in-depth information.

Edit: since this post, through various research, it seems that this doesn't really confer significant power savings.  I ended up just not bothering, as it merely hampered performance for little or no benefit

---

### Post by madchicken on 2006-06-22
Thank you very much krazykit, this thing was driving me crazy.

Bye

---

### Post by tim202 on 2007-09-07
krazykit, you are a genius.  thank you so much for posting this.

---

### Post by mfdc1969 on 2007-09-09
Hi,

I'm new to Linux and this is only my 3rd install but I just tried this on my HP dv2402ca (Celeron M 520 @ 1.6 MHz) and the first step:

$ sudo modprobe p4_clockmod

resulted in this message:

FATAL: Error inserting p4_clockmod (/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/p4-clockmod.ko): No such device

Any suggestions or help would be greatly appreciated!

Thanks,
Mike

---

### Post by ggaaron on 2007-11-30
You don't have a processor supported by this module. This is why this error shows up.

---

### Post by ProteinPappa on 2008-11-21
(old thread)
I've got a good ol' Pentium 4 2.8 GHz desktop processor, and I got the p4_clockmod to work. However, all it seems to do is reduce performance, but the CPU temperature, and I assume therefore also power consumption, stays the same. Is there any way to change this, or is my processor too old?

Oh, and thank you very much for the guide.


Edit: after some more reading I have discovered that the primary use for p4_clockmod is to reduce the temperature when the computer is working at full load, ie it won't get as hot maxed out on 700 MHz as on 2.8 GHz, though of course performance suffers. Which leads me to another question; would it be possible to govern the frequency based on the temperature?

---

### Post by andersja on 2009-10-06
Anyone know how this works/performs under Ubuntu Karmic (9.10) ?

---

### Post by krazykit on 2009-10-06
It should work identically; that is, no or insignificant power savings, just performance loss.  Don't bother.

---

