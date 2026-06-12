---
title: "Intermittent internet connection issues"
date: 2011-09-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lachild on 2011-09-24
Hey guys,

After an update last night I'm noticing that my wifi connection keeps dropping and reconnecting.  Looking in the forum I saw something about libnss3, so I double checked that the package is installed, and it is.  So I don't believe that it's due to this issue.

Looking further I noticed the following in dmesg after each drop and reconnect:

> 
[ 1197.990976] wlan0: disassociating from 00:1e:e5:5e:c7:2a by local choice (reason=3)
[ 1198.030445] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1198.030458] cfg80211: Restoring regulatory settings
[ 1198.030475] cfg80211: Calling CRDA to update world regulatory domain
[ 1198.032406] wlan0: deauthenticating from 00:1e:e5:5e:c7:2a by local choice (reason=3)
[ 1198.040244] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 1198.040254] cfg80211: World regulatory domain updated:
[ 1198.040260] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1198.040270] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1198.040278] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1198.040288] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1198.040296] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1198.040304] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1199.705980] wlan0: authenticate with 00:1e:e5:5e:c7:2a (try 1)
[ 1199.707806] wlan0: authenticated


Any idea why it would just randomly decide to disassociate itself? Or any idea what reason=3 is?

Thanks,
Westin

---

### Post by lachild on 2011-09-24
Looking further it looks like my neighbor just installed a new wifi router.  I changed the channel on my router and everything seems ok again.

Thanks,
Westin

---

