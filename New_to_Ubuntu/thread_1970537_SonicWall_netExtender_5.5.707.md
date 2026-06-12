---
title: "SonicWall netExtender 5.5.707"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by KirkDude on 2012-05-01
I'm trying to install SonicWall netExtender 5.5.707 on Ubuntu 12.04.

I'm getting a Missing library: libcrypto.so.6 error. How/where do I get this lib? I searched the software center, no luck. 

Thanks

---

### Post by lykeion on 2012-05-01
You could try to install this package: **libssl1.0.0**, it will install **libssl.so.1.0.0** and **libcrypto.so.1.0.0**

If this still not works you might have to make some symlinks manually like this:```
sudo ln -s /usr/lib/i386-linux-gnu/libcrypto.so.1.0.0 /usr/lib/libcrypto.so.6
sudo ln -s /usr/lib/i386-linux-gnu/libssl.so.1.0.0 /usr/lib/libssl.so.6
```

Hope it helps

---

### Post by Veoden on 2012-05-02
> **lykeion said:**
> You could try to install this package: **libssl1.0.0**, it will install **libssl.so.1.0.0** and **libcrypto.so.1.0.0**

If this still not works you might have to make some symlinks manually like this:```
sudo ln -s /usr/lib/i386-linux-gnu/libcrypto.so.1.0.0 /usr/lib/libcrypto.so.6
sudo ln -s /usr/lib/i386-linux-gnu/libssl.so.1.0.0 /usr/lib/libssl.so.6
```

Hope it helps

If you use Ubuntu 12.04 64Bits the ln is a bit different:

```

sudo ln -s /lib/x86_64-linux-gnu/libssl.so.1.0.0 /usr/lib/libssl.so.6
sudo ln -s /lib/x86_64-linux-gnu/libcrypto.so.1.0.0 /usr/lib/libcrypto.so.6


```

---

### Post by Ongxa41 on 2012-05-10
These links do actually work and will get netExtender installed.  However, I found a system flaw with Sonicwall that caused me large amounts of grief today.

With the symbolic links in place and netExtender not running (and connected), you cannot ping anything by hostname alone.  you can ping by IP or by FQDN, but not by host alone.

i found about 6 different things to try with samba configurations and network-manager configurations, hard coding the configurations onto the eth0...nothing worked.

i tried adding search domains to the config files...they're all basically ignored.

so...until Sonicwall updates their netExtender to work with the newest versions of libcrypto and libssl...i'm just going to remove the symbolic links when I'm not going to use VPN & put it back in place when I do need to connect via VPN.

I have a mixed environment that I manage (about 40 Linux servers and 80 Windows machines in an Active Directory, so you can understand the unfortunate need to be able to work by hostname when the previous network administrator decided that a 25 character long DN for our domain was appropriate.

just passing along the experience and much appreciated for the links...again...they do work like a charm!

---

### Post by sgray333 on 2012-06-19
I attempted to do this and still get the same error on install.  I have attempted with SonicWall 5.5 and 6.0.  Are there any other suggestions?

> **lykeion said:**
> You could try to install this package: **libssl1.0.0**, it will install **libssl.so.1.0.0** and **libcrypto.so.1.0.0**

If this still not works you might have to make some symlinks manually like this:```
sudo ln -s /usr/lib/i386-linux-gnu/libcrypto.so.1.0.0 /usr/lib/libcrypto.so.6
sudo ln -s /usr/lib/i386-linux-gnu/libssl.so.1.0.0 /usr/lib/libssl.so.6
```

Hope it helps

---

### Post by TBev0 on 2012-06-22
Try:

```
sudo ln -s /lib/i386-linux-gnu/libssl.so.1.0.0 /usr/lib/libssl.so.6
```
```
sudo ln -s /lib/i386-linux-gnu/libcrypto.so.1.0.0 /usr/lib/libcrypto.so.6
```

---

### Post by Killbam on 2012-08-18
TBev0 - Bingo!

---

