---
title: "Why is AUX-TEMP so high? How can i get the correct Temperature Values?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by jhulf on 2008-04-26
Hi there,

i am new to the PeeCee World aswell as to the Linux World. I am coming from the Apple Side of Life, where it never was nessecary to mess with Hardware Temperatures, Bios or Firmware Stuff.

Now that i am with Ubuntu, i really like what i see, and i found everything to be very usefull so far.

One thing though makes me a bit nervous. I installed 'lm-sensors' and ran 'sensors-detect' in the Terminal. 
The Output looks like this:

```
# sensors-detect revision 4609 (2007-07-14 09:28:39 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): yes
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel ICH9

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): yes
Module loaded successfully.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): yes
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x2e
Probing for `Myson MTP008'...                               No
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM78-J'...              No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM85 or LM96000'...     No
Probing for `Analog Devices ADM1027, ADT7460 or ADT7463'... No
Probing for `SMSC EMC6D100, EMC6D101 or EMC6D102'...        No
Probing for `Analog Devices ADT7462'...                     No
Probing for `Analog Devices ADT7467 or ADT7468'...          No
Probing for `Analog Devices ADT7470'...                     No
Probing for `Analog Devices ADT7473'...                     Success!
    (confidence 5, driver `to-be-written')
Probing for `Analog Devices ADT7475'...                     No
Probing for `Analog Devices ADT7476'...                     No
Probing for `Andigilog aSC7611'...                          No
Probing for `Andigilog aSC7621'...                          No
Probing for `National Semiconductor LM87'...                No
Probing for `National Semiconductor LM93'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Winbond W83791SD'...                           No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG'...                          No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L785TS-S'...                        No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1026'...                     No
Probing for `Analog Devices ADM1025'...                     No
Probing for `Analog Devices ADM1024'...                     No
Probing for `Analog Devices ADM1029'...                     No
Probing for `Analog Devices ADM1030'...                     No
Probing for `Analog Devices ADM1031'...                     No
Probing for `Analog Devices ADM1022'...                     No
Probing for `Texas Instruments THMC50'...                   No
Probing for `Analog Devices ADM1028'...                     No
Probing for `ITE IT8712F'...                                No
Probing for `SMSC DME1737'...                               No
Probing for `Fintek F75373S/SG'...                          No
Probing for `Fintek F75375S/SP'...                          No
Probing for `Fintek F75387SG/RG'...                         No
Probing for `Winbond W83791D'...                            No

Next adapter: SMBus I801 adapter at 0400 (i2c-3)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x44
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Next adapter: ISA main adapter (i2c-9191)
Do you want to scan it? (YES/no/selectively): yes
Can't open /dev/i2c-9191

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Winbond W83627DHG Super IO Sensors'                  Success!
    (address 0x290, driver `w83627ehf')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): yes
AMD K8 thermal sensors...                                   No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter '
    Busdriver `UNKNOWN', I2C address 0x2e
    Chip `Analog Devices ADT7473' (confidence: 5)

Driver `w83627ehf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `Winbond W83627DHG Super IO Sensors' (confidence: 9)

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter ISA main adapter
# Chip drivers
# no driver for Analog Devices ADT7473 yet
w83627ehf
coretemp
#----cut here----


Do you want to add these lines to /etc/modules automatically? (yes/NO)yes

```

but i don't really know what it means.

When i run 'sensors' in the terminal, i get the following with some Alarms. Especially the Aux-Temp is very high (stable at +119.0°C).

```
xyz@abc-desktop:~$ sensors
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:     +1.13 V  (min =  +0.00 V, max =  +1.74 V) 
in1:      +11.40 V  (min =  +3.48 V, max =  +3.38 V) ALARM
AVCC:      +3.33 V  (min =  +3.90 V, max =  +2.08 V) ALARM
3VCC:      +3.33 V  (min =  +1.57 V, max =  +1.28 V) ALARM
in4:       +0.09 V  (min =  +0.26 V, max =  +0.05 V) ALARM
in5:       +1.66 V  (min =  +0.78 V, max =  +0.51 V) ALARM
in6:       +4.12 V  (min =  +3.28 V, max =  +1.79 V) ALARM
VSB:       +3.33 V  (min =  +0.70 V, max =  +3.07 V) ALARM
VBAT:      +0.00 V  (min =  +0.00 V, max =  +0.13 V) 
Case Fan:    0 RPM  (min =  659 RPM, div = 128) ALARM
CPU Fan:  1259 RPM  (min =    0 RPM, div = 8) ALARM
Aux Fan:     0 RPM  (min =  329 RPM, div = 128) ALARM
fan4:        0 RPM  (min = 10546 RPM, div = 128) ALARM
fan5:        0 RPM  (min =    0 RPM, div = 128) ALARM
Sys Temp:    +30°C  (high =    +0°C, hyst =   +68°C)  
CPU Temp:  +34.0°C  (high = +80.0°C, hyst = +75.0°C)  
AUX Temp: +119.0°C  (high = +80.0°C, hyst = +75.0°C)   ALARM

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +27°C  (high =  +100°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +27°C  (high =  +100°C)                   

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +27°C  (high =  +100°C)                   

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +27°C  (high =  +100°C) 
```


My hardware looks like this:
-Asus P5E WS Pro
-Core 2 Quad Q6600 2.4GHz
-4 Gb Ram
-GPU: Quadro FX 570 
-Storage Samsung HD501LJ

Currently running Ubuntu 7.10 64bit very smooth with no freezes so far.

I am not really sure what the temperatures are all about because there are several Fans working all the time (not too loud), the cpu, gpu, harddrive all have their own Fans aswell as one in the Case.

What is to do about the temperatures, are these temperatures trustworthy, do i maybe have to tweak something, update the firmware or the bios? 

What are the correct Temperature Values?

Any advice would be much appreciated,

Thanks
jhulf

---

### Post by wesleybishop on 2010-06-21
Has this issue been resolved?

---

