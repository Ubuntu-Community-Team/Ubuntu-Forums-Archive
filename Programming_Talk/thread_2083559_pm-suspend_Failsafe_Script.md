---
title: "pm-suspend Failsafe Script"
date: 2012-11-12
forum: Programming Talk
---

### Post by jlacroix on 2012-11-12
I had a problem a week or so ago where I closed my lid, but my laptop did not go to sleep despite the fact that I have it set up in the settings to sleep when the lid is closed and AC is not plugged in. After about 10 minutes, I found my laptop roasting like an egg in my bag. THANKFULLY it survived, but it was so hot that I could barely touch the palmrest!

This has happened a second time (not suspending when I closed the lid, I double-checked the settings) but that time I checked before I put it in my bag.

I decided to write a bash script and use cron to create a failsafe, where if KDE doesn't put it to sleep like I told it to in the settings, the cron job will. So, I wrote the following script by Googling around for samples:

```
#!/bin/bash
# init

grep -q closed /proc/acpi/button/lid/LID/state
if [ $? = 0 ]
then
	## The laptop lid is closed. Let's find out if it's plugged in.
	grep -q 0 /sys/class/power_supply/AC/online
	if [ $? = 0 ]
	then
		sudo pm-suspend
        fi
fi
```

As you can probably guess, this script first checks to see if the lid is closed. if it is, it then checks to see if my AC adapter is plugged in. If it is not, it puts the laptop to sleep. This works. But...

...If I plug in the AC adapter after it goes to sleep, it immediately wakes up. is there a way to prevent that? Sometimes I plug it in just to charge.

Also, does my script look okay and can you think of any caveats I may not have accounted for?

---

