---
title: "Lenovo B570 Broadcom WiFi"
date: 2012-02-13
forum: New to Ubuntu
---

### Post by chubble10 on 2012-02-13
Hi

I recently installed Xubuntu in a dual boot with Windows 7. Xubuntu is nice and runs well, however I am unable to use my built in wireless card to connect to WiFi (Bluetooth works fine). I have connected to the internet via Ethernet and have downloaded and installed the Broadcom WiFi drivers that are present in the Additional Drivers tool. It seems to recognize that I have wireless as there is an option to enable wireless in the network tray indictor, however clicking on it seems to have no effect and it ramains saying that it is disabled (toggling the hardware wireless switch also makes no difference).
Output from sudo lshw:
```
phil@ubuntu:~$ sudo lshw
[sudo] password for phil: 
ubuntu                    
    description: Notebook
    version: Lenovo B570
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: administrator_password=unknown boot=normal chassis=notebook family=HuronRiver System frontpanel_password=unknown keyboard_password=unknown power-on_password=unknown sku=System SKUNumber uuid=4C7A7460-51AE-11E0-AF1E-8490C8C711E9
  *-core
       description: Motherboard
       product: Emerald Lake
       vendor: LENOVO
       physical id: 0
       version: FAB1
       serial: WB01642146
       slot: Part Component
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 44CN28WW
          date: 02/22/2011
          size: 128KiB
          capacity: 2496KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer int10video pc98 acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 30
          bus info: cpu@0
          version: 6.10.7
          serial: 0002-06A7-0000-0000-0000-0000
          slot: CPU
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 id=0 threads=4
        *-cache:0
             description: L1 cache
             physical id: 31
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 32
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through data
        *-cache:2
             description: L3 cache
             physical id: 33
             slot: L3-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 0.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 0.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 0.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 0.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 0.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 0.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 0.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 0.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 0.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 0.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 0.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 0.10
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 34
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5773CHS-CH9
             vendor: Samsung
             physical id: 0
             serial: C12F6025
             slot: ChannelA-DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: ChannelA-DIMM1
        *-bank:2
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5773CHS-CH9
             vendor: Samsung
             physical id: 2
             serial: C12F6024
             slot: ChannelB-DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: ChannelB-DIMM1
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:3000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:16 memory:d0605000-d060500f
        *-usb:0
             description: USB Controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:d060a000-d060a3ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:43 memory:d0600000-d0603fff
        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:d0500000-d05fffff
           *-network DISABLED
                description: Wireless interface
                product: BCM4313 802.11b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: ec:55:f9:18:53:bf
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=brcmsmac driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:d0500000-d0503fff
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:2000(size=4096) ioport:d0400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 06
                serial: f0:de:f1:4c:81:bd
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.11 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:41 ioport:2000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
        *-usb:1
             description: USB Controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d0609000-d06093ff
        *-isa
             description: ISA bridge
             product: HM65 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi4
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:40 ioport:3088(size=8) ioport:3094(size=4) ioport:3080(size=8) ioport:3090(size=4) ioport:3060(size=32) memory:d0608000-d06087ff
           *-disk
                description: ATA Disk
                product: WDC WD5000BPVT-2
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 02.0
                serial: WD-WX51A11K3064
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=3ba3bca5
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: a82b-06bb
                   size: 198MiB
                   capacity: 200MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-03-18 23:35:30 filesystem=ntfs state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /host
                   version: 3.1
                   serial: 000c8d15-b224-c346-83aa-6a49cec20b6c
                   size: 449GiB
                   capacity: 449GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-03-18 23:35:31 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 16GiB
                   capacity: 16GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 6467MiB
                 *-logicalvolume:1
                      description: Compaq diagnostics partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 10GiB
                      capabilities: boot
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7710H
                vendor: Optiarc
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: A833
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d0604000-d06040ff ioport:efa0(size=32)
     *-scsi
          physical id: 1
          bus info: usb@2:1.6
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=rts5139
        *-disk
             description: SCSI Disk
             product: xD/SD/M.S.
             vendor: Generic-
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             version: 1.00
             serial: 3
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
  *-battery
       product: Smart Battery
       vendor: Intel Corp.
       physical id: 1
       version: 2008
       serial: 1.0
       slot: Rear
  *-power UNCLAIMED
       description: TBD by ODM
       product: TBD by ODM
       vendor: TBD by ODM
       physical id: 2
       version: 1.0
       serial: TBD by ODM
       capacity: 32768mWh
phil@ubuntu:~$ 

```
Anyone any ideas?

---

### Post by ts3 on 2012-02-13
> description: Wireless interface
                product: BCM4313 802.11b/g/n Wireless LAN Controller

You need a solution that is specific for your wireless (BCM4313).  In particular, you need the bcmwl-kernel-source driver from Ubuntu Software Centre (open the software centre, type bcmwl and install the three packages that pop up).  You also need to make sure that no conflicting drivers such as b43 are loading.  

The broadcom page has a good readme.txt with an explanation how to get rid of conflicting drivers and if you search the forums for bcm4313 you'll find other posts about this (I wrote a saga on the subject back in November as I was struggling with the same issue :) )

Good luck and post if you need more details. 

Cheers :)

Edit: here's the link for the broadcom site: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by chubble10 on 2012-02-14
Hi
I have tried as you suggested and uninstalled all the other drivers, checked the blacklists and don't have b43 installed. I have also tried both the installation you described at [http://ubuntuforums.org/showthread.php?t=1889170](http://ubuntuforums.org/showthread.php?t=1889170) and the manual compiling on the same thread using the tar from the Broadcom site, but they don't seem to have made any difference and I am still unable to enable wireless :o
The outputs from lspci -k and nm-tool now look like this (I've filtered through the lspci one to make it a bit easier to find the network stuff):
```
phil@ubuntu:~$ lspci -k
<stuff filtered out>
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
	Subsystem: Broadcom Corporation Device 051b
	Kernel driver in use: wl
	Kernel modules: wl, bcma, brcmsmac
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: Lenovo Device 3975
	Kernel driver in use: r8169
	Kernel modules: r8169
phil@ubuntu:~$ 

```
and
```
phil@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unavailable
  Default:           no
  HW Address:        EC:55:F9:18:53:BF

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        F0:DE:F1:4C:81:BD

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


phil@ubuntu:~$ 

```
Any more help really appreciated as I am completely stumped! :confused:
Thanks
-Phil.

---

### Post by ts3 on 2012-02-14
> **chubble10 said:**
> Any more help really appreciated as I am completely stumped!  

I'll try but I myself know very little.  I'd check for hardware switches and remove them:
```
 sudo rfkill list all
sudo rfkill unblock all
```You seem to have the wl driver loaded so it shouldn't be blacklisted but I'd double-check for a separate file called "blacklist-local."
 
I'd also look at [https://help.ubuntu.com/11.10/ubuntu-help/net-wireless-troubleshooting.html](https://help.ubuntu.com/11.10/ubuntu-help/net-wireless-troubleshooting.html) and go through the various steps to try to pinpoint why the network shows as unavailable.  

Lastly, one of the experienced posters on the forums, wildmanne39, is doing a lot of wireless troubleshooting. I'd search for his posts and the 4313 driver and see what suggestions he's made to other people with the same blasted driver. :)

I am sorry, I don't know enough myself :( to suggest more or walk you through various possible solutions, the best I can do is make some educated guesses.

Cheers :)

EDITED to add: I also remember coming across posts by lenovo users mentioning that blacklisting the acer_wmi module helps but I have no idea why or how to check your set-up for this particular issue.

---

### Post by wildmanne39 on 2012-02-14
Hi, you have a driver conflict for starters, please do:
```
sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
unplug wired connection and reboot.

If it does not work we will troubleshoot your wireless.
Thanks

---

### Post by sadaruwan12 on 2012-02-14
OK Bro Now it's time I jump in as well.

For starters I have a lenovo B560 same issue came up when I installed 11.04 same exact situation you're in.

Then I managed to solve it but first befor I help you I want yoou to run the below command in the terminal and list the out put here.

```

 $ rfkill list all

```

Please list the output here so I can help you.

---

### Post by alee863 on 2012-02-17
Hi!
i have installed ubuntu window installer yesterday on my lenovo B570e.
facing the same problem with wifi. so i am posting my problem here...:(
i have never use linix before. it seems i will face many problams..:confused::confused:

But found this fouram very helpful...:)
i am posting my outputs, so that my problem will also b entertain..

```

jhon@ubuntu:~$ lspci -k

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Lenovo Device 30a1
    Kernel driver in use: ath9k
    Kernel modules: ath9k
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Lenovo Device 3975
    Kernel driver in use: r8169
    Kernel modules: r8169


```

```

jhon@ubuntu:~$ \nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        74:DE:2B:AA:6A:BD

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        F0:DE:F1:A5:15:C5

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


```

```

 jhon@ubuntu:~$ rfkill all
Usage:    rfkill [options] command
Options:
    --version    show version (0.4-1 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm

```

---

### Post by wildmanne39 on 2012-02-18
Hi alee863, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands for accuracy into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by sadaruwan12 on 2012-02-18
Oke first of all run this.

```
$ rfkill list all
```

Now this,

```
$ lsmod
```

Then please post back with the terminal out put.

---

### Post by alee863 on 2012-02-18
Thank you ...
OUTPUTS:
cat /etc/lsb-release; uname -a
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ubuntu 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


```lspci -nnk | grep -iA2 net
```
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lenovo Device [17aa:30a1]
    Kernel driver in use: ath9k
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169
```iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```rfkill list all
```

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```lsmod
```

Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  8 
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
joydev                 17693  0 
acer_wmi               23948  0 
snd_hda_intel          33390  4 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
arc4                   12529  2 
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                73882  0 
btusb                  18600  2 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ath9k                 127538  0 
v4l2_compat_ioctl32    17083  1 videodev
bluetooth             166112  23 bnep,rfcomm,btusb
serio_raw              13166  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ideapad_laptop         13871  0 
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
i915                  571221  3 
wmi                    19256  1 acer_wmi
snd                    68266  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              462046  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              312914  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
drm_kms_helper         42558  1 i915
drm                   236290  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
soundcore              12680  1 snd
video                  19412  1 i915
cfg80211              199630  3 ath9k,mac80211,ath
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
ahci                   26002  2 
r8169                  52788  0 
libahci                26861  1 ahci

```

---

### Post by alee863 on 2012-02-18
and please tell me what these outputs tell... :)
because my wifi is working fine in windows...
so it might b driver issue...:!:

---

### Post by wildmanne39 on 2012-02-18
Hi first you have a soft block let's remove it and see if it comes on.
```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot.
Thanks

---

### Post by alee863 on 2012-02-18
Thanks alot..! now i am using my wifi...!! :grin::grin::grin::grin::grin::grin::grin::grin:

can u please tell me what was the problem??

---

### Post by wildmanne39 on 2012-02-18
Hi alee863, I am glad it is working.

The module that tells the kernel to turn the wireless on sometimes does not work well and that was your problem.
Thanks

---

