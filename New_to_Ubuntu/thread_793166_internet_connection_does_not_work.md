---
title: "internet connection does not work"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by strnad on 2008-05-13
Hello,

I am using Ubuntu 7.10.

I have a problem with my internet connection. I use D-Link DES-1005D Fast ethernet desktop switch. When I plug the ethernet cable into the Notebook with Windows, the connection is made up automatically.

However this is not valid for Ubuntu. When I do it, Ubuntu tries to connect, but without any success. I called to my internet provider (telenet.be) and they told me, that they cannot give me any IP adresses or so, since all these information is passed on by the modem - D-Link.

Can you please help me how to set up the connection to get my internet working? I really do not want to go back to Windows.

Thanks

Sincerely

Peter

---

### Post by cyberbill on 2008-05-13
please post output of

sudo ifconfig

-cb

---

### Post by mapes12 on 2008-05-13
and the output from:

```
cat /etc/resolv.conf
```

and it might be helpful for us to look at the output from:

```
sudo lshw
```

---

### Post by strnad on 2008-05-13
sorry, but I am a total beginner,

how do I get this output? Where should I type it?

Thanks

Peter

---

### Post by mapes12 on 2008-05-13
OK

Applications>Accessories>Terminal

and type the commands from there.

---

### Post by strnad on 2008-05-13
OK, here are outputs:

user@user-laptop:~$ sudo config

[sudo] password for user:
sudo: config: command not found
user@user-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:92:53:D3:81  
          inet6 addr: fe80::21d:92ff:fe53:d381/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4707 (4.5 KB)  TX bytes:5730 (5.5 KB)
          Interrupt:19 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:1D:92:53:D3:81  
          inet addr:169.254.8.12  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

----------------------

user@user-laptop:~$ cat / etc/resolv.conf
cat: /: Is a directory
cat: etc/resolv.conf: No such file or directory

---------------------

user@user-laptop:~$ sudo lshw
user-laptop               
    description: Desktop Computer
    product: MSI Notebook VR610
    vendor: Micro-Star International
    version: Ver 1.000
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5
    configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-0000-001D9253D381
  *-core
       description: Motherboard
       product: MS-163B
       vendor: MSI
       physical id: 0
       version: Ver 1.000
       serial: BSS-0123456789
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: A163BAMS V1.0C (02/27/2008)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.8.2
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 800MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KB
             capacity: 256KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 256KB
             capacity: 512KB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM SDRAM [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 2GB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: Radeon X1200 Series
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi vga bus_master cap_list
                configuration: latency=64
        *-pci:1
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix cap_list
                configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 2)
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 3)
             vendor: ATI Technologies Inc
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8101E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 01
                serial: 00:1d:92:53:d3:81
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64 module=ahci
           *-disk
                description: SCSI Disk
                product: TOSHIBA MK1646GS
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: LB11
                serial: 18C3P5UIT
                size: 149GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 143GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux swap / Solaris partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 5530MB
                   capabilities: primary nofs
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
             capabilities: pm msi debug ehci bus_master cap_list
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
             capabilities: ht cap_list
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
             configuration: driver=ATIIXP_IDE latency=0 module=atiixp
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: Optiarc DVD RW AD-7530B
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: NX02
                   serial: 30648420 1367521Q111
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2 status=nodisc
        *-multimedia
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
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
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
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
     *-scsi:0
          physical id: 1
          bus info: usb@6:2
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Multi-Card
             vendor: Generic-
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdb
     *-scsi:1
          physical id: 2
          bus info: usb@6:9
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: USB Flash Disk
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdc
             version: 0.00
             size: 500MB
             capabilities: removable
             configuration: ansiversion=2
           *-disc
                physical id: 0
                logical name: /dev/sdc
                size: 500MB
                capabilities: partitioned partitioned:dos
              *-volume
                   description: W95 FAT32 partition
                   physical id: 1
                   logical name: /dev/sdc1
                   capacity: 499MB
                   capabilities: primary bootable

---

### Post by mapes12 on 2008-05-13
Too many spaces in the cat line cut and past this into terminal:

```
cat /etc/resolv.conf
```

This should list your nameserver

---

### Post by strnad on 2008-05-13
I did cut and paste and I got this:

bash: cat: command not found

I am little confused

---

### Post by strnad on 2008-05-13
I did cut and paste and I got this:

bash: cat: command not found

I am little confused

---

### Post by mapes12 on 2008-05-13
When you get the nameserver IP which will be something like 169.254.xx.xx

then in terminal:

```
ping -c4 169.254.xx.xx
```

post output back here.

---

### Post by strnad on 2008-05-13
but as I have written above, the command does not exist, when I copy it or when I write the command, it does not give me any output at all. :-(

---

### Post by mapes12 on 2008-05-13
Oh dear..............

Does your terminal prompt start:

```
user@user-laptop:~$
```

and if you type after this after the prompt:

```
man cat
```

what response do you get?

---

### Post by strnad on 2008-05-13
I get response in something like "user commands" cat 1 - they are explained there...

sorry for me being such a dummy, but this is the first time I am working with something else than Windows...

---

### Post by mapes12 on 2008-05-13
That's good. It looks like your terminal is working OK.

Have you tried again in the terminal:

```
cat /etc/resolv.conf
```

???

---

### Post by strnad on 2008-05-13
I tried it again,

I will describe step by step, what I do.

1. plug the ethernet cable into the notebook,
2. wait, untill the Ubuntu tries and finishes to connect to the internet. I have two "black" monitors icon onto the control panel,
3. I go to accessories - terminal,
4. type: cat /etc/resolv.conf
5. now, when I type it, nothing happens at all. That means that after I press enter, I get another line user@user-laptop: etc...

I try again: 

6. I copy and paste the command you wrote in the forum,
7. when I do that, I get following:
   bash:   cat: command not found

peter

---

### Post by mapes12 on 2008-05-13
Peter

the command:

```
cat
```

prints out the contents of the requested file. For some reason this basic command is not working on your machine. I don't know why  :confused:

If you have installed 7.10 from the Live CD all I can suggest is that you try again but download the alternate iso and load 7.10 using the text based installer.

Mark  :lolflag:

---

### Post by strnad on 2008-05-13
thanks for your help.... I will try to reinstall but I guess, I should go rather for 8.04

but theoretically...

what should I do next when this cat command will work?

thanks

peter

---

### Post by jhofmann on 2008-05-13
I'd like to suggest:
1.  Right now, your problems are with the terminal interface:  eg:  you don't understand yet how to type commands.  Look for simple bash tutorial, the simpler the better.  "bash" is the program you are actually talking to when you type things on the command line.

Back to the first time you typed the cat command:
you actually asked the cat command to print out the contents of the file /, and then the contents of the second file "file etc/resolv.conf"  You did this by leaving a space between "/" and "etc/resolv.conf"
The order of things on the command line is like this:
<command> <argument> <argument>, ...
The spaces between <command> and <argument> are absolutely necessary, and any space INSIDE an argument makes two arguments of it.

2.  We still want to see the contents of your /etc/resolv.conf file as well as the others.  

3.  Don't give up.  I've been doing this for quite a while, but I still remember the FRUSTRATION of not knowing how to get every little thing exactly right.  Keep trying, and keep posting.

Jim

---

### Post by lswest on 2008-05-13
i just wanted to point out, the cat command would not return anything if the file is empty, and since the OP says it did not (when he typed it) return anything, the file either doesn't exist, or is empty.

---

### Post by jhofmann on 2008-05-13
I tried cat with a non-existing file.  It complains.  So I guess the file is empty.  If it is, that sure would cause problems, wouldn't it?

Jim

---

### Post by mapes12 on 2008-05-13
If the file did not exist Ubuntu would return:

```

cat: /etc/resolv.conf: No such file or directory
```

From the above threads Cat is not returning anything.

If the file existed but was empy then the following code at least would be output but without the nameserver IP:

```
# generated by NetworkManager, do not edit!

search home
```

---

### Post by strnad on 2008-05-16
Hello guys, 

I hope you did not forget about me :-)

I have finally installed a new Ubuntu in text mode. I used 8.04, 64 kb mode. However, when I put the command we had problem with cat /etc/resolv.conf, I get different, but not pleasant response:

cat: /etc/resolv.conf No such file or directory

I do not understand it, because I have downloaded a fresh copy from the internet just a few hours ago.

Nevertheless, if it helps. When I was installing Ubuntu, I tried to configure the network as it is possible during the installation. However Ubuntu told me, that automatic configuration is not possible, because my network does not use DHCP.  But when I checked my settings in Windows, I get some DHCP IP address. Also I had to enter a name for my network - I used "user". I do not know, what that exactly means, but I want to provide you with as much (useful) information as possible.

---

### Post by strnad on 2008-05-19
Hello,

I have tried to put a command ifconfig and here is the output:

user@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:92:53:d3:81  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:840 (840.0 B)  TX bytes:6377 (6.2 KB)
          Interrupt:252 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8292 (8.0 KB)  TX bytes:8292 (8.0 KB)

then I tried the command ping -c4 127.0.0.1 and I got this:

user@ubuntu:~$ ping -c4 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.081 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.063 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.063 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.066 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 0.063/0.068/0.081/0.009 ms


Does that help anyhow?

Thanks

Peter

---

