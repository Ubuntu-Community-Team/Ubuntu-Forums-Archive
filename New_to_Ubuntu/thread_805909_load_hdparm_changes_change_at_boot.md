---
title: "load hdparm changes change at boot"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by SpinningAround on 2008-05-24
Since I got some problem with the load_cycle_count do i use hdparm -210 during battery power I do the change in the terminal, but I would like to make it so the changes are applied when i boot the computer. A side question is there something else I should know regarding the load_cycle_count?

---

### Post by unutbu on 2008-05-24
Have you read [http://ubuntuforums.org/showthread.php?t=591503?](http://ubuntuforums.org/showthread.php?t=591503?)
I know nothing about the load_cycle_count issue, but if you wish to run a command at boot, here is how you can do it:

```
gksudo gedit /etc/rc.local
```

Put the command you wish to run *above* the "exit 0" line.

I suspect you know, but it bears repeating that hdparm is a dangerous program -- if you use it improperly you can damage your hard drive.

---

### Post by sleepingdragon on 2008-05-24
I'm not sure about the load_cycle_count, but hdparm typically uses the flag *-k1* to keep its' settings. i.e., *sudo hdparm -k1 -d1 /dev/sda *

---

