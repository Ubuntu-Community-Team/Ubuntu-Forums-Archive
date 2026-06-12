---
title: "[SOLVED] How to: Microchip programmer under Ubuntu"
date: 2007-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Amazona aestiva on 2007-08-31
[SIZE="3"]***[COLOR="Red"]I warn you that here is no support, and the guide is to be used at your own risk![/COLOR]***[/SIZE]
[COLOR="SandyBrown"][SIZE="3"]**Microchip programmer under Ubuntu**
[/SIZE][/COLOR]
Piklab programs many type of microchips.

This is the alternative for Pickit in Windows.

It uses ICD2 Programmer, ICD1 Programmer, Pickit2 [COLOR="Red"]Firmware 1.x _ONLY_[/COLOR], Pickit1, Picstart Plus, GPSim and other programmers!

It knows .hex files.(MPLAB-IDE's .hex file for example)

[COLOR="RoyalBlue"]Install:[/COLOR] [COLOR="SeaGreen"]Last updated/checked:31-08-2007[/COLOR]


Follow the instructions exactly!
This isn't the latest... I'm working on it!
[COLOR="RoyalBlue"]
i386:[/COLOR]
1.Type:
```
wget http://kent.dl.sourceforge.net/sourceforge/piklab/piklab_0.14.2-1_i386.deb && wget http://ftp.kfki.hu/linux/ubuntu/pool/universe/f/fam/libfam0_2.7.0-11_i386.deb
```

2.Type:
```
sudo dpkg -i piklab_0.14.2-1_i386.deb libfam0_2.7.0-11_i386.deb
```
[COLOR="Red"]If it'll say something about failed to install libfam0 because libfam0c102, don't worry![/COLOR]

[COLOR="RoyalBlue"]amd64:[/COLOR]
???

Now Piklab should be in Apps. -> Development
or type:
```
piklab
```

[COLOR="SeaGreen"]I tested:[/COLOR]
Picstart Plus ---------------> Succeed
ICD2 Programmer ------> Succeed
ICD1 Programmer ------> I don't have this programmer.
Pickit2 Firmware 1.x --> Mine is Firmware 2.x.
Pickit1 -----------------------> I don't have this programmer.
[SIZE="3"]
[COLOR="DarkOrange"]Appendix:[/COLOR][/SIZE]
MPLAB-IDE 7.60 works correctly under wine...

[COLOR="RoyalBlue"]i386:[/COLOR]
Use this version of [Wine]("http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.44~winehq0~ubuntu~7.04-1_i386.deb") to install and run [MPLAB]("http://ww1.microchip.com/downloads/en/DeviceDoc/mp760a.zip").
[COLOR="Red"]NOTE:[/COLOR]
-A few error while install and need to close the install window with force.:-k
-Few errors while starting up.:-k
-I tested many functions including the "Project Wizard" and the "Build All".:)

[COLOR="RoyalBlue"]amd64:[/COLOR]
???

---

### Post by seijling on 2008-03-23
Quick question: How specifically did you get the ICD2 connected or working?  

The install was smooth but for some reason I cannot get the ICD2 to connect/reset the target.  Any hints?

Mike

---

### Post by Amazona aestiva on 2008-03-26
> **seijling said:**
> Quick question: How specifically did you get the ICD2 connected or working?  

The install was smooth but for some reason I cannot get the ICD2 to connect/reset the target.  Any hints?

Mike

Hi!

Try these libraries:
```
sudo apt-get install --reinstall libusb-0.1-4 libusb-dev
```

---

### Post by zalmoxes on 2009-03-20
how do i use PICki2 firmware 2.x... its not supported.

---

