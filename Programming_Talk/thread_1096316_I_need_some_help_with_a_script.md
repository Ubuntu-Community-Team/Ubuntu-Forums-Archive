---
title: "I need some help with a script"
date: 2009-03-14
forum: Programming Talk
---

### Post by gletob on 2009-03-14
Ok I'm looking to have a script that runs on boot that sets my bios RTC Alarm to boot the pc at 5:00:00 (Eastern Standard with Daylight saving).  

I've been reading this guide about RTC Alarm in Mythbuntu but I'm on ubuntu.

[http://www.mythtv.org/wiki/ACPI_Wakeup#Initiate_manually_2](http://www.mythtv.org/wiki/ACPI_Wakeup#Initiate_manually_2)

I followed the initialize manually instructions and it works.

---

### Post by gletob on 2009-03-14
Ok I'm looking to have a script that runs on boot that sets my bios RTC Alarm to boot the pc at 5:00:00 (Eastern Standard with Daylight saving).

I've been reading this guide about RTC Alarm in Mythbuntu but I'm on ubuntu.

[http://www.mythtv.org/wiki/ACPI_Wake...ate_manually_2](http://www.mythtv.org/wiki/ACPI_Wake...ate_manually_2)

I followed the initialize manually instructions and it works.

---

### Post by gletob on 2009-03-14
Anyone????

---

### Post by Eisenwinter on 2009-03-14
_[Start reading]("http://tldp.org/LDP/abs/html/")_

;)

---

### Post by unutbu on 2009-03-14
Put this in /usr/local/bin/wake_tomorrow
[PHP]
#!/usr/bin/env python
import datetime
import os
now=datetime.date.today()
oneday=datetime.timedelta(days=1)
tomorrow=now+oneday
morning=datetime.datetime(tomorrow.year,tomorrow.month,tomorrow.day,5,0,0)
os.system('echo %s > /sys/class/rtc/rtc0/wakealarm'%morning.strftime('%s'))
[/PHP]
Make it executable:```

chmod 755 /usr/local/bin/wake_tomorrow
```

Run 
```

sudo /usr/local/bin/wake_tomorrow
cat /sys/class/rtc/rtc0/wakealarm
cat /proc/driver/rtc
```

to see if it set the alrm_date and alrm_time as desired.
If everything looks fine, then next, edit /etc/rc.local by putting 
[PHP]
/usr/local/bin/wake_tomorrow[/PHP]

on the second to last line (above "exit 0"). This will make the machine run wake_tomorrow during each boot.

---

### Post by gletob on 2009-03-14
Thank you so much that will work perfectly!  If there was still a "thanks" button I would push it.

---

### Post by gletob on 2009-03-15
> **Eisenwinter said:**
> _[Start reading]("http://tldp.org/LDP/abs/html/")_

;)

Good Gosh!  I think I'll bookmark that it seems interesting.

BTW someone posted an answer.

[http://ubuntuforums.org/showthread.php?p=6896686](http://ubuntuforums.org/showthread.php?p=6896686)

---

### Post by gletob on 2009-03-15
> **sdsdfsg31 said:**
> Where to buy cheap [guild wars gold and ectos](http://www.guild-wars-gold.com/)? Order your Guild wars Platinum, Platinum - Factions - Nightfall - Prophecies, 24/7 and enjoy instant delivery.

Go away you stupid spammer.

---

### Post by bapoumba on 2009-03-15
Moved to PT and one post quoting spam deleted.

---

### Post by drubin on 2009-03-15
> **gletob said:**
> Anyone????

Please don't bump a thread that isn't even 1 hour old. Things take time to answer.

---

### Post by bapoumba on 2009-03-16
Threads merged.

---

