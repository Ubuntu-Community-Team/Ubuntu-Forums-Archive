---
title: "Missing eth0 interface"
date: 2017-02-15
forum: New to Ubuntu
---

### Post by laci1000 on 2017-02-15
Hello guys,

I just installed Ubuntu 16.04 LTS, and I'm trying to connect to the internet via ethernet but it's doesn't work.
I checked ifconfig, and I don't see 'eth0', only something 'enp2s0f0' and the 'lo'.
Also checked the /etc/network/interfaces, and added the following:
```
auto eth0
iface eth0 inet dhcp
```

```
dmesg | grep eth0
```
gives the following:
enp2s0f0: renamed from eth0

I've found a lot of similar issues online and tried almost every solution posted, but it isn't working.

Could you please advise?
Thank you!

---

### Post by The Cog on 2017-02-15
Just live with the fact it's called enp2s0f0 and not eth0. That's the new naming convention, apparently.
Use this instead:
```
auto enp2s0f0
iface enp2s0f0 inet dhcp
```

---

