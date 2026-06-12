---
title: "Small Networking Tip"
date: 2006-09-01
forum: Outdated Tutorials &amp; Tips
---

### Post by BatteryCell on 2006-09-01
Heres a real quick simple trick to finding your WAN IP address from the terminal:

```
lynx -dump www.whatismyip.com | grep . -m2
```

Because this might be a little much for some to remember you can also just make a bash script with that line in it and call it something shorter.

NOTE: You have to have lynx installed for this to work :wink:

---

