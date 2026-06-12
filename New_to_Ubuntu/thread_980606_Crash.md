---
title: "Crash"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by k12321 on 2008-11-13
my ubuntu 8.10 crashes often when i use open office and just now it crashed when i was simply going through my contacts 
should i remove ubuntu?or continue?

---

### Post by Ryadt on 2008-11-13
Can you post the output of```
top
```

---

### Post by k12321 on 2008-11-13
huhh am sorry i am not too familiar with ubuntu ..started using that 2-3 days ago...what should i post?and how?
thanks!

---

### Post by Ryadt on 2008-11-13
Go in the terminal (Applications > Accessories > Terminal), input the code ```
top
``` and then copy and paste the output here.

---

### Post by k12321 on 2008-11-13
```
top - 14:19:57 up 20 min,  2 users,  load average: 0.75, 0.71, 0.63
Tasks: 116 total,   1 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.7%us,  2.0%sy,  0.0%ni, 91.0%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1293412k total,  1264996k used,    28416k free,   347688k buffers
Swap:   195304k total,     4788k used,   190516k free,   527788k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5051 root      20   0  654m  66m 9904 S  5.7  5.3   2:18.14 Xorg               
 7212 girish    20   0  111m  25m  13m S  2.0  2.0   0:00.68 gnome-terminal     
 5873 girish    20   0  264m  82m  29m S  1.3  6.5   1:12.79 firefox            
 6986 girish    20   0 66948  29m  10m S  1.3  2.4   0:09.96 python             
 5400 girish    20   0 14176 5056 3696 S  0.7  0.4   0:13.20 at-spi-registry    
 5702 girish    20   0 16188 6636 5064 S  0.7  0.5   0:04.96 magnifier          
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.52 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       


```

---

### Post by Ryadt on 2008-11-13
Try to disable compiz and see if you keep experiencing the crash.```
metacity --replace
```

---

### Post by starcannon on 2008-11-13
I note that your using up nearly the entire 128mb of ram you have.
Minimum requirements as posted at the Open Office website is 256mb of ram with a recommended 512mb of ram; this is not a show stopper, indeed ram is fairly inexpensive, and even if more RAM is economically out of the question, one can always switch to Xubuntu, or even just install Abi Word for word processing, and Gnu Cash for spreadsheets (each of which have substantially lower system requirements.)
I think just looking at your top figures that you should be running at most Xubuntu(128mb min for liveCd, 172mb for install), though to really make a final determination I'd really like to see the output of:
```

sudo lshw

```
Once we have a look at your overall hardware we can then better help guide you to the the install best suited for your hardware abilities.

GL and have fun

> **k12321 said:**
> ```
top - 14:19:57 up 20 min,  2 users,  load average: 0.75, 0.71, 0.63
Tasks: 116 total,   1 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.7%us,  2.0%sy,  0.0%ni, 91.0%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1293412k total,  1264996k used,    28416k free,   347688k buffers
Swap:   195304k total,     4788k used,   190516k free,   527788k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5051 root      20   0  654m  66m 9904 S  5.7  5.3   2:18.14 Xorg               
 7212 girish    20   0  111m  25m  13m S  2.0  2.0   0:00.68 gnome-terminal     
 5873 girish    20   0  264m  82m  29m S  1.3  6.5   1:12.79 firefox            
 6986 girish    20   0 66948  29m  10m S  1.3  2.4   0:09.96 python             
  5400 girish    20   0[ 14176 5056]("skype:+1141765056?call") 3696 S  0.7  0.4   0:13.20 at-spi-registry    
  5702 girish    20   0[ 16188 6636]("skype:+1161886636?call") 5064 S  0.7  0.5   0:04.96 magnifier          
    1 root      20   0  3056 1884  564 S  0.0  0.1   0:01.52 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       


```

---

### Post by k12321 on 2008-11-13
> **starcannon said:**
> I note that your using up nearly the entire **128mb** of ram you have.


its not 1.28Gb ram?

---

### Post by k12321 on 2008-11-13
woow my ubuntu crashed again?it logged off to the main page 

now here is what you asked for 
```
ubuntu                    
    description: Desktop Computer
    product: MS - 7 1 4 4
    vendor: MICRO-STAR INTERNATIONAL CO., LTD
    version: 1.00
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: MS - 7 1 4 4
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       version: 1.00
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (07/25/2005)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Sempron(tm) Processor 2800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.2
          slot: Socket 940
          size: 1600MHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 8704MiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 8GiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-amd64 latency=8 module=amd64_agp
        *-pci
             description: PCI bridge
             product: VT8237 PCI bridge [K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV350 AS [Radeon 9550]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm bus_master cap_list
                configuration: latency=32 mingnt=8
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350 AS [Radeon 9550] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm cap_list
                configuration: latency=32 mingnt=8
        *-multimedia
             description: Multimedia audio controller
             product: CM8738
             vendor: C-Media Electronics Inc
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=C-Media PCI latency=32 maxlatency=24 mingnt=2 module=snd_cmipci
        *-storage
             description: RAID bus controller
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm bus_master cap_list
             configuration: driver=sata_via latency=32 module=sata_via
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk
                description: ATA Disk
                product: Maxtor 6Y080L0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: YAR4
                serial: Y28ZGHZC
                size: 76GiB (81GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=fd11fd11
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /host
                   logical name: /boot
                   version: 3.1
                   serial: 680a9aaa-2abb-2541-88e8-5bb645370f74
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-10-04 23:49:53 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 61GiB
                   capacity: 61GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 29GiB
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 32GiB
           *-cdrom
                description: DVD reader
                product: CDW/DVD TS-H492C
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: CM03
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:13:d3:38:b9:89
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=59.78.123.25 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
     *-pci:1
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8T800Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 106
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 107
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 108
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 109
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: da:0b:e7:47:82:33
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```


i did the metacity thing but 5 mins later it crashed to the log in page

---

### Post by k12321 on 2008-11-13
ok am moving to xubuntu 
how do i uninsatll ubuntu?

---

### Post by starcannon on 2008-11-13
> **k12321 said:**
> its not 1.28Gb ram?
Yeah it is, sorry my mistake. any way your using it up pretty fiercely.

---

### Post by k12321 on 2008-11-13
yeah... almost all 1.28
i removed Ubuntu..will try Kubuntu later on this week..
thanks for the help :D

---

