---
title: "Unable to boot - no display"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by NoGumption on 2013-02-23
I'm trying to run Ubuntu 10.04 on an old desktop. I had a problem installing from the disk (it would read the disk, show the word "Ubuntu" and the loading dots, but then the monitor would shut off saying "No VGA source detected"). I got around that [here]("http://ubuntuforums.org/showthread.php?t=1965973"). Got Ubuntu installed but am still having the same problem, except no loading screen. I tried to go through [this]("http://ubuntuforums.org/showthread.php?t=1743535&highlight=black+screen+boot") to figure out and maybe fix my problem, but I got lost pretty quick.

I can get the GRUB menu to show up (sometimes) by pressing <shift>.

I can (sometimes) get the text startup by pressing <ctrl><alt><F1>.

From the text startup (shell?) I can do

```
sudo service gdm start
```

to get ubuntu to (seemingly?) go to the regular login screen. If it says it's already running I can press <ctrl><alt><F7> to swap to it. It isn't always running.

I don't really understand the instructions other than that.

I used the gdm command and am currently upgrading to 12.04 to see if that fixes it.

The Hardware Drivers application didn't find anything.

If the 12.04 upgrade doesn't fix this any suggestions? And if it does, any ideas what was wrong?

If possible I'd also like an explanation of what it is exactly I did to go around my problem.

Please and thank you for any information.

---

### Post by mapes12 on 2013-02-23
Boot from a live CD then in Terminal ```
lshw
``` and post the output back here.

---

### Post by Mark Phelps on 2013-02-23
> **NoGumption said:**
> I can get the GRUB menu to show up (sometimes) by pressing <shift>.
GRUB menu doesn't show up by default unless you have more than one OS installed.  Pressing the SHIFT key is how you FORCE the menu to be displayed.  This is normal behaviour.

> I can (sometimes) get the text startup by pressing <ctrl><alt><F1>.The default is to boot into a desktop.  The key combination is how your FORCE it into booting into a command line interface (CLI).  This is normal behaviour.

> From the text startup (shell?) I can do

```
sudo service gdm start
```

to get ubuntu to (seemingly?) go to the regular login screen. Again - normal behaviour.

> I don't really understand the instructions other than that. You really don't need to be booting into a CLI unless you have some specific reason for doing that.  You can do what you need from the desktop.

> I used the gdm command and am currently upgrading to 12.04 to see if that fixes it.Sorry ... fixes what? Unless I missed something, everything you've told us so far is normal behaviour.

> The Hardware Drivers application didn't find anything. Again -- normal behaviour in the situation where you don't have hardware that requires special drivers.

> If the 12.04 upgrade doesn't fix this any suggestions? And if it does, any ideas what was wrong?Nothing appears to be wrong -- you just don't know how things are supposed to work.

---

### Post by mapes12 on 2013-02-23
Installing from an **Alternate CD** may also be worth a try. I had an old machine a while ago that wouldn't install from the live CD but installed OK with the alternate CD.

---

### Post by NoGumption on 2013-02-23
Sorry, I guess I wasn't very clear. The problem is the computer starts to boot, but before it gets to where I can do anything with Ubuntu the display shuts off. The monitor displays a message that says "VGA No Signal" for a few seconds, then shuts off.

If I press <ctrl><alt><F1> the CLI shows up, I enter my login and password through that, start the gdm and can continue as normal. I don't want to need to do that, I want the computer to turn on and start-up normal by itself.

I just restarted the computer for the 12.04 upgrade, display still shuts off. It is slightly different now though. First the monitor displays "OUT OF RANGE", then the Ubuntu with the five dots beneath it loading screen appears, then the monitor displays "VGA No Signal" and goes into standby. If I press <ctrl><alt><F1>, login, and start the gdm now; it goes to a broken version of that Ubuntu loading screen. The top about 1/4 of the screen is black, the word Ubuntu with the five dots is in the lower right corner, and the dots are frozen.

I am also unable to get the GRUB menu to show up now.

~~~~~~~~~~~~~~~

I was unable to boot from the live CD before. I had to do some [nomodeset thing]("http://ubuntuforums.org/showthread.php?t=1965973") and from there I just went straight to install. I'll try doing that again but tell it to boot Ubuntu from the disk this time.

---

### Post by NoGumption on 2013-02-23
lshw

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1015MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          size: 3GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82875P/E7210 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:d2000000-d3ffffff(prefetchable)
        *-pci:0
             description: PCI bridge
             product: 82875P/E7210 Processor to PCI to CSA Bridge
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:2000(size=4096) memory:d0100000-d01fffff memory:40000000-400fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 82547GI Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 00
                serial: 00:11:25:ac:4e:99
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI firmware=N/A ip=192.168.137.152 latency=0 mingnt=255 multicast=yes
                resources: irq:18 memory:d0120000-d013ffff memory:d0100000-d011ffff ioport:2000(size=32) memory:40000000-4001ffff(prefetchable)
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82875P/E7210 Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-pci:1
             description: PCI bridge
             product: 6300ESB 64-bit PCI-X Bridge
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
        *-usb:0
             description: USB Controller
             product: 6300ESB USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1400(size=32)
        *-usb:1
             description: USB Controller
             product: 6300ESB USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1420(size=32)
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 6300ESB Watchdog Timer
             vendor: Intel Corporation
             physical id: 1d.4
             bus info: pci@0000:00:1d.4
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d0000000-d000000f
        *-generic:2 UNCLAIMED
             description: PIC
             product: 6300ESB I/O Advanced Programmable Interrupt Controller
             vendor: Intel Corporation
             physical id: 1d.5
             bus info: pci@0000:00:1d.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-usb:2
             description: USB Controller
             product: 6300ESB USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d0000400-d00007ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: memory:d0200000-d02fffff memory:e0000000-efffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon RV100 QY [Radeon 7000/VE]
                vendor: ATI Technologies Inc
                physical id: 2
                bus info: pci@0000:04:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=66 mingnt=8
                resources: memory:e0000000-efffffff(prefetchable) ioport:3000(size=256) memory:d0200000-d020ffff memory:d0220000-d023ffff(prefetchable)
        *-isa
             description: ISA bridge
             product: 6300ESB LPC Interface Controller
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
             product: 6300ESB SATA Storage Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1470(size=16)
           *-cdrom
                description: SCSI CD-ROM
                product: CD-ROM SC-148A
                vendor: SAMSUNG
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: B403
                capabilities: removable audio
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 6300ESB SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1440(size=32)
ubuntu@ubuntu:~$ 


```

---

### Post by NoGumption on 2013-02-24
Just tried [Boot-Repair]("http://ubuntuforums.org/showthread.php?t=1769482&highlight=unable+boot"). I only did the recommended repair - it didn't fix my problem, the report is attached. If there's a more advanced something I should try, let me know. It also said to install pastebinit package. I tried sudo apt-get install pastebinit but got this:

```
ubuntu@ubuntu:~$ sudo apt-get install pastebinit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pastebinit is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package pastebinit has no installation candidate
ubuntu@ubuntu:~$ 
```

---

### Post by NoGumption on 2013-02-24
I can sometimes boot by pressing a button during the startup screen. The screen changes and starts as the CLI, but continues to the normal login screen after everything starts.

Anything on that?

Also, I still can't get the GRUB menu to show up. When I try pressing shift as Ubuntu starts up my monitor displays "OUT OF RANGE" until a few seconds after I stop pressing shift. I haven't tested how long, but as long as I keep repeatedly pressing shift the message stays displayed. I'm guessing this is something to do with the resolution it's trying to display in? Is this more likely a separate problem or part of the original? If separate, how do I fix this?

---

