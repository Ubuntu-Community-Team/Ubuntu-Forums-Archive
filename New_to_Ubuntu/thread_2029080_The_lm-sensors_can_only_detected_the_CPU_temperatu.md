---
title: "The lm-sensors can only detected the CPU temperature sensor"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by mmca on 2012-07-19
I have installed lm-sensors, and have used the command 'sensors-detect'. there is the result:

# sensors-detect revision 5984 (2011-07-10 21:22:53 +0200)
# System: Gigabyte Technology Co., Ltd. H61N-USB3

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found `ITE IT8728F Super IO Sensors'                        Success!
    (address 0x290, driver `to-be-written')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): y
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-i801' for device 0000:00:1f.3: Intel Cougar Point (PCH)
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: SMBus I801 adapter at 0500 (i2c-0)
Do you want to scan it? (yes/NO/selectively): y
Client found at address 0x4e
Probing for `National Semiconductor LM75'...                No
Probing for `National Semiconductor LM75A'...               No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6642'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6654'...                              No
Probing for `Maxim MAX6690'...                              No
Probing for `Maxim MAX6659'...                              No
Probing for `Maxim MAX6647'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Texas Instruments TMP411'...                   No
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP422'...                   No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `National Semiconductor LM64'...                No
Probing for `National Semiconductor LM73'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `NXP/Philips SA56004'...                        No
Probing for `Fintek F75121R/F75122R/RG (VID+GPIO)'...       No
Probing for `Fintek F75111R/RG/N (GPIO)'...                 No
Probing for `ITE IT8201R/IT8203R/IT8206R/IT8266R'...        Yes
    (confidence 6, not a hardware monitoring chip)
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

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written':
  * ISA bus, address 0x290
    Chip `ITE IT8728F Super IO Sensors' (confidence: 9)

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

Note: there is no driver for ITE IT8728F Super IO Sensors yet.
Check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for updates.

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK


but when I type 'sensors' in terminal,it only display the following:

~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +51.0°C  (high = +80.0°C, crit = +99.0°C)
Core 0:         +51.0°C  (high = +80.0°C, crit = +99.0°C)
Core 1:         +50.0°C  (high = +80.0°C, crit = +99.0°C)
Core 2:         +48.0°C  (high = +80.0°C, crit = +99.0°C)
Core 3:         +49.0°C  (high = +80.0°C, crit = +99.0°C)


My computer's motherboard manufacturer and model: Gigabyte H61N-USB3

Is there anybody who can tell me how to find all the sensors?

---

### Post by QIII on 2012-07-19
Did you type```
service module-init-tools start
```?

---

### Post by mmca on 2012-07-19
> **QIII said:**
> Did you type```
service module-init-tools start
```?

already typed 'sudo service module-init-tools start'

---

### Post by GreatDanton on 2012-07-19
If you have already done that, I suppose that you have sensors only for Cpu and nothing else, but since this is relative new computer, you should have other sensors too. Try reinstalling lm-sensors. One strange fact I came around, when I had drivers for my graphic card installed, sensors were not working.

---

### Post by mmca on 2012-07-21
> **GreatDanton said:**
> If you have already done that, I suppose that you have sensors only for Cpu and nothing else, but since this is relative new computer, you should have other sensors too. Try reinstalling lm-sensors. One strange fact I came around, when I had drivers for my graphic card installed, sensors were not working.
In the echo of "sensors-detect", I found a NOTE:

Note: there is no driver for ITE IT8728F Super IO Sensors yet.
Check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for updates.

So I download the source code of lm_sensors-3.3.2,and install it following the lm-sensors installation wizard.

This time, IT87 driver installed successfully. I think so, because there is not the NOTE again.

But the result is the same as before.

Why?

---

### Post by LordEager on 2012-07-21
Have you tried compiling it yourself?

---

### Post by mmca on 2012-07-21
> **LordEager said:**
> Have you tried compiling it yourself?

Do you mean compile the c file 'it87.c' ?

no.

could you give me some guide to compile it?

---

### Post by koehn on 2013-05-29
Download the it87 kernel module. You should have a directory with it87.c and Makefile. Do a normal `make && sudo make install`. Do a `sudo modprobe it87`. Bam. Add `it87` to /etc/modules and it will load every time.

Note that most kernel upgrade will require you to `make clean && make && sudo make install && modprobe it87` again.

---

