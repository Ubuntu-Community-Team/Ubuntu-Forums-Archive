---
title: "System lockups"
date: 2014-04-17
forum: New to Ubuntu
---

### Post by Larry_Klein on 2014-04-17
I have tried ubuntu,xubuntu,bodhi,lubuntu,LXLE,pclinuxos, and probably a few others with the same results - works great the first day and then the lockups begin and get worse until I give up and try something else. Booting in recovery and running the utilities don't help. I assume its a video card issue.

And as far as the hardware - Win XP runs flawlessly day in and day out.

HP Pavillion tower A264W
AMD Athlon XP 2800 processor
512 Ram
damaged onboard nvidia graphics
ATI Radeon 8500 AGP card

I love the linux and it seems to run faster than the XP. I don't have any linux installed right now, but would love to get it going again if anyone has any ideas.

---

### Post by Canterwood on 2014-04-17
Hello!

Can you describe exactly what happens during those lockups?

Is it possible for you to disable the onboard graphics card in the BIOS?

What would lead you to assume the (damaged) onboard graphics card is at fault? Is it detected by your OS? And what drivers are you using for it, if at all?

This info will help me and others determine what the problem is.

---

### Post by Warren Hill on 2014-04-17
Open a terminal and enter the following command

```
sudo lshw -C display
```

Post the output may give us a clue if graphics are the issue.

---

### Post by Larry_Klein on 2014-04-17
The lockups happen randomly and are total - no response from the keyboard or mouse. No hard drive cd or flash drive action.

The bios has two options, onboard and PCI - it is set to PCI (even though it is a agp card.)

I have no idea if the fried onboard graphics is causing the problem or if it is the card, or neither. Could the os be making calls to the onboard?

The os shows only the Radeon card.

---

### Post by Larry_Klein on 2014-04-17
I will need to install lubuntu to get you that info.

---

### Post by buzzingrobot on 2014-04-17
> **Larry_Klein said:**
> I will need to install lubuntu to get you that info.

For access to lshw?

If it isn't available, just install it:  "sudo apt-get install lshw" in a terminal.

---

### Post by Larry_Klein on 2014-04-17
> **Warren Hill said:**
> Open a terminal and enter the following command

```
sudo lshw -C display
```

Post the output may give us a clue if graphics are the issue.

lubuntu@lubuntu:~$ sudo lshw -C display
  *-display              
       description: VGA compatible controller
       product: R200 [Radeon 8500/8500 LE]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64 mingnt=8
       resources: irq:16 memory:e8000000-efffffff ioport:d800(size=256) memory:fda00000-fda0ffff memory:fd900000-fd91ffff


Again - I am not smart enough to be sure this a video issue, could be something else, but the most common cause I have found for hard freezes in these forums is ATI cards.

---

### Post by mörgæs on 2014-04-17
Have you tried running **memtest** from the boot menu?

---

### Post by Larry_Klein on 2014-04-17
> **mörgæs said:**
> Have you tried running **memtest** from the boot menu?

yes, i don't see problems.

---

### Post by Larry_Klein on 2014-04-17
> **Larry_Klein said:**
> The lockups happen randomly and are total - no response from the keyboard or mouse. No hard drive cd or flash drive action.

The bios has two options, onboard and PCI - it is set to PCI (even though it is a agp card.)

I have no idea if the fried onboard graphics is causing the problem or if it is the card, or neither. Could the os be making calls to the onboard?

The os shows only the Radeon card.

Full system info

H/W path        Device      Class          Description
======================================================
                            system         DK394A-ABA a264w
/0                          bus            A7N8X-LA
/0/0                        memory         64KiB BIOS
/0/4                        processor      AMD Athlon(tm) XP  2800+
/0/4/5                      memory         128KiB L1 cache
/0/4/6                      memory         512KiB L2 cache
/0/27                       memory         512MiB System Memory
/0/27/0                     memory         256MiB DIMM 100 MHz (10.0 ns)
/0/27/1                     memory         256MiB DIMM 100 MHz (10.0 ns)
/0/100                      bridge         nForce2 IGP2
/0/100/0.1                  memory         RAM memory
/0/100/0.2                  memory         RAM memory
/0/100/0.3                  memory         RAM memory
/0/100/0.4                  memory         RAM memory
/0/100/0.5                  memory         RAM memory
/0/100/1                    bridge         nForce2 ISA Bridge
/0/100/1.1                  bus            nForce2 SMBus (MCP)
/0/100/2                    bus            nForce2 USB Controller
/0/100/2.1                  bus            nForce2 USB Controller
/0/100/2.2                  bus            nForce2 USB Controller
/0/100/4        eth0        network        nForce2 Ethernet Controller
/0/100/6                    multimedia     nForce2 AC97 Audio Controler (MCP)
/0/100/8                    bridge         nForce2 External PCI Bridge
/0/100/8/7                  communication  LT WinModem
/0/100/9                    storage        nForce2 IDE
/0/100/d                    bus            nForce2 FireWire (IEEE 1394) Controll
/0/100/1e                   bridge         nForce2 AGP
/0/100/1e/0                 display        R200 [Radeon 8500/8500 LE]
/0/1            scsi0       storage       
/0/1/0.0.0      /dev/sda    disk           80GB ST380022A
/0/1/0.0.0/1    /dev/sda1   volume         74GiB Windows NTFS volume
/0/1/0.0.0/2    /dev/sda2   volume         510MiB Extended partition
/0/1/0.0.0/2/5  /dev/sda5   volume         510MiB Linux swap / Solaris partition
/0/2            scsi1       storage        
/0/2/0.0.0      /dev/cdrom  disk           DVD Writer 300n
/0/2/0.1.0      /dev/sr1    disk           CW038D CD-R/RW
/0/2/0.1.0/0    /dev/sr1    disk          
/0/2/0.1.0/0/1              volume         695MiB Hidden HPFS/NTFS partition
/0/3            scsi2       storage       
/0/3/0.0.0      /dev/sdb    disk           SCSI Disk
/0/3/0.0.1      /dev/sdc    disk           SCSI Disk
/0/3/0.0.2      /dev/sdd    disk           SCSI Disk
/0/3/0.0.3      /dev/sde    disk           SCSI Disk
/0/5            scsi5       storage

---

### Post by ibjsb4 on 2014-04-17
It seems you do have video support.

[http://wiki.cchtml.com/index.php/Hardware#Radeon_Legacy_.28Open_Source.29](http://wiki.cchtml.com/index.php/Hardware#Radeon_Legacy_.28Open_Source.29)

[http://manpages.ubuntu.com/manpages/saucy/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/saucy/man4/radeon.4.html)

---

