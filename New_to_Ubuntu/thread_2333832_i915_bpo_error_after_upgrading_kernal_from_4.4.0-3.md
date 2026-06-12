---
title: "i915_bpo error after upgrading kernal from 4.4.0-31 to 4.4.0-34"
date: 2016-08-13
forum: New to Ubuntu
---

### Post by jbrid2 on 2016-08-13
Hi,
Looking for some guidance on how to handle this suspected bug.

After upgrading to 4.4.0-34, I am receiving this error in syslog:

```
[    1.688565] [drm:intel_dp_link_training_clock_recovery [i915_bpo]] *ERROR* too many voltage retries, give up
[    1.688863] [drm:intel_dp_start_link_train [i915_bpo]] *ERROR* failed to train DP, aborting
[    1.968975] [drm:intel_dp_link_training_clock_recovery [i915_bpo]] *ERROR* too many voltage retries, give up
[    1.974801] [drm:intel_cpu_fifo_underrun_irq_handler [i915_bpo]] *ERROR* CPU pipe A FIFO underrun
[    1.975256] [drm:intel_dp_link_training_clock_recovery [i915_bpo]] *ERROR* too many voltage retries, give up
```

I also got this error during the installation of the new kernel:

> W: Possible missing firmware /lib/firmware/i915/skl_guc_ver6.bin for module i915_bpo

The primary symptom that brought this issue to my attention was that the display does not return when the machine returns from sleep. This symptom started after upgrading to 4.4.0-34.
I found some bug reports that are similar to this involving previous Kernal versions, but nothing current.

Thanks for any insight that you can provide. 

Other info:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

$ sudo lshw -c display  
  *-display               
       description: VGA compatible controller
       product: Sky Lake Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915_bpo latency=0
       resources: irq:123 memory:de000000-deffffff memory:c0000000-cfffffff ioport:f000(size=64)

$ vainfo
libva info: VA-API version 0.39.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.39 (libva 1.7.0)
vainfo: Driver version: Intel i965 driver for Intel(R) Skylake - 1.7.0
vainfo: Supported profile and entrypoints

$ inxi -b
Machine:System: Gigabyte product: N/A
            Mobo: Gigabyte model: H170M-D3H-CF v: x.x
            Bios: American Megatrends v: F6 date: 03/07/2016
CPU:Quad core Intel Core i5-6500 (-MCP-) speed/max: 800/3600 MHz
Graphics:Card: Intel Sky Lake Integrated Graphics
             Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
             Resolution: 1360x768@60.02hz
             GLX Renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2)
             GLX Version: 3.0 Mesa 11.2.0

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 06)

$  lsmod |grep video
video                  40960  1 i915_bpo


```

---

### Post by wildmanne39 on 2016-08-14
*Thread moved to **New to Ubuntu**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by arsenic23 on 2016-08-14
If you are using a skylake integrated GPU then I **highly** recommend trying the 4.7 kernel.  The stability and performance of the G4500 skylake (gpu) I just setup as a new TVPC improved in kernel 4.6.3, but upon switching to kernel 4.7, I was overjoyed at how much better the system is running.

My 4k upscaling is still less then perfect, but the system isn't a buggy mess anymore and performance is much better then under the other kernels I tried.

---

### Post by jbrid2 on 2016-08-15
> **arsenic23 said:**
> If you are using a skylake integrated GPU then I **highly** recommend trying the 4.7 kernel.  The stability and performance of the G4500 skylake (gpu) I just setup as a new TVPC improved in kernel 4.6.3, but upon switching to kernel 4.7, I was overjoyed at how much better the system is running.

My 4k upscaling is still less then perfect, but the system isn't a buggy mess anymore and performance is much better then under the other kernels I tried.

Thanks for the recommendation.

I have never installed a kernal before. Is [this ]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7/")the version that you are recommending and are [these good instructions]("http://linuxdaddy.com/blog/install-kernel-4-4-on-ubuntu/") on how to install?

Thanks!

---

### Post by Doug S on 2016-08-16
For your original issue, the various firmware packages are lagging behind the kernel. You can get the needed firmware from [here]("https://01.org/linuxgraphics/intel-linux-graphics-firmwares"). See also [here]("http://askubuntu.com/questions/811453/w-possible-missing-firmware-for-module-i915-bpo-when-updating-initramfs").

And yes, those instructions should work, and that kernel can be used, but I assume there is some Ubuntu version of it around somewhere by now (I don't know where).

---

### Post by arsenic23 on 2016-08-17
All you need to do is download:
```
linux-headers-4.7.0-040700_4.7.0-040700.201608021801_all.deb
linux-headers-4.7.0-040700-generic_4.7.0-040700.201608021801_amd64.deb
linux-image-4.7.0-040700-generic_4.7.0-040700.201608021801_amd64.deb

```
from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.7/) into a directory and run:
```
sudo dpkg -i *.deb
``` from the terminal.

Reboot and make sure you are using the new kernel with ```
uname -r
```.

I did a fresh 16.04 install, switched over to that kernel, and nothing else.  It fixed every problem I was having with the skylake GPU except slightly poorer up-scaling performance in linux compared to windows.  No more crashes, no more video issues with 10-bit or hecv, no more Steam crashes, everything just worked.  
Of course, if you have never installed a kernel before, please make sure you are familiar with how to roll back to your old kernel in case your particular hardware setup has an issue mine does not.

---

### Post by jbrid2 on 2016-08-18
Thanks to all for your help. I installed 4.7 and it is working well. It solved the original issue that I was having where the display did not return after the session returned from sleep.

Also, another tip that could help others:
In VLC I had to set the Video Output to 'Open GLX video output (VCB)' in the Video Settings. This solved another issue I was having with video playback.

---

