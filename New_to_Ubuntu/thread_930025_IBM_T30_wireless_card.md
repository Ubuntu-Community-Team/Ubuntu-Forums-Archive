---
title: "IBM T30 wireless card"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by nkingcade on 2008-09-25
[SIZE=3][FONT=Garamond]I just loaded 8.04 desktop on an IBM T-30. I know it is an old machine. However, the machine has a wireless network card that I can't access from the network manager. Is there something I'm not doing or wrong?:([/FONT][/SIZE]

---

### Post by phidia on 2008-09-25
Depending on what specific card you have you may need to install other programs.
If you open a terminal and enter > lshw -C network& > lspcithe resulting output posted here will let us know your card make & model hopefully.

---

### Post by bobnutfield on 2008-09-25
I believe that laptop used an IBM Highgate LAN card, which is probably actually an Orinoco card.  If that is the case, you are in luck because the Orinoco is natively supported in Linux.

---

### Post by nkingcade on 2008-09-25
This is the command output. It appears that I have a Aironet card. (hope it's supported)


   neal@neal-laptop:~$ lshw -C
  
  Hardware Lister (lshw) - B.02.12.01
  
  usage: lshw [-format] [-options ...]
  
         lshw -version
  
   
   
              -version        print program version (B.02.12.01)
  
   
   
  format can be
  
              -html           output hardware tree as HTML
  
              -xml            output hardware tree as XML
  
              -short          output hardware paths
  
              -businfo        output bus information
  
   
   
  options can be
  
              -class CLASS    only show a certain class of hardware
  
              -C CLASS        same as '-class CLASS'
  
              -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
  
              -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
  
              -quiet          don't display status
  
              -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
  
   
   
  neal@neal-laptop:~$ lshw
  
  WARNING: you should run this program as super-user.
  
  PCI (sysfs)  
  
  neal-laptop               
  
      description: Computer
  
      width: 32 bits
  
    *-core
  
         description: Motherboard
  
         physical id: 0
  
       *-memory
  
            description: System memory
  
            physical id: 0
  
            size: 511MiB
  
       *-cpu
  
            product: Mobile Intel(R) Pentium(R) 4 - M CPU 1.80GHz
  
            vendor: Intel Corp.
  
            physical id: 1
  
            bus info: cpu@0
  
            version: 15.2.7
  
            size: 1800MHz
  
            capacity: 1800MHz
  
            width: 32 bits
  
            capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts sync_rdtsc cid xtpr cpufreq
  
            configuration: id=0
  
          *-cache:0
  
               description: L1 cache
  
               physical id: 0
  
               size: 8KiB
  
          *-cache:1
  
               description: L2 cache
  
               physical id: 1
  
               size: 512KiB
  
       *-pci
  
            description: Host bridge
  
            product: 82845 845 [Brookdale] Chipset Host Bridge
  
            vendor: Intel Corporation
  
            physical id: 100
  
            bus info: pci@0000:00:00.0
  
            version: 04
  
            width: 32 bits
  
            clock: 33MHz
  
            configuration: driver=agpgart-intel module=intel_agp
  
          *-pci:0
  
               description: PCI bridge
  
               product: 82845 845 [Brookdale] Chipset AGP Bridge
  
               vendor: Intel Corporation
  
               physical id: 1
  
               bus info: pci@0000:00:01.0
  
               version: 04
  
               width: 32 bits
  
               clock: 66MHz
  
               capabilities: pci normal_decode bus_master
  
             *-display UNCLAIMED
  
                  description: VGA compatible controller
  
                  product: Radeon Mobility M7 LW [Radeon Mobility 7500]
  
                  vendor: ATI Technologies Inc
  
                  physical id: 0
  
                  bus info: pci@0000:01:00.0
  
                  version: 00
  
                  width: 32 bits
  
                  clock: 66MHz
  
                  capabilities: vga_controller bus_master cap_list
  
                  configuration: latency=66 mingnt=8
  
          *-usb:0
  
               description: USB Controller
  
               product: 82801CA/CAM USB Controller #1
  
               vendor: Intel Corporation
  
               physical id: 1d
  
               bus info: pci@0000:00:1d.0
  
               version: 02
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: uhci bus_master
  
               configuration: driver=uhci_hcd latency=0 module=uhci_hcd
  
          *-usb:1
  
               description: USB Controller
  
               product: 82801CA/CAM USB Controller #2
  
               vendor: Intel Corporation
  
               physical id: 1d.1
  
               bus info: pci@0000:00:1d.1
  
               version: 02
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: uhci bus_master
  
               configuration: driver=uhci_hcd latency=0 module=uhci_hcd
  
          *-usb:2
  
               description: USB Controller
  
               product: 82801CA/CAM USB Controller #3
  
               vendor: Intel Corporation
  
               physical id: 1d.2
  
               bus info: pci@0000:00:1d.2
  
               version: 02
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: uhci bus_master
  
               configuration: driver=uhci_hcd latency=0 module=uhci_hcd
  
          *-pci:1
  
               description: PCI bridge
  
               product: 82801 Mobile PCI Bridge
  
               vendor: Intel Corporation
  
               physical id: 1e
  
               bus info: pci@0000:00:1e.0
  
               version: 42
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: pci normal_decode bus_master
  
             *-pcmcia:0
  
                  description: CardBus bridge
  
                  product: PCI1520 PC card Cardbus Controller
  
                  vendor: Texas Instruments
  
                  physical id: 0
  
                  bus info: pci@0000:02:00.0
  
                  version: 01
  
                  width: 32 bits
  
                  clock: 33MHz
  
                  capabilities: pcmcia bus_master cap_list
  
                  configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
  
             *-pcmcia:1
  
                  description: CardBus bridge
  
                  product: PCI1520 PC card Cardbus Controller
  
                  vendor: Texas Instruments
  
                  physical id: 0.1
  
                  bus info: pci@0000:02:00.1
  
                  version: 01
  
                  width: 32 bits
  
                  clock: 33MHz
  
                  capabilities: pcmcia bus_master cap_list
  
                  configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
  
             *-network:0
  
                  description: Network controller
  
                  product: Cisco Aironet Wireless 802.11b
  
                  vendor: AIRONET Wireless Communications
  
                  physical id: 2
  
                  bus info: pci@0000:02:02.0
  
                  version: 00
  
                  width: 32 bits
  
                  clock: 33MHz
  
                  capabilities: bus_master cap_list
  
                  configuration: driver=airo latency=64 maxlatency=4 mingnt=4
  
             *-network:1
  
                  description: Ethernet interface
  
                  product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
  
                  vendor: Intel Corporation
  
                  physical id: 8
  
                  bus info: pci@0000:02:08.0
  
                  logical name: eth0
  
                  version: 42
  
                  serial: 00:09:6b:7a:8b:c0
  
                  width: 32 bits
  
                  clock: 33MHz
  
                  capabilities: bus_master cap_list ethernet physical
  
                  configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  
          *-isa
  
               description: ISA bridge
  
               product: 82801CAM ISA Bridge (LPC)
  
               vendor: Intel Corporation
  
               physical id: 1f
  
               bus info: pci@0000:00:1f.0
  
               version: 02
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: isa bus_master
  
               configuration: latency=0
  
          *-ide
  
               description: IDE interface
  
               product: 82801CAM IDE U100 Controller
  
               vendor: Intel Corporation
  
               physical id: 1f.1
  
               bus info: pci@0000:00:1f.1
  
               version: 02
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: ide bus_master
  
               configuration: driver=ata_piix latency=0 module=ata_piix
  
          *-serial UNCLAIMED
  
               description: SMBus
  
               product: 82801CA/CAM SMBus Controller
  
               vendor: Intel Corporation
  
               physical id: 1f.3
  
               bus info: pci@0000:00:1f.3
  
               version: 02
  
               width: 32 bits
  
               clock: 33MHz
  
               configuration: latency=0
  
          *-multimedia UNCLAIMED
  
               description: Multimedia audio controller
  
               product: 82801CA/CAM AC'97 Audio Controller
  
               vendor: Intel Corporation
  
               physical id: 1f.5
  
               bus info: pci@0000:00:1f.5
  
               version: 02
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: bus_master
  
               configuration: latency=0
  
          *-communication UNCLAIMED
  
               description: Modem
  
               product: 82801CA/CAM AC'97 Modem Controller
  
               vendor: Intel Corporation
  
               physical id: 1f.6
  
               bus info: pci@0000:00:1f.6
  
               version: 02
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: generic
  
               configuration: latency=0
  
  neal@neal-laptop:~$ 
  
  neal@neal-laptop:~$ lspci
  
  00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
  
  00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
  
  00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
  
  00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
  
  00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
  
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
  
  00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
  
  00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
  
  00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
  
  00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
  
  00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
  
  01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
  
  02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
  
  02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
  
  02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
  
  02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
  
  neal@neal-laptop:~$

---

### Post by bobnutfield on 2008-09-25
From what I have been able to read, it is supported in Linux and Ubuntu out of the box.  Open a terminal and type:

> sudo ifconfig -a

This will tell you if the card is being recognized.  If it is you can probably configure it pretty easy.

---

### Post by nkingcade on 2008-09-25
Only two interfaces that show up are;

1. Eth0

2. Lo

Why does the Aironet not show?

---

### Post by bobnutfield on 2008-09-25
This is an internal wireless chipset, right?  And did you use the -a after the ifconfig command?  It is showing in lspci, so it should have been listed in your networking hardware.  Let me do some checking..

---

### Post by nkingcade on 2008-09-25
Went to hardware test application. The app will recognize the card, but does not offer a test for it. Hmmmm??

---

### Post by bobnutfield on 2008-09-25
OK, found it.  Your hardware uses the airo driver, but you must blacklist some other modules first.  If that sounds cryptic, the solution is in this thread:

[http://ubuntuforums.org/showthread.php?t=867947&highlight=Cisco+Aironet+Wireless+802.11b]("http://ubuntuforums.org/showthread.php?t=867947&highlight=Cisco+Aironet+Wireless+802.11b")

Follow this thread and it should get you going.

---

### Post by nkingcade on 2008-09-25
I will try it and get back to you. Thanks.

---

### Post by bobnutfield on 2008-09-25
Late here, so I will bookmark this thread and see how you got on..

---

### Post by nkingcade on 2008-09-25
My wireless is up and running. Thank you all so very much. It is nice to know that you can get help when needed. Thanks again. Hopefully, I can get good enough to help someone in the same position someday. Thanks.

---

