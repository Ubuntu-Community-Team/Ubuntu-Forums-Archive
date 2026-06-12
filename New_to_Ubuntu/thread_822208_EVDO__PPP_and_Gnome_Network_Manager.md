---
title: "EVDO / PPP and Gnome Network Manager"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by isaidi on 2008-06-08
I have PPP / Peers working perfectly to run my evdo aircard.. with pon 
but how can i integrate this with Gnome Network Manager, so the rest of my Ubuntu thinks i am indeed connected to the net?

i have the following in my /etc/network/interfaces
```


iface ppp0 inet ppp
provider cdma

auto ppp0

```

so i can even use ifup -a to bring up ppp0
I

---

