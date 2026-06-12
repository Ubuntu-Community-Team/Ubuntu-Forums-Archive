---
title: "Can't understand CPU Scaling site"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by FOBoi1122 on 2008-06-03
So I am using a reference site to set up my Fujitsu T4220 Tablet, and under DSDT CPU Scaling, I'm not quite understanding the directions. For example, i don't know what (version string here) means,  or how to find (where you saved "initrd-add-dsdt"). Also the instructions say to save an image. If i do screw up, how do i revert back to the image? Thanks for your help.

---

### Post by sdennie on 2008-06-03
I'm not completely sure what you are asking.  However, custom DSDT solutions should only be used if you are absolutely positive you are having a problem and that a custom DSDT is the only way to fix it.  I'll happily help you do custom DSDT stuff if you are positive you need it but, you'll have to be more specific about exactly what your problem is.

---

### Post by FOBoi1122 on 2008-06-03
Right now, i think a lot of people are having this problem, which is that running linux on a T4220 gives only 800Mhz instead of the full 1.83Ghz it's suppose to, so the CPU is scaled down, and i haven't found a better solution to scale it back up. I'm not sure how to check my clock speed or anything so if u have some help with that too, that'd be great.

---

### Post by unutbu on 2008-06-03
Please post:
```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

---

### Post by FOBoi1122 on 2008-06-03
jay@jay-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
ondemand powersave userspace conservative performance 
jay@jay-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
ondemand


that's what i got

---

### Post by sdennie on 2008-06-03
The output of the following might also be useful:

```

cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq

```

---

### Post by FOBoi1122 on 2008-06-03
here's what i get:

jay@jay-laptop:~$ sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq
1801000
jay@jay-laptop:~$ sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
800000

---

### Post by sdennie on 2008-06-03
That's a good sign.  I would try this:

```

sudo apt-get install powertop
sudo powertop

```

Watch the top right of the screen and see if the CPU is ever switching frequencies.

---

### Post by FOBoi1122 on 2008-06-03
doing that right now. exactly what does powertop do? 
*edit, my laptop is dual core

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (23.3%)         1.81 Ghz     0.0%
C1                0.0ms ( 0.0%)         1.80 Ghz     0.0%
C2                0.2ms ( 0.9%)         1200 Mhz     0.0%
C3                1.3ms (75.8%)          800 Mhz   100.0%


Wakeups-from-idle per second : 648.5    interval: 10.0s
Power usage (ACPI estimate): 18.5W (1.5 hours)

Top causes for wakeups:
  35.1% (379.2)      <kernel IPI> : Rescheduling interrupts 
  15.1% (163.2)              java : futex_wait (hrtimer_wakeup) 
   7.9% ( 84.9)       <interrupt> : i915@pci:0000:00:02.0 
   7.1% ( 76.5)              java : schedule_timeout (process_timeout) 
   7.1% ( 76.4)           firefox : schedule_timeout (process_timeout) 
   6.2% ( 66.6)       <interrupt> : extra timer interrupt 

Suggestion: Enable SATA ALPM link power management via:
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.


and i ran it again...

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 7.2%)         1.81 Ghz     0.0%
C1                0.0ms ( 0.0%)         1.80 Ghz     0.0%
C2                0.1ms ( 0.1%)         1200 Mhz     0.0%
C3                2.2ms (92.7%)          800 Mhz   100.0%


Wakeups-from-idle per second : 432.8    interval: 3.0s
Power usage (ACPI estimate): 17.2W (1.4 hours) (long term: 22.2W,/1.1h)

Top causes for wakeups:
  44.3% (270.7)      <kernel IPI> : Rescheduling interrupts 
  15.1% ( 92.3)           firefox : schedule_timeout (process_timeout) 
  11.3% ( 69.0)       <interrupt> : i915@pci:0000:00:02.0 
   5.5% ( 33.3)       <interrupt> : extra timer interrupt 
   5.0% ( 30.7)   USB device  3-1 : Microsoft 3-Button Mouse with IntelliEye(TM)
   4.4% ( 27.0)       <interrupt> : uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3,
 uhci_hcd:usb4, uhci_hcd:usb5 
Suggestion: increase the VM dirty writeback time from 0.30 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
This wakes the disk up less frequenty for background VM activity

---

### Post by FOBoi1122 on 2008-06-03
bump?

---

### Post by unutbu on 2008-06-03
FOBoi1122, 

In a terminal run
```
watch -n 1 cat /sys/devices/system/cpu/*/cpufreq/scaling_cur_freq

```
You'll see a number (or numbers) representing the current clock speed of your CPU (or CPUs). 

Now run something with is CPU intensive, like glxgears. Does the CPU clockspeed jump to 1800000? If so, "on demand" scaling_governor is acting the way it should. I wouldn't recommend changing it. 

On the other hand, if it is stuck at 800000, perhaps try this:

Open a second terminal, and type
```

echo performance | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
Does the CPU clock speed jump to 1800000 in the first terminal window?

---

### Post by FOBoi1122 on 2008-06-03
sorry, no luck there :( 

I ran it, and both running and not running glxgears, i get 800000, 800000

when i try the next step, i get:

jay@jay-laptop:~$ echo performance | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
[sudo] password for jay: 
performance

and when i checked back at my window, i still got 
800000, 800000 every second

---

### Post by unutbu on 2008-06-03
Sorry, you've reach the end of my very limited knowledge.

---

### Post by sdennie on 2008-06-03
Powertop is a tool to tell you interesting things about what your CPU is doing (mostly in regards to power savings).  Unfortunately, in your case, it is indeed saying that the CPU is never going above 800Mhz so, your DSDT fix may actually be needed if it's known to work.

---

### Post by FOBoi1122 on 2008-06-03
Thanks for the reply, right now, i'm trying to follow the instructions for CPU scaling, but one of the links are dead. does anyone know how i could get in contact with the laptop testing team or find the working link? it's [http://ginkel2.boerde.de/Lifebook_4220/lt4220.tgz](http://ginkel2.boerde.de/Lifebook_4220/lt4220.tgz)

---

### Post by raccoonone on 2008-08-20
> **FOBoi1122 said:**
> Thanks for the reply, right now, i'm trying to follow the instructions for CPU scaling, but one of the links are dead. does anyone know how i could get in contact with the laptop testing team or find the working link? it's [http://ginkel2.boerde.de/Lifebook_4220/lt4220.tgz](http://ginkel2.boerde.de/Lifebook_4220/lt4220.tgz)

I'm looking for the updated DSDT file too. Anyone know where I can get it?

---

