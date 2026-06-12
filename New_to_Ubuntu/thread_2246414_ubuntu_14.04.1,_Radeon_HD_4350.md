---
title: "ubuntu 14.04.1, Radeon HD 4350"
date: 2014-09-30
forum: New to Ubuntu
---

### Post by selIs on 2014-09-30
I'm new to ubuntu help me slove It

It shows Gallium 0.4 on AMD RV710 

MY ORIGINAL IS ATI RADEON hd 4350

I'm new to ubuntu thing

---

### Post by Impavidus on 2014-09-30
13.10 is unsupported. It had only 9 months of support. With the repositories off line and no bug fixes it's not a good idea to try and fix it. Better install 14.04 LTS (=Long Term Support, 5 years).

---

### Post by papibe on 2014-09-30
Hi selIs. Welcome to the forum ):P

Unfortunately, version 13.10 has reached EOL (end of life) so in no longer supported.

I recommend you to download the new 14.04.01 version. I'd also recommend downloading it using a torrent client because that reduces the chances of file corruption (link [here]("http://www.ubuntu.com/download/alternative-downloads")).

Once you have installed the new version, please open a terminal run these commands, and post back the results (you can copy/paste the text):
```
lsb_release -a

lspci -nnk | grep -iA2 vga

lshw -C display

lsmod | grep -iE 'radeon|fglrx'
```
Regards.

---

### Post by Mark Phelps on 2014-09-30
> MY ORIGINAL IS ATI RADEON hd 4350

Then, you need to remain with the original Radeon drivers that get loaded as part of the initial installation.

AMD dropped fglrx driver support for their HD 4xxx series last year, and any Ubuntu version newer than 12.04.1 is going to have an X-server version that is incompatible with the AMD fglx drivers.

---

### Post by selIs on 2014-09-30
I INSTALLED 14.04.01

RUN TERMINA AND THIS WHAT I GET 

```

[LIST=1]
[*]lsb_release -a
[/LIST]
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
[LIST=1]
[*]  lspci -nnk | grep -iA2 vga
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV710 [Radeon HD 4350/4550] [1002:954f]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1613]
    Kernel driver in use: radeon
[*]lshw -C display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: RV710 [Radeon HD 4350/4550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:41 memory:e0000000-efffffff memory:febf0000-febfffff ioport:e000(size=256) memory:febc0000-febdffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
[*] lsmod | grep -iE 'radeon|fglrx'
radeon               1522474  4 
ttm                    85115  1 radeon
drm_kms_helper         53081  1 radeon
drm                   303102  6 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
[/LIST]

```

---

### Post by grahammechanical on 2014-09-30
For your information Gallium indicates that the system is using the default open source video driver and RV170 is most likely the AMD/ATI code number for the Radeon HD 4350.

I have an Nvidia GT220 and my details page says Gallium 0.4 on NVA5 and I know that NVA5 is the Nvidia code for its GT220 video adapter because I looked it up on the Nvidia web site. I also know that I have not installed the Nvidia proprietary video driver.

If you wish to activate the proprietary video driver then go to System Settings>Software and Updates>Additional Drivers tab and select one.

There is something that I do find strange about your report. Gallium is the code name for the open source video driver when running on an Nvidia graphic card. When the card is AMD/ATI the open source video driver should be called Radeon.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Oh, one more thing that you may be unaware of. AMD now own ATI and have done for a few years. What is your problem? 

Regards.

---

### Post by deadflowr on 2014-09-30
Was it always 14.04.01 or is it from clean upgrade from 13.10?

Also, is the gallium name still showing, where ever you saw it?

And have you run an update yet?

---

### Post by papibe on 2014-09-30
Thanks.

It looks you're all set.

The card is recognized, the correct driver was assigned, and it is properly loaded.

Is the resolution OK?

Regards.

---

### Post by Bucky Ball on 2014-09-30
Changed thread title for clarity. ;)

---

### Post by selIs on 2014-10-01
> **deadflowr said:**
> Was it always 14.04.01 or is it from clean upgrade from 13.10?

Also, is the gallium name still showing, where ever you saw it?

And have you run an update yet?

yeah It show 

an update not yet.

> **papibe said:**
> Thanks.

It looks you're all set.

The card is recognized, the correct driver was assigned, and it is properly loaded.

Is the resolution OK?

Regards.

yeah Its ok but low qualIty on Games and so laggy 

any help please?

---

### Post by Mark Phelps on 2014-10-01
> yeah Its ok but low qualIty on Games and so laggy 

The default Radeon driver does OK on gaming and, in my experience, has not been "laggy" -- but, as with the others, I'm concerned that it doesn't show Radeon as the driver.  

Sorry, but there are no "Additional Drivers" for your video chipset.  AMD dropped support for that chipset last year.

---

