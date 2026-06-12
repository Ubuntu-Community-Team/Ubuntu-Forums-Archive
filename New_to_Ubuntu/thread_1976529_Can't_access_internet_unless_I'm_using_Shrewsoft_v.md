---
title: "Can't access internet unless I'm using Shrewsoft vpn"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by lifelike27 on 2012-05-08
Hi guys,

I had a 11.10 64 bit installation that had Shrewsoft installed on it and working fine. After I upgraded to 12.04 I needed to use the vpn and since then, I haven't been able to use the internet with out it.

I can connect to a wireless network just fine.
I figured uninstalling it might remove the confusion as well, but it didn't.

I checked under the networking system settings and there isn't any proxy there

I think there might be some configuration that was left behind that I need to remove..

I would really appreciate the help, thanks!

---

### Post by Ms. Daisy on 2012-05-10
Have you tried```
sudo apt-get purge shrewsoft
```

---

### Post by lifelike27 on 2012-05-10
A nice guy known as DarwinSurvivor on the #ubuntu irc helped me solve my problem.

Shrewsoft edited my /etc/resolv.conf file leaving my organizations namespace and dns server in the file even when the vpn client wasn't running (or in my case removed entirely).

The simplest fix was to remove the entries or just comment them out.

---

