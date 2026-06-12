---
title: "What is Winbond W83627HF/F/HG/G Super IO Sensors"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by ShirishAg75 on 2008-06-22
Hi all, 
      I feel like a beginner all the time. So here's a beginner question on the same. I ran sudo sensors-detect and got the following output 

```

shirish@Mugglewille:~$ sudo sensors-detect
[sudo] password for shirish: 
# sensors-detect revision 5016 (2007-11-11 22:20:16 +0100)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): Yes
Probing for PCI bus adapters...
Use driver `i2c-i810' for device 0000:00:02.0: Intel 82845G GMCH

We will now try to load each adapter module in turn.
Module `i2c-i810' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): Yes
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: I810/I815 I2C Adapter (i2c-0)
Do you want to scan it? (YES/no/selectively): Yes

Next adapter: I810/I815 DDC Adapter (i2c-1)
Do you want to scan it? (YES/no/selectively): Yes
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: saa7130[0] (i2c-2)
Do you want to scan it? (YES/no/selectively): Yes

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): Yes
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
Do you want to scan for Super I/O sensors? (YES/no): Yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `**Winbond W83627HF/F/HG/G Super IO Sensors'**            Success!
    (address 0x290, driver `w83627hf')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): Yes
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `w83627hf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `**Winbond W83627HF/F/HG/G Super IO Sensors**' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
w83627hf
#----cut here----

Do you want to add these lines automatically? (yes/NO)yes

```

Now my query is what is this **Winbond W83627HF/F/HG/G Super IO Sensors ? **, doing a google search doesn't get me anything much about what this sensor is all about although I do get some bug report. 

I'm using lm-sensors 1:3.0.0-4ubuntu1 package.

---

### Post by mcduck on 2008-06-22
That's a sensor chip, located on yor motherboard and built by Winbond.

The sensor chip gathers data from temperature sensors, fan speeds and so on.

What the sensors-detect is now trying to do is to enable the driver needed to access data from that chip, you'll need to have the driver module loaded for various system monitoring programs (like lm-sensors) to work.

---

### Post by ShirishAg75 on 2008-06-22
I said last and its there in /etc/modules 

Now how do I use it to know what the temperatures are?

Any info. would be nice.

---

### Post by mcduck on 2008-06-23
It's been a while since I've needed lm-sensors, but the command to get the sensor readings should be simply "sensors".

It might take a bit more than that to get it working in the first place, but as I said it's been a while, and the last machine I've had that needed lm-sensors had a rather rare sensor chip and I and because of that I had to do a bit more tweaking than what's probably needed in most cases..

---

