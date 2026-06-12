---
title: "Poor velocity write to the Pen Drive - Lubuntu 18.04.2 LTS"
date: 2019-04-26
forum: New to Ubuntu
---

### Post by sed_faster on 2019-04-26
Hello,

How can I measure the velocity and process to write in external drive through my Linux. I create this script:
```

#!/bin/bash
lsb_release -a>>log.txt
uname -a>>log.txt
date>>log.txt
cp -pv /media/user/e6fd712f-812234234345c-4d56-b418b3cdf4/user/Downloads/lubuntu-18.04.2-desktop-amd648.iso /media/user/8GB/>>log.txt
date>>log.txt

```

And this is the log data:
```

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic
Linux user 4.18.0-18-generic #19~18.04.1-Ubuntu SMP Fri Apr 5 10:22:13 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Start: 23:13:35 

'/media/user/SSD/user/Downloads/lubuntu-18.04.2-desktop-amd648.iso' -> '/media/user/8GB/lubuntu-18.04.2-desktop-amd648.iso'

Finished: 23:21:57 

$ ls -lh
total 2,2G
-rw-r--r-- 1 user user 1,1G  lubuntu-18.04.2-desktop-amd648.iso
-rw-r--r-- 1 user user 1,1G  lubuntu-18.04.2-desktop-amd64.iso
drwxr-xr-x 2 user user  16K 'System Volume Information'

```

My system is:
```

$ sudo lshw -class cpu
  *-cpu                     
       description: CPU
       product: Intel(R) Core(TM) i5-7500 CPU @ 3.40GHz
       vendor: Intel Corp.
       physical id: 4b
       bus info: cpu@0
       version: Intel(R) Core(TM) i5-7500 CPU @ 3.40GHz
       serial: To Be Filled By O.E.M.
       slot: LGA1151
       size: 3675MHz
       capacity: 4005MHz
       width: 64 bits
       clock: 100MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp flush_l1d cpufreq
       configuration: cores=4 enabledcores=4 threads=4

$ free -m
              total        used        free      shared  buff/cache   available
Mem:           7911         675        6271         123         964        6866
Swap:           450           0         450


```

The same pen drive ([https://www.verbatim.com/prod/flash-memory/usb-drives/everyday-usb-drives/pinstripe-usb-drive-sku-49062/](https://www.verbatim.com/prod/flash-memory/usb-drives/everyday-usb-drives/pinstripe-usb-drive-sku-49062/)) over windows 10 I can send the same drive between pc to Pen and Pen to PC in less one minute. How can I improve my Linux?
By the way I installed my system through ISO on website [https://lubuntu.me/](https://lubuntu.me/)
Thanks

---

### Post by sed_faster on 2019-04-30
Hello folks,

I formatted the pendrive as ext4 and run this script:
```

#!/bin/bash
date>>log.txt
cp -pv lubuntu-18.04.2-desktop-amd64.iso /media/user/8GB/
date>>log.txt
sudo umount /media/user/8GB
date>>log.txt

```
And the result is:
```

03:38:05 WEST 2019
03:38:07 WEST 2019
03:41:17 WEST 2019

```
What could be causing this slowness?
Thanks

---

### Post by oldrocker99 on 2019-05-01
To burn an .iso image to a thumb drive, it **MUST** be formatted as FAT, not any other file system. Than, it should definitely run fine.

---

