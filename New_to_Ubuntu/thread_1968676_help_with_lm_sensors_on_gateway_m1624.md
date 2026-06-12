---
title: "help with lm sensors on gateway m1624"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by roloracer on 2012-04-29
hey I've been looking all over the web trying to solve my problem but I've had no luck, I have a gateway m1624 notebook dualbooting ubuntu 11.10 64bit/windows 7 ultimate 32bit, now I'm working on setting up lm_sensors and fancon to control and increase my fanspeed to maintain my temps low while I build android/cm9 from source.

 I'm doing sensor detect and following steps found here but when I finish sensor detectI can't gain control because it says I'm missing the device folder in /sys/class/hwmon/hwmon0/device: No such file or directory.


[B]This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

```
Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   Success!
    (driver `k8temp')
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found `ITE IT8512E/F Super IO'                              
    (no hardware monitoring capabilities)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600/SB700/SB800 SMBus
Module i2c-dev loaded successfully.

Next adapter: SMBus PIIX4 adapter at 8410 (i2c-0)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x50
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

Next adapter: Radeon i2c bit bus 0xc0 (i2c-1)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: Radeon i2c bit bus 0x90 (i2c-2)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: Radeon i2c bit bus 0x91 (i2c-3)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: Radeon i2c bit bus 0x92 (i2c-4)
Do you want to scan it? (YES/no/selectively): yes

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `k8temp' (autoloaded):
  * Chip `AMD K8 thermal sensors' (confidence: 9)

No modules to load, skipping modules configuration.

Unloading i2c-dev... OK
Unloading cpuid... OK

roloracer@roloracer-M-1624:~$ ./fancon.sh
./fancon.sh: line 9: cd: /sys/class/hwmon/hwmon0/device: No such file or directory

-----------------------------------------
-        SysInfo            -
-----------------------------------------
cat: temp2_input: No such file or directory
cat: temp1_input: No such file or directory
Temperature CPU:        0.0 C
Temperature System        0.0 C
cat: fan2_input: No such file or directory
cat: fan1_input: No such file or directory
cat: fan5_input: No such file or directory
cat: fan3_input: No such file or directory
CPU Fan:             rpm
Case1 Fan:             rpm
Case2 Fan:             rpm
Frontal Fan:             rpm
```

I need to make or to add a config file for making adjustments for the fan and really need help to make this happen.

Thanks. ):P
[/B]

---

### Post by CharlesA on 2012-04-29
sensors-detect did not detect any modules to load. What does running:

```
sensors
```

Say?

---

### Post by roloracer on 2012-05-10
> **CharlesA said:**
> sensors-detect did not detect any modules to load. What does running:

```
sensors
```Say?
this is what comes up!

```
roloracer@roloracer-M-1624:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +47.0°C  (crit = +95.0°C)

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +44.0°C  
Core0 Temp:   +43.0°C  
Core1 Temp:   +50.0°C
Core1 Temp:   +50.0°C
```I've been searching with no luck in this matter , my laptop is overheating because the cpu fan is not increasing speed when the cpu load increases.

---

### Post by CharlesA on 2012-05-10
There you go then. :)

---

### Post by roloracer on 2012-05-11
> **CharlesA said:**
> There you go then. :)
so now what? how do I go about making it have the proper modules to load the configuration for fan control? do I need to make a custom kernel with such?? :confused:

---

### Post by CharlesA on 2012-05-11
I don't think there is a way to control the fans, but you can keep an eye on the temps with sensors.

---

### Post by roloracer on 2012-05-11
> **CharlesA said:**
> I don't think there is a way to control the fans, but you can keep an eye on the temps with sensors.
thanks but I already have psensor-temperature monitor for that, I guess I'll keep looking but in the mean time I'm gonna take it apart, clean it and dust off the fan and heatsink, take processor off and put artic silver on it and see if it helps a bit. :)

---

