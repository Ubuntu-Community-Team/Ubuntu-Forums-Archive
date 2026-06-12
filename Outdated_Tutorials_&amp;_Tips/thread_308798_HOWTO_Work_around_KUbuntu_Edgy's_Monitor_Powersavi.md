---
title: "HOWTO: Work around KUbuntu Edgy's Monitor Powersaving bug"
date: 2006-11-28
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2006-11-28
If you're a KUbuntu Edgy user, you probably have experienced bug [http://launchpad.net/bugs/65791](http://launchpad.net/bugs/65791). Simply put, you set your screen to turn off in 2 minutes. After a logout/login, suddenly that value is set to 60 times the original setting (120 minutes).

The bug is filed in Launchpad, and so far the culprit has not been identified. This is a dirty workaround until this bug is resolved. Specifically, this script will monitor your DPMS timeout setting every 10 seconds, and if it deviates from the expected setting, it'll reset it.


**Installing the workaround:**
Save the following code as /usr/local/bin/dpmswatch:
```

#!/usr/bin/python
import os
import time
while True:
  st=os.popen('xset -q | grep Standby').read()[:-1].strip()
  if st != "Standby: 120    Suspend: 120    Off: 120":
    print "Bad DPMS:",st
    os.system('xset dpms 120 120 120')
  time.sleep(10)

```

Save the following code in ~/.kde/Autostart/dpms
```

#!/bin/bash
/usr/local/bin/dpmswatch &

```

Run the following two commands:

```

sudo chmod +x /usr/local/bin/dpmswatch
chmod +x ~/.kde/Autostart/dpms

```

Logoff and log back in. Yes, this is a really dirty workaround. This example assumes you want your display to shut off after 2 minutes of inactivity. You can change 120 to a different number if you need a different timeout.

---

### Post by tubunu on 2006-12-03
Thanks a lot! I'll give it a try right away! :)

---

### Post by jeremy on 2006-12-10
I have used this workaround, it seems to work in that the settings are saved, but in the last 4 or 5 days, after a while the monitor 'forgets' to turn itself off, and all I can do is to 're-apply' the settings in kcontrol.

---

### Post by gatewayasteroid on 2007-01-19
I solved just by putting in ~/.kde/Autostart a simple script containing:

[I]sleep 300
xset dpms 0 0 300[/I]

This way, every reboot the DPMS settings are reloaded.

---

### Post by jdong on 2007-01-19
UPDATE: After a bit of code searching I did find the culprit, and after a few different proposed patches one did get accepted into Feisty and also KDE 3.5.6.

So the good news is that this will no longer happen in Feisty, and in KDE 3.5.6 Edgy packages when they get released for kubuntu.org

No response on my query if there will be a  stable-release-update, so let's hang tight :)

---

### Post by apdt on 2007-03-22
> **gatewayasteroid said:**
> I solved just by putting in ~/.kde/Autostart a simple script containing:

[I]sleep 300
xset dpms 0 0 300[/I]

This way, every reboot the DPMS settings are reloaded.

A Slight refinement on the above to read the setting from the displayconfigrc:

```
#!/bin/bash

sleep 300  #5 mins

CONFIGFILE="$HOME/.kde/share/config/displayconfigrc"

DPMSLINE=`grep dpmsSeconds $CONFIGFILE | head -1`
DPMSSECONDS=${DPMSLINE#dpmsSeconds=}

/usr/bin/xset dpms $DPMSSECONDS $DPMSSECONDS $DPMSSECONDS
```

---

### Post by HasratUSA on 2007-03-25
Just stating that this bug exists but not on my machine. I first installed Ubuntu and later installed KDE

---

