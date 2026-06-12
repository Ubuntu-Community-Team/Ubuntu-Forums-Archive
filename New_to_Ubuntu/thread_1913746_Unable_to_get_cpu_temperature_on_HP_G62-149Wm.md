---
title: "Unable to get cpu temperature on HP G62-149Wm"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by allergygorilla23 on 2012-01-23
Hi guys, i'm setting up an HP G62-149Wm with ubuntu 10.04 64 bits and gnome, and i'm having problems detecting the sensors. I tried installing sensors-lm but when i run sensors-detect it shows

"Sorry, no sensors were detected.
This is relatively common on laptops, where thermal management is
handled by ACPI rather than the OS."
(all the results are negative)

The only thing that worked so far is installing the "computertemp" applet for gnome panel, and it only shows my HD temp. When i go to preferences, in "select sensor to monitor" i have 2 options, HDDTEMP and Kernel i2c sensors, the first one shows the hard drive temp correctly and the second one returns "no thermal zones" in the "select thermal zone" box. 

Why does the computertemp applet show a sensor that lm-sensors doesn't detect? 

Any help would be really appreciated.
Thanks in advance!

---

### Post by dargaud on 2012-01-23
My guess is that lm-sensor uses the i2c protocol while the other uses ACPI calls, hence the differeing results, but I'm no specialist on the subject.

---

### Post by allergygorilla23 on 2012-01-23
I've already installed acpi and acpitools, and neither detect anything on either fan speed or thermal information (acpitools -t returns "no thermal information found")

Any ideas?

---

### Post by sandyd on 2012-01-23
> **fede333lago said:**
> Hi guys, i'm setting up an HP G62-149Wm with ubuntu 10.04 64 bits and gnome, and i'm having problems detecting the sensors. I tried installing sensors-lm but when i run sensors-detect it shows

"Sorry, no sensors were detected.
This is relatively common on laptops, where thermal management is
handled by ACPI rather than the OS."
(all the results are negative)

The only thing that worked so far is installing the "computertemp" applet for gnome panel, and it only shows my HD temp. When i go to preferences, in "select sensor to monitor" i have 2 options, HDDTEMP and Kernel i2c sensors, the first one shows the hard drive temp correctly and the second one returns "no thermal zones" in the "select thermal zone" box. 

Why does the computertemp applet show a sensor that lm-sensors doesn't detect? 

Any help would be really appreciated.
Thanks in advance!
Weird.
Temperature for Core ix series is managed by coretemp.
Should be detected by lm_sensors

---

### Post by allergygorilla23 on 2012-01-23
Yes, i also tried everything on here [http://ubuntuforums.org/showthread.php?t=1576310](http://ubuntuforums.org/showthread.php?t=1576310) (same processor) and nothing worked, i'm thinking maybe its a bug for this processor?

---

### Post by allergygorilla23 on 2012-01-25
Any new ideas on this matter?

---

