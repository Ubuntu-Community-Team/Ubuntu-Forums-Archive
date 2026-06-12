---
title: "have to reboot to log in to my computer after goes in sleep mode"
date: 2014-08-30
forum: New to Ubuntu
---

### Post by linux_newf on 2014-08-30
Can you kind folks help me out?

---

### Post by TheFu on 2014-08-31
You'll need to help us out first.
hardware?
**lshw**
Which version/release of ubuntu?
Which kernel?
have you modified anything in /etc/systemd/ or /etc/udev/?

Does the BIOS support standby mode?
Did it ever work before?

---

### Post by linux_newf on 2014-11-16
ok AMD dual core, A4-1250 (1.0 GHz) 4g ddr3, 500gbb hdd.

---

### Post by matt_symes on 2014-11-16
Hi

Is this a laptop or a desktop ?

Does it happen if you suspend the PC or does it happen if it suspends after the suspend timeout ?

More information is needed about your hardware. Run the lshw command from the terminal and post the results into your next post.

Kind regards

---

### Post by linux_newf on 2014-11-16
Thanks, i actually changed my "other drivers" last night to the open source one for radeonn i think its call. Laptop running a lot better from that. Even logged in from sleep mode this morning with no issues. Usually if i can log in wifi won't work anyway so i have to reboot. I also installed the xbuntu desktop, eventhough i still think its ubuntu but when she boots up xbuntu boot screen apppears... no idea

```
brad@brad-Aspire-V5-122P:~$  lshw
WARNING: you should run this program as super-user.
brad-aspire-v5-122p       
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3326MiB
     *-cpu
          product: AMD A4-1250 APU with Radeon(TM) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf eagerfpu pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt topoext perfctr_nb perfctr_l2 arat xsaveopt hw_pstate proc_feedback npt lbrv svm_lock nrip_save tsc_scale flushbyasid decodeassists pausefilter pfthreshold bmi1 cpufreq
     *-pci:0
          description: Host bridge
          product: Family 16h Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Kabini [Radeon HD 8210]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:77 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:2000(size=256) memory:f0900000-f093ffff memory:f0960000-f097ffff
        *-multimedia:0
             description: Audio device
             product: Advanced Micro Devices, Inc. [AMD/ATI]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:75 memory:f0940000-f0943fff
        *-pci
             description: PCI bridge
             product: Family 16h Processor Functions 5:1
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:50 memory:f0800000-f08fffff ioport:f0a00000(size=1048576)
           *-network
                description: Wireless interface
                product: QCA9565 / AR9565 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlan0
                version: 01
                serial: 1c:3e:84:d2:e2:4f
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.13.0-39-generic firmware=N/A ip=10.108.63.72 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:32 memory:f0800000-f087ffff memory:f0a00000-f0a0ffff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:f0948000-f0949fff
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:2118(size=8) ioport:2124(size=4) ioport:2110(size=8) ioport:2120(size=4) ioport:2100(size=16) memory:f094f000-f094f3ff
        *-usb:1
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:f094e000-f094efff
        *-usb:2
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f094d000-f094d0ff
        *-usb:3
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:f094c000-f094cfff
        *-usb:4
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 39
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f094b000-f094b0ff
        *-serial UNCLAIMED
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:76 memory:f0944000-f0947fff
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-generic
             description: SD Host controller
             product: FCH SD Flash Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.7
             bus info: pci@0000:00:14.7
             version: 01
             width: 64 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=sdhci-pci latency=39
             resources: irq:16 memory:f094a000-f094a0ff
     *-pci:1
          description: Host bridge
          product: Family 16h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:02.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 16h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 16h Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 16h Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 16h Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 16h Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: Family 16h Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
brad@brad-Aspire-V5-122P:~$ 

```

---

### Post by matt_symes on 2014-11-16
Hi

You should be able to change to the xubuntu desktop from the login screen.

Does this mean your suspend issues are fixed (including wifi) ?

If wifi is not fixed, does restarting network manager fix it ?

```
sudo service network-manager restart
```

Kind regards

---

### Post by linux_newf on 2014-11-16
yeah i just figured out i can use different desktops on the login screen! i'm using xbuntu now seems more smooth then unity. I think things are better i will see, thanks!

---

### Post by TheFu on 2014-11-16
To get this stuff working, I had to modify some configs in /etc/systemd and create a few scripts for specific hardware for the suspend and wake-up actions under older Ubuntu releases.  That was last spring - haven't noticed it was needed with 14.04.  That machine runs an AMD E350 APU with a Radeon GPU onboard. Networking wasn't the issue for me, waking up the audio and HDMI video where issues.  Sometimes the audio devices disappear until a reboot happens. Forcing a load of the kernel module didn't help. But this is about your issue, not mine. ;)

---

