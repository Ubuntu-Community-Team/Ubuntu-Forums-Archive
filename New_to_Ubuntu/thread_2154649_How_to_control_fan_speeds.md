---
title: "How to control fan speeds"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by NRF19 on 2013-06-15
Hi,

Now I've seen that this has been posted a hundred million times before and so I'm sorry to quiz about it. 

My CPU fan is incredibly loud to the point it overpowers my sound system. 
I checked using an app called Hardware Sensors Indicator and it shows Fan1 to be running @ 3409 RPM, I believe this to be my CPU fan. Using the same app my CPU temps are in the range of 30-37C and therefore I think I could lower the speed of the CPU fan safely, am I right in thinking this?

Anyway, I found this guide 

[HTML]http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/[/HTML]

The only problem is I don't understand what to do at this point

```
sudo modprobe *module1 module2*


```

In running sudo sensors-detect I get all of this, what is the module I type for my CPU fan?

```
# sensors-detect revision 5984 (2011-07-10 21:22:53 +0200)
# System: Gigabyte Technology Co., Ltd. G41M-Combo

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
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
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      Yes
Found `ITE IT8720F Super IO Sensors'                        Success!
    (address 0x290, driver `it87')
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
interfaces? (YES/no): yes
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: i915 gmbus ssc (i2c-0)
Do you want to scan it? (YES/no/selectively): yes
ye
Next adapter: i915 gmbus vga (i2c-1)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: i915 gmbus panel (i2c-2)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: i915 gmbus dpc (i2c-3)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: i915 gmbus dpb (i2c-4)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: i915 gmbus dpd (i2c-5)
Do you want to scan it? (YES/no/selectively): yes

Next adapter: SMBus I801 adapter at 0500 (i2c-6)
Do you want to scan it? (yes/NO/selectively): yes
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

Driver `it87':
  * ISA bus, address 0x290
    Chip `ITE IT8720F Super IO Sensors' (confidence: 9)

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
it87
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)yes
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK



```

I am running ubuntu 12.04 on a core 2 quad processor. I appreciate any help with this matter. 

Thanks

---

### Post by dino99 on 2013-06-15
first check the bios settings about powersaving (set it ondemand)

[http://blog.tube42.se/?p=1225](http://blog.tube42.se/?p=1225)

the fan speed depend on the powersaving settings

---

### Post by 2F4U on 2013-06-15
Since you already installed the sensors package what temperatures are reported? The reason for fans running on full speed is often a high temperature and the systems tries to prevent overheating.

---

### Post by NRF19 on 2013-06-15
> **2F4U said:**
> Since you already installed the sensors package what temperatures are reported? The reason for fans running on full speed is often a high temperature and the systems tries to prevent overheating.

Just checked and at 3409 RPM the temps are 30-37 degrees across the 4 cores, that's cool right? And the fan is at this speed from boot.

---

### Post by NRF19 on 2013-06-15
> **dino99 said:**
> first check the bios settings about powersaving (set it ondemand)

[http://blog.tube42.se/?p=1225](http://blog.tube42.se/?p=1225)

the fan speed depend on the powersaving settings

Checked my BIOS and the only thing relevant was a SMART Fan Control which increases or decreases speed as necessary, however the speed remains static at 3409 regardless of the temperature (which showed at 27 degrees Celsius) 

I installed the package from the above link and changed it to ondemand but nothing changed fan speed wise again, I'm at the point where I'm contemplating buying a new fan, but am worried that it'll be equally as loud.

---

### Post by TNFrank on 2013-06-15
I've also seen it where the fan is always on if your laptop(that is if you're running this on a laptop) is plugged in but throttles down for times when you're running on battery power to conserve the battery.

---

### Post by NRF19 on 2013-06-15
> **TNFrank said:**
> I've also seen it where the fan is always on if your laptop(that is if you're running this on a laptop) is plugged in but throttles down for times when you're running on battery power to conserve the battery.

It's a desktop, but thanks anyway

---

### Post by TNFrank on 2013-06-15
Ahh, ok then, it's a desktop computer so you'll be plugged in all the time and won't have to worry about the battery going dead.  I'm sure there's a program or something you can install in Terminal to use to set the points where it'll come on and go off, in fact I saw one here the other day but can't remember where.  I'm sure someone here knows how to get the fix for you. Good luck.

---

