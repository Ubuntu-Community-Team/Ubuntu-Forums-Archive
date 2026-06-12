---
title: "[SOLVED] 'computertemp' does not work"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by AceDip on 2008-10-29
I ve installed computertemp to monitor the temp of my computer/devices from the synaptic.I then added it to the taskbar.
But it lays there with a big red cross sign and shows 'No Thermal Monitor Support' when cursor moves over it..
kindly hlep

---

### Post by earthpigg on 2008-10-29
[http://computertemp.berlios.de/help.php]("http://computertemp.berlios.de/help.php")

> How to show debug information on tooltip
To get some dbug information on applet's tooltip, you should do this:


try that yet, just to get a hint at whats wrong?

---

### Post by mkvnmtr on 2008-10-29
I think you have to install the sensors also. I was never able to get them installed on my powerpc unit. I did find some tutorials so it may work for you.

---

### Post by earthpigg on 2008-10-29
> **mkvnmtr said:**
> I think you have to install the sensors also. I was never able to get them installed on my powerpc unit. I did find some tutorials so it may work for you.

my laptop is nothing special, dirt cheap from ibuypower.com of all places.... i installed computertemp out of curiosity from this thread, and it works fine.

the vast majority of computers, i think, have sensors installed by default. apparently, your powerpc computer did not... maybe?

thread maker: is your computer also an apple...?

---

### Post by bapoumba on 2008-10-29
I the meantime, you can use:
```
acpi -V
```
from a terminal.
I monitor quite loosely the temps :)

---

### Post by AceDip on 2008-10-29
hey mkvnmtr..
you are talking about some tutorials, but where is it...i cant see any

---

### Post by AceDip on 2008-10-29
> **bapoumba said:**
> I the meantime, you can use:
```
acpi -V
```
from a terminal.
I monitor quite loosely the temps :)
I tried what you said and here it is
```

:~$ acpi -V
No support for device type: thermal

```

---

### Post by AceDip on 2008-10-29
> **earthpigg said:**
> [http://computertemp.berlios.de/help.php]("http://computertemp.berlios.de/help.php")




try that yet, just to get a hint at whats wrong?
I had gone through the help index earlier also but it just dint help.
well i've tried all small remedies like reinstallation etc, but couldnt go along.
There couldnt possibly be anything wrong with the machine ??

---

### Post by durand on 2008-10-29
> **AceDip said:**
> I tried what you said and here it is
```

:~$ acpi -V
No support for device type: thermal

```

Uhm...isn't that because there are no sensors on your computer? Mine doesn't have any and neither do a lot of others since they're mainly on laptops.

---

### Post by coolbrook on 2008-10-29
I suggest you install lm-sensors

```
sudo apt-get install lm-sensors
```

then once installed run

```
sensors-detect
```
and follow the instructions, basically saying yes to everything and ensuring you do the **sudo modprobe modulename** command for each module listed and **sudo depmod -a**.  That might get your sensors working for Computertemp.

---

### Post by mkvnmtr on 2008-10-29
As I recall Coolbrook has got it right for installing the sensors. You will have to watch the terminal and answer yes from time. That was where my problem was. It could not connect to some sensors. Apple is a problem sometimes. As for where I got the information, it was quite some time ago and I don't remember. You see I kind of an old guy and if I don't tell my wife I can't remember hardly anything.

---

### Post by AceDip on 2008-10-30
> **coolbrook said:**
> I suggest you install lm-sensors

```
sudo apt-get install lm-sensors
```

then once installed run

```
sensors-detect
```
and follow the instructions, basically saying yes to everything and ensuring you do the **sudo modprobe modulename** command for each module listed and **sudo depmod -a**.  That might get your sensors working for Computertemp.

Thanks man.I did as you said and it started working after a reboot.But i'm not able to comprehend what is it showing..i mean i want to monitor processor and disk temperature both instead it has only :
kernel i2c sensors
kernel i2c sensors hwmon

As on their webpage they have
[HTML]
Which sensors can Computertemp monitor?
You're computer must have one of this:
- acpi thermal support
- ibm laptop acpi
- adt746x (ibook and powerbook)
- windfarm (apple g5 computers)
- omnibook (hp and toshiba models)
- i8k (dell latitude and inspiron)
- i2c sensors kernel modules
- hddtemp hard disk monitor
[/HTML]How do i get others, atleast the HDD one.
Thanks again.

and also thankyou everyone.

---

### Post by coolbrook on 2008-10-30
> **AceDip said:**
> i want to monitor processor and disk temperature both instead it has only :
kernel i2c sensors
kernel i2c sensors hwmon


My guess is either your motherboard only has a sensor for the processor or whatever other gauges you have aren't supported by lm-sensors.  A more experienced user may be able to shed some light for us.

---

### Post by AceDip on 2008-10-31
> **coolbrook said:**
> My guess is either your motherboard only has a sensor for the processor or whatever other gauges you have aren't supported by lm-sensors.  A more experienced user may be able to shed some light for us.
Hi everyone..
Here is the final solution to my problem, i guess so!!
I installed following from Synaptic
[HTML]- hdd temp
- sensors-applet
- collectd
[/HTML]

they cretainly required other libraries,which was also done.But now i can monitor everything on my pc i.e. HDD temp,CPU temp, fan speeds, voltage sensors and many more.
Its really good, worth trying ..
But i have a feeling that, the above sensors only work after installing the lm-sensors and dont stand alone.

---

### Post by kweinert on 2010-05-04
Thanks for this.

It used to work in Koala, quit working in Lynx.

This post got it working again.

---

### Post by Cavsfan on 2010-10-13
Sweet! :) 

All I had to install through Synaptic was **sensors-applet** and I now have GPU temp, 4 core temps and 3 fan speeds - 8 icons on  my top panel.
I really don't need the fan speeds, but they are there for now. It was displaying 3 other temps and my HD temp, but those are not needed either.
But, it's nice they were available.

This is as good as windows. I had speedfan displaying GPU temp and coretemp displaying the 4 core temps. They are all in different colors.
I tried to change the colors, but don't really care that much. I am just happy to see the temps!
:guitar:

---

### Post by mlnease on 2012-08-05
> **AceDip said:**
> Hi everyone..
Here is the final solution to my problem, i guess so!!
I installed following from Synaptic
[HTML]- hdd temp
- sensors-applet
- collectd
[/HTML]they cretainly required other libraries,which was also done.But now i can monitor everything on my pc i.e. HDD temp,CPU temp, fan speeds, voltage sensors and many more.
Its really good, worth trying ..
But i have a feeling that, the above sensors only work after installing the lm-sensors and dont stand alone.
AceDip,

Thanks!  I know this thread is ancient but I really do appreciate the help.  It worked for me.  I still don't know at what point to set the alarm (especially in Celsius) but that I should be able to work out myself.

Thanks again.  Love this forum.

mike

---

### Post by wildmanne39 on 2012-08-05
Old thread closed.

---

