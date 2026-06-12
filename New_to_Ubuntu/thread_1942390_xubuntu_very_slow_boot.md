---
title: "xubuntu very slow boot"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by mockbeggars on 2012-03-17
I’ve just replaced Windows 7 with Xfce 4 Desktop Environment version 4.6 on a Toshiba NB305 netbook. Once booted up, everything works fine, but the booting  up process takes several minutes to complete. Here are the 2 critical bits of the dmesg output. Surely there’s something I can do about this? But what?

[   11.891852] EXT4-fs (sda1): recovery complete
[   17.821122] EXT4-fs (sda1): mounted filesystem with ordered data mode
[  328.126568] Adding 2975736k swap on /dev/sda5.  Priority:-1 extents:1 across:2975736k 
[  328.148622] udev: starting version 151

.....

[  335.900204] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[  374.358115] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  374.376216] r8169: eth0: link down
[  374.376943] ADDRCONF(NETDEV_UP): eth0: link is not ready

....

[  381.444989] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  391.828062] wlan0: no IPv6 routers present
robert@robert-netbook:~$

---

### Post by TeoBigusGeekus on 2012-03-19
I think you should disable ipv6.
As for the recovery part, does it do it every time you boot?
If so, your hard drive might be starting to fail.

---

