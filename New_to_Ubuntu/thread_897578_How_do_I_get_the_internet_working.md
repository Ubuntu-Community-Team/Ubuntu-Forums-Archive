---
title: "How do I get the internet working?"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by douggiephresh on 2008-08-22
I just installed the latest version of Ubuntu. I have no previous Linux knowledge. I have a Dell Inspiron 1501. Also, what driver(s) do I need to install to get my ATI video card to work?

---

### Post by livestockPimp on 2008-08-22
Well, for the internet how do you connect? 3G card, dialup, router, ADSL modem that needs a PC to initiate a ppp connection.

As for the vid card what ATI card it it?
Can you post the output of "lspci"

---

### Post by tuxxy on 2008-08-22
It should be connected out of the box if your running a wired ethernet, also for drivers try system > admin > hardware drivers to enable them once your internet is up

---

### Post by douggiephresh on 2008-08-22
I access the internet wirelessly. And as for the last thing you said, what is posting the output?

---

### Post by jose158 on 2008-08-22
> **douggiephresh said:**
> I access the internet wirelessly. And as for the last thing you said, what is posting the output?
Type in terminal(Applications -> Accessories -> Terminal) type "lspci" and post what you got here.

---

### Post by douggiephresh on 2008-08-22
Thanks for the help. 

doug@doug-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
doug@doug-laptop:~$

---

### Post by psycosmyth on 2008-08-22
Click on the connection icon at the top (two pc's) left click I think, and see if there are any connections. right click to edit manualy and see if "wireless" is listed, if it is just set it up for DHCP in properties.
You have to click the administrator button in the network applet.
There are hundreds of posts on Broadcom cards here. Yours should work as is.

---

### Post by douggiephresh on 2008-08-22
sorry, but im new to this. Can you be any clearer. I tried to do what you said, but I dont see exactly what your talking about.

---

### Post by douggiephresh on 2008-08-22
I see the two monitors on the top, enable wireless is checked, but I still cannot get online

---

### Post by douggiephresh on 2008-08-22
bump

---

### Post by douggiephresh on 2008-08-22
does this help? 

```
description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1918MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RS485 [Radeon Xpress 1100 IGP]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=66 mingnt=8
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Network controller
                product: BCM94311MCG wlan mini-PCI
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0 module=ssb
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64 module=ahci
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1

             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=64 module=pata_atiixp
        *-multimedia
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 02
                serial: 00:1d:09:b6:9f:30
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:08:01.0
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-system:1 UNCLAIMED
                description: System peripheral
                product: R5C843 MMC Host Controller
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:08:01.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1e:8c:4c:4c:0c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

---

### Post by overdrank on 2008-08-22
> **douggiephresh said:**
> bump

Hi and welcome, if you could connect to the internet wired it would make things easier. If you look under system,, administration, hardware drivers. You should see the drivers that you will need for you wireless and ATI graphics. If you can connect via a wired connection to install these then you should be good to go. :)

---

### Post by douggiephresh on 2008-08-22
I hardwired myself to the internet, but it still does not work.

---

### Post by Kevbert on 2008-08-22
Please take a look at this [[COLOR="Red"]website[/COLOR]]("http://www.ubuntu1501.com/").  It's especially made for your PC.

---

### Post by douggiephresh on 2008-08-22
that website didnt really help me. There is nothing else that I can do?

---

### Post by overdrank on 2008-08-22
> **douggiephresh said:**
> that website didnt really help me. There is nothing else that I can do?

Hi and check the network manager like you did earlier for the wireless. If you installed Ubuntu without the wired connection you will have to enable it. Also you may have to enable your repos also.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
I said maybe because I remember having to do it once when I installed without the wired connection. :)

---

### Post by douggiephresh on 2008-08-22
This is so discouraging, I need the internet and I have to go back to windows.

---

### Post by tuxulin on 2008-08-22
before heading back to winXP :)
please try this site 
[http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html](http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html)

a similar webpage was provided before in this post, however this is
slightly different 

thanks
Tuxulin

---

### Post by douggiephresh on 2008-08-22
See, i tried that, but i get an error for finding ndiswrapper and i cannot access ftp.dell, the step right after finding ndiswrapper. I found a couple files with ndiswrapper in the name on the ubuntu install disk, but i dont know what to do with them

---

### Post by douggiephresh on 2008-08-22
bump

---

### Post by boulash on 2008-08-22
just a guess, that might be the same problem as mine...
[http://ubuntuforums.org/showthread.php?t=896382](http://ubuntuforums.org/showthread.php?t=896382)

please help!

---

### Post by tuxulin on 2008-08-22
try [http://ftp.us.dell.com/network/R140747.EXE](http://ftp.us.dell.com/network/R140747.EXE) in the browser. then hit save.

to install the the ndis files put the ubuntu cd in 
goto software sources and make sure "CDrom with ubuntu 8.04" is check 
then close the dialog box.
do the update.
head over to teminal and redo 
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common (hopefully this time it will see it on the CD)

if all goes well go back to sources software and uncheck the ubuntu CD
and go with the rest of the guide on the site.

i hope this will help
Tuxulin

---

### Post by douggiephresh on 2008-08-22
tuxlin, much thanks!! I got internet access by wiring my laptop directly to the router, and i completed the process for ndiswrapper, and i now see that my wifi light has come on. but, when i unplug my laptop, i still cannot access the internet wirelessly! what next?

---

### Post by tuxulin on 2008-08-22
glad to hear you made it atleast 50/50 :)

can you try this in the terminal
sudo iwlist scanning

what was the result ?

---

### Post by tuxulin on 2008-08-22
i looked through the guide and didnt not see these.....

so im guessing here .... if you do nat have these then 
please try to install them.

if you do have them already then you should see in the 
terminal near the ending 
nothing to update 0 remove 0 install 0 or words
 
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

thank again
Tuxulin

edit
then restart the machine again

---

