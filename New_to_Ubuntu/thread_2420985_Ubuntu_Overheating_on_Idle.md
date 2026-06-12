---
title: "Ubuntu Overheating on Idle"
date: 2019-06-14
forum: New to Ubuntu
---

### Post by kuuhaku89 on 2019-06-14
Hello guys,

I am fairly new to Ubuntu and had installed ubuntu 18.04 on my laptop (Dell g7 7590). It had a severe heating issue even on idle, where it would even reach 71[SUP]&#8203;o[/SUP]C. Is this normal? I tried installing TLP, Slimbook, powertop, laptop-mode etc. Nothing seems to work. I tried Ubuntu 19.04 and I am facing the same problems. Plz help me out.

---

### Post by Autodave on 2019-06-14
My first thought is that something isn't telling the truth about temperature.  With the laptop off for at least a few hours, what is the temp when you first start it back up again?  What program are you using to obtain the temp?

---

### Post by kuuhaku89 on 2019-06-14
When I first turn on the PC its cool (35 to 45 centigrade maybe), but heats up within the first 10 minutes of usage (55 to 60) and sometimes reaches 71, where I switch it off immediately.
I use psensors to detect the Temp.

---

### Post by koollaydtac on 2019-06-14
I gotta be honest I am kind of curious about the same thing myself too. I recently installed it myself and I'll have two readings. One saying average which shows the same range usually what my windows programs do and another one maximum which can be some where between 10 to 20 degrees higher. I've yet to find anything on google explaining what the difference is or what that's all about either. I've installed Sensors Utility and Hardware Sensors Indicator from the store along with 3 of the GNOME Shell Extension's I believe. Sensory Perception, Sensors, and Hardware Sensors Indicator. I believe Sensory Perception is the one that stays on though and is at the top of my screen. Like the OP I am wondering if the OS runs my rig hotter or just isn't giving me the correct temperature information.

---

### Post by kuuhaku89 on 2019-06-14
Also when i try:

```
sensors|grep fan
```

I get no output
How do I resolve this?

---

### Post by crip720 on 2019-06-14
Probably just means that the fan has no sensor for it, quite a few laptops don't.

---

### Post by kuuhaku89 on 2019-06-14
The fans worked in Windows without any issues. They also work in Ubuntu but no where near the required speed. They just spin at bare minimum.

---

### Post by kuuhaku89 on 2019-06-14
When I run:

```

sudo sensors-detect

```

It gets stuck here:

```
kuuhaku@kuuhaku:~$ sudo sensors-detect --auto# sensors-detect revision $Revision$
# System: Dell Inc. G7 7590 (laptop)
# Board: Dell Inc. 0T3CD6
# Kernel: 5.0.0-16-generic x86_64
# Processor: Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz (6/158/10)


Running in automatic mode, default answers to all questions
are assumed.


Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 16h thermal sensors...                           No
AMD Family 17h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
Intel 5500/5520/X58 thermal sensor...                       No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No


Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0xfe00
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No


Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No


Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Using driver `i2c-i801' for device 0000:00:1f.4: Cannon Lake-H (PCH)


Next adapter: NVIDIA GPU I2C adapter (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x18
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
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
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Texas Instruments TMP400'...                   No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `National Semiconductor LM95233'...             No
Probing for `National Semiconductor LM95234'...             No
Probing for `National Semiconductor LM95235'...             No
Probing for `National Semiconductor LM95245'...             No
Probing for `National Semiconductor LM64'...                No
Probing for `SMSC EMC1047'...                               No
Probing for `SMSC EMC1402'...                               No
Probing for `SMSC EMC1403'...                               No
Probing for `SMSC EMC1404'...                               No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `ST STTS2002'...                                No
Probing for `ST STTS3000'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `IDT TSE2004'...                                No
Probing for `IDT TS3001'...                                 No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP9804'...                          No
Probing for `Microchip MCP9808'...                          No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP98244'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Probing for `ON CAT34TS02C'...                              No
Probing for `ON CAT34TS04'...                               No
Probing for `Atmel AT30TS00'...                             No
Probing for `Giantec GT30TS00'...                           No
Client found at address 0x19
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
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
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Texas Instruments TMP400'...                   No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `National Semiconductor LM95231'...             No
Probing for `National Semiconductor LM95241'...             No
Probing for `National Semiconductor LM95245'...             No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `ST STTS2002'...                                No
Probing for `ST STTS3000'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `IDT TSE2004'...                                No
Probing for `IDT TS3001'...                                 No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP9804'...                          No
Probing for `Microchip MCP9808'...                          No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP98244'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Probing for `ON CAT34TS02C'...                              No
Probing for `ON CAT34TS04'...                               No
Probing for `Atmel AT30TS00'...                             No
Probing for `Giantec GT30TS00'...                           No
Client found at address 0x1a
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
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
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Texas Instruments TMP400'...                   No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `ST STTS2002'...                                No
Probing for `ST STTS3000'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `IDT TSE2004'...                                No
Probing for `IDT TS3001'...                                 No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP9804'...                          No
Probing for `Microchip MCP9808'...                          No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP98244'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Probing for `ON CAT34TS02C'...                              No
Probing for `ON CAT34TS04'...                               No
Probing for `Atmel AT30TS00'...                             No
Probing for `Giantec GT30TS00'...                           No
Client found at address 0x1b
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `ST STTS2002'...                                No
Probing for `ST STTS3000'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `IDT TSE2004'...                                No
Probing for `IDT TS3001'...                                 No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP9804'...                          No
Probing for `Microchip MCP9808'...                          No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP98244'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Probing for `ON CAT34TS02C'...                              No
Probing for `ON CAT34TS04'...                               No
Probing for `Atmel AT30TS00'...                             No
Probing for `Giantec GT30TS00'...                           No
Client found at address 0x1c
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP441'...                   No
Probing for `SMSC EMC1072'...                               No
Probing for `SMSC EMC1073'...                               No
Probing for `SMSC EMC1074'...                               No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `ST STTS2002'...                                No
Probing for `ST STTS3000'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `IDT TSE2004'...                                No
Probing for `IDT TS3001'...                                 No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP9804'...                          No
Probing for `Microchip MCP9808'...                          No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP98244'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Probing for `ON CAT34TS02C'...                              No
Probing for `ON CAT34TS04'...                               No
Probing for `Atmel AT30TS00'...                             No
Probing for `Giantec GT30TS00'...                           No
Client found at address 0x1d
Probing for `TI / National Semiconductor ADC128D818'...     No
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP441'...                   No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `ST STTS2002'...                                No
Probing for `ST STTS3000'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `IDT TSE2004'...                                No
Probing for `IDT TS3001'...                                 No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP9804'...                          No
Probing for `Microchip MCP9808'...                          No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP98244'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Probing for `ON CAT34TS02C'...                              No
Probing for `ON CAT34TS04'...                               No
Probing for `Atmel AT30TS00'...                             No
Probing for `Giantec GT30TS00'...                           No
Client found at address 0x1e
Probing for `TI / National Semiconductor ADC128D818'...     No
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP441'...                   No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `ST STTS2002'...                                No
Probing for `ST STTS3000'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `IDT TSE2004'...                                No
Probing for `IDT TS3001'...                                 No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP9804'...                          No
Probing for `Microchip MCP9808'...                          No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP98244'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Probing for `ON CAT34TS02C'...                              No
Probing for `ON CAT34TS04'...                               No
Probing for `Atmel AT30TS00'...                             No
Probing for `Giantec GT30TS00'...                           No
Client found at address 0x1f
Probing for `TI / National Semiconductor ADC128D818'...     No
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP441'...                   No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `ST STTS2002'...                                No
Probing for `ST STTS3000'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `IDT TSE2004'...                                No
Probing for `IDT TS3001'...                                 No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP9804'...                          No
Probing for `Microchip MCP9808'...                          No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP98244'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Probing for `ON CAT34TS02C'...                              No
Probing for `ON CAT34TS04'...                               No
Probing for `Atmel AT30TS00'...                             No
Probing for `Giantec GT30TS00'...                           No
Client found at address 0x28
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM96080'...             No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Nuvoton NCT7802Y'...                           No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Client found at address 0x29
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM96080'...             No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Nuvoton NCT7802Y'...                           No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
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
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Texas Instruments TMP400'...                   No
Probing for `National Semiconductor LM95235'...             No
Probing for `National Semiconductor LM95245'...             No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Probing for `SMSC EMC1402'...                               No
Probing for `SMSC EMC1403'...                               No
Probing for `SMSC EMC1404'...                               No
Client found at address 0x2a
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM96080'...             No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Nuvoton NCT7802Y'...                           No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
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
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Texas Instruments TMP400'...                   No
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP441'...                   No
Probing for `National Semiconductor LM95231'...             No
Probing for `National Semiconductor LM95233'...             No
Probing for `National Semiconductor LM95241'...             No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Client found at address 0x2b
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                
```

How do i resolve this?

---

### Post by CatKiller on 2019-06-14
> **kuuhaku89 said:**
> When I first turn on the PC its cool (35 to 45 centigrade maybe), but heats up within the first 10 minutes of usage (55 to 60) and sometimes reaches 71, where I switch it off immediately.
I use psensors to detect the Temp.

First of all, unless you shut it down properly, turning it off suddenly is way more harmful than letting it run at 71°C. That temperature is hot, sure, but not very hot. Things will generally start throttling at about 80°C.

As far as I can tell from a quick search, since you didn't list the hardware, that's a gaming laptop with very power hungry components, and laptops lack airflow generally. It's going to be hotter than a desktop whatever you do.

For fan control to work, something has to control the fan. This should be obvious. If the laptop came with Windows, it probably also came with software to control the fan. That won't help you if you aren't using Windows. The next option is to have the motherboard control the fans directly. That's how the software works, after all: it reads the output from the temperature signal and sends a signal to the fan controller to increase or decrease the (PWM) voltage. Most BIOSes will have an option to make those decisions themselves. That way, it doesn't matter which operating system you're using.

If you want to control the fans using software on Linux, you need to be able to read the sensor values for the temperature, and also be able to write a signal to the fan controller. The details for the sensor chips and fan controllers are rarely made publicly available, so they have to be reverse-engineered. If the people writing the software don't have access to the hardware you're using, or they can't make sense of the signals, you're SOL. Most motherboard manufacturers don't make their own chips, though: they use something off the shelf. So someone may have already done the work for you, but they equally might not have been able to.

If you're going that route, you need lm-sensors to be able to display readings for the temperatures you're interested in, and for the fans you want to control, and for those readings to be accurate: often the sensor output needs an offset to be applied to accurately reflect reality, and that only comes with testing. Then you can configure fancontrol to increase or decrease the fan speeds based on temperature.

TL;DR: do it in the BIOS.

---

### Post by Doug S on 2019-06-14
turbostat (linux-tools-common) package will work with your processor. Myself, I haven't used "sensors" for years.
As a starting point, I would suggest something like this (the load is ramped up and then down):

```
doug@s15:~/temp-k-git/linux/drivers/cpufreq$ [COLOR="#FF0000"]sudo turbostat --quiet --Summary --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,GFXWatt,IRQ --interval 15[/COLOR]
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt GFXWatt
0.32    2602    1294    27      4.10    0.23
3.09    3745    1835    41      8.41    0.23
8.42    3793    3350    29      16.77   0.23
23.93   3531    8091    51      22.81   0.23
76.51   3500    23522   58      58.58   0.23
85.49   3500    26284   61      59.72   0.23
100.00  3500    30618   64      60.93   0.23
100.00  3500    30606   68      61.66   0.23
100.00  3500    30592   70      62.17   0.23
100.00  3500    30607   72      62.55   0.23
100.00  3500    30609   72      62.82   0.23
100.00  3500    30602   74      62.99   0.23
97.53   3500    30018   75      63.12   0.23
24.71   3611    9265    50      30.20   0.23
0.04    1600    774     46      4.16    0.23
0.05    1601    940     44      4.09    0.23
0.54    2142    2037    41      4.36    0.23
0.02    1601    315     40      3.99    0.23
0.02    1601    433     38      3.97    0.23
0.02    1601    595     37      3.95    0.23
0.02    1600    322     36      3.93    0.23
0.01    1600    285     35      3.92    0.23
0.02    1600    270     35      3.91    0.23
0.01    1600    281     33      3.89    0.23
0.02    1600    318     33      3.89    0.23

```Also note that there is no such thing as "idle" on any Ubuntu desktop version based computer with a GUI. Even doing nothing, there is a lot of stuff going on. The above turbostat stuff was done on my test server (no GUI), with a bunch of services disabled, such that "idle" really has very little left to do.

EDIT: For readers that wonder why the CPU frequencies dropped from 3.8GHz to 3.5 GHz under higher load: The reason is the processor does this by itself as a function of how many cores are active. This information is can also be in the turbostat output if the "--quiet" option is removed. Excerpt:

```
cpu1: MSR_TURBO_RATIO_LIMIT: 0x23242526
35 * 100.0 = 3500.0 MHz max turbo 4 active cores
36 * 100.0 = 3600.0 MHz max turbo 3 active cores
37 * 100.0 = 3700.0 MHz max turbo 2 active cores
38 * 100.0 = 3800.0 MHz max turbo 1 active cores

```

---

### Post by crip720 on 2019-06-14
Ubuntu or the powers that be, have changed it to Linux-tools-generic.

---

### Post by Doug S on 2019-06-15
> **crip720 said:**
> Ubuntu or the powers that be, have changed it to Linux-tools-generic.To what does "it" refer?
If you meant turbostat, then I disagree.

Although, I admit, I do not use the version from the package because it has insane and completely unnecessary dependencies.

Reference: [https://packages.ubuntu.com/search?searchon=contents&keywords=turbostat&mode=exactfilename&suite=disco&arch=any](https://packages.ubuntu.com/search?searchon=contents&keywords=turbostat&mode=exactfilename&suite=disco&arch=any)

---

### Post by CatKiller on 2019-06-15
> **Doug S said:**
> Although, I admit, I do not use the version from the package because it has insane and completely unnecessary dependencies.

[Reference](https://packages.ubuntu.com/search?searchon=contents&keywords=turbostat&mode=exactfilename&suite=disco&arch=any)
Those aren't dependencies, they are packages that provide a version of turbostat. Linux-tools-common is the one to use if you're using Linux Standard Base, and one of the others if you aren't.

This is very off-topic.

---

### Post by j2ee on 2019-06-16
> **kuuhaku89 said:**
> Hello guys,

I am fairly new to Ubuntu and had installed ubuntu 18.04 on my laptop (Dell g7 7590). It had a severe heating issue even on idle, where it would even reach 71[SUP]&#8203;o[/SUP]C. Is this normal? I tried installing TLP, Slimbook, powertop, laptop-mode etc. Nothing seems to work. I tried Ubuntu 19.04 and I am facing the same problems. Plz help me out.

Don't make too much sense for me installing Ubuntu in a gaming laptop...

---

### Post by Doug S on 2019-06-17
sensors doesn't give me any fan information either, so I did an experiment just listening to the fan as a function of processor temperature. Any fan speed increase was minimal until somewhere in the 70-75 degree range, and it ramped up from there.

Myself, I don't worry at all about processor package temperature until it is in the 80s.

---

