---
title: "[SOLVED] 8.10 Wireless Issues"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by timClicks on 2008-11-02
Hi all,

When I upgraded to Intrepid, I lost my wireless. wlan0 seems to default to disabled and the switch on the switch laptop doesn't alter anything.

I'm using the iwl3495 driver for an Intel wireless. Can anyone point me to a good post/how to or better yet take a quick look at the code below and suggest a fix? Thanks!

**lspci -v (extract)**

```

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1000
	Flags: fast devsel, IRQ 17
	Memory at fe1ff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [e0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 02-a8-09-ff-ff-77-1b-00
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

```

**lshw -C Network (extract)**

```

 *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:09:a8:02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

```

**iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

### Post by Sand Lee on 2008-11-03
Maybe this will help? [Ubuntu 8.10 Release Notes]("http://www.ubuntu.com/getubuntu/releasenotes/810#Cannot%20reactivate%20Intel%203945/4965%20wireless%20if%20booting%20with%20killswitch%20enabled")

---

### Post by MichaelSwengel on 2008-11-03
timClicks,

Have you tried looking in the Hardware Drivers panel in System > Administration?

There MAY be better drivers available for your hardware that will let your wireless work.

If you have looked there, what do you see?

Regards,
MS

---

### Post by Sand Lee on 2008-11-03
Nah, timClicks has an Intel wireless card so there shouldn't be anything in Hardware Drivers.

---

### Post by MichaelSwengel on 2008-11-03
> **Sand Lee said:**
> Nah, timClicks has an Intel wireless card so there shouldn't be anything in Hardware Drivers.


A couple of my studio computers use Intel wireless cards and were able to retrieve the drivers from Hardware Drivers.

You never know, Sand Lee. ;)

---

### Post by Sand Lee on 2008-11-03
heheh, you learn something new everyday :)

---

### Post by MichaelSwengel on 2008-11-04
> **Sand Lee said:**
> heheh, you learn something new everyday :)

How true. :guitar:

---

### Post by timClicks on 2008-11-07
> **MichaelSwengel said:**
> timClicks,

Have you tried looking in the Hardware Drivers panel in System > Administration?

There MAY be better drivers available for your hardware that will let your wireless work.

If you have looked there, what do you see?

Regards,
MS

Thanks for the suggestion Michael. This was one the things I tried myself, but to no avail. I am still wireless-less.

Will look through the 8.10 release docs for any known issues. Otherwise I might submit a bug report b/c there doesn't seem to be anything wrong...

Tim

---

### Post by timClicks on 2008-11-07
> **Sand Lee said:**
> Maybe this will help? [Ubuntu 8.10 Release Notes]("http://www.ubuntu.com/getubuntu/releasenotes/810#Cannot%20reactivate%20Intel%203945/4965%20wireless%20if%20booting%20with%20killswitch%20enabled")
Hey Sand Lee - it looks like this is my issue. Thanks for your help!

I've got my wireless working. Here is the [direct link](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/193970) to the Launchpad bug. The fix that worked for me was:

sudo rmmod iwl3945
sudo modprobe iwl3945
sudo rmmod iwlagn
sudo modprobe iwlagn

then restarted PC

---

