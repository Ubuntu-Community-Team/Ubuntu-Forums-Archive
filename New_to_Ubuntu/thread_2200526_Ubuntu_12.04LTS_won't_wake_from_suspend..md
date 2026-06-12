---
title: "Ubuntu 12.04LTS won't wake from suspend."
date: 2014-01-19
forum: New to Ubuntu
---

### Post by Myfathersheart on 2014-01-19
I am running 12.04LTS alongside a Windows 7 dual boot. I have been using Ubuntu for a week now.  Currently, my laptop won't wake from suspend.

I have found a few posts on this issue here in these forums, and on Google, but the solutions I have found seem to be hardware specific.  

Therefore, I opted to make a new thread in hopes that I can get my machine working with suspend. I greatly appreciate any help I can get on this. 


I read in another post that the following information may be helpful.

```
 [COLOR=#000000][FONT=Ubuntu Mono]pastebinit /var/log/pm-suspend.log [/FONT][/COLOR]
```
returned this: [http://paste.ubuntu.com/6783391/](http://paste.ubuntu.com/6783391/) 

```
 lspci -vnn | grep -A12 VGA 
```

returned this:
```

00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6520G] [1002:9647] (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device [17aa:3970]
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 3000 [size=256]
	Memory at f0300000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: radeon
	Kernel modules: radeon
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6630M/6650M/6750M/7670M/7690M] [1002:6741] (prog-if 00 [VGA controller])
	Subsystem: Lenovo Radeon HD 6650M [17aa:3970]
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0200000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 2000 [size=256]
	[virtual] Expansion ROM at f0220000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Kernel driver in use: radeon

```

and 


```
 [COLOR=#000000][FONT=Ubuntu Mono]cat /proc/cmdline [/FONT][/COLOR]
```

returned this: 
BOOT_IMAGE=/boot/vmlinuz-3.8.0-35-generic root=UUID=D80EB5960EB56DDE loop=/ubuntu/disks/root.disk ro quiet splash vt.handoff=7

---

### Post by matthew.carnovale on 2014-01-19
Do you know which kernal you're running? I had similar troubles with suspend after a fresh install of 12.04 LTS and it turned out I just needed one more run of:

sudo apt-get update 
sudo apt-get upgrade

That brought my kernal up to 3.8 and resolved my post-suspend freeze issue.

---

### Post by Myfathersheart on 2014-01-20
My kernal is 3.8, and just for good measure I did the update/upgrade, but this didn't fix the issue.

The computer does seem to enter suspend, and seems to wake up (I can hear the fan turn on, and my power lights come on), but the screen remains black.

---

### Post by Myfathersheart on 2014-01-22
I'm sure there is an Ubuntu wizard out there who can help me with this. :D

---

### Post by Jay_N on 2014-04-17
I'm having the same issue. After resume, all I get is a black screen. Everything else comes on but the screen remains black. I've tried a script and that didn't work. I've also updated with one of the above suggestions and that didn't help the suspend issue either.

---

### Post by Myfathersheart on 2014-04-19
It turns out my problem was that I had installed Ubuntu through windows using Wubi. That installation method doesn't support suspend.

---

### Post by david98 on 2014-04-19
Just to let you know that Wubi is no longer supported so I would refrain from using it in the future.

---

### Post by Jay_N on 2014-04-27
I just updated my NVIDIA driver and that fixed the issue. They had a fix for their driver that had an issue with the balck screen upon resume.

---

### Post by HDTimeshifter on 2014-05-11
I've had this problem since the previous release last fall with my GeForce 9500 GT. I just went into Additional Drivers and changed from X.Org X Server to NVIDIA binary driver - version 331.38 from nvidia-331-updates (proprietary). The other nvidia-331 (proprietary, tested) did not work either. My PC now wakes from suspend, however the network (Atheros) is no longer enabled and I have to reboot again to get it to work. Does anyone know how to get the networking to resume?

---

