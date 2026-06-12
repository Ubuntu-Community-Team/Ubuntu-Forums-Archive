---
title: "How to go from xubuntu 13.10 to ubuntu 13.10"
date: 2014-02-10
forum: New to Ubuntu
---

### Post by maazmahmood on 2014-02-10
Now I have my own personal files on the xubuntu. So will the following code work:

```
[COLOR=#000000][FONT=Ubuntu Mono]Sudo apt-get install ubuntu-desktop
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get purge xubuntu-desktop #optional[/FONT][/COLOR]
```

Or will I need something else to make sure all my games and everything are still there?

---

### Post by sudodus on 2014-02-11
It is easy to install another desktop environment, but it is harder and more risky to remove a [previous] desktop environment. If you run only the first of the two commands, xubuntu-desktop will stay and occupy some desk space. Furthermore, there will be some doublets in the meny system / dash, but you can live with that.

You will have the option to select 'session' at the login screen, so at any time, you can switch between Unity and Xubuntu (and simple XFCE).

Games and other installed program will stay, unless you remove them.

---

### Post by maazmahmood on 2014-02-11
Oh, so this command isn't installing Ubuntu it's just installing the Unity desktop enviroment? And I think I have my thing set to not ask for login, and login immediately, will I just need to logout and log back in?

And just to reiterate, I'll only need the first command right? And what are the commands to try other desktop environments like cinnamon and gnome 3.10?

---

### Post by Bucky Ball on 2014-02-11
What are the specs on the machine you are running? RAM and CPU specifically ...

---

### Post by maazmahmood on 2014-02-11
What's the command to chek PC specks again. Something lshw -short

---

### Post by sudodus on 2014-02-11
try ```
sudo lshw
```

and to save the output to a file lshw.txt

```
sudo -s
lshw > lshw.txt
exit

```
or use ***hardinfo*** with a graphical user interface

---

### Post by maazmahmood on 2014-02-11
Voila Specs

> maaz-xubuntu    description: Desktop Computer
    product: GT5628 ()
    vendor: Gateway
    serial: CSX7A 710 00635
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=7EA81BD2-6E26-11DC-A606-000C6E0802BC
  *-core
       description: Motherboard
       product: DG33SXG2
       vendor: Intel Corporation
       physical id: 0
       version: AAD94468-501
       serial: BQSX739001HV
       slot: Base Board Chassis Location
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          slot: J1PR
          size: 1596MHz
          capacity: 4GHz
          width: 64 bits
          clock: 266MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=3
        *-cache:0
             description: L2 cache
             physical id: 1
             slot: Unknown
             size: 4MiB
             capacity: 4MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 3
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 3.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 3.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 3.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 3.4
             width: 64 bits
             capabilities: logical
     *-cache
          description: L1 cache
          physical id: 2
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 4
          version: DPP3510J.15A.0316.2008.0522.1909
          date: 05/22/2008
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: OCZ2P10662G
             vendor: 0x7F7F7F7FB0000000
             physical id: 0
             serial: 0x00000000
             slot: J6H1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 1
             serial: NO DIMM
             slot: J6H2
        *-bank:2
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: OCZ2P10662G
             vendor: 0x7F7F7F7FB0000000
             physical id: 2
             serial: 0x00000000
             slot: J6J1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM DDR2 [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 3
             serial: NO DIMM
             slot: J6J2
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:e0000000-e2ffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G92 [GeForce 9800 GTX / 9800 GTX+]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:48 memory:e2000000-e2ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:2000(size=128)
        *-communication UNCLAIMED
             description: Communication controller
             product: 82G33/G31/P35/P31 Express MEI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: latency=0
             resources: memory:e3125900-e312590f
        *-network
             description: Ethernet interface
             product: 82562V-2 10/100 Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth1
             version: 02
             serial: 00:1c:c0:07:15:45
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=1.1-2 ip=10.0.0.96 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:46 memory:e3100000-e311ffff memory:e3124000-e3124fff ioport:30e0(size=32)
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:30c0(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:30a0(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:3080(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:17 memory:e3125400-e31257ff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:47 memory:e3120000-e3123fff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:4000(size=4096) memory:f8000000-f81fffff ioport:f8200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:5000(size=4096) memory:f8400000-f85fffff ioport:f8600000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:6000(size=4096) memory:f8800000-f89fffff ioport:f8a00000(size=2097152)
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:7000(size=4096) memory:f8c00000-f8dfffff ioport:f8e00000(size=2097152)
        *-pci:5
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:8000(size=4096) memory:f9000000-f91fffff ioport:f9200000(size=2097152)
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:3060(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:3040(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:3020(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:e3125000-e31253ff
        *-pci:6
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:1000(size=4096) memory:e3000000-e30fffff ioport:f9400000(size=1048576)
           *-storage
                description: Mass storage controller
                product: ITE 8211F Single Channel UDMA 133
                vendor: Integrated Technology Express, Inc.
                physical id: 2
                bus info: pci@0000:07:02.0
                version: 11
                width: 32 bits
                clock: 66MHz
                capabilities: storage pm bus_master cap_list rom
                configuration: driver=pata_it821x latency=64 maxlatency=8 mingnt=8
                resources: irq:18 ioport:1018(size=8) ioport:1024(size=4) ioport:1010(size=8) ioport:1020(size=4) ioport:1000(size=16) memory:f9400000-f941ffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW322/323 [TrueFire] 1394a Controller
                vendor: LSI Corporation
                physical id: 3
                bus info: pci@0000:07:03.0
                version: 70
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=24 mingnt=12
                resources: irq:19 memory:e3000000-e3000fff
        *-isa
             description: ISA bridge
             product: 82801IR (ICH9R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:21 ioport:3458(size=8) ioport:346c(size=4) ioport:3450(size=8) ioport:3468(size=4) ioport:3430(size=16) ioport:3420(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:e3125800-e31258ff ioport:3000(size=32)
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:21 ioport:3448(size=8) ioport:3464(size=4) ioport:3440(size=8) ioport:3460(size=4) ioport:3410(size=16) ioport:3400(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3160812AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AH
             serial: 5LSAP9B1
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0002f533
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 6005ed87-8619-43fb-b0d9-42bb62451f40
                size: 147GiB
                capacity: 147GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-02-05 18:24:00 filesystem=ext4 lastmountpoint=/ modified=2014-02-10 15:05:34 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-02-10 15:05:34 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2038MiB
                capacity: 2038MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2038MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 3
          logical name: scsi4
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD RW AD-7173A
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1-04
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom




---

### Post by sudodus on 2014-02-11
> **maazmahmood said:**
> Oh, so this command isn't installing Ubuntu it's just installing the Unity desktop enviroment? And I think I have my thing set to not ask for login, and login immediately, will I just need to logout and log back in?

And just to reiterate, I'll only need the first command right? And what are the commands to try other desktop environments like cinnamon and gnome 3.10?

I think your computer can run Ubuntu (it has enough 'horsepower in CPU and GPU').

You select '***session***' at the login screen in order to switch between Xubuntu and Ubuntu.

I would not clutter a working installation with a lot of desktop environments, that might be hard to get rid without destroying something. The best way is to test desktop environments in a separate installed system (in another partition) or running live systems.

---

### Post by Bucky Ball on 2014-02-11
That machine has the RAM to run Virtualbox. Why not try them out as virtual machines?

---

### Post by maazmahmood on 2014-02-11
So what is the command to try other desktop enviroments (such as cinnamon, gnome etc.) 
Also how do I get rid of desktop enviroments?

But please help me understand something here, the desktop enviroments are just that right, not installing a new OS. Like if I got xfce on ubuntu machine I still have ubuntu, right? Or do i now have xubuntu? Becasue on my virtual ubuntu machine, I tried out the sudo-apt get install xubuntu-desktop, and now at the beginning of everything it says xubuntu.

Ok, so here is my deal: On my actual machine I have xubuntu 13.10. The desktop enviroment is meh, but the unity Desktop I like, I haven't gotten to try out the other such as cinnamon and gnome. Is there a web page with the commands get/remove desktop environments, or maybe a software that manages these desktop enviroments

---

### Post by Bucky Ball on 2014-02-11
xubuntu-desktop is like installing xubuntu over Ubuntu. That's why. As suggested ... if you install xfce4 you are only installing the desktop enviroment. In my opinion it is a bad idea to start installing *buntu-desktop anything. You are going to end up with confusion, duplication and bloat. I always advise against it. DE only. That's all you need, but amazing how many people actually advise others to install the 'whatever-desktop'. Bad.

---

### Post by maazmahmood on 2014-02-11
So what is the command to install/uninstall the respective DE's for Unity and Cinnamon?
Because I have xubuntu, but I don't really like Xcfe DE. Now as far as sepcs go could my computer handle the Unity DE? If not I'll probably just end up getting either Linux Mint completely or Cinnamon DE

---

### Post by Bucky Ball on 2014-02-11
Open a terminal:

sudo apt-get install unity

That's it.

---

### Post by maazmahmood on 2014-02-12
So I'm guessing same goes for Cinnamon as well? And what about specs, you've seen them would you recommend Unity with those specs? And would it be ok if I installed let's say Unity or even Cinnamon, and uninstalled XCFE?

---

### Post by Bucky Ball on 2014-02-12
> **sudodus said:**
> I think your computer can run Ubuntu (it has enough 'horsepower in CPU and GPU').



> **Bucky Ball said:**
> That machine has the RAM to run Virtualbox. Why not try them out as virtual machines?

Once again, yes. Your computer has the grunt to run whatever you like.

> **maazmahmood said:**
>  And would it be ok if I installed let's say Unity or even Cinnamon, and uninstalled XCFE?

Entirely up to you.

---

### Post by maazmahmood on 2014-02-12
To completely remove a DE, what do I need to do? A simple sudo apt-get purge?

---

### Post by Bucky Ball on 2014-02-12
I don't know how effectively or completely one can remove a desktop environment, but yes, purge. After that, it is convention to run:

sudo apt-get autoremove

... to (hopefully) clean up what might be left.

---

### Post by deadflowr on 2014-02-12
> **maazmahmood said:**
> To completely remove a DE, what do I need to do? A simple sudo apt-get purge?

I won't say to run any of the commands from here
[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

But simply that this is basically what you would have to do to completely remove a DE.

Again for clarity, I wouldn't fully endorse running these commands, as some of them are probably out of date.
Just a quick idea of what would need to be done.

---

### Post by Dennis N on 2014-02-12
> **maazmahmood said:**
> To completely remove a DE, what do I need to do? A simple sudo apt-get purge?

The desktops you install like  xubuntu-desktop, lubuntu-desktop, ubuntu-desktop are metapackages which cause all the many desktop components to install. But, if you remove ubuntu-desktop for example, none of the components actually is removed by that removal.

Simulated removal of ubuntu-desktop from this computer:

```
dn@Roxanne:~$ apt-get -s remove ubuntu-desktop
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  liblaunchpad-integration1 gir1.2-unique-3.0
  linux-headers-3.2.0-55-generic-pae linux-headers-3.2.0-45
  linux-headers-3.2.0-52 linux-headers-3.2.0-48 linux-headers-3.2.0-54
  linux-headers-3.2.0-55 linux-headers-3.2.0-56
  linux-headers-3.2.0-52-generic-pae linux-headers-3.2.0-56-generic-pae
  linux-headers-3.2.0-48-generic-pae linux-headers-3.2.0-45-generic-pae
  libjpeg62 linux-headers-3.2.0-54-generic-pae libiptcdata0
Use 'apt-get autoremove' to remove them.
[B]The following packages will be REMOVED:
  ubuntu-desktop[/B]
0 upgraded, 0 newly installed, **1 to remove** and 8 not upgraded.
Remv ubuntu-desktop [1.267.1]

```

only one package gets removed and that package is not software, but just the list of things to install.

So you will have a difficult job finding and removing what it installed.

Extra: use the command **apt-cache showpkg ubuntu-desktop** and look at dependencies. That is what would be installed by ubuntu-desktop. Of course, some may already be installed by some other package beforehand.

---

### Post by vasa1 on 2014-02-12
> **deadflowr said:**
> ... as some of them are probably out of date.
Just a quick idea of what would need to be done.
Whatever is installed (and possibly removed) at the time of installing a DE (or anything else for that matter) can be worked out from */var/log/apt/history.log*. That's essentially what the Psychocat's oneliner is based on.

The relevant entry in history.log needs a bit of massaging, but that's it.

---

### Post by Bucky Ball on 2014-02-12
> **Dennis N said:**
> Most of these desktops you install like xfce4, xubuntu-desktop, lubuntu-desktop, ubuntu-desktop 

Will people never get this? xfce4 is a desktop ENVIRONMENT. Installing *ubuntu-desktop ANYTHING is pretty much equivalent to installing another flavour over the one you already have installed. A DE does NOT drag in all the default apps. A *buntu-desktop DOES. Xfce4 is used in LOTS of other distros. Xubuntu-desktop is used in one, because it is one! Pretty much.

Please people, there is a clear distinction between a desktop environment, e.g. xfce4, lxde, unity, and installing a 'desktop', namely installing another OS on top of what you already have, respectively, xubuntu-desktop, lubuntu-desktop, ubuntu-desktop. Please make that distinction!

Removing a DE is as simple as pulling 'xfce4' or 'lxde' or whatever. Removing a *buntu-desktop is a totally different matter. Please stop advising people to install *buntu-desktop unless that is specifically what you mean. Installing 'xfce4' or xubuntu-desktop are FAAAAR from the same and are definitely not interchangable commands. *_They are not the same at all and do not achieve the same ends!_*

Rant over. ;)

PS: I do minimal installs. If I then add xfce4 I have the Ubuntu base kernel with xfce4 as a desktop environment. That's it. No apps. If I were to install xubuntu-desktop I have Xubuntu, all apps and everything else. No point in a minimal install then as I could have simply installed Xubuntu and saved some time. Any flavour is simply the kernel base with *buntu-desktop plopped on top. The 'desktop' drags in the apps, etc. Xfce4 and the Ubuntu kernel = no apps until I add them.

So, imagine a machine with kubuntu-desktop, ubuntu-desktop, lubuntu-desktop, xubuntu-desktop. You are effectively running four OS on one base kernel. A messy, unweildy hybrid with a ton of bloat, duplication and redundancy. I ought to know, I've been there! ;)

---

### Post by Dennis N on 2014-02-12
I will remove xfce4 to be accurate. It is a desktop environment. But it is still a metapackage.

---

### Post by maazmahmood on 2014-02-12
I tried sudo apt-get install unity on a xubuntu virtual machine, and logged out and didn't see it in the drop down

---

### Post by deadflowr on 2014-02-12
What options do you have at the login screen?

---

### Post by maazmahmood on 2014-02-12
Just the Ubuntu, Ubuntu 2D, and recovery console.

---

### Post by deadflowr on 2014-02-12
> **maazmahmood said:**
> Just the Ubuntu, Ubuntu 2D, and recovery console.

Ubuntu is unity from the desktop session standpoint.
But don't know why 2d would show up in 13.10.
(Ubuntu2d (also known as unity-2d) was dropped because they merged it into main unity)

These are booting into xfce?

I wonder if you need to install something like lightdm or unity-greeter.

---

### Post by maazmahmood on 2014-02-13
Oh, I'm sorry, I was looking at the Ubuntu VM when I said that, all I see is xfce session and Xubuntu session (after writing sudo apt-get install Unity, on xubuntu VM)

---

### Post by maazmahmood on 2014-02-13
Oh, I'm sorry, I was looking at the Ubuntu VM when I said that, all I see is xfce session and Xubuntu session (after writing sudo apt-get install Unity, on xubuntu VM)

---

### Post by deadflowr on 2014-02-13
> **maazmahmood said:**
> Oh, I'm sorry, I was looking at the Ubuntu VM when I said that, all I see is xfce session and Xubuntu session (after writing sudo apt-get install Unity, on xubuntu VM)

I'm not sure what is missing.

Maybe open a terminal and run
```
ls /usr/share/xsessions
```
what are listed.

---

### Post by maazmahmood on 2014-02-16
I tried gertting Cinnamon, it actually worked out quite nicely, I followed this link:

[http://askubuntu.com/questions/292394/how-to-completely-remove-unity-and-replace-it-with-cinnamon](http://askubuntu.com/questions/292394/how-to-completely-remove-unity-and-replace-it-with-cinnamon)

and it also provides commands to clean out unity, if I enter those commands will it break the xfce session as well?

---

### Post by deadflowr on 2014-02-16
Running commands to remove something should always be done after a little investigation.
see if what is to be removed will affect the xfce session.
Like if the two desktops(unity and xfce) share a package.

---

### Post by vasa1 on 2014-02-16
> **maazmahmood said:**
> ... if I enter those commands will it break the xfce session as well?
You have VMs ... test and please let us know!

---

