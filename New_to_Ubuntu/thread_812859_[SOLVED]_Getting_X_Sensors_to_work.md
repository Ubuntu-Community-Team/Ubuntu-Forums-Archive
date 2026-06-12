---
title: "[SOLVED] Getting X Sensors to work"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Dumpy Dumpster on 2008-05-30
I have downloaded X Sensors from the Add/Remove programmes list and it appears in Applications > System Tools.  However when I click on it nothing happens.  How do I get it to run?  Thanks.

---

### Post by forestpixie on 2008-05-30
First - have you run sensors-detect?

```
sudo sensors-detect
```

Second - if you have then probably need to add the path to the sensors file it produces - Right click on menu then edit menu - navigate to the xsensors entry. Right click and edit that and then add > -c /etc/sensors3.conf to the launcher properties

---

### Post by Dumpy Dumpster on 2008-05-30
Thank you forestpixie.  I have now run the 'sensors-detect', but cannot find the 'Menu' to right click on!  Sorry, another piece of advice needed!

---

### Post by forestpixie on 2008-05-30
Your menu bar in the panel at the top or bottom - the ordinary menu you use to get anywhere :)

Right click that one - then edit menu

---

### Post by Dumpy Dumpster on 2008-06-07
Sorry, but cannot find this with Hardy.  Should of mentioned my version before - my fault.  But why does it not just WORK when downoaded without wasting everyone's very good and kind help on various additions and add-ons?  The programme writers must take some responibility here.

---

### Post by gdebat on 2008-06-19
You're right dumpy .. amen.

Anyway I have hardy and got it to work :

```
sudo /usr/sbin/sensors-detect
```

Answer YES for each and every question

```
sudo modprobe XXXX
```
where XXXX is the code given by the previous command . would be something like this : w83627hf

Right click on the main Ubuntu menu (on the main panel), click on "Edit Menus", go to Applications -> System Tools, right click on the "X Sensors" entry, Properties, and append -c /etc/sensors3.conf to the command (it would look something like "/usr/bin/xsensors -c /etc/sensors3.conf" - without quotes)

Works like charm :popcorn:

---

### Post by Dumpy Dumpster on 2008-06-19
Sorry, but I have been remise in not keeping up with this thread.  Actually I found that GKrellm in Synaptic gave a VERY good instantaneous readout of temps/voltages. As much or as little  as you want, and I now have them sitting on my lower tool bar.  This is a great programme and better than X Sensors!
My thanks to all who have contributed to solving my question.

---

### Post by foska on 2008-06-21
Worked for me

> **gdebat said:**
> You're right dumpy .. amen.

Anyway I have hardy and got it to work :

```
sudo /usr/sbin/sensors-detect
```

Answer YES for each and every question

```
sudo modprobe XXXX
```
where XXXX is the code given by the previous command . would be something like this : w83627hf

Right click on the main Ubuntu menu (on the main panel), click on "Edit Menus", go to Applications -> System Tools, right click on the "X Sensors" entry, Properties, and append -c /etc/sensors3.conf to the command (it would look something like "/usr/bin/xsensors -c /etc/sensors3.conf" - without quotes)

Works like charm :popcorn:

---

### Post by jlh68 on 2009-09-16
I cannot get the XXXX code, not can I get X Sensors to work.

---

### Post by Hellrazer on 2009-12-08
> **Dumpy Dumpster said:**
> Sorry, but I have been remise in not keeping up with this thread.  Actually I found that GKrellm in Synaptic gave a VERY good instantaneous readout of temps/voltages. As much or as little  as you want, and I now have them sitting on my lower tool bar.  This is a great programme and better than X Sensors!
My thanks to all who have contributed to solving my question.

I tried using GKrellm which installed and seems to run fine, but I can't seem to figure out how to configure it to show my CPU temp.

Thanks,
Hellrazer

---

### Post by Dumpy Dumpster on 2009-12-11
Hi Hellrazer,
In fact I gave up on GKrellm in favour of lm-sensors from Synaptic.  You will also need sensors-applet plus libsensors-applet-plugin0 as well. Install and run sudo sensors-detect, answer yes to all, reboot and then you can configure how many voltages,temps(including CPU) and fan speeds you want.
I have these sitting in lower menu bar.   Happy Christmas!

---

### Post by erenay on 2010-02-02
> **jlh68 said:**
> I cannot get the XXXX code, not can I get X Sensors to work.

I also cannot see the XXXX code. This is the response that I got:

```

eren@laptop1:~/workspace/cassandra$ sudo sensors-detect
[sudo] password for eren: 
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): Y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): Y
Module loaded successfully.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): Y
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: intel drm CRTDDC_A (i2c-0)
Do you want to scan it? (YES/no/selectively): Y

Next adapter: intel drm LVDSDDC_C (i2c-1)
Do you want to scan it? (YES/no/selectively): Y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): Y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): Y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found `Nat. Semi. PC87591 Super IO'                         
    (but not activated)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): Y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue:  

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)Y

```

---

### Post by Junkieman on 2010-02-11
> **erenay said:**
> I also cannot see the XXXX code. This is the response that I got:

```

To load everything that is needed, _add this to /etc/modules_:

#----cut here----
# Chip drivers
[COLOR="Blue"]coretemp[/COLOR]
#----cut here----

```

Adding coretemp to /etc/modules will load that module automatically at startup. you can do that with ```
sudoedit /etc/modules
```

What gdebat was saying, is to load that module now manually, without having to restart, by running ```
sudo modprobe coretemp
``` 

After which you should get some results running sensors in the terminal. Great stuff.

Now to setup the GUI so that it works, edit it's menu shortcut as posted earlier, adding "-c /etc/sensors3.conf" to the end of the command. Leave a space between the original command and the one you tack on.

I have to add, mine picked up coretemp and lm85. Seems like lm85 is used to report in the GUI, but my lm85 doesnt give any results, only coretemp gives results in the terminal. Fine by me, at least I get the numbers :)

---

### Post by jmstern on 2010-05-15
Thank you for the above - I now get nice display showing the temps <cores are running about 127c.??? -= which undboubtedly led to multiple middle of the night shutdowns.  

So next, i need to clear  any cat hair from the fans, heat sink, and re-gel the heat sink.  Any other ideas to cool this puppy?

---

