---
title: "Error Message running lm-sensors diagnostic program."
date: 2013-08-12
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2013-08-12
Hi All

I was running a program to see what, if any, temperature sensors I had on my hardware. I will post the whole output, but I am really interested in the error message at the bottom of the output:

```

glenn@design:~$ sudo sensors-detect
# sensors-detect revision 5984 (2011-07-10 21:22:53 +0200)
# System: Acer Aspire M1200/3200/5200
# Board: Acer RS780HVF

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                             No
AMD K8 thermal sensors...                                      No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...               No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
Intel digital thermal sensor...                                   No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                         No
VIA Nano thermal sensor...                                     No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                             No
Trying family `VIA/Winbond/Nuvoton/Fintek'...              No
Trying family `ITE'...                                                Yes
Found `ITE IT8718F Super IO Sensors'                        Success!
    (address 0xe80, driver `it87')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                             No
Trying family `VIA/Winbond/Nuvoton/Fintek'...              No
Trying family `ITE'...                                                No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): y
Probing for `IPMI BMC KCS' at 0xca0...                       No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                      No
Probing for `Winbond W83782D' at 0x290...                      No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600/SB700/SB800 SMBus
Module i2c-dev loaded successfully.

Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-0)
Do you want to scan it? (yes/NO/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                     Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                    No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                     Yes
    (confidence 8, not a hardware monitoring chip)

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `it87':
  * ISA bus, address 0xe80
    Chip `ITE IT8718F Super IO Sensors' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
it87
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading cpuid... OK

glenn@design:~$ service module-init-tools start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.70" (uid=1000 pid=5321 comm="start module-init-tools ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
glenn@design:~$ 

```

Any help with why those modules wouldnt load, would be appreciated.

Glenn.

---

### Post by Mark Phelps on 2013-08-12
Try running the "service" command with "sudo" and see if that makes any difference.

---

### Post by tgalati4 on 2013-08-12
Make sure that *it87* got placed in your /etc/modules file.  Then reboot and your sensors should show up.

```
cat /etc/modules
(reboot)
sensors
```

They should show up:

tgalati4@Mint14-Extensa ~ $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +57.0°C  (crit = +95.0°C)
temp2:        +57.0°C  (crit = +105.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +54.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:       +56.0°C  (high = +100.0°C, crit = +100.0°C)

---

