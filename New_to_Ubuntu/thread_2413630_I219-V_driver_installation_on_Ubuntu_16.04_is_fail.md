---
title: "I219-V driver installation on Ubuntu 16.04 is failing"
date: 2019-02-28
forum: New to Ubuntu
---

### Post by prb23 on 2019-02-28
I am trying to install e1000e-3.4.2.0 version for Ubuntu 16.04. After checking all the past posts on the same issue as [here]("https://unix.stackexchange.com/questions/294753/intel-ethernet-connection-i219-v-not-working-under-linux-on-an-asuspro-b-laptop/295052?newreg=d3044b97b2ee42798e58714ac75e7a6f") I made the required changes in the nvm.c but still, it is not working. My configurations are as follows :
```
00:00.0 Host bridge: Intel Corporation Device 3ec2 (rev 07)
00:01.0 PCI bridge: Intel Corporation Sky Lake PCIe Controller (x16) (rev 07)
00:14.0 USB controller: Intel Corporation Device a2af
00:14.2 Signal processing controller: Intel Corporation Device a2b1
00:16.0 Communication controller: Intel Corporation Device a2ba
00:17.0 SATA controller: Intel Corporation Device a282
00:1b.0 PCI bridge: Intel Corporation Device a2e7 (rev f0)
00:1c.0 PCI bridge: Intel Corporation Device a290 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Device a298 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device a2c9
00:1f.2 Memory controller: Intel Corporation Device a2a1
00:1f.3 Audio device: Intel Corporation Device a2f0
00:1f.4 SMBus: Intel Corporation Device a2a3
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-V
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1b06 (rev a1) 01:00.1 Audio device: NVIDIA Corporation Device 10ef (rev a1)
```
The error I am getting :
```
Makefile:975: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
    make[1]: *** No rule to make target 'driver/e1000e-3.4.0.2/src'.  Stop.
    make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-45-generic'
    Makefile:273: recipe for target 'default' failed
    make: *** [default] Error 2
    filename:       /lib/modules/4.15.0-45-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
    version:        3.2.6-k
    license:        GPL
    description:    Intel(R) PRO/1000 Network Driver
    author:         Intel Corporation, <linux.nics@intel.com>     
srcversion: 010F824B54BE2AA7285BF59
```I am pretty new to Ubuntu. Sorry if I am missing some information. I would appreciate your advice on this. Thank you.

---

### Post by DuckHook on 2019-03-02
Welcome to the forums, prb23

I am way out of my league here, but your makefile error does say:> …please install libelf-dev, libelf-devel or elfutils-libelf-devel…so you should try installing one of those packages. Other than this simple observation, I'm afraid that compiling drivers is something I've only done a handful of times, so my ability to help will be strictly limited.

---

### Post by jeremy31 on 2019-03-02
I don't think it is a dependency issue, prb23 what is the full path of the directory?  If there are spaces in the path, it will fail to build.  I would bet there is a space before driver/e1000e-3.4.0.2/src

---

