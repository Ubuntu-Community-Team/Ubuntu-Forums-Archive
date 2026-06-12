---
title: "Power management internals of lightdm"
date: 2017-04-22
forum: New to Ubuntu
---

### Post by arjo129 on 2017-04-22
Hi, 
So I encountered a problem with ubuntu's suspend. When I am logged in and close my lid the laptop immediately suspends. However when I wake it up again if I do not login the laptop will not suspend (i.e. the system doesnt suspend .

This is my systemd log:

```

Apr 22 22:19:32 arjo-MacBookPro systemd-logind[752]: Lid closed.
Apr 22 22:19:32 arjo-MacBookPro systemd-logind[752]: Suspending...
Apr 23 07:40:07 arjo-MacBookPro systemd-logind[752]: Lid opened.
Apr 23 07:40:07 arjo-MacBookPro systemd-logind[752]: Operation 'sleep' finished.
Apr 23 07:40:12 arjo-MacBookPro systemd-logind[752]: Lid closed.

```

After Lid closed, it doesnt suspend. This can be a problem as I might close my lid in a hurry and put it in my backpack leading to severe overheating.
Now, when I went to the systemd-logind configuration I found all the options were commented out. So my question is what is the mechanism lightdm and unity use to control power events? (I would rather fix whatever configuration file is associated with them then have systemd interfere, I've already seen some fixes which uncomment the systemd configuration file and I'll be doing that as an interim measure).

---

