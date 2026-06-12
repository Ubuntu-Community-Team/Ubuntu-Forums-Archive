---
title: "Autologin timeout does not work (11.10)"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by arodulfo on 2011-11-17
Dear all,

I have just installed Oneiric Ocelot from a CD. 
This operation worted out some problems and got me closer to the target than ever, but didn't reach it yet.

I managed to instruct the login manager to auto-login, to use the username I wanted and to start XFCE session. However, the login manager doesn't wait for an eventual alternate user login, as it used to in former releases.

Here's the contents of */etc/lightdm/lidghtdm.conf*:
```
[SeatDefaults]
autologin-guest=true
autologin-user=username
autologin-user-timeout=30
autologin-session=lightdm-autologin
user-session=xfce
greeter-session=lightdm-gtk-greeter

```You see, my aim was to have some time for an eventual change of startup user, in case any administrative works were needed or whatever.

Just to complete the picture, I'm using an old HP Vectra VL-400, with full SDRAM installed (max. is 512 MiB) and 150 GiB HDD

UPDATE: I have tried many different settings for *autologin-user-timeout*, with no success. No matter if the value is set to 0, 10 or 100, it doesn't affect the actual behaviour of the system, which keeps starting the set user with no delay.
Some people out there says *lightdm* is not mature enough for the task. I don't know.

Any hint will be wellcome.
Kind regards

---

