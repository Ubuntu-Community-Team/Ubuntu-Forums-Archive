---
title: "lmsensors not reading correct temp"
date: 2015-04-06
forum: New to Ubuntu
---

### Post by Cowboy303 on 2015-04-06
Howdy yall, I recently built my first computer and put Ubuntu on it.  The issue I'm having is I can't seem to read the CPU temp, voltages, or fan speed with anything I've tried.  However the UEFI displays them all, and seem to be fairly accurate.

A couple specs:
CPU: AMD A8 6600K
MotherBoard: MSI a78m-e35
Video Card: Geforce GT630

You can see in these screen shots that the CPU temp (the one on the left) isn't displaying correctly, the top bar randomly changes from 0-30 Celsius.

[IMG]http://s20.postimg.org/wt4oegy25/Screenshot_from_2015_04_06_08_53_00.png[/IMG]

[IMG]http://s20.postimg.org/4uainlwfh/Screenshot_from_2015_04_06_08_52_13.png[/IMG]

Here you can see the only thing that gets displayed with "sensors"

```
myer@AMD-A8:~$ sensorsk10temp-pci-00c3
Adapter: PCI adapter
temp1:         +2.8°C  (high = +70.0°C)
                       (crit = +70.0°C, hyst = +69.0°C)



```

And here is the results for "sensors-detect"

```
myer@AMD-A8:~$ sudo sensors-detect
[sudo] password for myer: 
# sensors-detect revision 6170 (2013-05-20 21:25:22 +0200)
# System: MSI MS-7721 [6.0]
# Board: MSI A78M-E35 (MS-7721)


This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.


Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): YES
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
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No


Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found unknown chip with ID 0x1106
    (logical device 4 has address 0x295, could be sensors)


Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): YES
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No


Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): YES
Probing for `National Semiconductor LM78' at 0x290...       Success!
    (confidence 6, driver `lm78')
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No


Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): YES
Using driver `i2c-piix4' for device 0000:00:14.0: AMD Hudson-2 SMBus
Module i2c-dev loaded successfully.


Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-0)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)


Next adapter: SMBus PIIX4 adapter at 0b20 (i2c-1)
Do you want to scan it? (YES/no/selectively): YES


Next adapter: NVIDIA i2c adapter 0 at 1:00.0 (i2c-2)
Do you want to scan it? (yes/NO/selectively): YES 


Next adapter: NVIDIA i2c adapter 1 at 1:00.0 (i2c-3)
Do you want to scan it? (yes/NO/selectively): YES
Client found at address 0x4a
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


Next adapter: NVIDIA i2c adapter 6 at 1:00.0 (i2c-4)
Do you want to scan it? (yes/NO/selectively): YES


Now follows a summary of the probes I have just done.
Just press ENTER to continue: 


Driver `lm78':
  * ISA bus, address 0x290
    Chip `National Semiconductor LM78' (confidence: 6)


To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
lm78
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!


Do you want to add these lines automatically to /etc/modules? (yes/NO)YES
Successful!


Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service kmod start'
to load them.


Unloading i2c-dev... OK
Unloading cpuid... OK



```

```
myer@AMD-A8:~$ sensors -vsensors version 3.3.4 with libsensors version 3.3.4



```

Thanks for looking, if there is any other info you need please feel free to ask.

---

### Post by dino99 on 2015-04-06
this has always been an issue, as i'm remembering. Better to install plugin like the ones you find into extensions.gnome.org
but you also can test psensor (search for it into the dash or synaptic)

---

### Post by Cowboy303 on 2015-04-06
psensor gives me the same results

[IMG]http://s20.postimg.org/xl7cdo299/Screenshot_from_2015_04_06_10_38_38.png[/IMG]

---

### Post by Mopar1973Man on 2015-05-13
I see my Conky panel script is being used. ;) Cowboy you need to tweak it... 

As for the temperatures and such I'm also looking to resolve a voltage issue as well. But I'm thinking its the lm-sensors software not seeing the information correctly. Going up in kernel did help my lm-sensors to at least report good temperatures but the voltages are still wonky.

```

radeon-pci-0008
Adapter: PCI adapter
temp1:        +37.4°F  (crit = +248.0°F, hyst = +194.0°F)

it8603-isa-0290
Adapter: ISA adapter
in0:          +0.82 V  (min =  +1.58 V, max =  +0.48 V)  ALARM
in1:          +1.63 V  (min =  +2.21 V, max =  +0.17 V)  ALARM
in2:          +2.03 V  (min =  +1.58 V, max =  +0.77 V)  ALARM
in3:          +2.02 V  (min =  +1.03 V, max =  +0.04 V)  ALARM
in4:          +1.22 V  (min =  +1.13 V, max =  +0.46 V)  ALARM
3VSB:         +3.26 V  (min =  +1.01 V, max =  +3.98 V)
Vbat:         +3.17 V  
+3.3V:        +3.36 V  
fan1:        2008 RPM  (min =  200 RPM)
fan2:        1721 RPM  (min =  602 RPM)
temp1:       +100.4°F  (low  = +82.4°F, high = +35.6°F)  ALARM  sensor = thermistor
temp2:        +89.6°F  (low  = +226.4°F, high = +33.8°F)  ALARM  sensor = thermistor
temp3:       -198.4°F  (low  = +111.2°F, high = -155.2°F)  sensor = thermistor
intrusion0:  ALARM

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +46.8°F  (high = +158.0°F)
                       (crit = +158.0°F, hyst = +156.2°F)

michael@michael:~$ 

```

```

michael@michael:~$ uname -a
Linux michael.morningstar.com 3.16.0-37-generic #51~14.04.1-Ubuntu SMP Wed May 6 15:23:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
michael@michael:~$
```

---

### Post by QIII on 2015-05-13
Hello!

I'll pitch in here with a partial explanation of your CPU temp issue.

AMD CPUs do not report an absolute physical temperature.  They report some sort of goofy unit they call "degrees" that represents a differential between the physical temperature and the value reported to the fan controller to keep the fan running at a speed required to keep the CPU below its maximum absolute physical temperature.

So, for instance, you see a report of 2.8 degrees at idle, which is utter nonsense.  That's cold enough for an "ice cold" beer.

As the physical temperature rises, this differential reading approaches the actual physical temperature asymptotically, meaning that it becomes more and more accurate.  So when your CPU is working hard, the temperature returned by the sensor is closer to the actual physical temperature.

Crazy, but I've learned to tolerate it over the years.

In your conky, you can look for the temperature of k10temp-pci-00c3.  But you'll get that crazy number.

I have a couple of scripts.  One of them just adds 10 degrees to the reported temperature and I call that from my conky.  That gives me a reading that is a little low at idle and a little high at full blast.  Close enough.  Between that and the fan speed, you can be pretty confident that you know how your CPU is responding.

I also have another script that I have been tweaking that takes the sensor temperature and, based on the current fan speed, interpolates a factor between the minimum fan speed at idle and the maximum fan speed to more closely approximate the actual physical temperature.  That one is not yet good enough for me to feel comfortable passing it around for people to depend on.

Unfortunately, I'm not at my machine at home right now, so I can't post the script or the line from my conky.

I'll try to remember to do that when I get home.

(Edit:  AMD wackiness rises with the APUs, since the are designed to run at higher temps because both the CPU and GPU are on the same die.)

---

### Post by UltimateCat on 2015-05-13
Try the sensors cmd:

```
root@cat:~# sensors -f | grep -i temp
temp1:       +122.0°F  
root@cat:~# 


```

For more information run man sensors:-

Hope that helps.

---

### Post by QIII on 2015-05-14
I went ahead and finished my AMD temperature correcting script for my conky and put it in place.  Here you see, both idle and under load, three "readings" on my CPU temp.

One is the raw k10temp.  One is a custom reading via my script.  One is just adding 20C to the k10temp because I don't believe my CPU is running cold enough to cool my sodas.

The k10temp at idle is ridiculously low.  Adding 20C to it makes the idle number look better, but the load "temperature" is clearly too high.

Somewhere in between is probably right, so we need some sort of dynamic correction.  The "Custom" reading is that dynamic correction.

Here are a couple of screen shots:

Load:

[ATTACH=CONFIG]261968[/ATTACH]

Idle:

[ATTACH=CONFIG]261969[/ATTACH]

And here is the really rough script.  Read the comments for what I was attempting to do and why.

```
#!/bin/bash

# AMD processors do not report a physical temperature.  Can we generate
# something reasonable for our conky?

#******************************************************************************
# ***** From lm-sensors wiki at their website: ********************************
#******************************************************************************

# coretemp returns unrealistic values
#
# The temperature value returned by the coretemp driver isn't absolute. It's a 
# thermal margin from the critical limit, and the greater the margin, the worse 
# the accuracy. It isn't really returning degrees Celsius. At high temperatures, 
# the (small) thermal margin is almost expressed in degrees Celsius, but at low 
# temperature, the (high) thermal margin is no longer expressed in actual 
# degrees Celsius.
#
# So, if the temperature value reported by coretemp is unrealistically low, all 
# it means is that you are far away from the critical limit so your systems are 
# running totally fine and cool and you don't have to worry at all. 
# Unfortunately, there is no way to improve the readings, this is a hardware 
# limitation.
#
# Additionally, the critical limit value may be wrong on come CPU models. We 
# may be able to address this problem over time, but again it's not really a 
# problem in the first place. All that really matters is how far the 
# measurement is from that limit. If the difference is above 40 pseudo degrees 
# Celsius (again these are not real degrees Celsius!) then you're safe.
#******************************************************************************


#******************************************************************************
# ***** From the k10temp module documantation: ********************************
#******************************************************************************

# There is one temperature measurement value, available as temp1_input in
# sysfs. It is measured in degrees Celsius with a resolution of 1/8th degree.
# Please note that it is defined as a relative value; to quote the AMD manual:
#
#    Tctl is the processor temperature control value, used by the platform to
#    control cooling systems. Tctl is a non-physical temperature on an
#    arbitrary scale measured in degrees. It does _not_ represent an actual
#    physical temperature like die or case temperature. Instead, it specifies
#    the processor temperature relative to the point at which the system must
#    supply the maximum cooling for the processor's specified maximum case
#    temperature and maximum thermal power dissipation.
#
# The maximum value for Tctl is available in the file temp1_max.
#
# If the BIOS has enabled hardware temperature control, the threshold at
# which the processor will throttle itself to avoid damage is available in
# temp1_crit and temp1_crit_hyst.
#******************************************************************************



# For those of you following along, I'm going to make a few of very stupid 
# and very wrong assumptions to see if I can get a more reasonable and workable 
# CPU temp reading at a glance:
#
# 1.  Since this reading is supposed to drive cooling, assume that means
#     how fast the fan runs
# 2.  Assume the relationship to the fan speed is linear.
# 3.  Assume that at max fan speed, the k10temp is roughly the same as the 
#     physical temp

# IF YOU USE THIS AND BREAK YOUR SYSTEM, IT'S ON YOU!


# Here are some basic values I'm assuming from observing my own system --
# an FX-8350 cooled by a monster Noctua HSF.
# These will take a bit of observation for another system.
idle_correction=20
no_correction=0
min_fanspeed=500
max_fanspeed=1200
speed_span=$(( ($max_fanspeed - $min_fanspeed) ))

# Get the CPU temp and HSF fan speed from sensors.  This may take some fiddling
# depending on your motherboard.
cpu_temp=$(sensors k10temp-pci-00c3 | grep 'temp1' | awk -F'.' '{print $1}'| awk -F'+' '{print $2}')
fanspeed=$(sensors it8728-isa-0228 | grep 'fan1' | awk '{print $2}' | cut -c1-4)

# If fanspeed<=500, factor = 1, so correction = idle_correction
# If fanspeed>=1200, factor = 0, so correction = 0
# Otherwise, calculate correction

if [ $fanspeed -le $min_fanspeed ]
then
    # At idle, add the idle correction
    final_temp=$(( ($cpu_temp + $idle_correction) ))
    echo $final_temp

elif [ $fanspeed -ge $max_fanspeed ]
then
    # At max fan speed, assume k10temp approaches physical temp
    final_temp=$cpu_temp
    echo $final_temp
else
    # Interpolate a correction based on fan speed
    fan_diff=$(( ($max_fanspeed - $fanspeed) ))
    
    # A little trick here, since integer division returning values less than
    # 1 gives 0.
    correction_factor=$(( (($fan_diff) * 100 )/ ($speed_span) ))
    correction=$(( ($idle_correction * $correction_factor) ))
    
    # And now we need a useful integer.
    correction=$(( ($correction / 100) ))
    
    # Calculate the corrected temperature
    final_temp=$(( ($cpu_temp + $correction) ))
    echo $final_temp
  
fi


```

---

