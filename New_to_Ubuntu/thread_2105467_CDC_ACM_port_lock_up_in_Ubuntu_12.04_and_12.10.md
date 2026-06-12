---
title: "CDC_ACM port lock up in Ubuntu 12.04 and 12.10"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by MrPrawn on 2013-01-16
Hello,

I have experienced a problem when attempting to communicate with a device via Minicom on Ubuntu 12.04 and Ubuntu 12.01. On plugging in the device, I can see that it enumerates correctly creating 7 ACM ports. However, when I try to open multiple ports (with sudo minicom -o -D /dev/ttyACMx) I may be able to communicate with a device on one port, but when switching to another Minicom session, I cannot communicate with this port. It appears as if the ports experience a lockup. Sometimes unplugging/re-inserting the USB cable resolves the problem releasing one of the ports, but it is not possible to communicate simultaneously on multiple minicom sessions - it appears as if only one port is accessible at one time with the others being blocked. However, the device does seem to execute the commands (even though the ports seem blocked; but there is no local echo of characters nor any response from the device in this case).

I have only seen this problem on a dedicated Ubuntu machine, and not when using VMware Player and a virtual machine on Windows 7. Additionally, I haven't seen the problem on a Windows 7 machine, so I doubt there is a problem with the device itself.

One interesting/useful piece of information, is that when I plugged the device into the Windows 7 machine, VMware Player shows the following message:

"The device xxx was unable to connect to its ideal host controller. An attempt will be made to connect this device to the best available host controller. This may result in undefined behavior for this device".

After accepting this message, I can have multiple minicom sessions open and communicate on multiple ports simultaneously without experiencing any lock-up. Would this message indicate a potential issue with Ubuntu?

Is there any known issue regarding the CDC_ACM port lock up? If not, what else could I try to resolve the problem.

Many thanks for you responses.

---

