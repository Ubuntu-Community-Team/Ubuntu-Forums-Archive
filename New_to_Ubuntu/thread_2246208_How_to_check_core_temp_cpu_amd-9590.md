---
title: "How to check core temp cpu amd-9590"
date: 2014-09-29
forum: New to Ubuntu
---

### Post by ivan54 on 2014-09-29
```
# sensors-detect revision 6170 (2013-05-20 21:25:22 +0200)
# System: MSI MS-7640 [3.0]
# Board: MSI 990FXA-GD65 (MS-7640)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           Success!
    (driver `k10temp')
AMD Family 15h power sensors...                             Success!
    (driver `fam15h_power')
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found `Fintek F71889A Super IO Sensors'                     Success!
    (address 0x480, driver `f71882fg')

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): Using driver  `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc  SB600/SB700/SB800 SMBus
Module i2c-dev loaded successfully.

Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-0)
Do you want to scan it? (yes/NO/selectively): Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: SMBus PIIX4 adapter at 0b20 (i2c-1)
Do you want to scan it? (yes/NO/selectively): 
Next adapter: NVIDIA i2c adapter 0 at 1:00.0 (i2c-2)
Do you want to scan it? (yes/NO/selectively): 
Next adapter: NVIDIA i2c adapter 1 at 1:00.0 (i2c-3)
Do you want to scan it? (yes/NO/selectively): 
Next adapter: NVIDIA i2c adapter 2 at 1:00.0 (i2c-4)
Do you want to scan it? (yes/NO/selectively): 
Next adapter: NVIDIA i2c adapter 6 at 1:00.0 (i2c-5)
Do you want to scan it? (yes/NO/selectively): Client found at address 0x4a
Probing for `National Semiconductor LM75'...                No
Probing for `National Semiconductor LM75A'...               No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7410/ADT7420'...             No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Maxim MAX6642'...                              No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `NXP/Philips SA56004'...                        No
Client found at address 0x4b
Probing for `National Semiconductor LM75'...                No
Probing for `National Semiconductor LM75A'...               No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7410/ADT7420'...             No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Maxim MAX6642'...                              No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `NXP/Philips SA56004'...                        No
Probing for `Analog Devices ADT7481'...                     No

Next adapter: NVIDIA i2c adapter 7 at 1:00.0 (i2c-6)
Do you want to scan it? (yes/NO/selectively): 
Next adapter: NVIDIA i2c adapter 8 at 1:00.0 (i2c-7)
Do you want to scan it? (yes/NO/selectively): 
Next adapter: NVIDIA i2c adapter 11 at 1:00.0 (i2c-8)
Do you want to scan it? (yes/NO/selectively): Adapter cannot be probed, skipping.
Now follows a summary of the probes I have just done.
Just press ENTER to continue: 
Driver `k10temp' (autoloaded):
  * Chip `AMD Family 15h thermal sensors' (confidence: 9)

Driver `fam15h_power' (autoloaded):
  * Chip `AMD Family 15h power sensors' (confidence: 9)

Driver `f71882fg':
  * ISA bus, address 0x480
    Chip `Fintek F71889A Super IO Sensors' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
f71882fg
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service kmod start'
to load them.

Unloading i2c-dev... OK
Unloading cpuid... OK

```

and after that i type sensors

```
koiv@koiv:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +5.8°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +87.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       77.56 W  (crit = 219.76 W)

f71889a-isa-0480
Adapter: ISA adapter
+3.3V:        +3.30 V  
in1:          +1.11 V  (max =  +2.04 V)
in2:          +1.50 V  
in3:          +0.95 V  
in4:          +1.08 V  
in5:          +1.09 V  
in6:          +1.14 V  
3VSB:         +3.31 V  
Vbat:         +3.28 V  
fan1:        2400 RPM
fan2:           0 RPM  ALARM
fan3:        1236 RPM
temp1:        +36.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp2:        +46.0°C  (high = +85.0°C, hyst = +79.0°C)
                       (crit = +107.0°C, hyst = +101.0°C)  sensor = thermistor
temp3:        +32.0°C  (high = +70.0°C, hyst = +68.0°C)
                       (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor
```

how to know cpu core temp?
It should display something like:
>  coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +46.0C  (high = +76.0C, crit = +100.0C)

 coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +44.0C  (high = +76.0C, crit = +100.0C)

 … 

System Hardware:
Processor: AMD FX-9590 Eight-Core @ 4.70GHz (8 Cores), Motherboard: MSI  990FXA-GD65 (MS-7640) v3.0, Chipset: AMD RD890 bridge, Memory: 16384MB,  Disk: 128GB Corsair Force GS + 2000GB Western Digital WD20EZRX-00D,  Graphics: MSI NVIDIA GeForce GTX 760 2048MB (540/3004MHz), Audio:  Realtek ALC892, Monitor: LG E2250, Network: Realtek RTL8111/8168/8411

Software:
OS: Ubuntu 14.04, Kernel: 3.13.0-36-generic (x86_64), Desktop: Unity  7.2.2, Display Server: X Server 1.15.1, Display Driver: NVIDIA 331.38,  Compiler: GCC 4.8.2, File-System: ext4, Screen Resolution: 1920x1080

---

### Post by redrumrogue on 2014-09-29
Hi there!  This might help you ...

[http://blog.felipe.lessa.nom.br/?p=93](http://blog.felipe.lessa.nom.br/?p=93)

---

### Post by redrumrogue on 2014-09-29
You may also find the psensor package useful as you can plot temperature graphs over time and customize the names of the sensors in the psensor preferences.```
sudo apt-get install psensor
```

---

### Post by Mike_Walsh on 2014-09-29
I'll back redrumrogue up on that.

And if you **want**, you can go one further than that, and install the current 'beta' version of pSensor; it has a number of 'experimental' features in it, mainly displaying selected temperatures alongside the indicator in the top menu bar:-

 [http://www.webupd8.org/2014/06/psensor-updated-with-option-to-display.html](http://www.webupd8.org/2014/06/psensor-updated-with-option-to-display.html)

The ppa name might put you off, as it's called 'psensor-unstable'; but I have been using this for quite a few months now, and it's actually **very **stable.

The version in the Software Centre is the previous version to this, and doesn't have the 'experimental' feature; but I've used the 'beta', as that was the feature I especially wanted. You have a continuous readout of what your CPU's doing.....including load, too.

It's a useful package. The only slight glitch is that just occasionally, it won't auto-start, and you'll need to manually start it from the Dash; but I guess you're looking at maybe one fail in 30 starts.....I can live with that! (You DO need to set it up for 'auto-start' in Preferences.)


Regards,

Mike.

---

### Post by ivan54 on 2014-09-29
no i use psensor too but i want to get like this information

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +51.0°C  (high = +74.0°C, crit = +100.0°C)
Core 1:       +46.0°C  (high = +74.0°C, crit = +100.0°C)
Core 2:       +45.0°C  (high = +74.0°C, crit = +100.0°C)
Core 3:       +48.0°C  (high = +74.0°C, crit = +100.0°C)

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +47.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +95.0°C, hyst =  +2.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

```

now i get this information :

```
k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +8.4°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +87.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       58.01 W  (crit = 219.76 W)

f71889a-isa-0480
Adapter: ISA adapter
+3.3V:        +3.30 V  
in1:          +0.92 V  (max =  +2.04 V)
in2:          +1.50 V  
in3:          +0.95 V  
in4:          +1.08 V  
in5:          +1.09 V  
in6:          +1.14 V  
3VSB:         +3.33 V  
Vbat:         +3.28 V  
fan1:        2400 RPM
fan2:           0 RPM  ALARM
fan3:        1242 RPM
temp1:        +34.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp2:        +42.0°C  (high = +85.0°C, hyst = +79.0°C)
                       (crit = +107.0°C, hyst = +101.0°C)  sensor = thermistor
temp3:        +29.0°C  (high = +70.0°C, hyst = +68.0°C)
                       (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor
```

---

### Post by redrumrogue on 2014-09-29
In that case my first reply on this thread might help you.. beyond that i do not know.

---

### Post by ivan54 on 2014-09-29
> **redrumrogue said:**
> In that case my first reply on this thread might help you.. beyond that i do not know.

thx a lot for very fast respond and plz check on this :
[http://ubuntuforums.org/showthread.php?t=2208165&page=2&p=13131932#post13131932 ]("http://ubuntuforums.org/showthread.php?t=2208165&page=2&p=13131932#post13131932")

> thx a lot, sorry for my bad english still work on it :D 

---

### Post by deadflowr on 2014-09-29
From where do outputs one and two from post #5 come from?
Same machine?
Same OS version(example Ubuntu 14.04 for each, or a different os version for each)?

It seems you have differing modules loaded on each.

It is also unclear, cause you didn't mention it, but you did run **sudo service kmod restart**, right?
I think you did, but every little thing to know helps.

---

### Post by ivan54 on 2014-09-29
> **deadflowr said:**
> From where do outputs one and two from post #5 come from?
Same machine?
Same OS version(example Ubuntu 14.04 for each, or a different os version for each)?

It seems you have differing modules loaded on each.

It is also unclear, cause you didn't mention it, but you did run **sudo service kmod restart**, right?
I think you did, but every little thing to know helps.

different machine, same os (ubuntu 14.04 64-bit)

this one run on : 
> ```
koko@rumah:~$ sudo !!
sudo lshw -short
[sudo] password for koko: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
H/W path         Device      Class       Description
====================================================
                             system      EP45-UD3P ()
/0                           bus         EP45-UD3P
/0/0                         memory      128KiB BIOS
/0/4                         processor   Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
/0/4/a                       memory      64KiB L1 cache
/0/4/b                       memory      2MiB L2 cache
/0/19                        memory      4GiB System Memory
/0/19/0                      memory      2GiB DIMM 800 MHz (1.2 ns)
/0/19/1                      memory      DIMM [empty]
/0/19/2                      memory      2GiB DIMM 800 MHz (1.2 ns)
/0/19/3                      memory      DIMM [empty]
/0/100                       bridge      4 Series Chipset DRAM Controller
/0/100/1                     bridge      4 Series Chipset PCI Express Root Port
/0/100/1/0                   display     G92 [GeForce 9800 GTX+]
/0/100/1a                    bus         82801JI (ICH10 Family) USB UHCI Controller #4
/0/100/1a.1                  bus         82801JI (ICH10 Family) USB UHCI Controller #5
/0/100/1a.2                  bus         82801JI (ICH10 Family) USB UHCI Controller #6
/0/100/1a.7                  bus         82801JI (ICH10 Family) USB2 EHCI Controller #2
/0/100/1b                    multimedia  82801JI (ICH10 Family) HD Audio Controller
/0/100/1c                    bridge      82801JI (ICH10 Family) PCI Express Root Port 1
/0/100/1c.3                  bridge      82801JI (ICH10 Family) PCI Express Root Port 4
/0/100/1c.3/0                storage     JMB363 SATA/IDE Controller
/0/100/1c.3/0.1              storage     JMB363 SATA/IDE Controller
/0/100/1c.4                  bridge      82801JI (ICH10 Family) PCI Express Root Port 5
/0/100/1c.4/0    eth0        network     RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/1c.5                  bridge      82801JI (ICH10 Family) PCI Express Root Port 6
/0/100/1c.5/0    eth1        network     RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/1d                    bus         82801JI (ICH10 Family) USB UHCI Controller #1
/0/100/1d.1                  bus         82801JI (ICH10 Family) USB UHCI Controller #2
/0/100/1d.2                  bus         82801JI (ICH10 Family) USB UHCI Controller #3
/0/100/1d.7                  bus         82801JI (ICH10 Family) USB2 EHCI Controller #1
/0/100/1e                    bridge      82801 PCI Bridge
/0/100/1e/7                  bus         TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
/0/100/1f                    bridge      82801JIR (ICH10R) LPC Interface Controller
/0/100/1f.2                  storage     82801JI (ICH10 Family) 4 port SATA IDE Controller #1
/0/100/1f.3                  bus         82801JI (ICH10 Family) SMBus Controller
/0/100/1f.5                  storage     82801JI (ICH10 Family) 2 port SATA IDE Controller #2
/0/1             scsi0       storage     
/0/1/0.0.0       /dev/sda    disk        500GB ST3500413AS
/0/1/0.0.0/1     /dev/sda1   volume      243MiB Linux filesystem partition
/0/1/0.0.0/2     /dev/sda2   volume      465GiB Extended partition
/0/1/0.0.0/2/5   /dev/sda5   volume      465GiB Linux LVM Physical Volume partition
/0/1/0.1.0       /dev/cdrom  disk        iHAS122   8
/0/2             scsi2       storage     
/0/2/0.0.0       /dev/sdb    disk        320GB WDC WD3200AAJS-0
/0/2/0.0.0/1     /dev/sdb1   volume      298GiB EXT4 volume

```



```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +51.0°C  (high = +74.0°C, crit = +100.0°C)
Core 1:       +46.0°C  (high = +74.0°C, crit = +100.0°C)
Core 2:       +44.0°C  (high = +74.0°C, crit = +100.0°C)
Core 3:       +48.0°C  (high = +74.0°C, crit = +100.0°C)

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +47.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +95.0°C, hyst =  +2.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

```

this run on :
> ```
koiv@koiv:~$ sudo lshw -short
[sudo] password for koiv: 
H/W path        Device      Class       Description
===================================================
                            system      MS-7640 (To be filled by O.E.M.)
/0                          bus         990FXA-GD65 (MS-7640)
/0/0                        memory      64KiB BIOS
/0/4                        processor   AMD FX(tm)-9590 Eight-Core Processor
/0/4/5                      memory      384KiB L1 cache
/0/4/6                      memory      8MiB L2 cache
/0/4/7                      memory      8MiB L3 cache
/0/26                       memory      16GiB System Memory
/0/26/0                     memory      8GiB DIMM DDR3 Synchronous 800 MHz (1,2 ns)
/0/26/1                     memory      DIMM Synchronous [empty]
/0/26/2                     memory      8GiB DIMM DDR3 Synchronous 800 MHz (1,2 ns)
/0/26/3                     memory      DIMM Synchronous [empty]
/0/100                      bridge      RD890 PCI to PCI bridge (external gfx0 port B)
/0/100/0.2                  generic     RD990 I/O Memory Management Unit (IOMMU)
/0/100/2                    bridge      RD890 PCI to PCI bridge (PCI express gpp port B)
/0/100/2/0                  display     GK104 [GeForce GTX 760]
/0/100/2/0.1                multimedia  GK104 HDMI Audio Controller
/0/100/5                    bridge      RD890 PCI to PCI bridge (PCI express gpp port E)
/0/100/5/0      eth0        network     RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/7                    bridge      RD890 PCI to PCI bridge (PCI express gpp port G)
/0/100/7/0                  bus         uPD720200 USB 3.0 Host Controller
/0/100/11                   storage     SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
/0/100/12                   bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/12.2                 bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/13                   bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/13.2                 bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/14                   bus         SBx00 SMBus Controller
/0/100/14.2                 multimedia  SBx00 Azalia (Intel HDA)
/0/100/14.3                 bridge      SB7x0/SB8x0/SB9x0 LPC host controller
/0/100/14.4                 bridge      SBx00 PCI to PCI Bridge
/0/100/14.5                 bus         SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
/0/100/16                   bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/16.2                 bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/101                      bridge      Family 15h Processor Function 0
/0/102                      bridge      Family 15h Processor Function 1
/0/103                      bridge      Family 15h Processor Function 2
/0/104                      bridge      Family 15h Processor Function 3
/0/105                      bridge      Family 15h Processor Function 4
/0/106                      bridge      Family 15h Processor Function 5
/0/1            scsi0       storage     
/0/1/0.0.0      /dev/sda    disk        128GB Corsair Force GS
/0/1/0.0.0/1    /dev/sda1   volume      100MiB Windows NTFS volume
/0/1/0.0.0/2    /dev/sda2   volume      80GiB Windows NTFS volume
/0/2            scsi1       storage     
/0/2/0.0.0      /dev/sdb    disk        2TB WDC WD20EZRX-00D
/0/2/0.0.0/1    /dev/sdb1   volume      886GiB Windows NTFS volume
/0/2/0.0.0/2    /dev/sdb2   volume      488GiB Windows NTFS volume
/0/2/0.0.0/3    /dev/sdb3   volume      292GiB Windows NTFS volume
/0/2/0.0.0/4    /dev/sdb4   volume      195GiB Extended partition
/0/2/0.0.0/4/5  /dev/sdb5   volume      192GiB Linux filesystem partition
/0/2/0.0.0/4/6  /dev/sdb6   volume      2860MiB Linux swap / Solaris partition
/0/3            scsi2       storage     
/0/3/0.0.0      /dev/cdrom  disk        DVDRAM GH24NSB0
```



```
koiv@koiv:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +14.8°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +87.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:      109.67 W  (crit = 219.76 W)

f71889a-isa-0480
Adapter: ISA adapter
+3.3V:        +3.31 V  
in1:          +0.92 V  (max =  +2.04 V)
in2:          +1.50 V  
in3:          +0.95 V  
in4:          +1.08 V  
in5:          +1.09 V  
in6:          +1.14 V  
3VSB:         +3.33 V  
Vbat:         +3.28 V  
fan1:        2392 RPM
fan2:           0 RPM  ALARM
fan3:        1228 RPM
temp1:        +35.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp2:        +42.0°C  (high = +85.0°C, hyst = +79.0°C)
                       (crit = +107.0°C, hyst = +101.0°C)  sensor = thermistor
temp3:        +29.0°C  (high = +70.0°C, hyst = +68.0°C)
                       (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor
```

i did **sudo service kmod restart **and still nothing happen

---

### Post by ivan54 on 2014-09-29
and i want asking this one : 

```
Phoronix Test Suite v5.2.1
Interactive Benchmarking

System Hardware:
Processor: AMD FX-9590 Eight-Core @ 4.70GHz (8 Cores), Motherboard: MSI  990FXA-GD65 (MS-7640) v3.0, Chipset: AMD RD890 bridge, Memory: 16384MB,  Disk: 128GB Corsair Force GS + 2000GB Western Digital WD20EZRX-00D,  Graphics: MSI NVIDIA GeForce GTX 760 2048MB (1019/3004MHz), Audio:  Realtek ALC892, Monitor: LG E2250, Network: Realtek RTL8111/8168/8411



1: Run A Test
2: Run A Suite [A Collection Of Tests]
3: Run Complex System Test
4: Show System Hardware / Software Information
5: Show Auto-Detected System Sensors
6: Set Test Run Repetition
7: Backup Results To Media Storage
8: Exit
Select Task: 4

System Software / Hardware Information

Hardware:
Processor: AMD FX-9590 Eight-Core @ 4.70GHz (8 Cores), Motherboard: MSI  990FXA-GD65 (MS-7640) v3.0, Chipset: AMD RD890 bridge, Memory: 16384MB,  Disk: 128GB Corsair Force GS + 2000GB Western Digital WD20EZRX-00D,  Graphics: MSI NVIDIA GeForce GTX 760 2048MB (1019/3004MHz), Audio:  Realtek ALC892, Monitor: LG E2250, Network: Realtek RTL8111/8168/8411

Software:
OS: Ubuntu 14.04, Kernel: 3.13.0-36-generic (x86_64), Desktop: Unity  7.2.2, Display Server: X Server 1.15.1, Display Driver: NVIDIA 331.38,  OpenGL: 4.3.0, Compiler: GCC 4.8.2, File-System: ext4, Screen  Resolution: 1920x1080




1: Run A Test
2: Run A Suite [A Collection Of Tests]
3: Run Complex System Test
4: Show System Hardware / Software Information
5: Show Auto-Detected System Sensors
6: Set Test Run Repetition
7: Backup Results To Media Storage
8: Exit
Select Task: 5

Detected System Sensors

CPU Fan Speed: 2392 RPM
CPU Frequency: 1400.00 Megahertz
CPU Power Consumption: 86.22 Watts
CPU Temperature: 4.63 Celsius
CPU Usage: 2.02 Percent
GPU Fan Speed: 34 Percent
GPU Frequency: 1019 Megahertz
GPU Temperature: 34 Celsius
GPU Usage: 1 Percent
Drive Read Speed: 0.00 MB/s
Drive Write Speed: 0.00 MB/s
Memory Usage: 2155 Megabytes
Network Usage: 0 Kilobytes/second
Swap Usage: 0 Megabytes
System Fan Speed: 1238 RPMs
System Iowait: 0.00 Percent
System Temperature: 29.00 Celsius
System V3 Voltage: 3.30 Volts

```

CPU Temperature: 4.63 Celsius << but if i use "sensors && inxi -s" cpu: 35.0C 

what real CPU temp?

```
koiv@koiv:~$ sensors && inxi -s
k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +7.2°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +87.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       81.88 W  (crit = 219.76 W)

f71889a-isa-0480
Adapter: ISA adapter
+3.3V:        +3.30 V  
in1:          +1.42 V  (max =  +2.04 V)
in2:          +1.50 V  
in3:          +0.95 V  
in4:          +1.08 V  
in5:          +1.09 V  
in6:          +1.14 V  
3VSB:         +3.31 V  
Vbat:         +3.28 V  
fan1:        2400 RPM
fan2:           0 RPM  ALARM
fan3:        1230 RPM
temp1:        +35.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp2:        +42.0°C  (high = +85.0°C, hyst = +79.0°C)
                       (crit = +107.0°C, hyst = +101.0°C)  sensor = thermistor
temp3:        +29.0°C  (high = +70.0°C, hyst = +68.0°C)
                       (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor

Sensors:   System Temperatures: cpu: 35.0C mobo: 42.0C gpu: 29C 
           Fan Speeds (in rpm): cpu: 2400 fan-2: 0 fan-3: 1230 
```

> sorry for my bad english, still work on it :grin:

---

### Post by QIII on 2014-09-29
Hello!

You are clearly looking at two different machines: one is and Intel machine and the other your specified AMD machine.

k10temp is your AMD CPU on the AMD machine.  k10temp does not give temps by core, but only the CPU temp.  Added to that, the k10temp does not give an actual temperature, but an arbitrary value in degrees that AMD defines as some sort of relative value used to drive the fan speed versus the critical temperature of the CPU.

If you ask me, an AMD user, this is entirely asinine.  But it is what it is.  Clearly the value you are getting from k10temp is garbage in terms of actual, real-world temperature.

In your motherboard readings, temp1, temp2 or temp3, you are probably getting a CPU temperature reading indirectly.  You will have to research your motherboard to find out which is which.  But it looks like temp1 is giving you the CPU temp.  But it is still going to be that silly arbitrary AMD reading unless your mobo is reporting the temperature of the socket -- which will be cooler than the CPU itself.

In any case, the "by core" temperature you are seeing with your Intel CPU won't apply to the AMD CPU.

---

### Post by ivan54 on 2014-09-29
> **QIII said:**
> Hello!

You are clearly looking at two different machines: one is and Intel machine and the other your specified AMD machine.

k10temp is your AMD CPU on the AMD machine.  k10temp does not give temps by core, but only the CPU temp.  Added to that, the k10temp does not give an actual temperature, but an arbitrary value in degrees that AMD defines as some sort of relative value used to drive the fan speed versus the critical temperature of the CPU.

If you ask me, an AMD user, this is entirely asinine.  But it is what it is.  Clearly the value you are getting from k10temp is garbage in terms of actual, real-world temperature.

In your motherboard readings, temp1, temp2 or temp3, you are probably getting a CPU temperature reading indirectly.  You will have to research your motherboard to find out which is which.  But it looks like temp1 is giving you the CPU temp.  But it is still going to be that silly arbitrary AMD reading unless your mobo is reporting the temperature of the socket -- which will be cooler than the CPU itself.

In any case, the "by core" temperature you are seeing with your Intel CPU won't apply to the AMD CPU.

thx very helpful, anyway i want ask about this comparation value "if i use **Phoronix Test Suite v5.2.1 Interactive Benchmarking **CPU Temperature: 4.63 Celsius, but if i use **"sensors && inxi -s"** cpu: 35.0C", so what information *represent real* cpu temp?

i using corsair hydro series h100i

---

### Post by QIII on 2014-09-29
*Neither*, unfortunately.

As I said, AMD does not report an actual temperature, but an arbitrary number in degrees that controls the fan speed relative to the critical temperature of the CPU.  And they are notoriously inaccurate at idle doing even that.  

Here is the bad news from AMD's own documentation:

> 
  Tctl is the processor temperature control value, used by the platform to
  control cooling systems. Tctl is a non-physical temperature on an
  arbitrary scale measured in degrees. It does _not_ represent an actual
  physical temperature like die or case temperature. Instead, it specifies
  the processor temperature relative to the point at which the system must
  supply the maximum cooling for the processor's specified maximum case
  temperature and maximum thermal power dissipation.

Any software sensor depends on what is reported to it.  All it can give you is the inaccurate and arbitrary temperature reported by the CPU.  So neither the Phoronix test suite not sensors can give you a "real temperature."

If your motherboard reports an actual physical temperature of the socket (which you will have to research), you might take a guess that the CPU is 5 to 10 degrees hotter than the socket.  That's not a sure thing, though.

With an AMD CPU, the only way to know the actual physical temperature for sure is with a temperature probe of some sort on the CPU (you can only get to the edge, since the HSF will be on the face).  That may be a physical probe or a laser probe.

For my purposes, I have a script that takes k10temp and adds 10 degrees to display in my conky and I also display the motherboard's reported k10temp value.  But my k10temp is somewhat more reasonable.

Your temp of 7-something degrees is definitely useless (even with your liquid cooling solution the lowest temperature you could possibly ever achieve is the ambient temperature -- which won't happen), so you may have to go with the motherboard's reading from (it looks like) temp1.  But you will have to find out if that is the temp the mobo is getting from the on-die thermistor or from its own sensor on the socket.

---

### Post by ivan54 on 2014-09-29
> **QIII said:**
> *Neither*, unfortunately.

As I said, AMD does not report an actual temperature, but an arbitrary number in degrees that controls the fan speed relative to the critical temperature of the CPU.  And they are notoriously inaccurate at idle doing even that.  

Here is the bad news from AMD's own documentation:


Any software sensor depends on what is reported to it.  All it can give you is the inaccurate and arbitrary temperature reported by the CPU.

If your motherboard reports an actual physical temperature of the socket (which you will have to research), you might take a guess that the CPU is 5 to 10 degrees hotter than the socket.  That's not a sure thing, though.

With an AMD CPU, the only way to know the actual physical temperature for sure is with a temperature probe of some sort on the CPU (you can only get to the edge, since the HSF will be on the face).  That may be a physical probe or a laser probe.

For my purposes, I have a script that takes k10temp and adds 10 degrees to display in my conky and I also display the motherboard's reported k10temp value.  But my k10temp is somewhat more reasonable.

Your temp of 7-something degrees is definitely useless, so you may have to go with the motherboard's reading from (it looks like) temp1.  But you will have to find out if that is the temp the mobo is getting from the on-die thermistor or from its own sensor on the socket.

oh okay that solved my problem, so that make Intel better than amd. 
thx for ur respond :D

---

### Post by QIII on 2014-09-29
No, that doesn't make AMD better or worse than Intel.  It only means that the temperature reading is not dependable.

Whether or not the CPU is better or worse depends on how you use it and its results in performance tests.

---

### Post by Mike_Walsh on 2014-09-30
This article from [www.overclockers.com]("http://www.overclockers.com") might also provide some illumination on the way that the data from the DTS (Digital Temperature Sensor) is used. It's from a review of the CoreTemp monitoring software from 2006, in the very early days of multi-core processors:-

[http://www.overclockers.com/measuring-cpu-dual-core-temps/](http://www.overclockers.com/measuring-cpu-dual-core-temps/)

In particular, this section discusses the different ways that both AMD and Intel implement the same set of data:-

> [COLOR=#333333][FONT=Arial]Both Intel and AMD use the DTS to determine overheating and protect the CPU from damage by either throttling or completely shutting the system down, depending on the threshold that the temperature has crossed.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]The DTS was first officially introduced in the Core Duo (Yonah) processor by Intel and it was carried on into the Core 2 Duo series. AMD officially introduced DTS with the release of Rev F chips &#8211; however after some testing, it became apparent that DTS was there since the first Athlon 64 chip![/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Intel also claims that their DTS is placed in the hottest part of the core, while AMD doesn&#8217;t say exactly where the DTS is placed, but I am certain it&#8217;s not one of the coolest parts.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]From a lot of testing, I have come to the conclusion that for an Intel CPU, the temperatures reported by the DTS make a lot of sense. Intel&#8217;s white papers say that their DTS is calibrated and ready to use when their chips leave the factory.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]In Rev F chips from AMD, the reported temperature also seems to be quite accurate, but from different reports and white papers I&#8217;ve seen, the CPU leaves the factory without having the DTS properly calibrated. AMD claims it could have an accuracy range of ±14ºC. The only thing I&#8217;ve noticed is some older AMD CPUs either have a very large delta between two cores or sometimes give some really low temperature readings. I guess this is understandable as this feature was unofficial in those CPUs.[/FONT][/COLOR]



This article is about dual-core processors in particular, but I would hazard a guess that the implementation is like as not the same on all modern CPUs.

Food for thought?

Regards,

Mike.

---

### Post by ivan54 on 2014-10-01
i check temp using corsair link application in windows 7, thx for information really helpful

Phoronix Test Suite v5.2.1  Interactive Benchmarking    System Hardware have same value with corsair app on win7


thx all

---

