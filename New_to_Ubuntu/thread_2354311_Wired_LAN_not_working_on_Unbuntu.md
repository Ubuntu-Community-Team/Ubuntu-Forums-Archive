---
title: "Wired LAN not working on Unbuntu"
date: 2017-03-01
forum: New to Ubuntu
---

### Post by solentmancub on 2017-03-01
Hello all, I am  newbie to Ubuntu and I have an issue with an old laptop. I have installed Ubuntu and the WIFI works great. However the LAN port is not working and i can't fathom out why. I want to keep WIFI and use the LAN Port o connect to a portable NAS box so I can steam movies. Any ideas on how i can resolve this?

Mt interface file looks like this:
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

Regards

SP

---

### Post by cariboo on 2017-03-01
Could you post the results of:

```
sudo lshw -C network
```

---

### Post by dajavex71 on 2017-03-01
Please post the results of > sudo ifconfig -a
I suspect, that depending on the result of that you may need to add to your interfaces file.
example: Replacing eth0 for the specified adapter
> auto eth0
iface eth0 inet dhcp

---

