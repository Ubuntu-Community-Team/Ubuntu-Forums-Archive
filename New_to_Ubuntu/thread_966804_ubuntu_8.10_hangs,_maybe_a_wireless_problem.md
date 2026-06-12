---
title: "ubuntu 8.10 hangs, maybe a wireless problem"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Vincent Plagnol on 2008-11-01
Dear Ubuntu users,

I have issues with the new ubuntu 8.10 on my laptop: it systematically hangs after a few minutes. 

The laptop is a ThinkPad x61, and I think the problem comes from the wireless. If I do not login to my home wireless network the laptop keeps working, and if I do it freezes completely after a short while, it just hangs. My network is a WPA2, so maybe this is specific to this encryption? I had no problem before with the previous version of Ubuntu.

Using lpsci my network hardware info is:
Network Controller: Intel PRO/Wireless 4965 AG or AGN (Kedron)


My other lead is a CUPS problem that seems to come up in the logs but that seems less likely, given the observation that I need to login on the wireless network to see the crash.

Has anyone experienced something similar? Any hint that could help me fix things?

Thanks,

Vincent

---

### Post by Vincent Plagnol on 2008-11-01
OK I have just found this, which will probably solve my problem:


System lock-ups with Intel 4965 wireless

The version of the iwlagn wireless driver for Intel 4965 wireless chipsets included in Linux kernel version 2.6.27 causes kernel panics when used with 802.11n or 802.11g networks. Users affected by this issue can install the linux-backports-modules-intrepid package, to install a newer version of this driver that corrects the bug. (Because the known fix requires a new version of the driver, it is not expected to be possible to include this fix in the main kernel package.)

---

