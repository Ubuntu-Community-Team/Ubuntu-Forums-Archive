---
title: "Scree Resolution Won't Rest to 1024x768"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by John Flick on 2013-07-18
My screen resolution won't reset to 1024x768.  I now have Ubuntu 12.04 on my system (originally, it was version 10.10 when I began in 2011.  I like it and am enjoying learning from it.)  HOWEVER, three days ago, I downloaded a proprietary printer driver from my SETTINGS menu.  After the download the monitor's screen resolution settings were stuck on LAPTOP [4.5 inches].   Removing the DOCKY from the screen's bottom section still didn't help, for I couldn't gain access to the RESET SETTINGS.  I'm baffled!   What can I do to correct this problem?  Please advise.  THANK YOU!  Sincerely, John Flick

---

### Post by nerdtron on 2013-07-18
In the terminal try:```
sudo xrandr -s 1024x768
```

---

