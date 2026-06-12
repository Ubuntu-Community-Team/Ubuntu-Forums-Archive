---
title: "How to enable Huge Pages support for all nodes"
date: 2021-09-29
forum: New to Ubuntu
---

### Post by xfi on 2021-09-29
Greetings!

I have Ubuntu 20.04.3 LTS server fresh install with 8 nodes (2xAMD 7551 processor) and 32GB of memory. I would need to have Huge Pages enabled for all of the nodes, however for some reason I can enable them only for 2 out of 8 nodes. 

What I have done so far is: 

added "vm.nr_hugepages = 1024" to /etc/sysctl.conf

appended the following to /etc/default/grub AND updated grub "sudo grub-mkconfig -o /boot/grub/grub.cfg" AND rebooted machine
GRUB_CMDLINE_LINUX_DEFAULT="default_hugepagesz=2M hugepagesz=1G hugepages=8"
GRUB_CMDLINE_LINUX="default_hugepagesz=2M hugepagesz=1G hugepages=8"

```
cat /proc/meminfo | grep Huge
AnonHugePages:      2048 kB
ShmemHugePages:        0 kB
FileHugePages:         0 kB
HugePages_Total:    1024
HugePages_Free:     1024
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
Hugetlb:        10485760 kB
```

```
cat /sys/devices/system/node/node*/meminfo | fgrep Huge
Node 0 AnonHugePages:         0 kB
Node 0 ShmemHugePages:        0 kB
Node 0 FileHugePages:        0 kB
Node 0 HugePages_Total:     0
Node 0 HugePages_Free:      0
Node 0 HugePages_Surp:      0
Node 1 AnonHugePages:     14336 kB
Node 1 ShmemHugePages:        0 kB
Node 1 FileHugePages:        0 kB
Node 1 HugePages_Total:   512
Node 1 HugePages_Free:    512
Node 1 HugePages_Surp:      0
Node 2 AnonHugePages:         0 kB
Node 2 ShmemHugePages:        0 kB
Node 2 FileHugePages:        0 kB
Node 2 HugePages_Total:     0
Node 2 HugePages_Free:      0
Node 2 HugePages_Surp:      0
Node 3 AnonHugePages:         0 kB
Node 3 ShmemHugePages:        0 kB
Node 3 FileHugePages:        0 kB
Node 3 HugePages_Total:     0
Node 3 HugePages_Free:      0
Node 3 HugePages_Surp:      0
Node 4 AnonHugePages:         0 kB
Node 4 ShmemHugePages:        0 kB
Node 4 FileHugePages:        0 kB
Node 4 HugePages_Total:     0
Node 4 HugePages_Free:      0
Node 4 HugePages_Surp:      0
Node 5 AnonHugePages:      2048 kB
Node 5 ShmemHugePages:        0 kB
Node 5 FileHugePages:        0 kB
Node 5 HugePages_Total:   512
Node 5 HugePages_Free:    512
Node 5 HugePages_Surp:      0
Node 6 AnonHugePages:         0 kB
Node 6 ShmemHugePages:        0 kB
Node 6 FileHugePages:        0 kB
Node 6 HugePages_Total:     0
Node 6 HugePages_Free:      0
Node 6 HugePages_Surp:      0
Node 7 AnonHugePages:         0 kB
Node 7 ShmemHugePages:        0 kB
Node 7 FileHugePages:        0 kB
Node 7 HugePages_Total:     0
Node 7 HugePages_Free:      0
Node 7 HugePages_Surp:      0

```

Additionally, what would be reasonable settings for Huge Pages so that maximum of 75% of the memory capacity would be reserved for this? I'm trying to accomplish a working setup with [cpuminer-gr-avx2]("https://github.com/WyvernTKC/cpuminer-gr-avx2"). 

Thank you for any help in advance!

---

### Post by xfi on 2021-09-30
Okay, so it seems this is likely a memory configuration based issue.  Need to install more RAM sticks in order to give all nodes access to  memory.

---

