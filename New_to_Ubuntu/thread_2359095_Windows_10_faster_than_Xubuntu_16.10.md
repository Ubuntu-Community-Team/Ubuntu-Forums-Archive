---
title: "Windows 10 faster than Xubuntu 16.10"
date: 2017-04-20
forum: New to Ubuntu
---

### Post by diegorangel on 2017-04-20
I have a netbook Asus Eee Pc model 1015BX, 2 GB RAM, 320 GB SATA HD 
[B]AMD C-60 1.0 GHz two cores processor with Radeon HD 6290 Graphics


[/B]Windows 10 pro 64-bit recent installed runs perfectly but a little slow

I use this netbook to read emails, download torrent and for YouTube. It plays 1080p videos very nice, also 1080p YouTube with Microsoft Edge and Google Chrome,.By the way this Radeon AMD card has the aim of play full 1080p HD videos as it is stamped on the netbook case

I decided to try Xubutu 16.10 64-bit to have a lighter and faster experience in this netbook but i am very disappointed

I installed it in dual boot with 150 GB in the final half of hard disk with 2GB swap. Installation was fine but It is quite slow now. Slower than Windows 10 and I can't even play 720p Youtube videos. The most I can do is use the Firefox and It's an annoying task because it freezes all the time


I think there is some problem with the video driver, I don't know

Is there any solution to this problem? Should I give up linux and back to windows? Is this netbook not compatible with Xubuntu?

Thank You!

---

### Post by TheFu on 2017-04-20
Welcome to the forums.

Did you install the non-free GPU drivers?  On a slow machine, that will be very important.

A little about Ubuntu versions ... 
Beware that 16.10 support ends in July, so in a month or so, you'll want to move to 17.04, then 17.10 before the next LTS.  I only use LTS releases with 5 yrs of support. All others have just 9 months (or so) of support. End users should probably stay on LTS when possible. I'm running 16.04 on this machine, but all my others run 14.04 still.

---

### Post by RobGoss on 2017-04-20
Hello and welcome to the forum,

> Is there any solution to this problem? Should I give up Linux and back to windows? Is this netbook not compatible with Xubuntu?]

How can you give up so soon? I'm assuming you're just starting out correct? Linux will require a lot of time and patience's, reading about how Linux is used may be the place to start, these forums have just about all the information you'll need to fix just about any issue that come your way 

let's take a look to see what video driver you're using try running the following command
```
lshw 
```

Post the results using the code tags

---

### Post by diegorangel on 2017-04-20
> Beware that 16.10 support ends in July, so in a month or so, you'll want  to move to 17.04, then 17.10 before the next LTS.  I only use LTS  releases with 5 yrs of support. All others have just 9 months (or so) of  support. End users should probably stay on LTS when possible. I'm  running 16.04 on this machine, but all my others run 14.04 still.

I'm sorry, the os is Xubuntu 16.04.2 LTS. Some reason I wrote 16.10 I'm sorry

> let's take a look to see what video driver you're using try running the following command
     Code:
     lshw 
Post the results using the code tags


```
descrição: Notebook
    produto: 1015BX (1015BX)
    fabricante: ASUSTeK Computer INC.
    versão: x.x
    serial: C6OAB2011268
    largura: 64 bits
    capacidades: smbios-2.6 dmi-2.6 vsyscall32
    configuração: boot=normal chassis=notebook family=Eee PC sku=1015BX uuid=86901730-6079-2134-1436-10BF48E3A5B6
  *-core
       descrição: Placa-mãe
       produto: 1015BXO
       fabricante: ASUSTeK Computer INC.
       ID físico: 0
       versão: x.xx
       serial: EeePC-0123456789
       slot: To be filled by O.E.M.
     *-firmware
          descrição: BIOS
          fabricante: American Megatrends Inc.
          ID físico: 0
          versão: 0610
          date: 04/16/2012
          tamanho: 64KiB
          capacidade: 1984KiB
          capacidades: pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          descrição: CPU
          produto: AMD C-60 APU with Radeon(tm) HD Graphics
          fabricante: Advanced Micro Devices [AMD]
          ID físico: 4
          informações do barramento: cpu@0
          versão: AMD C-60 APU with Radeon(tm) HD Graphics
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          tamanho: 1GHz
          capacidade: 1GHz
          largura: 64 bits
          clock: 100MHz
          capacidades: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf eagerfpu pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt cpb hw_pstate vmmcall arat npt lbrv svm_lock nrip_save pausefilter cpufreq
          configuração: cores=2 enabledcores=2
        *-cache:0
             descrição: L1 cache
             ID físico: 5
             slot: L1-Cache
             tamanho: 128KiB
             capacidade: 128KiB
             capacidades: internal write-back unified
             configuração: level=1
        *-cache:1
             descrição: L2 cache
             ID físico: 6
             slot: L2-Cache
             tamanho: 1MiB
             capacidade: 1MiB
             capacidades: internal varies data
             configuração: level=2
     *-memory
          descrição: Memória do sistema
          ID físico: 18
          slot: Placa do sistema ou placa-mãe
          tamanho: 2GiB
        *-bank:0
             descrição: DIMM DDR3 Síncrono 1333 MHz (0,8 ns)
             produto: Array1_PartNumber0
             fabricante: A1_Manufacturer0
             ID físico: 0
             serial: A1_SerNum0
             slot: A1_DIMM0
             tamanho: 2GiB
             largura: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             descrição: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2013-04-07 17:30+0000Last-Translator: Neliton Pereira Jr. <nelitonpjr@gmail.com>Language-Team: Brazilian Portuguese <pt_BR@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2016-06-27 17:08+0000X-Generator: Launchpad (build 18115) Síncrono [vazio]
             produto: Array1_PartNumber1
             fabricante: A1_Manufacturer1
             ID físico: 1
             serial: A1_SerNum1
             slot: A1_DIMM1
     *-pci:0
          descrição: Host bridge
          produto: Family 14h Processor Root Complex
          fabricante: Advanced Micro Devices, Inc. [AMD]
          ID físico: 100
          informações do barramento: pci@0000:00:00.0
          versão: 00
          largura: 32 bits
          clock: 66MHz
          configuração: latency=32
        *-display
             descrição: VGA compatible controller
             produto: Wrestler [Radeon HD 6290]
             fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
             ID físico: 1
             informações do barramento: pci@0000:00:01.0
             versão: 00
             largura: 32 bits
             clock: 33MHz
             capacidades: pm pciexpress msi vga_controller bus_master cap_list rom
             configuração: driver=radeon latency=0
             recursos: irq:24 memória:d0000000-dfffffff porta de E/S:f000(tamanho=256) memória:feb00000-feb3ffff memória:c0000-dffff
        *-multimedia:0
             descrição: Audio device
             produto: Wrestler HDMI Audio
             fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
             ID físico: 1.1
             informações do barramento: pci@0000:00:01.1
             versão: 00
             largura: 32 bits
             clock: 33MHz
             capacidades: pm pciexpress msi bus_master cap_list
             configuração: driver=snd_hda_intel latency=0
             recursos: irq:25 memória:feb44000-feb47fff
        *-pci:0
             descrição: PCI bridge
             produto: Family 14h Processor Root Port
             fabricante: Advanced Micro Devices, Inc. [AMD]
             ID físico: 4
             informações do barramento: pci@0000:00:04.0
             versão: 00
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:16 memória:fea00000-feafffff
           *-network
                descrição: Interface sem fio
                produto: AR9285 Wireless Network Adapter (PCI-Express)
                fabricante: Qualcomm Atheros
                ID físico: 0
                informações do barramento: pci@0000:01:00.0
                nome lógico: wlp1s0
                versão: 01
                serial: 00:08:ca:cf:69:c7
                largura: 64 bits
                clock: 33MHz
                capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuração: broadcast=yes driver=ath9k driverversion=4.8.0-46-generic firmware=N/A ip=192.168.0.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                recursos: irq:16 memória:fea00000-fea0ffff
        *-pci:1
             descrição: PCI bridge
             produto: Family 14h Processor Root Port
             fabricante: Advanced Micro Devices, Inc. [AMD]
             ID físico: 5
             informações do barramento: pci@0000:00:05.0
             versão: 00
             largura: 32 bits
             clock: 33MHz
             capacidades: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuração: driver=pcieport
             recursos: irq:17 porta de E/S:e000(tamanho=4096) memória:fe900000-fe9fffff
           *-network
                descrição: Ethernet interface
                produto: AR8152 v2.0 Fast Ethernet
                fabricante: Qualcomm Atheros
                ID físico: 0
                informações do barramento: pci@0000:02:00.0
                nome lógico: enp2s0
                versão: c1
                serial: 10:bf:48:e3:a5:b6
                capacidade: 100Mbit/s
                largura: 64 bits
                clock: 33MHz
                capacidades: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuração: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
                recursos: irq:26 memória:fe900000-fe93ffff porta de E/S:e000(tamanho=128)
        *-storage
             descrição: SATA controller
             produto: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
             ID físico: 11
             informações do barramento: pci@0000:00:11.0
             versão: 00
             largura: 32 bits
             clock: 66MHz
             capacidades: storage ahci_1.0 bus_master cap_list
             configuração: driver=ahci latency=32
             recursos: irq:19 porta de E/S:f140(tamanho=8) porta de E/S:f130(tamanho=4) porta de E/S:f120(tamanho=8) porta de E/S:f110(tamanho=4) porta de E/S:f100(tamanho=16) memória:feb4c000-feb4c3ff
        *-usb:0
             descrição: USB controller
             produto: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
             ID físico: 12
             informações do barramento: pci@0000:00:12.0
             versão: 00
             largura: 32 bits
             clock: 66MHz
             capacidades: ohci bus_master
             configuração: driver=ohci-pci latency=32
             recursos: irq:18 memória:feb4b000-feb4bfff
           *-usbhost
                produto: OHCI PCI host controller
                fabricante: Linux 4.8.0-46-generic ohci_hcd
                ID físico: 1
                informações do barramento: usb@3
                nome lógico: usb3
                versão: 4.08
                capacidades: usb-1.10
                configuração: driver=hub slots=5 speed=12Mbit/s
        *-usb:1
             descrição: USB controller
             produto: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
             ID físico: 12.2
             informações do barramento: pci@0000:00:12.2
             versão: 00
             largura: 32 bits
             clock: 66MHz
             capacidades: pm debug ehci bus_master cap_list
             configuração: driver=ehci-pci latency=32
             recursos: irq:17 memória:feb4a000-feb4a0ff
           *-usbhost
                produto: EHCI Host Controller
                fabricante: Linux 4.8.0-46-generic ehci_hcd
                ID físico: 1
                informações do barramento: usb@1
                nome lógico: usb1
                versão: 4.08
                capacidades: usb-2.00
                configuração: driver=hub slots=5 speed=480Mbit/s
        *-usb:2
             descrição: USB controller
             produto: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
             ID físico: 13
             informações do barramento: pci@0000:00:13.0
             versão: 00
             largura: 32 bits
             clock: 66MHz
             capacidades: ohci bus_master
             configuração: driver=ohci-pci latency=32
             recursos: irq:18 memória:feb49000-feb49fff
           *-usbhost
                produto: OHCI PCI host controller
                fabricante: Linux 4.8.0-46-generic ohci_hcd
                ID físico: 1
                informações do barramento: usb@4
                nome lógico: usb4
                versão: 4.08
                capacidades: usb-1.10
                configuração: driver=hub slots=5 speed=12Mbit/s
        *-usb:3
             descrição: USB controller
             produto: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
             ID físico: 13.2
             informações do barramento: pci@0000:00:13.2
             versão: 00
             largura: 32 bits
             clock: 66MHz
             capacidades: pm debug ehci bus_master cap_list
             configuração: driver=ehci-pci latency=32
             recursos: irq:17 memória:feb48000-feb480ff
           *-usbhost
                produto: EHCI Host Controller
                fabricante: Linux 4.8.0-46-generic ehci_hcd
                ID físico: 1
                informações do barramento: usb@2
                nome lógico: usb2
                versão: 4.08
                capacidades: usb-2.00
                configuração: driver=hub slots=5 speed=480Mbit/s
              *-usb
                   descrição: Vídeo
                   produto: USB 2.0 UVC VGA WebCam
                   fabricante: Azurewave
                   ID físico: 2
                   informações do barramento: usb@2:2
                   versão: 12.04
                   serial: 0x0001
                   capacidades: usb-2.00
                   configuração: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-serial DISPONÍVEL
             descrição: SMBus
             produto: SBx00 SMBus Controller
             fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
             ID físico: 14
             informações do barramento: pci@0000:00:14.0
             versão: 42
             largura: 32 bits
             clock: 66MHz
             configuração: latency=0
        *-multimedia:1
             descrição: Audio device
             produto: SBx00 Azalia (Intel HDA)
             fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
             ID físico: 14.2
             informações do barramento: pci@0000:00:14.2
             versão: 40
             largura: 64 bits
             clock: 33MHz
             capacidades: pm bus_master cap_list
             configuração: driver=snd_hda_intel latency=32
             recursos: irq:16 memória:feb40000-feb43fff
        *-isa
             descrição: ISA bridge
             produto: SB7x0/SB8x0/SB9x0 LPC host controller
             fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
             ID físico: 14.3
             informações do barramento: pci@0000:00:14.3
             versão: 40
             largura: 32 bits
             clock: 66MHz
             capacidades: isa bus_master
             configuração: latency=0
        *-pci:2
             descrição: PCI bridge
             produto: SBx00 PCI to PCI Bridge
             fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
             ID físico: 14.4
             informações do barramento: pci@0000:00:14.4
             versão: 40
             largura: 32 bits
             clock: 66MHz
             capacidades: pci subtractive_decode bus_master vga_palette
     *-pci:1
          descrição: Host bridge
          produto: Family 12h/14h Processor Function 0
          fabricante: Advanced Micro Devices, Inc. [AMD]
          ID físico: 101
          informações do barramento: pci@0000:00:18.0
          versão: 43
          largura: 32 bits
          clock: 33MHz
     *-pci:2
          descrição: Host bridge
          produto: Family 12h/14h Processor Function 1
          fabricante: Advanced Micro Devices, Inc. [AMD]
          ID físico: 102
          informações do barramento: pci@0000:00:18.1
          versão: 00
          largura: 32 bits
          clock: 33MHz
     *-pci:3
          descrição: Host bridge
          produto: Family 12h/14h Processor Function 2
          fabricante: Advanced Micro Devices, Inc. [AMD]
          ID físico: 103
          informações do barramento: pci@0000:00:18.2
          versão: 00
          largura: 32 bits
          clock: 33MHz
     *-pci:4
          descrição: Host bridge
          produto: Family 12h/14h Processor Function 3
          fabricante: Advanced Micro Devices, Inc. [AMD]
          ID físico: 104
          informações do barramento: pci@0000:00:18.3
          versão: 00
          largura: 32 bits
          clock: 33MHz
          configuração: driver=k10temp
          recursos: irq:0
     *-pci:5
          descrição: Host bridge
          produto: Family 12h/14h Processor Function 4
          fabricante: Advanced Micro Devices, Inc. [AMD]
          ID físico: 105
          informações do barramento: pci@0000:00:18.4
          versão: 00
          largura: 32 bits
          clock: 33MHz
     *-pci:6
          descrição: Host bridge
          produto: Family 12h/14h Processor Function 6
          fabricante: Advanced Micro Devices, Inc. [AMD]
          ID físico: 106
          informações do barramento: pci@0000:00:18.5
          versão: 00
          largura: 32 bits
          clock: 33MHz
     *-pci:7
          descrição: Host bridge
          produto: Family 12h/14h Processor Function 5
          fabricante: Advanced Micro Devices, Inc. [AMD]
          ID físico: 107
          informações do barramento: pci@0000:00:18.6
          versão: 00
          largura: 32 bits
          clock: 33MHz
     *-pci:8
          descrição: Host bridge
          produto: Family 12h/14h Processor Function 7
          fabricante: Advanced Micro Devices, Inc. [AMD]
          ID físico: 108
          informações do barramento: pci@0000:00:18.7
          versão: 00
          largura: 32 bits
          clock: 33MHz
     *-scsi
          ID físico: 1
          nome lógico: scsi0
          capacidades: emulated
        *-disk
             descrição: ATA Disk
             produto: ST9320325AS
             fabricante: Seagate
             ID físico: 0.0.0
             informações do barramento: scsi@0:0.0.0
             nome lógico: /dev/sda
             versão: SDM1
             serial: 6VDF4ZJW
             tamanho: 298GiB (320GB)
             capacidades: partitioned partitioned:dos
             configuração: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=5283725d
           *-volume:0
                descrição: Windows NTFS volume
                ID físico: 1
                informações do barramento: scsi@0:0.0.0,1
                nome lógico: /dev/sda1
                versão: 3.1
                serial: fc0b-de87
                tamanho: 498MiB
                capacidade: 500MiB
                capacidades: primary ntfs initialized
                configuração: clustersize=4096 created=2017-03-27 18:21:06 filesystem=ntfs label=Reservado pelo Sistema modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                descrição: Windows NTFS volume
                ID físico: 2
                informações do barramento: scsi@0:0.0.0,2
                nome lógico: /dev/sda2
                versão: 3.1
                serial: 30343c26-99ff-8042-842d-a07a435b9b7e
                tamanho: 139GiB
                capacidade: 139GiB
                capacidades: primary ntfs initialized
                configuração: clustersize=4096 created=2017-03-27 18:21:11 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:2
                descrição: volume EXT4
                fabricante: Linux
                ID físico: 3
                informações do barramento: scsi@0:0.0.0,3
                nome lógico: /dev/sda3
                nome lógico: /
                versão: 1.0
                serial: 0a4c35ba-0cb0-41f9-86bc-6e73ddc6369e
                tamanho: 155GiB
                capacidade: 155GiB
                capacidades: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuração: created=2017-04-20 10:02:12 filesystem=ext4 lastmountpoint=/ modified=2017-04-20 19:50:36 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-04-20 19:50:43 state=mounted
           *-volume:3
                descrição: Linux swap volume
                ID físico: 4
                informações do barramento: scsi@0:0.0.0,4
                nome lógico: /dev/sda4
                versão: 1
                serial: 208a4a6b-b1bb-4d6f-8694-fe477a614e58
                tamanho: 2499MiB
                capacidade: 2499MiB
                capacidades: primary nofs swap initialized
                configuração: filesystem=swap pagesize=4096
  *-battery
       descrição: Níquel-cádmio Battery
       produto: Battery Name
       fabricante: Battery Manufacturer
       ID físico: 1
       versão: 01/01/2007
       serial: Serial Number
       slot: Location of the battery
rangel@rangel-1015BX:~$ ^C
rangel@rangel-1015BX:~$ 


```

Thanks

---

### Post by RobGoss on 2017-04-20
Have you tried using the proprietary drives provided?

Go to Software & Updates, choose  Additional drivers, choose the appropriate drivers for your machine, restart your system and see how it performs

---

### Post by QIII on 2017-04-20
Starting with 16.04, there is no proprietary driver that will work with that GPU.  AMD has dropped fglrx support and that GPU will not work with AMDGPU or AMDGPU-PRO.

The default open source driver currently being used is the only option.

---

### Post by mörgæs on 2017-04-22
In extension of what is posted above: The open source drivers are in a steady development and if you are using old software like Buntu LTS you are left with yesterday's news. 

I suggest that you try Buntu 17.04 to see if the drivers here are faster and/or more stable. Not promising you anything but it's an easy test to do.

---

