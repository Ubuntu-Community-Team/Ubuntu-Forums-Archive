---
title: "Screen, Graphics and input settings not detected"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by cressrt on 2012-11-14
On trying to boot up my PC I am getting a message that " "the system is running in low graphics mode" as your screen, graphics card and input device settings could not be detected correctly. You will need to configure these yourself."
The next screen gives options but no keys work to select anything so I am unable to get any further.
I have tried running in Recover mode and previous versions but to no good.
The PC is currently dual boot and is ok in windows, using Ubuntu 12.04.
I have a 12.10 boot on a USB but have not tried this yet, I am using an old PC for this message.
Any suggestions..

---

### Post by dannyboy79 on 2012-11-14
hit ctrl-alt-f1 to get to tty1, login to the textual environment. run this command to see what graphics card you have

```
lspci | grep VGA
```

---

### Post by cressrt on 2012-11-14
This gives
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
Thanks

---

### Post by Simon65 on 2012-11-14
I have the same problem.  I have been running 12.04 for a wile with no problems, now all of a sudden it comes up with that message.  I've managed to boot up from the installation CD with no problem (I'm using that boot up now).  I ran the suggested code and my graphics card was listed but my laptop still won't boot normally.

I considered re-installing Ubuntu to try to solve this but don't know if it's possible to do that without losing all the files I have in my Home folder.

---

### Post by dannyboy79 on 2012-11-15
> **Simon65 said:**
> I have the same problem.  I have been running 12.04 for a wile with no problems, now all of a sudden it comes up with that message.  I've managed to boot up from the installation CD with no problem (I'm using that boot up now).  I ran the suggested code and my graphics card was listed but my laptop still won't boot normally.

I considered re-installing Ubuntu to try to solve this but don't know if it's possible to do that without losing all the files I have in my Home folder.
is it possible you had a kernel update? try to boot into an older kernel and see if it works like it used to for ya.

To the OP, I am not sure how to help you as I don't experience the issue since I don't have that graphics controller. Hopefully someone else will come along to help you. Check google in the meantime

---

### Post by cressrt on 2012-11-16
I have had to reinstall, as nothing else would work, I upgraded from 12.4 to 12.10 but still the same problem. I now have a working OS but now have another problem as the Wireless is not showing or connecting, I assume this is a driver issue?

---

### Post by idoitprone on 2012-11-16
> **cressrt said:**
> I have had to reinstall, as nothing else would work, I upgraded from 12.4 to 12.10 but still the same problem. I now have a working OS but now have another problem as the Wireless is not showing or connecting, I assume this is a driver issue?

```
lspci -nnk
```

'?

---

### Post by cressrt on 2012-11-16
I have rebooted and run the code, this is the output
[HTML]00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel modules: i2c-i801
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: intel ips
    Kernel modules: intel_ips
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
    Kernel driver in use: tg3
    Kernel modules: tg3
02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
    Subsystem: Foxconn International, Inc. Device [105b:e040]
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0487]
[/HTML]

Copied from another PC connected OK to WiFI.

---

### Post by idoitprone on 2012-11-16
```
02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n 
[14e4:4358]
    Subsystem: Foxconn International, Inc. Device 
[105b:e040]

```
 
I do not see a driver
 
If you have internet then
 
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
 
If you have to download the package then 
 
download the correct architucture
[http://packages.ubuntu.com/quantal/admin/bcmwl-kernel-source](http://packages.ubuntu.com/quantal/admin/bcmwl-kernel-source)
 
 
x86  - 32bit
amd64  - 64 bit
 
install

---

### Post by cressrt on 2012-11-17
Thanks, I downloaded via another PC as I have no access, however the file will not install. When it opens up the install option is not highlighted to allow you to "click" on it. I tried other packages and these were all the same; not sure if it is because I'm not connected to the Internet or there is something wrong with the Software Centre.
Any other suggestions or is it to be a reinstall?

---

### Post by cressrt on 2012-11-17
Gave up and reinstalled but is still the same, still unable to install drivers!? Is there another way around this?

---

### Post by cressrt on 2012-11-17
I have reinstalled AGAIN but this time with 12-04 that I previously used. This gave me an option to install the drivers, which I did, this allowed the connection to be established and I now have a working PC again.
I believe there is an issue with 12.10 and the Broadcom drivers that need addressing.

---

