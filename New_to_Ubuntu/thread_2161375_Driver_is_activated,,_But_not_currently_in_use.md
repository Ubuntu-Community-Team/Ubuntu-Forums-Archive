---
title: "Driver is activated,, But not currently in use"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by Nayab Basha Sayed on 2013-07-10
I installed graphic driver.
It shows "Driver is activated,, But not currently in use"
What is meant by that? and how to make use of it?
I've got AMD Radeon 6600 series graphic card.

---

### Post by farrinux on 2013-07-10
Did you reboot the machine after installing the driver?

---

### Post by gifford on 2013-07-10
Is Unity working for you? Also, what version of Ubuntu are you using?
There is a bug with jockey that fails to report when the proprietary driver is in use and will give the message "[COLOR=#000000]Driver is activated,, But not currently in use"
See this link:[/COLOR][https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/1178853](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/1178853)[COLOR=#000000] 
Try this command in your terminal:
fglrxinfo
It should return something like this if your driver is activated and in use:
[/COLOR]display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI FirePro V4800 (FireGL) Graphics Adapter
OpenGL version string: 4.2.11978 Compatibility Profile Context FireGL

---

