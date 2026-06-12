---
title: "Sensors applet showing incorrect data"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by cait on 2008-07-02
I just installed the sensors applet because I'd particularly like to keep track of the CPU temp, but it's giving me strange options. In BIOS, I can look at CPU and motherboard temps (nothing else). In sensors-applet, I can only choose from GPU and ambient temperature.  The temperature readings in the applet are about 10 degrees higher (C) than the temperatures in BIOS. I'm not sure if this is just a labeling/temperature estimation problem, or if these are really reading from different devices than BIOS does. I've tried the **sensors** command; it tells me to run sensors-detect and install any needed kernel drivers. When I go through that, it checks everything and then has me paste some info into /etc/modules, but nothing changes, even after a restart. 

Any suggestions? I'm pretty new to all of this. I can give exact specs/output if that would help figure out what's going on - I'm not sure what would be useful. Thanks!!

---

### Post by philinux on 2008-07-02
What's your motherboard make and model.

What's the output of sensors-detect.

You can run it again and copy/paste the output.

---

### Post by kansasnoob on 2008-07-02
I've also had problems with sensors applet and have found that

> computertemp

from synaptic works well most of the time.

Of course you'll have to right click the panel and find Computer Temperature Monitor to finish the job.

[ATTACH]76148[/ATTACH]

---

### Post by cait on 2008-07-02
kansasnoob: I forgot, I did actually try computertemp before, and it just says "No thermal monitor support!" and doesn't let me change any preferences. I'm not sure if this can be fixed or not.

philinux: I have an Asus P5Q Pro motherboard.

Here is the output from running sensors-detect again:

```
# sensors-detect revision 5016 (2007-11-11 22:20:16 +0100)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): 
Probing for PCI bus adapters...
Found unknown SMBus adapter 8086:3a30 at 0000:00:1f.3.
Sorry, no known PCI bus adapters found.

We will now try to load each adapter module in turn.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): 
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x4a
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x4b
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621'...                No
Probing for `Maxim MAX6650/MAX6651'...                      No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): 
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
Probing for `Winbond W83L786NR/NG/R/G'...                   No
Probing for `Winbond W83L785TS-S'...                        No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1026'...                     No
Probing for `Analog Devices ADM1025'...                     No
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
Probing for `Analog Devices ADM1024'...                     No
Probing for `Winbond W83791D'...                            No
Client found at address 0x70
Probing for `Philips Semiconductors PCA9540'...             No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): 
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
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found unknown chip with ID 0xa513
    (logical device B has address 0x290, could be sensors)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): 
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter '
    Busdriver `UNKNOWN', I2C address 0x2e
    Chip `Analog Devices ADT7473' (confidence: 5)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
# no driver for Analog Devices ADT7473 yet
#----cut here----

```

Sorry if you didn't need that whole thing.  Thanks for your help!

---

### Post by philinux on 2008-07-03
I think the answer is in the output, It's not finding stuff. Your mb might not have the sensors.

Here's the important bits from mine. See the difference.

```
Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      Yes
Found `ITE IT8712F Super IO Sensors'                        Success!
    (address 0x290, driver `it87')
Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): 
AMD K8 thermal sensors...                                   Success!
    (driver `k8temp')

```

---

### Post by cait on 2008-07-03
Ok, thanks. One last question... any idea why BIOS can see stuff and sensors-detect can't? Or maybe something is just labeled wrong somewhere, since both places show two devices just with different names...?

---

### Post by Marshal0505 on 2008-07-03
I have the same mainboard and i'm assuming that the software just isn't supporting the sensors available on this mainboard.Nothing wrong with the sensors themselves.I don't even think the board is supported by ubuntu.

---

### Post by cait on 2008-07-03
Yeah, I also had a lot of trouble first booting/installing Ubuntu and then getting online in it. I think at least some of that might have been the mobo. Have you found any temperature monitoring software that does work with the board? I had some trouble with CPU temp in the very beginning (I built the computer myself), and if possible, I'd still like to find a way to keep an eye on this wihtout having to boot into BIOS all the time. It looks like it might be hard/impossible to find something that works with it, though.

---

### Post by Marshal0505 on 2008-07-04
> **cait said:**
> Yeah, I also had a lot of trouble first booting/installing Ubuntu and then getting online in it. I think at least some of that might have been the mobo. Have you found any temperature monitoring software that does work with the board? I had some trouble with CPU temp in the very beginning (I built the computer myself), and if possible, I'd still like to find a way to keep an eye on this wihtout having to boot into BIOS all the time. It looks like it might be hard/impossible to find something that works with it, though.

I had a heck of a time getting the build-in lan to work, and Ubuntu could only detect HDs with HDs set to 'raid' in bios.
And basicly i'm just hoping that support for this board will improve in time.I think it's only been introduced a few months ago (may?), but overall i'm very pleased by it's performance.It's rock solid.I can monitor the temperature on hard disks and gpu

---

### Post by drs305 on 2008-07-04
Another temp/fan/cpu monitor is gkrellm.
```
sudo aptitude install gkrellm
```

I haven't found it in the menus but starting this gui app in terminal with "gkrellm &" works just fine.

---

### Post by Marshal0505 on 2008-07-04
Hm, I'm very much liking how this looks.I'll give it a try :)
Thank you very much

---

### Post by cait on 2008-07-05
Thanks! I installed Windows over Ubuntu so I could set up a dual-boot, but Windows is giving me so many problems (I'm really considering whether I need Windows... I am NOT happy with it right now) so I probably won't be back on Ubuntu for a few days, but I'll try that out then.

---

