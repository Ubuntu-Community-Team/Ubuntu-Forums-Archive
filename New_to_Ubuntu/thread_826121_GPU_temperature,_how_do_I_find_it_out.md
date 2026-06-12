---
title: "GPU temperature, how do I find it out?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Tom--d on 2008-06-11
It says it all in the title, 

I have a Intel 956 chipset in my laptop.

Please, some help as I think its overheating :( Or is very hot. 


By any chance, where is the GPU located? Under/near the touchpad? (as it gets hot :( too hot)

Thank you all, 
Tom

---

### Post by sam_delta on 2008-06-11
CPU temp
[http://www.xawk.com/ubuntu-cpu-temperature.html](http://www.xawk.com/ubuntu-cpu-temperature.html)
[http://ubuntuforums.org/showthread.php?t=687688](http://ubuntuforums.org/showthread.php?t=687688)

EDIT i though it was CPU
ill see if i can get some gpu info
which video card do you havE?

sam

---

### Post by Daveth on 2008-06-11
and what laptop - the chipset may not be the heat source!

---

### Post by sam_delta on 2008-06-11
yea, have you tryd lm-sensors?```
sudo apt-get install lm-sensors
```

sam

---

### Post by Tom--d on 2008-06-11
My laptop is a Toshiba A200 IVO, its new. got it the beginning of this year.

My grapphics card id:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller
```

---

### Post by Tom--d on 2008-06-11
> **sam_delta said:**
> yea, have you tryd lm-sensors?```
sudo apt-get install lm-sensors
```

sam

```
tom@Laptop:~$ sudo sensors-detect
# sensors-detect revision 5016 (2007-11-11 22:20:16 +0100)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801H ICH8

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 1c20 (i2c-0)
Do you want to scan it? (YES/no/selectively): y
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

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
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
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0xfc11
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): y
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: y

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

Do you want to add these lines automatically? (yes/NO)y
tom@Laptop:~$ 

```

did it work?

---

### Post by sam_delta on 2008-06-11
yes, now you need to install a simple aplication to see those readings, just go into add/remove and install "X sensors", then run it, it should be under applications>system tools and it will display lm-sensors readings

EDIT- i believe that you have to restart ubuntu after installing lm-sensors, so the kernel loads the modules

sam

---

### Post by Tom--d on 2008-06-11
```
tom@Laptop:~$ xsensors
Error opening config file: /etc/sensors.conf
Use -c option to specify location of lm_sensors configuration file.
tom@Laptop:~$ 

```

:\

Also, 
```
tom@Laptop:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +47.0°C  (crit = +100.0°C)                  


```
Nothing about GPU, just CPU :(

---

### Post by stchman on 2008-06-11
> **Tom--d said:**
> ```
tom@Laptop:~$ xsensors
Error opening config file: /etc/sensors.conf
Use -c option to specify location of lm_sensors configuration file.
tom@Laptop:~$ 

```

:\

Also, 
```
tom@Laptop:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +47.0°C  (crit = +100.0°C)                  


```
Nothing about GPU, just CPU :(

Remember most laptops use shared memory and therefore more than likely will have no sensor on the graphics processor.  Only your higher end dedicated graphics cards from Nvidia and ATI will have sensors on them.

My 7600GT and 8800GT have sensors on them and the nvidia-settings program reports the GPU temp.  Now CPUs will usually have a sensor on them.

How do you know it is the graphics processor in the laptop that is the culprit of the heat build up?

The hdd is usually located in the front of the laptop near the touchpad.

Also maybe your cooling fan and fins are dirty.  Blow a little compressed air in the fan inlet to loosen up dirt.

---

### Post by Tom--d on 2008-06-11
But my fan is at the back. 

And yes, it could be the HDD as its right next to the touchpad. How do I make that cooler? and can I find out the interal temp of the hdd?

And, could I be able to change the speed of the hdd?

Thanks

---

### Post by sam_delta on 2008-06-11
try ```
sudo cp /etc/sensors3.conf /etc/sensors.conf
```

or install/upgrage  libsensors3 

then run again xsensors
sam

---

### Post by Tom--d on 2008-06-11
> **stchman said:**
> 
Also maybe your cooling fan and fins are dirty.  **Blow a little compressed air in the fan inlet to loosen up dirt.**


What do you recommend? a hover? to is that too powerful?

---

### Post by Tom--d on 2008-06-11
> **sam_delta said:**
> try ```
cp /etc/sensors3.conf /etc/sensors.conf
```
sam

```
tom@Laptop:~$ sudo cp /etc/sensors3.conf /etc/sensors.conf
[sudo] password for tom: 
tom@Laptop:~$ xsensors
Sensor 'coretemp' not supported by xsensors!
Sensor 'coretemp' not supported by xsensors!
tom@Laptop:~$ 


```

---

### Post by sam_delta on 2008-06-11
sry i duno how to fix that... im sorry, you better remove lm-sensors and xsensors and try another alternative

ima google a little bit and see if i find something, ill come back and post

sam

---

### Post by sam_delta on 2008-06-11
for your hard drive temp

```
sudo aptitude install smartmontools
```

then monitor the temp with 
```
sudo smartctl -a /dev/hda | grep Temp
```

where /dev/hda is the hdd device you want to get the temp from (your harddrive)

sam

---

### Post by stchman on 2008-06-11
> **Tom--d said:**
> What do you recommend? a hover? to is that too powerful?

A can of compressed air.

---

### Post by Tom--d on 2008-06-11
tom@Laptop:~$ sudo hddtemp /dev/sda
/dev/sda: TOSHIBA MK1237GSX: 42°C
tom@Laptop:~$ 


Is that a good temp for a hdd?

also, is there any gui displaying my hdd temp and rpm?

---

### Post by sam_delta on 2008-06-11
42 celsius is fine, i believe that hdd should not exceed 55-60 depending on the manufacturer, ive seen some people with hdd working at 50-55 under normal working conditions, no problems, so your fine with the hdd

i duno about any other gui for showing temps, ive used program called "gdesklets" and "screenlets" with those your able to put screenlets with monitors on your desktop as if they where part of your background

sam

---

### Post by Tom--d on 2008-06-11
Thank you :)

Well, it doesnt have to be a gui. command line is preferred :)

But how do I find out my true rpm and be able to change then? (make it slower)

---

### Post by sam_delta on 2008-06-11
no problem

sry i duno how to change your hdd speed, but just curios why would you do that?

you can change the power managment using hdparm (man hdparm, for more info), you can make it more agressive, which will affect the number of times your hdd parks, making the hdd to park more times is safer for data loss due to bumps, but will tire your hdd more as it increases its load cycle on each park. in the other hand, making it less agressive, it will park less often so in theory this will make your hdd last even more, but it will be more sensitive for bumps as the hdd is spinning and rarely parks, for this same fact that its almost always spinning, itll also increase its temp

sam

---

### Post by st33med on 2008-06-11
To check the temp inside your laptop (Usually near your CPU), type:
```
acpi -tf
```
Remove the 'f' if you want Celsius temperature.

> What do you recommend? a hover? to is that too powerful?

No, a can of air should do fine. You can find that in any hardware store and most computer outlets.

Also, you could try undervolting your laptop to produce less heat from the CPU. However, it does not decrease memory, GPU, or HDD temp. It lowered mine by about 20 degrees.
[HowTo: Undervolt your CPU]("http://ubuntuforums.org/showthread.php?t=786402")

---

### Post by tbfly on 2008-10-25
I just make a little program to detect my laptop's GM965's temperature.
It seems work.
It was based on coreboot's intelboot code, and improved to support GM965.

It's binary:

[http://att.newsmth.net/att.php?s.392.656329.476](http://att.newsmth.net/att.php?s.392.656329.476)

---

### Post by Ripfox on 2008-10-25
I like to install two apps from synaptic to get both temps from my machines.

hddtemp

sensors-applet

Then right click the gnome panel and add sensor app and configure it to see both temps.

---

### Post by Tom--d on 2008-10-25
> **tbfly said:**
> I just make a little program to detect my laptop's GM965's temperature.
It seems work.
It was based on coreboot's intelboot code, and improved to support GM965.

It's binary:

[http://att.newsmth.net/att.php?s.392.656329.476](http://att.newsmth.net/att.php?s.392.656329.476)

Thank you. It worked!

57C good for it?
CPU is around 49C all the time.

---

### Post by tbfly on 2008-10-26
> **Tom--d said:**
> Thank you. It worked!

57C good for it?
CPU is around 49C all the time.

[http://www.coreboot.org/pipermail/coreboot/2008-October/040866.html](http://www.coreboot.org/pipermail/coreboot/2008-October/040866.html)

I just release the code.
Hope you like it.

The process of "calibrated current temperature" transfer to "degree Centigrade" need improve.

---

### Post by Tom--d on 2008-10-26
> **tbfly said:**
> [http://www.coreboot.org/pipermail/coreboot/2008-October/040866.html](http://www.coreboot.org/pipermail/coreboot/2008-October/040866.html)

I just release the code.
Hope you like it.

The process of "calibrated current temperature" transfer to "degree Centigrade" need improve.

Thanks!

Would be good if this was improved and can be displayed in Conky :D:D and/or LM Sensors :D

---

