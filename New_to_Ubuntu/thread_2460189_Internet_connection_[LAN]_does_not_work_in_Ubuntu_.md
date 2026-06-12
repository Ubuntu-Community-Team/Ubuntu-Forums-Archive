---
title: "Internet connection [LAN] does not work in Ubuntu / Linux (all distros)"
date: 2021-04-04
forum: New to Ubuntu
---

### Post by pratyakshm on 2021-04-04
LAN only works in Live boot. After Ubuntu is installed, it no longer works, and shows something similar to "network activation failed" or something like that.
My network adapter is "Realtek PCIe GbE Family Controller".
PC specs: 
Processor:    AMD Ryzen 5 3400G with Radeon Vega 11
Installed RAM:    16.0 GB 
BIOS Version: American Megatrends Inc. F52, 03-08-2020
BaseBoard Manufacturer: Gigabyte Technology Co., Ltd
BaseBoard Product: A32M-H-CF


Please let me know if information regarding anything else is needed, I would be happy to provide it. I'm eager to solve this issue ASAP.

---

### Post by TheFu on 2021-04-04
Standard troubleshooting would be to compare the differences between the setup that works and the one that doesn't.

First thing to compare are the driver used on each. I suspect the issue is a different driver being used post-install.  If they are the same, we have to look elsewhere.
```
lspci -vk |egrep --after-context=8 'Ethernet|Network'
```
should work for any PCIe connected NIC.

Because it is a fresh install the easy tools to get that information aren't available and can't be installed due to the networking issue. The easier commands are:
```
inxi -N
sudo lshw -C network
```
but these won't work until those tools are installed.

---

### Post by ActionParsnip on 2021-04-04
Can you ping the default gateway IP (your router's internal IP)?
Can you ping 8.8.8.8?
Can you ping bbc.co.uk?
Have you rebooted your router?

---

### Post by mastablasta on 2021-04-06
i believe there is something wrong with configuration if this is on ubuntu 20.04. the LAN connection just drops. i seen it at my kids laptop, but i haven't had the time to fix it yet.  he would have wi-fi working well, but LAN connection just dissapears (stops working)  or doesn't work from start.

however in your case you say it was working. so it could also mean that the driver package is not being loaded. Make sure realtek driver is loaded. dependign on the chip you might be able to add it from repository. for example here is a similar issue: [https://askubuntu.com/questions/1258241/no-ethernet-connection-available-in-ubuntu-20-04](https://askubuntu.com/questions/1258241/no-ethernet-connection-available-in-ubuntu-20-04)

---

