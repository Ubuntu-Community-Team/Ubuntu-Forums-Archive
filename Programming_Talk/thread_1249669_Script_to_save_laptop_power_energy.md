---
title: "Script to save laptop power energy"
date: 2009-08-25
forum: Programming Talk
---

### Post by pi4r0n on 2009-08-25
Hello ALL

It might be really really dummy question/idea but are they any scripts that can save energy of our laptops.

What I mean is to have a scrip that will read battery information and if better is to low (lets say 10%) then it will turn it on and if its fully charged to switch it off ??

If this post is too dummy then do not hesitate to delete it :)

Cheers

pi4r0n

---

### Post by pepperphd on 2009-08-25
Have you taken a look at this?

[http://spidertools.com/ub_power.php](http://spidertools.com/ub_power.php)

---

### Post by pi4r0n on 2009-08-26
Looks OK **pepperphd** but what I am really interested (need) is some kind of information about power plug in laptops


[LIST]
[*]How the ubuntu system know that power cable is pluged or unpluged
[/LIST]
So what i would like to do is to have a scrip to run in cron every 5 min to check battery status based on acpi output and in batery was full charged then the script would send some kind of message to ubuntu saying there is no power cable pluged in and systm will use bater at this stage and if batter was 10% then again send message saying there is a power cable pluged in 

Do you know what i mean if not I can explane bit more :)

Cheers

Arek

---

### Post by eldragon on 2009-08-26
you are asking for laptop-mode-tools.

its more than just a script, but it does what you want.

acpi is the one responsible for detecting AC/Battery status.

anyway, check laptop-mode-tools.

---

### Post by TheStatsMan on 2009-08-26
[http://ubuntuforums.org/showthread.php?t=988309](http://ubuntuforums.org/showthread.php?t=988309)

---

