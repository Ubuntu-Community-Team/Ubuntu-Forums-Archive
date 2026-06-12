---
title: "***boot problems please help!***"
date: 2016-11-04
forum: New to Ubuntu
---

### Post by shyler-casavant on 2016-11-04
Hello! 

I just did a nice clean install of Ubuntu 16.04 with encryption; after having a dual boot system. 
I wiped everything, installed and life was good. 
Then, i updated my system and enabled my restricted drivers.
Then, i rebooted; problem time! 

Here's what happens.

1. Dell logo appears.
2. Ubuntu encrypted password request (super big & doesn't accept password).
3. I hit ctrl+alt+del.
4. Dell logo appears again. 
5. Grub screen pops.
6. If I choose Ubuntu; it sits with a blinking white _ (I have a SSD; too slow after 2 - 3 minutes)
7. I hit ctrl+alt+del
8. Dell logo appears again.
9. Grub screen again
10. I choose advanced options
11. I choose update grub
12. It boots! 

Even tried  

 1. That boot-repair package from Yann MRN and ... 
2. sudo update-grub

***OUTPUT OF SUDO UPDATE-GRUB***
[B][I]Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-21-generic
Found initrd image: /boot/initrd.img-4.4.0-21-generic
done
[/I][/B]
No fix! Whatcha all thinking?

Thanks All, 

Shyler

---

### Post by T.J. on 2016-11-05
I am just guessing, but I suspect that you have an Nvidia or some other card using a commercial driver that is not supported by kernel mode setting.

Try adding "nomodeset" to your kernel boot parameters in the boot screen.  If the machine boots properly - it is the problem.  Add nomodeset to your /etc/default/grub file next to "splash" and then update your bootloader.   You might lose your fancy logo splash but booting should be more reliable.

---

### Post by mörgæs on 2016-11-05
In stead of guessing I would prefer getting to know the exact hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by shyler-casavant on 2016-11-05
Mr. TJ - I attempted your resolution with no love!
Mr. mörgæs - Please see below!

Thanks everyone!
Shyler

```
computer
    description: Laptop
    product: Latitude E6420
    vendor: Dell Inc.
    version: 01
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=laptop uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 038C0K
       vendor: Dell Inc.
       physical id: 0
       version: A00
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A23
          date: 01/04/2016
          size: 64KiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-2640M CPU @ 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-2640M CPU @ 2.80GH
          serial: [REMOVED]
          slot: CPU 1
          size: 3299MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm epb tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm ida arat pln pts cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal varies unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal varies unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 41
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 0
             serial: [REMOVED]
             slot: ChannelA-DIMM0
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5273DH0-CH9
             vendor: Samsung
             physical id: 1
             serial: [REMOVED]
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:e3000000-e40fffff ioport:d0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GF119M [NVS 4200M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:29 memory:e3000000-e3ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:3000(size=128) memory:e4000000-e407ffff
           *-multimedia
                description: Audio device
                product: GF119 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:e4080000-e4083fff
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
             configuration: driver=mei_me latency=0
             resources: irq:27 memory:e4db0000-e4db000f
        *-network
             description: Ethernet interface
             product: 82579LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: enp0s25
             version: 04
             serial: [REMOVED]
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:25 memory:e4d00000-e4d1ffff memory:e4d80000-e4d80fff ioport:4040(size=32)
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:e4d70000-e4d703ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-45-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:30 memory:e4d60000-e4d63fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:e4c00000-e4cfffff
           *-network
                description: Wireless interface
                product: Centrino Ultimate-N 6300
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 35
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-45-generic firmware=9.221.4.1 build 25532 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:28 memory:e4c00000-e4c01fff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:2000(size=4096) memory:e4100000-e4afffff ioport:e2100000(size=10485760)
        *-pci:4
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:e4b00000-e4bfffff
           *-generic
                description: SD Host controller
                product: OZ600FJ0/OZ900FJ0/OZ600FJS SD/MMC Card Reader Controller
                vendor: O2 Micro, Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:e4b20000-e4b201ff
           *-storage UNCLAIMED
                description: Mass storage controller
                product: O2 Micro, Inc.
                vendor: O2 Micro, Inc.
                physical id: 0.1
                bus info: pci@0000:05:00.1
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:e4b10000-e4b10fff memory:e4b00000-e4b007ff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:17 memory:e4d50000-e4d503ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-45-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
                 *-usb UNCLAIMED
                      description: Generic USB device
                      product: 5880
                      vendor: Broadcom Corp
                      physical id: 8
                      bus info: usb@2:1.8
                      version: 1.01
                      serial: [REMOVED]
                      capabilities: usb-1.10
                      configuration: maxpower=100mA speed=12Mbit/s
        *-isa
             description: ISA bridge
             product: QM67 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: RAID bus controller
             product: 82801 Mobile SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:26 ioport:4090(size=8) ioport:4080(size=4) ioport:4070(size=8) ioport:4060(size=4) ioport:4020(size=32) memory:e4d40000-e4d407ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:e4d30000-e4d300ff ioport:4000(size=32)
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 850
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2B6Q
             serial: [REMOVED]
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=fdd1ec11
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: [REMOVED]
                size: 487MiB
                capacity: 487MiB
                capabilities: primary bootable extended_attributes large_files ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2016-11-05 08:00:02 mount.fstype=ext2 mount.options=rw,relatime,block_validity,barrier,user_xattr,acl mounted=2016-11-05 08:00:02 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 232GiB
                capacity: 232GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 232GiB
  *-battery
       product: DELL 5CGM4A7
       vendor: Samsung SDI
       physical id: 1
       version: 00/04/2016
       serial: [REMOVED]
       slot: Sys. Battery Bay
       capacity: 48840mWh
       configuration: voltage=11.1V
```

---

### Post by ajgreeny on 2016-11-05
You do have an nvidia card as suspected by the previous two posters, but I do not know enough about them to be certain which card version it is from the lshw output, but I believe it might be a GeeForce 610M.

Do you remember which nvidia proprietary driver you chose?  It might be worth seeing if you can get a different version from the Additional Drivers utility.

Did the nomodeset boot option not get you to a low resolution GUI desktop?  It normally does. and from there you can try again to install another nvidia driver.

---

### Post by shyler-casavant on 2016-11-05
Yeah the nomodeset didn't do anything unfortunately. Maybe I put it in the wrong spot? 

Also, I used the NVIDIA binary driver - version 367.57 from nvidia-367(proprietary, tested)

I picked it right off the top on the additional drivers - that normally works - but things change; I get it.

[I]
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **nomodeset**"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"[/I]

---

### Post by T.J. on 2016-11-05
You did fine. Did you update-grub afterward?  Otherwise, changes will not take effect.  If that does not work, we will need to try something. Add " vga=0x318" to the nomodeset.  This will force X11 to boot in VGA standard mode and then we can see about installing the Nvidia supported driver.  After we do that, you can remove both nomodeset and vga from the line, and the Nvidia driver should take over.

---

### Post by shyler-casavant on 2016-11-05
I did as suggested - 
It turned the prompt for a encrypt password to a more appropriate looking size. 
Now, it will still not accept any keyboard input except CTRL+ALT+DEL and grub will come back; 
I then choose the advanced options and boom update the grub from there and then it will boot - 
what are you guys thinking now about the keyboard input craziness? Here's my grub config as it sits now. 
Ya'll are awesome!

[I]# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="**quiet splash nomodeset vga=0x318**"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

[/I]

---

### Post by T.J. on 2016-11-05
Would you mind posting a screenshot?  I'm having a hard time understanding what you mean precisely.

---

### Post by shyler-casavant on 2016-11-05
Alrighty - got it fixed here - it was a strange bug - did some googling and got it to boot and take a password. 

Before, I would reboot and get stuck on the crypt password request - it would not take my password! 

The screen looked like this below[IMG]http://i.stack.imgur.com/tLuxr.jpg[/IMG]

So what I did was get into the grub file and remove 

"quiet splash" from below and sudo update-grub: BOOM! It took my password in terminal land!
[I]
GRUB_CMDLINE_LINUX_DEFAULT="**quiet splash nomodeset vga=0x318**"
[/I]
So now my grub config looks like this - it works perfect.[I]

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="nomodeset vga=0x318"**
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

[/I]Still interested in the possibility of a splash screen - any idea why this would take input but the splash wouldn't?

---

### Post by T.J. on 2016-11-05
Okay, from the picture your video card is working.  At this point it appears you have encrypted your hard drive during install.   Once a drive is encrypted it cannot be accessed without a password. If you do not remember your password, you are totally out of luck, and will have to erase it and start over.

---

### Post by oldfred on 2016-11-06
The vga setting is obsolete. Grub tries to use Ubuntu default, but sometimes needs its own setting.

 vga=xxx is a deprecated boot option
Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
replace "set gfxmode=auto" by "set gfxmode=1366x768"

---

### Post by T.J. on 2016-11-06
> **oldfred said:**
> The vga setting is obsolete. Grub tries to use Ubuntu default, but sometimes needs its own setting.

 vga=xxx is a deprecated boot option
Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
replace "set gfxmode=auto" by "set gfxmode=1366x768"

With respect, I disagree.  It is not depreciated as long as the kernel supports it - regardless of how Grub, Ubuntu or even Debian feels on the matter.  It will still work to diagnose problems with KMS drivers (which are part of the kernel). There are many issues in the Nvidia cards, especially the 900 series and up because of firmware.  IMHO, it is actually better to disable KMS entirely when using them.

"If the command line provided by the boot loader is entered by the
user, the user may expect the following command line options to work.
They should normally not be deleted from the kernel command line even
though not all of them are actually meaningful to the kernel.  Boot
loader authors who need additional command line options for the boot
loader itself should get them registered in
Documentation/kernel-parameters.txt to make sure they will not
conflict with actual kernel options now or in the future.

  vga=<mode>
    <mode> here is either an integer (in C notation, either
    decimal, octal, or hexadecimal) or one of the strings
    "normal" (meaning 0xFFFF), "ext" (meaning 0xFFFE) or "ask"
    (meaning 0xFFFD).  This value should be entered into the
    vid_mode field, as it is used by the kernel before the command
    line is parsed."


[https://www.kernel.org/doc/Documentation/x86/boot.txt](https://www.kernel.org/doc/Documentation/x86/boot.txt)

---

### Post by T.J. on 2016-11-06
[URL="https://ubuntuforums.org/member.php?u=2049208"][B][COLOR=#000000]shyler-casavant, 


[/COLOR][/B][COLOR=#000000][/COLOR][COLOR=#000000][/COLOR][/URL] Did you have any luck with your password?

---

### Post by Paul_Berry on 2016-11-17
I have this exact same problem, the password is not the issue. I and the person who posted can not put our password in, it wont let you. I have run with this graphics card with Ubuntu for over a year and a recent kernel update killed it all.  I get the exact same screen and if I go into advanced and try altering things I get vga=xxxx is no longer valid.  The thing is the graphics card and the drivers do work because I made my way in using and older kernel.  Im not an expert on grub so I struggle with this, and yes I can see that grub is forcing us into a graphics mode that prevents entering the password. The can not click in the password field or get a cursor in that field. So you just get stuck. Going into safe graphics mode produces other problems where you cant toggle the mode selection.  Can someone be clear for me on what I need to alter in grub at boot, Ive been on window all week because of this.  Thanks people I really appreciate any help right now.

---

### Post by oldfred on 2016-11-17
Have you tried nomodeset?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Boot-Repair can reset the gfxmode setting, so you boot with your screen setting size.
       
 From a grub command line to see available settings pressing <c> & escape to get back to menu
vbeinfo 
    See Boot-Repair's advanced settings & grub option for gfxmode

 [URL="https://help.ubuntu.com/community/Boot-Repair"]https://help.ubuntu.com/community/Boot-Repair

      [/URL]
 Details on settings in /etc/default/grub
 info -f grub -n 'Simple configuration'
> `GRUB_GFXMODE'

  Set the resolution used on the `gfxterm' graphical terminal.  Note
 that you can only use modes which your graphics card supports via
 VESA BIOS Extensions (VBE), so for example native LCD panel
 resolutions may not be available.  The default is `auto', which
 tries to select a preferred resolution.  *Note gfxmode::. 
      [URL="https://help.ubuntu.com/community/Boot-Repair"]
[/URL]

---

### Post by Paul_Berry on 2016-11-21
First, thanks for the reply.  First the problem I had was on 4.4.0-45-generic, ok I did nomodeset, and my nvidia drivers had been previously purged so it booted into desktop in Nouvea, loaded the nvidia drivers and then went to reboot, did nomodeset and yes!!!! It worked.  I decided that I would read all about Grub later and make any file changes I needed to make sure it stayed in nomodeset, later.  I had work to catch up on. 

Ok now the story does not end here.  Ubuntu must of updated while I was working, and now nomodeset does not work. I checked the kernel and yep it had updated it to 4.4.0-47-generic, I go into grub and remove quiet splash and put nomodeset and it boots to a coloured screen with no box to put encryption password. Ok so I did safe boot in 4.4.0-47-generic, go into root terminal purge nvidia, reboot, black screen, no nouvea.  Ok back out drop down into 4.4.0-45-generic and boot and Im in nouvea.

Now my question is this, what on earth is going on.?  I have been on Ubuntu for over ten years, my machine is not old and this all worked, the kernel updates are wiping it out in different ways now.

---

### Post by oldfred on 2016-11-21
How did you install nVidia drivers?
If you install the .run directly from nVidia you have to reinstall with dkms with every kernel update.
If from repository or from ppa, then it is automatically included in new kernel updates.

---

