---
title: "Temp. Sensors"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by uzzo2 on 2008-07-18
can any one tell me how to find which sensors are which on my panel. they're labeled temp 1, temp 2, and temp 3. temp 1 is running a little warm at idle for my taste. 
it8718-isa-0a10
Adapter: ISA adapter
in0:         +1.38 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.25 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.07 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +3.09 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +2.98 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +0.10 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +0.13 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +3.01 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.26 V
fan1:       2436 RPM  (min =    0 RPM)
fan2:       2177 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:       +57.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermal diode
temp2:       +46.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
temp3:       +39.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
cpu0_vid:   +0.913 V

---

### Post by drs305 on 2008-07-18
If you are using lm-sensors, there is a file called /etc/sensors3.conf (your filename may vary depending on the version you are running) that states:
```

# The CPU sensor can be any of temp1, temp2 or temp3 - it's motherboard
# dependent. Same for the motherboard temperature.

```

I had to enter the setup during boot to compare the temps to those I recorded just before I did a reboot.

That being said, for my ASUS motherboard, temp1 was the CPU and temp2 was the motherboard. Your results will/may vary.

In my notes, the following two commands are supposed to provide CPU temps:
```

cat /proc/acpi/thermal_zone/*/temperature
acpi -t

```

---

### Post by uzzo2 on 2008-07-18
> **drs305 said:**
> If you are using lm-sensors, there is a file called /etc/sensors3.conf (your filename may vary depending on the version you are running) that states:
```

# The CPU sensor can be any of temp1, temp2 or temp3 - it's motherboard
# dependent. Same for the motherboard temperature.

```

I had to enter the setup during boot to compare the temps to those I recorded jsut before I did a reboot.

That being said, for my ASUS motherboard, temp1 was the CPU and temp2 was the motherboard. Your results will/may vary.

In my notes, the following two commands are supposed to provide CPU temps:
```

cat /proc/acpi/thermal_zone/*/temperature
acpi -t

```

ok, thanks, i'd like to find out because it acts so crazy. just a few seconds after the original post it came down and the same sensor now is sitting at 35 degrees celcius, it just does that every now and then. i'm just wondering, i took the cover off to make sure all the fans were running. all of them were running, but the power supply fan was running much slower than than my cpu and case fans.

---

### Post by Malta paul on 2008-07-18
This may help you:
file:///usr/share/doc/lm-sensors/doc/lm_sensors-FAQ.html
[http://sensors-applet.sourceforge.net/](http://sensors-applet.sourceforge.net/)

Edit: I should have mentioned that I use Lm-sensors and they identify the temp sensors by name.
[http://www.lm-sensors.org/](http://www.lm-sensors.org/)

Have fun

---

### Post by uzzo2 on 2008-07-18
> **drs305 said:**
> If you are using lm-sensors, there is a file called /etc/sensors3.conf (your filename may vary depending on the version you are running) that states:
```

# The CPU sensor can be any of temp1, temp2 or temp3 - it's motherboard
# dependent. Same for the motherboard temperature.

```

I had to enter the setup during boot to compare the temps to those I recorded jsut before I did a reboot.

That being said, for my ASUS motherboard, temp1 was the CPU and temp2 was the motherboard. Your results will/may vary.

In my notes, the following two commands are supposed to provide CPU temps:
```

cat /proc/acpi/thermal_zone/*/temperature
acpi -t

```

ok, i got in to bios but wasn't really sure what to do, went to the command line and typed sensors. same as in terminal and i got a bad command error.

---

### Post by uzzo2 on 2008-07-18
> **Malta paul said:**
> This may help you:
file:///usr/share/doc/lm-sensors/doc/lm_sensors-FAQ.html
[http://sensors-applet.sourceforge.net/](http://sensors-applet.sourceforge.net/)

Edit: I should have mentioned that I use Lm-sensors and they identify the temp sensors by name.
[http://www.lm-sensors.org/](http://www.lm-sensors.org/)

Have fun

i'm using lm-sensors as well it just doesn't name them for some reason.

---

### Post by drs305 on 2008-07-18
> **uzzo2 said:**
> ok, i got in to bios but wasn't really sure what to do ...

After entering BIOS, just look around and find the the temperature readings. In my ASUS BIOS, they are located under "Power, Hardware Monitor". 

I compared the temps in BIOS with the temps I'd recorded a few minutes earlier. In my case, the motherboard and CPU temps were different enough that I could easily guess which was which in 'sensors'. I then edited the sensors.conf file and added comments under the it8716 entries so I could look it up when I later forgot.

---

### Post by Malta paul on 2008-07-18
Try right clicking on your temps and select preferences, then in 'Display' set 'Icon with value' also in preference set 'beside labels / icons'

Hope this works for you :)

---

### Post by uzzo2 on 2008-07-18
> **Malta paul said:**
> Try right clicking on your temps and select preferences, then in 'Display' set 'Icon with value' also in preference set 'beside labels / icons'

Hope this works for you :)
tried that and it didn't work, thanks anyway

---

### Post by uzzo2 on 2008-07-18
> **drs305 said:**
> After entering BIOS, just look around and find the the temperature readings. In my ASUS BIOS, they are located under "Power, Hardware Monitor". 

I compared the temps in BIOS with the temps I'd recorded a few minutes earlier. In my case, the motherboard and CPU temps were different enough that I could easily guess which was which in 'sensors'. I then edited the sensors.conf file and added comments under the it8716 entries so I could look it up when I later forgot.
your bios must look a lot different than mine. when mine starts up all i see is 4 different versions of the OS, 2 of them are recovery mode. you use the up or down arrows to select which one and hit enter to boot. or you can select e to edit the commands before booting. or, c for a command line.

---

### Post by drs305 on 2008-07-18
> **uzzo2 said:**
> your bios must look a lot different than mine. when mine starts up all i see is 4 different versions of the OS, 2 of them are recovery mode. you use the up or down arrows to select which one and hit enter to boot. or you can select e to edit the commands before booting. or, c for a command line.

You are confusing BIOS with BOOT. BIOS is entered as the computer starts up, before any system is loaded. You usually enter it by hitting the DEL key, F1, etc. It depends on your BIOS. Usually as the computer begins to start you can just begin hitting the DEL key (or F1 etc) until it enters Setup. On my computer, I hit the DELete key just after I hear the first beep.

Once you have entered the BIOS setup, you can search for the temperature readings. They will be listed under something else, such as Power.

---

### Post by uzzo2 on 2008-07-18
> **drs305 said:**
> You are confusing BIOS with BOOT. BIOS is entered as the computer starts up, before any system is loaded. You usually enter it by hitting the DEL key, F1, etc. It depends on your BIOS. Usually as the computer begins to start you can just begin hitting the DEL key (or F1 etc) until it enters Setup. On my computer, I hit the DELete key just after I hear the first beep.

Once you have entered the BIOS setup, you can search for the temperature readings. They will be listed under something else, such as Power.
ok,thanks, i finally got to it, i guess its been a while since i've went into bios for anything. it's only showing 2 temps. cpu temp-45 degrees(it was closest to my temp 1 on the panel and system temp- 37 degrees( i think that one would have to be temp 2). wonder what temp 3 is?

---

### Post by Malta paul on 2008-07-18
You could give 'X Sensors' a try. Mine also gives the names alongside the temps.  Applications>add/remove, then search X sensors.
It will then install in System Tools.

Good luck :(

---

### Post by uzzo2 on 2008-07-18
> **Malta paul said:**
> You could give 'X Sensors' a try. Mine also gives the names alongside the temps.  Applications>add/remove, then search X sensors.
It will then install in System Tools.

Good luck :(
thanks malta, yea i have x sensors installed but when you click on applications>system tools>x sensors, it doesn't do anything.:confused:

---

### Post by Malta paul on 2008-07-18
Wow that is strange, :confused:   Here is a copy of my desktop

I do hope someone can give you an answer!

---

### Post by uzzo2 on 2008-07-18
> **Malta paul said:**
> Wow that is strange, :confused:   Here is a copy of my desktop

I do hope someone can give you an answer!
yea, i like that, maybe someone can help me figure it out. i'm assuming that picture is the x-sensor program.

---

### Post by drs305 on 2008-07-18
> **uzzo2 said:**
> thanks malta, yea i have x sensors installed but when you click on applications>system tools>x sensors, it doesn't do anything.:confused:

If you open it in terminal, using the command 'xsensors', you will see an error message. Most likely it will be something telling you it can't find the sensors.conf file. 

I believe the error message also tells you how to start it from the command line with a switch to point it to the correct location of your sensors.conf file.

I don't think it supported my it-8716 setup but maybe you will have better luck.

---

### Post by cariboo on 2008-07-18
Start xsensors in a terminal it should echo back why it is not working, I get this output:

[CODEjuser@intrepid:~$ xsensors
Sensor 'k8temp' not supported by xsensors!
Sensor 'w83627ehf' not supported by xsensors!][/CODE]

I've got an AMD2-64, I just at the sensors to the panel. I have two core temp, cpu fan and 4 hard drives.

Jim

---

### Post by uzzo2 on 2008-07-18
> **cariboo907 said:**
> Start xsensors in a terminal it should echo back why it is not working, I get this output:

[CODEjuser@intrepid:~$ xsensors
Sensor 'k8temp' not supported by xsensors!
Sensor 'w83627ehf' not supported by xsensors!][/CODE]

I've got an AMD2-64, I just at the sensors to the panel. I have two core temp, cpu fan and 4 hard drives.

Jim
thanks guys, tried xsensors in terminal and this is what i got.
Error opening config file: /etc/sensors.conf
Use -c option to specify location of lm_sensors configuration file.

---

### Post by drs305 on 2008-07-18
> **uzzo2 said:**
> thanks guys, tried xsensors in terminal and this is what i got.
Error opening config file: /etc/sensors.conf
Use -c option to specify location of lm_sensors configuration file.

That is the error I mentioned. You would run (if you have an /etc/sensors.conf). If you have the file in another location, substitute that wit the full pathname for '/etc/sensor.conf' :
```
xsensors -c /etc/sensors.conf
```

If you don't know where it is, this will search for all files that contain 'sensors' and 'conf'. Most likely it is sensors.conf or some variation:
```
sudo find / -type f -iname sensors*conf
```

---

### Post by uzzo2 on 2008-07-18
> **drs305 said:**
> That is the error I mentioned. You would run (if you have an /etc/sensors.conf). If you have the file in another location, substitute that wit the full pathname for '/etc/sensor.conf' :
```
xsensors -c /etc/sensors.conf
```

If you don't know where it is, this will search for all files that contain 'sensors' and 'conf'. Most likely it is sensors.conf or some variation:
```
sudo find / -type f -iname sensors*conf
```

ok, did that and got this.
phillip@phillip-desktop:~$ sudo find / -type f -iname sensors*conf
[sudo] password for phillip: 
find: /home/phillip/.gvfs: Permission denied
/etc/sensors3.conf
phillip@phillip-desktop:~$ xsensors -c /etc/sensors3.conf
Sensor 'it8718' not supported by xsensors!

how do you guys remember all this stuff anyway, with brains like that who needs computers.:lolflag:

---

### Post by schekn on 2009-06-07
I have the same problem: the xsensors window is just blank.
Restarted my computer twice. Ran xsensors -c /etc/xsensors.conf - but the result is still the same: blank window and terminal output is sensor it87 is not supported by xsensors

P.S. I do have this sensor's info in the /etc/modules file.

From what I read here everybody solved this by just rebooting. Is there still anybody having the same problem? What can be causing this lack of output while "sensors" runs just fine?

If not xsensors, what else can I use?

Thank you

---

