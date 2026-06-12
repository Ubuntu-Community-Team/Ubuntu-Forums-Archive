---
title: "laptop does not shutdown on critical"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by !ndy on 2008-08-15
hi, 

my laptop does not shut down properly on critical. 
it just dies out in one second. 
i was trying to setup the power management, but nothing helps.
even when charging or dicharging, i see just the percentage and unknown time? i would like to see the real time :-)

thx in advance

---

### Post by wolfen69 on 2008-08-15
what do you mean by "on critical"?

---

### Post by Ptero-4 on 2008-08-15
> **wolfen69 said:**
> what do you mean by "on critical"?

When the battery is running out of charge (like 5%).

---

### Post by !ndy on 2008-08-15
i do not really know myself :-)

i just want the computer to do "something", when battery looses power.
i do not want all my usaved work to get lost. 
that is what is happening now. 
i would like something like in windows -- "wait please ... system preparing to standby" or something like that. 
that is quite usual with laptops also in linux systems, i suppose?

thank you

---

### Post by anotherdisciple on 2008-08-15
Under (System > Preferences > Power Management) you have the option to make it turn off, suspend, etc. when battery power is low.

[IMG]http://www.ubuntu.com/files/GutsyImages/Power-Management-Prefs.jpg[/IMG]

Have you tried playing with that option?

---

### Post by !ndy on 2008-08-15
i was thinking about somthing like this:

- setting up the level of "critical". maybe my laptop does not understand, what critical is... and what to do, when it IS critical

i did some research:
[http://ubuntuforums.org/showthread.php?t=487258](http://ubuntuforums.org/showthread.php?t=487258)
and this may be a good script for auto-hibernation, if someone confirms:
[http://www.filewatcher.com/p/acpi-support_0.21_amd64.deb.19282/etc/acpi/hibernate.sh.html](http://www.filewatcher.com/p/acpi-support_0.21_amd64.deb.19282/etc/acpi/hibernate.sh.html)
hope this also serves to someone someday :-)

thank you, guys!

---

### Post by Ptero-4 on 2008-08-15
Did you have to pass any of the usual flags (pci=noacpi, acpi=off, noapic, nolapic) to grub to boot your computer properly? Those flags disable acpi support which removes those power management options. You may try to remove them one by one and reboot after each one you remove to see if you can get to a point where it reboots and power management works as you want.

---

