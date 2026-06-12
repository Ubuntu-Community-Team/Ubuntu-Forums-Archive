---
title: "I'm having problems with PowerTOP"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2008-05-28
i've been trying to tweak my laptop to get as much battery life as possible (i'm up to about 20 minutes now! but i've got a replacement battery on the way)

i've been having some issues with the settings not "sticking" i'll hit the button indicated to make the changes, but then the same prompt comes up a few minutes later. why aren't the settings staying?

```
     PowerTOP version 1.9       (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 4.3%)         1.67 Ghz   100.0%
C1                0.0ms ( 0.0%)         1333 Mhz     0.0%
C2                6.4ms (11.8%)         1000 Mhz     0.0%
C3                5.0ms (83.8%)


Wakeups-from-idle per second : 187.2    interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
  44.2% (114.2)      <kernel IPI> : Rescheduling interrupts 
  20.2% ( 52.2)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   6.3% ( 16.2)       <interrupt> : extra timer interrupt 
   6.0% ( 15.4)       <interrupt> : iwl3945 
   6.0% ( 15.4)           firefox : futex_wait (hrtimer_wakeup) 
   5.1% ( 13.2)       <interrupt> : libata 

Suggestion: Disable 'hal' from polling your cdrom with:
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a

 **Q - Quit**   **R - Refresh**   **K - kill hald-addon-storage** 
```

```
     PowerTOP version 1.9       (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (11.6%)         1.67 Ghz   100.0%
C1                0.0ms ( 0.0%)         1333 Mhz     0.0%
C2                1.9ms (10.2%)         1000 Mhz     0.0%
C3                2.1ms (78.2%)


Wakeups-from-idle per second : 423.6    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  49.6% (326.2)      <kernel IPI> : Rescheduling interrupts 
  27.6% (181.4)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   5.0% ( 32.8)       <interrupt> : extra timer interrupt 
   3.8% ( 25.1)           firefox : futex_wait (hrtimer_wakeup) 
   3.6% ( 23.9)       <interrupt> : iwl3945 
   2.7% ( 17.8)       <interrupt> : acpi 

Suggestion: Enable the ondemand cpu speed governor for all processors via:
 echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

 **Q - Quit**   **R - Refresh**   **O - enable Ondemand governor**
```

```
     PowerTOP version 1.9       (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 5.9%)         1.67 Ghz   100.0%
C1                0.0ms ( 0.0%)         1333 Mhz     0.0%
C2                3.3ms (17.0%)         1000 Mhz     0.0%
C3                4.1ms (77.1%)


Wakeups-from-idle per second : 241.5    interval: 5.0s
no ACPI power usage estimate available

Top causes for wakeups:
  60.4% (241.8)      <kernel IPI> : Rescheduling interrupts 
   7.5% ( 30.0)       <interrupt> : extra timer interrupt 
   7.4% ( 29.6)       <interrupt> : acpi 
   6.6% ( 26.4)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   3.9% ( 15.6)           firefox : futex_wait (hrtimer_wakeup) 
   3.7% ( 15.0)       compiz.real : schedule_timeout (process_timeout) 

Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
This wakes the disk up less frequenty for background VM activity
 **Q - Quit**   **R - Refresh**   **W - Increase Writeback time**
```

i've tried simply copy/pasting the suggested command into another terminal window, but it says "permission denied"

```
ryan@ryan-laptop:~$ sudo echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Permission denied
```

```
ryan@ryan-laptop:~$ sudo echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
bash: /proc/sys/vm/dirty_writeback_centisecs: Permission denied
```

it seems one worked:
```
ryan@ryan-laptop:~$ sudo hal-disable-polling --device /dev/cdrom
[sudo] password for ryan: 
Following symlink from /dev/cdrom to /dev/scd0.
Polling for drive /dev/cdrom have been disabled. The fdi file written was
  /etc/hal/fdi/information/media-check-disable-storage_model_DVD_RW_DVR_K06RS.fdi
```

what should i do to make these suggestions stick?

---

### Post by ethoxyethaan on 2008-05-28
if you diden't already. try typing 'sudo powertop'

if that wont solve it try

'sudo su' then 'powertop'

or c&p the commands in root shell with sudo su aswell.

maybe it has somthing to do with the chmode of the directory try and post the output.

---

### Post by sayakb on 2008-05-28
```
sudo chmod +w /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
And try again. Similarly, for the other file.

If this doesn't work, try
```
sudo chown username:group filename
```

---

### Post by unutbu on 2008-05-28
Sonic Reducer, this avoids the 'permission denied' problem:
```
sudo su
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
hal-disable-polling --device /dev/cdrom
```

If you want to make these permanent, 

```
gksu gedit /etc/rc.local
```
Put the three commands at the end of the file, but *above* the "exit 0" line.

I found this here:
[http://ubuntuforums.org/archive/index.php/t-306986.html](http://ubuntuforums.org/archive/index.php/t-306986.html)
[http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling](http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling)

---

