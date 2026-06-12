---
title: "Dell Dimension 2400 problem"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by chaoszerox on 2012-01-23
Windows is failing for me so I'm using Ubuntu.
Everything is working fine for me besides having any hardware acceleration for video on this old Dell PC.
System -> Admn.  -> Hardware Drivers SHOWS NOTHING but a blank boxes and the text above
No proprietary drivers are in use on this system.
Ubuntu 10.04.3 fresh install, with all system updates, still no luck.
Tried Ubuntu 11.10 with all updates as well to no success.
I'd be lovely to get some anime to play on this machine properly :P
Attached is all info that would be needed.
Any help getting the GFX driver working is very much appreciated, as I tried searching around for a while, and got nowhere =D

---

### Post by 3rdalbum on 2012-01-23
I don't think that file actually says what your graphics is. Easy way to find out:

```
lspci
```

If it's an Intel graphics chip then that explains why you've not got any "proprietary" drivers listed. Intel's drivers are open-source and already included with Ubuntu.

If it's an older ATI chip (ATI Radeon, without the "HD" in the name) then ATI no longer supports those chips and the only driver you can use is the default open-source driver.

What is the exact problem you're encountering that makes you think you don't have the proper graphics driver?

---

### Post by chaoszerox on 2012-01-23
> **3rdalbum said:**
> I don't think that file actually says what your graphics is. Easy way to find out:

```
lspci
```If it's an Intel graphics chip then that explains why you've not got any "proprietary" drivers listed. Intel's drivers are open-source and already included with Ubuntu.

If it's an older ATI chip (ATI Radeon, without the "HD" in the name) then ATI no longer supports those chips and the only driver you can use is the default open-source driver.

What is the exact problem you're encountering that makes you think you don't have the proper graphics driver?
```

```00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

I understand now about the drivers now.
It doesn't seem this PC can take 720p video. The same video I can play on my year old beast can play on this, it plays but laggy, and unwatchable
Standard definition seems to work though, and that'll do for this old thing.

Thanks for your help

---

