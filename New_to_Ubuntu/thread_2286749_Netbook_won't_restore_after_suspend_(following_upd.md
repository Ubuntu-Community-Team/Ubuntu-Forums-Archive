---
title: "Netbook won't restore after suspend (following update)"
date: 2015-07-14
forum: New to Ubuntu
---

### Post by 0149 on 2015-07-14
I searched the available threads and I didn't see a solution to my problem. Basically, the screen stays black (eg, with no restore) after I suspend the system from either (a) the terminal, (b) the logout menu, or (c) closing the lid. As a temporary solution, I've gone to the power settings and excluded suspending as an option, instead relying on lockscreen and shut-down.
 
What can I post to help you help me? I know that these threads usually require lots of technical information, but I don't know how to do that.

---

### Post by 0149 on 2015-07-15
It would be nice if anyone could help. My netbook keeps running out of power because I can't suspend it. Thanks!

---

### Post by sudodus on 2015-07-15
Welcome to the Ubuntu Forums :-)

I don't know much about suspend - I don't use it. (But I do use Lubuntu.)

Please tell us as many details as possible about your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

You can reply with your own words or attach the output file **lshw.txt** of these commands in a terminal window

```

sudo -s
lshw -sanitize > lshw.txt
exit  # from superuser

```

and which version of Lubuntu you are using. The name of the iso file, that you downloaded would tell us, or the output of the following commands

```
lsb_release -a
uname -a
```

-o-

Does suspend work, when you boot a live session from the USB drive?

-o-

I think and hope that several people can help you, when we know more about your computer.

---

### Post by matt_symes on 2015-07-15
Hi

Also post your log file around the time you resume.

/var/log/syslog

I'm betting it's graphics

Kind regards

---

### Post by 01492 on 2015-07-20
I tried to copy and paste this into the terminal: 
sudo -s
lshw -sanitize > lshw.txt
exit  # from superuserbut I didn't get any output as you suggested I would.

I did get a bunch of stuff when I stopped after the "sanitize" command. Here it is:


```
computer                  
    description: Computer
    width: 32 bits
    capabilities: smbios-2.7
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1900MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU  N2840  @ 2.16GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.8
          serial: [REMOVED]
          size: 1582MHz
          capacity: 2582MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer rdrand lahf_lm 3dnowprefetch ida arat epb dtherm tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms cpufreq
          configuration: id=2
        *-logicalcpu:0
             description: Logical CPU
             physical id: 2.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 2.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 2.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 2.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 2.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 2.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 2.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 2.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 2.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 2.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 2.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 2.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 2.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 2.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 2.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 2.10
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0e
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:91 memory:90000000-903fffff memory:80000000-8fffffff ioport:2050(size=8)
        *-generic:0
             description: SD Host controller
             product: Atom Processor Z36xxx/Z37xxx Series SDIO Controller
             vendor: Intel Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci-pci latency=0
             resources: irq:18 memory:90921000-90921fff memory:90920000-90920fff
        *-storage
             description: SATA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 0e
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:88 ioport:2048(size=8) ioport:205c(size=4) ioport:2040(size=8) ioport:2058(size=4) ioport:2020(size=32) memory:9091f000-9091f7ff
        *-usb:0
             description: USB controller
             product: Atom Processor Z36xxx/Z37xxx Series USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 0e
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:87 memory:90900000-9090ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 3.19.0-22-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 3.19
                capabilities: usb-3.00
                configuration: driver=hub slots=1 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 3.19.0-22-generic xhci-hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 3.19
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb:0
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 2
                   bus info: usb@1:2
                   version: 85.37
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb
                      description: Bluetooth wireless interface
                      vendor: Lite-On Technology Corp.
                      physical id: 1
                      bus info: usb@1:2.1
                      version: 0.02
                      capabilities: bluetooth usb-1.10
                      configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:1
                   description: Video
                   product: HD WebCam
                   vendor: SunplusIT INC.
                   physical id: 4
                   bus info: usb@1:4
                   version: 22.04
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-generic:1
             description: SD Host controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci-pci latency=0
             resources: irq:23 memory:9091e000-9091efff memory:9091d000-9091dfff
        *-generic:2
             description: Encryption controller
             product: Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:90 memory:90800000-908fffff memory:90700000-907fffff
        *-multimedia
             description: Audio device
             product: Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 0e
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:92 memory:90910000-90913fff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096)
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:4000(size=4096) memory:90600000-906fffff
           *-network
                description: Wireless interface
                product: QCA9565 / AR9565 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.19.0-22-generic firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:90600000-9067ffff memory:90680000-9068ffff
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:1000(size=4096) memory:90500000-905fffff ioport:90400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 0c
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:89 ioport:1000(size=256) memory:90500000-90500fff memory:90400000-90403fff
        *-usb:1
             description: USB controller
             product: Atom Processor Z36xxx/Z37xxx Series USB EHCI
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:90918000-909183ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 3.19.0-22-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 3.19
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@3:1
                   version: 0.14
                   capabilities: usb-2.00
                   configuration: driver=hub slots=4 speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: Atom Processor Z36xxx/Z37xxx Series Power Control Unit
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-serial UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:90919000-9091901f ioport:2000(size=32)
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD2500LPVX-2
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1A01
             serial: [REMOVED]
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=022e61b3
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 230GiB
                capacity: 230GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2015-01-13 18:54:49 filesystem=ext4 lastmountpoint=/ modified=2015-07-20 12:33:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-07-20 12:33:48 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1932MiB
                capacity: 1932MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1932MiB
                   capabilities: nofs
```

Here's the output I got for lsb_release -a

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 15.04
Release:	15.04
Codename:	vivid



And here's the output I got for uname -a

Linux evan-Aspire-ES1-111M 3.19.0-22-generic #22-Ubuntu SMP Tue Jun 16 17:14:22 UTC 2015 i686 i686 i686 GNU/Linux

> **matt_symes said:**
> Hi

Also post your log file around the time you resume.

/var/log/syslog

I'm betting it's graphics

Kind regards

That's the problem--*I can't resume*.

I can't suspend, lock screen, hibernate, or even shut down any more, unless my netbook either (a) runs out of power, or (b) I hold down the power button until I force the netbook to shut down.

---

### Post by matt_symes on 2015-07-23
Hi

> I can't suspend, lock screen, hibernate, or even shut down any more, unless my netbook either (a) runs out of power, or (b) I hold down the power button until I force the netbook to shut down. 

Thanks for the clarification. That's a major problem then.

Open a terminal and type

```
echo shutdown | /sys/power/disk
```

Does it shutdown ? It is does then it may suggest an ACPI issue.

Also try

```
echo reboot | /sys/power/disk
```

Does it reboot ?

Kind regards

---

### Post by 01492 on 2015-08-10
Sorry about the delay. 

When I tried both of your suggestions, I got "permission denied" from the terminal.

I tried your commands with "sudo" in front, but that gave me the same permission denied message:

```
bash: /sys/power/disk: Permission denied
```

I tried it again using a terminal window that I opened with the terminal command. So it says I'm using root@computer-name ... but I'm still getting "permission denied."

Okay, I followed some instructions I saw [here]("http://askubuntu.com/questions/201534/sudo-non-password-access-to-sys-power-state") [askubuntu.com] and I came up with a way to sudo your "echo" suggestions:

```
root@computer-name:~# echo shutdown | sudo tee /sys/power/disk
```

and the terminal answered,

```
shutdown
```

Likewise, I tried this:

```
root@computer-name:~# echo reboot | sudo tee /sys/power/disk
```

and I got this:

```
reboot
```

Okay, just for laughs I tried changing the vertical pipe | to an angle bracket > since that's something I saw [here]("https://help.ubuntu.com/community/PowerManagement/Hibernate"), so I made these commands:

```
echo shutdown > /sys/power/disk
echo reboot > /sys/power/disk
```

But nothing happened.

---

### Post by 01492 on 2015-08-19
Can anyone help me out?

---

### Post by matt_symes on 2015-08-19
Hi

Sorry for the delay. I was afk for a week or so and your reply fell from my subscriptions.

Also, sorry for missing out the sudo tee in those two commands. I can only assume I had a brain fart while writing that post.

Anyway, I take it that the laptop did not shutdown or reboot ? You kind or never answered that question.

Kind regards

---

### Post by deathbyfreezeray on 2015-10-11
I have this exact computer. Are you using it in UEFI mode or bios? The bios on this laptop is buggy as mentioned here [https://wiki.archlinux.org/index.php/Acer_Aspire_E11_Series](https://wiki.archlinux.org/index.php/Acer_Aspire_E11_Series). If you install in UEFI mode, it should work right.

Note to install in UEFI mode, you must have secure boot **enabled **or it will not work. You either _convert your system to UEFI_, a complicated process detailed here [http://askubuntu.com/questions/509423/which-commands-to-convert-a-ubuntu-bios-install-to-efi-uefi-without-boot-repair](http://askubuntu.com/questions/509423/which-commands-to-convert-a-ubuntu-bios-install-to-efi-uefi-without-boot-repair), or you can _reinstall in UEFI mode_. However, you *must* keep UEFI enabled, and you have to go into the secure boot setting, find your EFI partition, and select the shimx64.efi as trusted for executing by going into your bios settings (hold f2), and using "select file as trusted for executing" somewhere in the settings. You do this after converting or installing ubuntu in UEFI mode. If you do not set shimx64.efi as trusted for executing using secure boot, the firmware will say there is no operating system (even if secure boot is disabled).

Note: if your firmware settings will not let you change secure boot settings, it is because you did not set a password.

Using UEFI instead of legacy (bios) mode will solve this problem.

---

### Post by 01492 on 2015-10-13
Wow! What an amazing coincidence. And thanks for responding to this very old thread.

As I understand it, you're saying I can either go through the convoluted process of converting my system, or I can reinstall entirely. They both sound so attractive! /s

So before I choose an approach, my question for you is this--do you know of a good tutorial for backing up my data? I don't want to lose anything from this netbook.

No sweat! I was inattentive to this thread as well.

To answer your question, yes I am still having the same problem. I've been making due by closing all apps and holding the power key down to shut the system.

---

### Post by deathbyfreezeray on 2015-10-13
I couldn't say which backup solution would be the easiest, but there is a list of documented ones on the official Ubuntu help page here: [http://help.ubuntu.com/community/BackupYourSystem#Backup_Utilities](http://help.ubuntu.com/community/BackupYourSystem#Backup_Utilities)

I do agree that a backup/reinstall is probably easier and less risky than the alternative.

---

