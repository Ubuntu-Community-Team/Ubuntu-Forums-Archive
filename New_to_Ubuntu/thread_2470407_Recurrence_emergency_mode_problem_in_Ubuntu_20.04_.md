---
title: "Recurrence emergency mode problem in Ubuntu 20.04 LTS"
date: 2021-12-29
forum: New to Ubuntu
---

### Post by anupamjamatia on 2021-12-29
Hi Ubuntu Community, I am facing recurrence "emergency mode" problem while booting my Ubuntu 20.04 LTS. I do repair using the fsck command. After fsck command it repaired and run smoothly, but again after 2 to 3 reboot it appears the "emergency mode". I am not able to get rid of this problem. 
While installing the OS, what i did was, I choose /swap, /boot and root (/) in SSD Drive and /home in SATA  Drive. Can anyone please help me out from this problem please. 

My system configuration is:

```
Architecture:                    x86_64
CPU op-mode(s):                  32-bit, 64-bit
Byte Order:                      Little Endian
Address sizes:                   39 bits physical, 48 bits virtual
CPU(s):                          12
On-line CPU(s) list:             0-11
Thread(s) per core:              2
Core(s) per socket:              6
Socket(s):                       1
NUMA node(s):                    1
Vendor ID:                       GenuineIntel
CPU family:                      6
Model:                           158
Model name:                      Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz
Stepping:                        10
CPU MHz:                         2200.000
CPU max MHz:                     4100.0000
CPU min MHz:                     800.0000
BogoMIPS:                        4399.99
Virtualization:                  VT-x
L1d cache:                       192 KiB
L1i cache:                       192 KiB
L2 cache:                        1.5 MiB
L3 cache:                        9 MiB
NUMA node0 CPU(s):               0-11
Vulnerability Itlb multihit:     KVM: Mitigation: VMX disabled
Vulnerability L1tf:              Mitigation; PTE Inversion; VMX conditional cach
                                 e flushes, SMT vulnerable
Vulnerability Mds:               Mitigation; Clear CPU buffers; SMT vulnerable
Vulnerability Meltdown:          Mitigation; PTI
Vulnerability Spec store bypass: Mitigation; Speculative Store Bypass disabled v
                                 ia prctl and seccomp
Vulnerability Spectre v1:        Mitigation; usercopy/swapgs barriers and __user
                                  pointer sanitization
Vulnerability Spectre v2:        Mitigation; Full generic retpoline, IBPB condit
                                 ional, IBRS_FW, STIBP conditional, RSB filling
Vulnerability Srbds:             Mitigation; Microcode
Vulnerability Tsx async abort:   Not affected
Flags:                           fpu vme de pse tsc msr pae mce cx8 apic sep mtr
                                 r pge mca cmov pat pse36 clflush dts acpi mmx f
                                 xsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rd
                                 tscp lm constant_tsc art arch_perfmon pebs bts 
                                 rep_good nopl xtopology nonstop_tsc cpuid aperf
                                 mperf pni pclmulqdq dtes64 monitor ds_cpl vmx e
                                 st tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_
                                 1 sse4_2 x2apic movbe popcnt tsc_deadline_timer
                                  aes xsave avx f16c rdrand lahf_lm abm 3dnowpre
                                 fetch cpuid_fault epb invpcid_single pti ssbd i
                                 brs ibpb stibp tpr_shadow vnmi flexpriority ept
                                  vpid ept_ad fsgsbase tsc_adjust sgx bmi1 avx2 
                                 smep bmi2 erms invpcid mpx rdseed adx smap clfl
                                 ushopt intel_pt xsaveopt xsavec xgetbv1 xsaves 
                                 dtherm ida arat pln pts hwp hwp_notify hwp_act_
                                 window hwp_epp sgx_lc md_clear flush_l1d

```
```

$ cat /proc/meminfo
MemTotal:       16177684 kB
MemFree:         9998688 kB
MemAvailable:   12475024 kB
Buffers:          138024 kB
Cached:          2800548 kB
SwapCached:            0 kB
Active:           953824 kB
Inactive:        4628380 kB
Active(anon):       9116 kB
Inactive(anon):  2914916 kB
Active(file):     944708 kB
Inactive(file):  1713464 kB
Unevictable:          32 kB
Mlocked:              32 kB
SwapTotal:      20507644 kB
SwapFree:       20507644 kB
Dirty:               164 kB
Writeback:             0 kB
AnonPages:       2643716 kB
Mapped:           855564 kB
Shmem:            286716 kB
KReclaimable:     156516 kB
Slab:             310376 kB
SReclaimable:     156516 kB
SUnreclaim:       153860 kB
KernelStack:       20576 kB
PageTables:        48420 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    28596484 kB
Committed_AS:   13617700 kB
VmallocTotal:   34359738367 kB
VmallocUsed:       90788 kB
VmallocChunk:          0 kB
Percpu:            13120 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
ShmemHugePages:        0 kB
ShmemPmdMapped:        0 kB
FileHugePages:         0 kB
FilePmdMapped:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
Hugetlb:               0 kB
DirectMap4k:      524608 kB
DirectMap2M:     7651328 kB
DirectMap1G:     8388608 kB

```
```
cat /proc/version
Linux version 5.11.0-43-generic (buildd@lcy02-amd64-036) (gcc (Ubuntu 9.3.0-17ubuntu1~20.04) 9.3.0, GNU ld (GNU Binutils for Ubuntu) 2.34) #47~20.04.2-Ubuntu SMP Mon Dec 13 11:06:56 UTC 2021



```
```
$ lspci
00:00.0 Host bridge: Intel Corporation 8th Gen Core Processor Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 07)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10)
00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
00:14.3 Network controller: Intel Corporation Wireless-AC 9560 [Jefferson Peak] (rev 10)
00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
00:17.0 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 10)
00:1b.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #21 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #9 (rev f0)
00:1d.5 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #14 (rev f0)
00:1d.7 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #16 (rev f0)
00:1f.0 ISA bridge: Intel Corporation HM470 Chipset LPC/eSPI Controller (rev 10)
00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
01:00.0 VGA compatible controller: NVIDIA Corporation GP104BM [GeForce GTX 1070 Mobile] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GP104 High Definition Audio Controller (rev a1)
3b:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM961/PM961
3c:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 16)
3d:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)

```
```
$ lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0         7:0    0     4K  1 loop /snap/bare/5
loop1         7:1    0  99.4M  1 loop /snap/core/11993
loop2         7:2    0  61.9M  1 loop /snap/core20/1270
loop3         7:3    0     9M  1 loop /snap/canonical-livepatch/126
loop4         7:4    0   219M  1 loop /snap/gnome-3-34-1804/72
loop5         7:5    0  55.4M  1 loop /snap/core18/2128
loop6         7:6    0 134.4M  1 loop /snap/skype/197
loop7         7:7    0   219M  1 loop /snap/gnome-3-34-1804/77
loop8         7:8    0 164.8M  1 loop /snap/gnome-3-28-1804/161
loop9         7:9    0  65.1M  1 loop /snap/gtk-common-themes/1515
loop10        7:10   0  54.2M  1 loop /snap/snap-store/558
loop11        7:11   0  43.3M  1 loop /snap/snapd/14295
loop12        7:12   0 323.6M  1 loop /snap/telegram-desktop/3455
loop13        7:13   0    51M  1 loop /snap/snap-store/547
loop14        7:14   0  65.2M  1 loop /snap/gtk-common-themes/1519
loop15        7:15   0   140K  1 loop /snap/gtk2-common-themes/13
loop16        7:16   0 323.5M  1 loop /snap/kde-frameworks-5-qt-5-15-core20/14
loop17        7:17   0  55.5M  1 loop /snap/core18/2253
loop18        7:18   0 247.9M  1 loop /snap/gnome-3-38-2004/87
loop19        7:19   0  32.3M  1 loop /snap/snapd/12704
loop20        7:20   0 150.2M  1 loop /snap/okular/109
sda           8:0    0 931.5G  0 disk 
&#9492;&#9472;sda1        8:1    0 931.5G  0 part /home
nvme0n1     259:0    0 119.2G  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0   857M  0 part /boot/efi
&#9500;&#9472;nvme0n1p2 259:2    0   2.8G  0 part /boot
&#9500;&#9472;nvme0n1p3 259:3    0  19.6G  0 part [SWAP]
&#9492;&#9472;nvme0n1p4 259:4    0  96.1G  0 part /

```
```
$ sudo fdisk -l | grep '^Disk /dev/'
Disk /dev/loop0: 4 KiB, 4096 bytes, 8 sectors
Disk /dev/loop1: 99.45 MiB, 104267776 bytes, 203648 sectors
Disk /dev/loop2: 61.93 MiB, 64913408 bytes, 126784 sectors
Disk /dev/loop3: 9.3 MiB, 9465856 bytes, 18488 sectors
Disk /dev/loop4: 219 MiB, 229638144 bytes, 448512 sectors
Disk /dev/loop5: 55.45 MiB, 58130432 bytes, 113536 sectors
Disk /dev/loop6: 134.44 MiB, 140963840 bytes, 275320 sectors
Disk /dev/loop7: 219 MiB, 229638144 bytes, 448512 sectors
Disk /dev/nvme0n1: 119.25 GiB, 128035676160 bytes, 250069680 sectors
Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk /dev/loop8: 164.78 MiB, 172761088 bytes, 337424 sectors
Disk /dev/loop9: 65.1 MiB, 68259840 bytes, 133320 sectors
Disk /dev/loop10: 54.24 MiB, 56872960 bytes, 111080 sectors
Disk /dev/loop11: 43.28 MiB, 45371392 bytes, 88616 sectors
Disk /dev/loop12: 323.61 MiB, 339316736 bytes, 662728 sectors
Disk /dev/loop13: 50.98 MiB, 53432320 bytes, 104360 sectors
Disk /dev/loop14: 65.22 MiB, 68378624 bytes, 133552 sectors
Disk /dev/loop15: 140 KiB, 143360 bytes, 280 sectors
Disk /dev/loop16: 323.52 MiB, 339222528 bytes, 662544 sectors
Disk /dev/loop17: 55.5 MiB, 58183680 bytes, 113640 sectors
Disk /dev/loop18: 247.93 MiB, 259948544 bytes, 507712 sectors
Disk /dev/loop19: 32.3 MiB, 33865728 bytes, 66144 sectors
Disk /dev/loop20: 150.17 MiB, 157462528 bytes, 307544 sectors


```
```
H/W path         Device        Class          Description
=========================================================
                               system         Computer
/0                             bus            Motherboard
/0/0                           memory         15GiB System memory
/0/1                           processor      Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz
/0/100                         bridge         8th Gen Core Processor Host Bridge/DRAM Registers
/0/100/1                       bridge         Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16)
/0/100/1/0                     display        GP104BM [GeForce GTX 1070 Mobile]
/0/100/1/0.1                   multimedia     GP104 High Definition Audio Controller
/0/100/4                       generic        Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
/0/100/8                       generic        Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
/0/100/12                      generic        Cannon Lake PCH Thermal Controller
/0/100/14                      bus            Cannon Lake PCH USB 3.1 xHCI Host Controller
/0/100/14.2                    memory         RAM memory
/0/100/14.3      wlo1          network        Wireless-AC 9560 [Jefferson Peak]
/0/100/16                      communication  Cannon Lake PCH HECI Controller
/0/100/17                      storage        82801 Mobile SATA Controller [RAID mode]
/0/100/1b                      bridge         Cannon Lake PCH PCI Express Root Port #21
/0/100/1d                      bridge         Cannon Lake PCH PCI Express Root Port #9
/0/100/1d/0                    storage        NVMe SSD Controller SM961/PM961
/0/100/1d/0/0    /dev/nvme0    storage        SAMSUNG MZVLW128HEGR-000H1
/0/100/1d/0/0/1  /dev/nvme0n1  disk           NVMe namespace
/0/100/1d.5                    bridge         Cannon Lake PCH PCI Express Root Port #14
/0/100/1d.5/0    eno1          network        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/1d.7                    bridge         Cannon Lake PCH PCI Express Root Port #16
/0/100/1d.7/0                  generic        RTS522A PCI Express Card Reader
/0/100/1f                      bridge         HM470 Chipset LPC/eSPI Controller
/0/100/1f.3                    multimedia     Cannon Lake PCH cAVS
/0/100/1f.4                    bus            Cannon Lake PCH SMBus Controller
/0/100/1f.5                    bus            Cannon Lake PCH SPI Controller
/0/2                           system         PnP device PNP0c02
/0/3                           system         PnP device PNP0b00
/0/4                           generic        PnP device INT3f0d
/0/5                           generic        PnP device HPQ8001
/0/6                           generic        PnP device SYN327c
/0/7                           system         PnP device PNP0c02
/0/8                           system         PnP device PNP0c02
/0/9                           system         PnP device PNP0c02
/0/a                           system         PnP device PNP0c02
~


```

Thanks and regards 
anupam

---

### Post by Bashing-om on 2021-12-29
anupamjamatia - Hello

As the file system experiences recurrent inconsistencies maybe there are hardware problems with the drives.

Have you ran the smart test to see if there are reported errors/conditions ?
 [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

as a guide to do these test.

[INDENT]hope this helps
[/INDENT]

---

