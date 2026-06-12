---
title: "Live USB Frozen On Boot On Acer Swift 3"
date: 2021-08-10
forum: New to Ubuntu
---

### Post by minedani129 on 2021-08-10
I have an Acer Swift 3 SF314-41 laptop that I am trying to install Ubuntu on using the live USB (Ubuntu hasn't been previously installed). 

The bootloader screen shows up normally and I am able to select "Ubuntu" option. The Acer and Ubuntu logo shows up and there is a little loading circle. However, around 30 seconds in, the screen just freezes and I can't do anything unless I restart the computer. 

I have tried disabling splash and quiet in GRUB in order to view the logs while Ubuntu is trying to boot. It hangs on two start jobs: "A start job is running for monitoring of LVM2 mirrors...", and "A start job is running for Wait for udev to complete device initialization". And I expected it to give some error but the command line ended up freezing as well.

System specs:
- Ryzen 5 3500U with Vega 8 graphics
- 10 GB RAM
- 512GB SSD

I have tried:
- nomodeset
- other distros (debian, kubuntu, fedora, opensuse), basically everything has the exact same problem

I am unsure how to proceed from here. 

Thank you for your help.

---

### Post by The Cog on 2021-08-10
I'm on an Acer swift 3 right now. Love it. 
**sudo lshw** says:
```
    product: Swift SF314-42 (0000000000000000)
    vendor: Acer
    version: V1.04
...
     *-cpu
          description: CPU
          product: AMD Ryzen 7 4700U with Radeon Graphics


```
I had a lot of trouble with it until I installed the 20.04 HWE (hardware enablement) package, that installs a later kernel with more up-to-date drivers. I seem to have been too busy to update beyond 20.04 so far.
This seems to be the package I installed: linux-generic-hwe-20.04-edge
But of course, you have to get the OS installed first. My suggestions are:
* Install the latest available - 21.04
* Try installing Xubuntu rather than plain Ubuntu
* Try using nomodeset as a boot option (although I can't find good instructions on how to do that right now).

---

### Post by minedani129 on 2021-08-10
The Ubuntu version I was trying to install was 21.04. I tried installing Xubuntu with nomodeset but the same error occurred. Also tried installing debian.

---

### Post by minedani129 on 2021-08-11
Seems that this is a recurring problem with my specific laptop model's SSD. You have to disable NVME APST in boot options with nvme_core.default_ps_max_latency_us=0.

---

### Post by The Cog on 2021-08-11
Eeew! That's not a problem I had. Do we have the same model swift and/or the same model SSD? 
From sudo lshw, my ssd is:
```
              *-nvme0
                   description: NVMe device
                   product: SAMSUNG MZVLQ1T0HALB-00000
                   physical id: 0
                   logical name: /dev/nvme0

```

---

### Post by minedani129 on 2021-08-11
My particular model has:
```

*-nvme0 
                   description: NVMe device 
                   product: WDC PC SN520 SDAPNUW-512G-1014 
                   physical id: 0 
                   logical name: /dev/nvme0 

```

and so far after that fix mostly everything has been working fine and I have Ubuntu installed.

---

