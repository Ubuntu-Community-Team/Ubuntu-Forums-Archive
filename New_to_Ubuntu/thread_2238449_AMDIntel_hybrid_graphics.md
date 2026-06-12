---
title: "AMD/Intel hybrid graphics"
date: 2014-08-08
forum: New to Ubuntu
---

### Post by justin60 on 2014-08-08
Hi All,

brand new to linux here and I installed Ubuntu 14.04 on my Lenovo W500 Laptop.  I am getting errors on startup 

dmesg | grep radeon
[   12.959881] [drm] radeon kernel modesetting enabled.
[   12.959964] radeon 0000:01:00.0: enabling device (0106 -> 0107)
[   14.408231] radeon 0000:01:00.0: Fatal error during GPU init
[   14.408492] [drm] radeon: finishing device.
[   14.411890] radeon: probe of 0000:01:00.0 failed with error -12

The Fatal error during GPU init and the failed with error -12 are both shown during startup.

Here is my gpu-manager output.

gpu-manager
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
Found "/dev/dri/card0", driven by "i915"
output 0:
    LVDS connector
output 1:
    VGA connector
Number of connected outputs for /dev/dri/card0: 2
Does it require offloading? yes
grep dmesg status 256
dmesg status 256 == 0? No
grep dmesg status 256
dmesg status 256 == 0? No
Is nvidia loaded? no
Was nvidia unloaded? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is intel loaded? yes
Is radeon loaded? yes
Is nouveau loaded? no
Vendor/Device Id: 8086:2a42
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 1002:9591
BusID "PCI:1@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...
last cards number = 1
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Is nvidia enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is nvidia available? no
Is fglrx available? no
Is mesa available? yes
Is pxpress available? no
Is prime available? no
Single card detected
Nothing to do
No change - nothing to do


as you can see there are a few additional errors found in here.  I am looking for some help as I have exhausted my limited knowledge trying to troubleshoot this through google, and other forums.

Thanks in advance please let me know if I can provide any additional meaningful data for you to help me along the way.

Please be patient with me as I am very new and may have to ask for very specific details to track down other info!

Thanks.

Tony

---

### Post by slooksterpsv on 2014-08-08
What kind of graphics card is it?

If when you're about to move from the Lenovo screen to booting Ubuntu, if you hold down the shift key (or keep pressing it) a grub menu should show where you can edit boot parameters. If you press e, go to the end where it says quiet splash and add: nomodeset  try booting that way and see if it lets you in. If you're already in and able to get the graphical elements, have you installed or tried to install fglrx? - Software Center -> Edit -> Sources -> Additional Drivers tab.

If it's anythin like 4000 series or prior, it's no longer supported at least for additional drivers, otherwise we may be able to install the fglrx (additional drivers package) to get it working. Best information we could use is what kind of graphics card it is.

---

### Post by sotiris2 on 2014-08-08
He also has intel graphics.

---

### Post by justin60 on 2014-08-08
> **slooksterpsv said:**
> What kind of graphics card is it?

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV635/M86 [Mobility Radeon HD 3650]

---

### Post by Mark Phelps on 2014-08-08
It's a complicated problem to fix:  [http://ubuntuforums.org/showthread.php?t=1930450&highlight=switchable+graphics]("http://ubuntuforums.org/showthread.php?t=1930450&highlight=switchable+graphics")

---

### Post by grahammechanical on 2014-08-08
It is my guess that you have AMD/Intel hybrid graphics. I do not think that you are using the proprietary video driver. This may help

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Regards.

---

### Post by justin60 on 2014-08-08
> **Mark Phelps said:**
> It's a complicated problem to fix:  [http://ubuntuforums.org/showthread.php?t=1930450&highlight=switchable+graphics](http://ubuntuforums.org/showthread.php?t=1930450&highlight=switchable+graphics)

I am following the guide you sent out, but I am getting a syntax error when running the below command.

$ sudo sh ./amd-driver-installer-12-4-x86.x86_64.run --buildpkg Ubuntu/precise
: not foundr-installer-12-4-x86.x86_64.run: 1: ./amd-driver-installer-12-4-x86.x86_64.run: 
./amd-driver-installer-12-4-x86.x86_64.run: 2: ./amd-driver-installer-12-4-x86.x86_64.run: Syntax error: redirection unexpected

The previous command appears to me to have worked ok.

$ wget [http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run)
--2014-08-08 14:00:37--  [http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run)
Resolving www2.ati.com (www2.ati.com)... 23.10.236.96
Connecting to www2.ati.com (www2.ati.com)|23.10.236.96|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://support.amd.com/en-us/download/incomplete](http://support.amd.com/en-us/download/incomplete) [following]
--2014-08-08 14:00:37--  [http://support.amd.com/en-us/download/incomplete](http://support.amd.com/en-us/download/incomplete)
Resolving support.amd.com (support.amd.com)... 23.10.235.218
Connecting to support.amd.com (support.amd.com)|23.10.235.218|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 49893 (49K) [text/html]
Saving to: ‘amd-driver-installer-12-4-x86.x86_64.run’

100%[============================================================>] 49,893      --.-K/s   in 0.007s  

2014-08-08 14:00:38 (6.37 MB/s) - ‘amd-driver-installer-12-4-x86.x86_64.run’ saved [49893/49893]

---

