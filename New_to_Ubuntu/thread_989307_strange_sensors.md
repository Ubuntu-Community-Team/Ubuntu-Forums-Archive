---
title: "strange sensors ?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by krtica on 2008-11-21
Does this look ok?

alen@Tribut:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +44.0°C  (crit = +105.0°C)                  
temp2:       +31.3°C  (crit = +108.0°C)                  
temp3:       +50.0°C  (crit = +110.0°C)                  
temp4:       +50.0°C  (crit = +256.0°C)                  
temp5:       +44.0°C  (crit = +108.0°C) 

Are those critical temps too high?
especialy this +256.0°C...

---

### Post by krtica on 2008-11-21
XSensors doesn't work.
None of gDesklets regarding temperature (CPU/HD) doesn't show anything.

---

### Post by cariboo on 2008-11-21
Have you tried the sensors applet. That's what I use it looks like the sensors on your motherboard are not supported. This is what mine looks like. See screenshot.

Jim

---

### Post by krtica on 2008-11-21
Thank you for an answer.

Is this dangerous if my sensors doesn't work? :shock:

I tried:
[http://ubuntuforums.org/showthread.php?t=92504](http://ubuntuforums.org/showthread.php?t=92504)
[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)
and
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Now I have:

$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +44.0°C  (crit = +105.0°C)                  
temp2:       +26.9°C  (crit = +108.0°C)                  
temp3:       +50.0°C  (crit = +110.0°C)                  
temp4:       +45.0°C  (crit = +256.0°C)                  
temp5:       +44.0°C  (crit = +108.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +46.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +46.0°C  (high = +100.0°C, crit = +100.0°C)  

And Sensor Applet reporting CPU temp ~27C...

There are also some TZ0, TZ1, TZ3, TZ4 and TZ5 (there is no TZ2) sensors in acpi section of Sensor tab of Sensor Applet Preferences window , and some temp1, temp2 (CPU), temp3, temp4 and temp5 in i2c-sys section...

Is there anyone to tell me is it ok, and do I need to do something about this?
:shock:

---

### Post by krtica on 2008-11-21
I also found this line during
**$ sudo sensors-detect**

Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x3600


Need some advice, please... :(

---

### Post by krtica on 2008-11-21
I observed Sensor Applet for some (long) time... :D

Does this have any sense? :confused:

**TZO** and **temp4** -- ~50°C -- [COLOR="Red"]mainbord/chipset?[/COLOR]
**TZ1** and **temp5** -- ~55°C-59°C -- [COLOR="Red"]CPU?[/COLOR]
**TZ2** --- does not exist
**TZ3** and **temp1** -- 1-2°C more or less then TZ1 and temp5 -- [COLOR="Red"]other CPU?[/COLOR] (Core2Duo)
**TZ4** and **temp2** -- 27°C ([COLOR="Red"]???[/COLOR])
**TZ5** and **temp3** -- 0°C when fan quiet, 50°C when I hear it -- [COLOR="Red"]CPU Fan?[/COLOR]

:confused:

PS: This is HP 550 laptop.

---

