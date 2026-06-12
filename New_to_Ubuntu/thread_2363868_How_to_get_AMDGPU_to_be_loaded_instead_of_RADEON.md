---
title: "How to get AMDGPU to be loaded instead of RADEON?"
date: 2017-06-15
forum: New to Ubuntu
---

### Post by spockswhitepants on 2017-06-15
I added the Padoka stable PPA and it installed a bunch of stuff but I am still running radeon drivers. What do I have to do to switch to the AMDGPU drivers? 

```
> lshw -c video
  *-display               
       description: VGA compatible controller
       product: Bonaire XTX [Radeon R7 260X/360]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:137 memory:c0000000-cfffffff memory:d0000000-d07fffff ioport:e000(size=256) memory:dfd00000-dfd3ffff memory:c0000-dffff


```

```
> lspci -k | grep -EA2 'VGA|3D'
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Bonaire XTX [Radeon R7 260X/360]
        Subsystem: Gigabyte Technology Co., Ltd Bonaire XTX [Radeon R7 260X/360]
        Kernel driver in use: radeon
```

```
> lsmod | grep radeon
radeon               1515520  18
i2c_algo_bit           16384  1 radeon
ttm                   102400  1 radeon
drm_kms_helper        167936  1 radeon
drm                   368640  12 radeon,ttm,drm_kms_helperlsmod
```

Running Kubuntu 16.04 with KDE backports PPA
```
> uname -a
Linux 4.8.0-54-generic #57~16.04.1-Ubuntu SMP Wed May 24 16:22:28 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

Do I need a newer kernel?

---

### Post by spockswhitepants on 2017-06-15
I installed a new kernel (4.11.5):

```
> uname -a
Linux 4.11.5-041105-generic #201706141137 SMP Wed Jun 14 15:39:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

And now amdgpu shows up in lsmod.

```
> lsmod | grep -i amdgpu
amdgpu               1572864  0
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                    94208  2 amdgpu,radeon
drm_kms_helper        155648  2 amdgpu,radeon
drm                   352256  10 amdgpu,radeon,ttm,drm_kms_helper


```

It is still loading radeon, though. I tried adding blacklist radeon to /etc/modprobe.d/blacklist.conf and that didn't help. It still loads radeon instead of amdgpu.

---

### Post by deadflowr on 2017-06-15
The card belongs to the sea islands family which uses the radeon driver.
[https://www.x.org/wiki/RadeonFeature/]("https://www.x.org/wiki/RadeonFeature/")
I also see the the bonaire firmware is marked in the /lib/firmware/radeon folder.
No bonaire in the lib/firmware/amdgpu folder.

---

### Post by spockswhitepants on 2017-06-15
This card is listed as [supported by amdgpu-pro]("http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Driver-for-Linux-Release-Notes.aspx") - so how can it not be supported by amdgpu which amdgpu-pro runs on top of? I have also tried loading amdgpu-pro but haven't had any luck there. I get a black screen or command prompt (assuming because amdgpu is not there and required for amdgpu-pro to load). I would be happy with anything other than radeon which gives terrible performance - much worse than the old fglrx I ran under 14.04.

I also found [this]("https://www.phoronix.com/scan.php?page=news_item&px=AMD-R7-260X-AMDGPU") from a year and a half ago where Phoronix tested amdgpu on the same card. At the time it required a kernel option but I don't think that applies any more.

---

### Post by QIII on 2017-06-15
You said you installed from a PPA.  Do you know if that PPA is up to date?

There are instructions on the AMD page you referenced that describe how to install the newest driver.  Have you tried that?

---

### Post by spockswhitepants on 2017-06-15
```
Mesa Graphics Stable Padoka Repo

 This is the stable MESA and LLVM (currently at mesa 17.1.x and LLVM 4.0.x).
```

There is also an unstable PPA but I have not tried that one. There is also an Oabif PPA. But I don't think the issue is the PPA - I don't think it ever gets to the point where any of that stuff is ever loaded, because RADEON driver is always loading.

The instructions AMD provides for installing amdgpu-pro are pretty basic and basically no help. It just says to update your system and then extract the archive and run their script - no mention of radeon vs amdgpu etc. Luckily the uninstall script works great.

---

### Post by spockswhitepants on 2017-06-16
I will just end up replacing the AMD with nVidia hardware. I appreciate AMDs stance on open source and all that but I can't get their open source drivers to work and the old proprietary drivers (which were never wonderful but at least I could get them to work) are now unsupported and the new proprietary drivers only run on top of their open source driver (that I can't get to work), what good does it do me? I'm sure there's some way to get it to work but heck if I know how and spending hours or days messing with video drivers and trying to guess what is wrong is not on my top 1000 list of fun things to do. Neither is getting 6 fps on the lowest settings @ 1080p on a card that should be able to do at least 6 times that. Hopefully I will have better luck with the proprietary nVidia drivers.

---

