---
title: "ACPI problem? battery problem?"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by moonbat% on 2008-06-19
im running 8.04 on my dell inspiron e1505 laptop.  ive been having power problems for a while, which i thought were related to my old, frayed power adapter.

now that ive bought a new one, which works fine, i still have the same power problem.  whenever i unplug my adapter, my laptop shuts down after one or two minutes.  also, whenever i unplug my adapter, the red emergency losing power LED on my laptop flashes.  

i installed powertop to look at what went on inside my laptop and this is what came out:

```
PowerTOP version 1.9       (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (21.0%)         1.84 Ghz     9.6%
C1                0.0ms ( 0.0%)         1333 Mhz     0.0%
C2                0.4ms ( 3.9%)         1000 Mhz    90.4%
C3                0.9ms (75.0%)


Wakeups-from-idle per second : 915.7    interval: 5.0s
[COLOR="Red"]no ACPI power usage estimate available[/COLOR]

Top causes for wakeups:
  39.4% (601.0)      <kernel IPI> : Rescheduling interrupts 
  11.5% (176.0)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   7.4% (112.8)       <interrupt> : eth0 
   6.8% (103.6)           firefox : schedule_timeout (process_timeout) 
   6.6% (100.0)       <interrupt> : uhci_hcd:usb4 
   6.6% (100.0)   /sys/bus/usb/devices/4-2 

Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
This wakes the disk up less frequenty for background VM activity
```    

wtf?  is it an acpi problem or a battery problem?  help plz.

---

### Post by sdennie on 2008-06-19
What is the output of:

```

cat /proc/acpi/battery/*/info

```

---

### Post by Het Irv on 2008-06-19
How old is the battery in your Laptop, and over its lifetime did you ever run it down all the way?  If so how often?  Alot of times the battery will lose its ability to hold a charge after a while.  One of the things you can do to extend the life of your battery is to run it all the way down and recharged it every so often.

---

