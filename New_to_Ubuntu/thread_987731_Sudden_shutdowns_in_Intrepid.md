---
title: "Sudden shutdowns in Intrepid"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Brantai on 2008-11-19
I just did a fresh install of 8.10 Desktop and had managed to get everything working, but it's started shutting down suddenly whenever the CPU is being used intensively.
This is a dual-boot xp/linux HP Pavillion dv2000, and I've tried running it with all three versions of the proprietary NVIDIA drivers available in the Hardware Drivers menu, as well as with none of them enabled, with and without desktop effects.

Every time I'd change the configuration, start it up and start playing OpenArena, and after a few minutes it would go to the shutdown screen and power off.

I'd assume it's a hardware issue, but this only happens in Ubuntu (ran fine in Windows all day), and only started after I wiped my Hardy install and installed Intrepid.

Here's the output from my reboots:

```
brantai@laptop:~$ last reboot
reboot   system boot  2.6.27-7-generic Wed Nov 19 17:49 - 18:08  (00:19)    
reboot   system boot  2.6.27-7-generic Tue Nov 18 18:53 - 19:55  (01:02)    
reboot   system boot  2.6.27-7-generic Tue Nov 18 18:47 - 18:52  (00:04)    
reboot   system boot  2.6.27-7-generic Tue Nov 18 17:30 - 18:38  (01:08)    
reboot   system boot  2.6.27-7-generic Tue Nov 18 16:27 - 17:27  (01:00)    
reboot   system boot  2.6.27-7-generic Tue Nov 18 15:59 - 16:02  (00:03)    
reboot   system boot  2.6.27-7-generic Mon Nov 17 22:44 - 23:00  (00:15)    
reboot   system boot  2.6.27-7-generic Mon Nov 17 21:34 - 21:50  (00:16)    
reboot   system boot  2.6.27-7-generic Mon Nov 17 20:05 - 21:33  (01:27)    
reboot   system boot  2.6.27-7-generic Mon Nov 17 18:02 - 18:41  (00:39)    
reboot   system boot  2.6.27-7-generic Mon Nov 17 17:49 - 18:01  (00:11)    
reboot   system boot  2.6.27-7-generic Sun Nov 16 23:10 - 17:46  (18:35)    
reboot   system boot  2.6.27-7-generic Sun Nov 16 20:49 - 22:59  (02:09)    
reboot   system boot  2.6.27-7-generic Sun Nov 16 10:16 - 20:40  (10:23)    
reboot   system boot  2.6.27-7-generic Sun Nov 16 01:57 - 02:49  (00:52)    
reboot   system boot  2.6.27-7-generic Sat Nov 15 20:58 - 01:56  (04:58)    
reboot   system boot  2.6.27-7-generic Sat Nov 15 07:26 - 20:57  (13:30)    

wtmp begins Sat Nov 15 07:26:16 2008
```

And here's the last few shutdowns from /var/log/messages:

```
Nov 18 17:07:29 laptop -- MARK --
Nov 18 17:27:29 laptop -- MARK --
Nov 18 17:27:55 laptop kernel: [ 3647.024287] ACPI: Critical trip point
Nov 18 17:27:55 laptop kernel: [ 3647.339084] pidgin[6106]: segfault at 11 ip b7c1ae6a sp bffb1190 error 4 in libgtk-x11-2.0.so.0.1400.4[b79cf000+395000]
Nov 18 17:27:56 laptop bonobo-activation-server (brantai-8436): could not associate with desktop session: Failed to connect to socket /tmp/dbus-jTso6QEdiA: Connection refused
Nov 18 17:27:57 laptop kernel: [ 3649.036359] apm: BIOS not found.
Nov 18 17:28:03 laptop kernel: [ 3655.148340] ip6_tables: (C) 2000-2006 Netfilter Core Team
Nov 18 17:28:06 laptop exiting on signal 15


Nov 18 17:50:20 laptop -- MARK --
Nov 18 18:10:20 laptop -- MARK --
Nov 18 18:30:20 laptop -- MARK --
Nov 18 18:38:34 laptop kernel: [ 4114.600460] apm: BIOS not found.
Nov 18 18:38:40 laptop kernel: [ 4120.733793] ip6_tables: (C) 2000-2006 Netfilter Core Team
Nov 18 18:38:42 laptop exiting on signal 15

Nov 18 19:13:02 laptop -- MARK --
Nov 18 19:33:02 laptop -- MARK --
Nov 18 19:53:02 laptop -- MARK --
Nov 18 19:55:22 laptop kernel: [ 3761.206591] ACPI: Critical trip point
Nov 18 19:55:28 laptop kernel: [ 3767.718999] apm: BIOS not found.
Nov 18 19:55:36 laptop kernel: [ 3775.626557] ip6_tables: (C) 2000-2006 Netfilter Core Team
Nov 18 19:55:37 laptop kernel: [ 3776.214010] ACPI: Critical trip point
Nov 18 19:55:40 laptop exiting on signal 15
```

I'm pretty sure the answer is in there, but I don't know enough to figure it out.  Any thoughts?

---

### Post by drascus on 2008-11-19
It looks to me as though your ACPI trip point need to be modified in some way. If I understand right that at a certain point your computer is using enough resources to trip the ACPI and cause your computer to shutdown. you may be able to modify something to allow you to use that amount of resources without a shutdown. here others seem to be having a similar issue
[http://ubuntuforums.org/showthread.php?t=968754&highlight=ACPI+modification](http://ubuntuforums.org/showthread.php?t=968754&highlight=ACPI+modification)

---

### Post by Brantai on 2008-11-23
I've tried swapping powernowd out for cpufreqd (since my processor seems to only support two voltages, anyway) and turned off all of the configurable trip points (UPS out of power, battery out of power, lid closed, etc) and it's still doing it.  I added a CPU and voltage monitor to my gnomebar and it seems that it typically happens when it's at the higher voltage and using a lot of CPU.
Normally, I'd assume that pointed to the hardware, but it worked fine in Hardy and continues to work fine in XP.
Any other ideas?  Other places to check the ACPI config?

Edit: Also tried running it on AC without the battery in, to no avail.

---

### Post by jnorthr on 2008-11-23
any chance this is a temperature-related issue ? maybe it over-heats when stressed ?

---

### Post by Brantai on 2008-11-23
> **jnorthr said:**
> any chance this is a temperature-related issue ? maybe it over-heats when stressed ?

That really was my first thought, since I've had a desktop go that way before due to a broken GPU fan.  I don't know why it would be running hotter in intrepid when I'm surfing the net and playing cards than it would in XP when I'm playing oblivion, though.

---

### Post by kafkaian on 2009-01-07
This has happened to mine since 8.04. Dapper was the most reliable with my hardware configuration.

I have issued bug reports but to no avail.

I just want something reliable and don't have the time to mess around - so ultimately I may now be forced to ditch Ubuntu. Great pity really.

---

### Post by waspbr on 2009-01-07
longshot, but have you tried updating your bios?

---

