---
title: "wifi doesn't work"
date: 2011-06-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2011-06-11
Hello everyone, I noticed that sometimes after a reboot, wifi does not work: it connects flawlessy to my access point, but it's impossible to surf internet, or to reach the access point ip itself.

I noticed lots of messages in dmesg about wifi


```
[  505.645720] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  505.645732] cfg80211: Regulatory domain changed to country: US
[  505.645737] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  505.645744] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  505.645751] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  505.645758] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  505.645765] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  505.645772] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  505.645779] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)

```

Actually my country is not US, so that might be the problem.
I can fix it by toggling wifi connectivity several times

---

### Post by jerrylamos on 2011-06-12
After a lot of work managed to get an Oneiric install on and updated to 12 June by using wired internet.  Wireless now working on this Acer Aspire one netbook.  Quite a thrash, see my post complaining the daily builds are way way down level.

Jerry

---

