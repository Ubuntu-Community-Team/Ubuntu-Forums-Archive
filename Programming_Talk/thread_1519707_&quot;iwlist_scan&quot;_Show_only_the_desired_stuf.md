---
title: "&quot;iwlist scan&quot; Show only the desired stuff?"
date: 2010-06-28
forum: Programming Talk
---

### Post by JohnHeikkila on 2010-06-28
Hey,
Is it possible in any way to have "**iwlist scan**"
show *only* the things I need like nothing _but_ these 
```
wlan0     Scan completed :
          Cell 01 - Address: [address]
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-1 dBm  
                    Encryption key:on
                    ESSID:"[Network_name]"
```

I know I can show only my desired interface by adding "**iwlist [interface] scanning**".

---

### Post by mainerror on 2010-06-28
Maybe this.

> iwlist [interface] scan | head -n 7

---

### Post by JohnHeikkila on 2010-06-28
It works!
Thank you ;-)

---

