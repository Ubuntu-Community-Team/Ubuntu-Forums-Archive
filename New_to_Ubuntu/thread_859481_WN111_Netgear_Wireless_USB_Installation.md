---
title: "WN111 Netgear Wireless USB Installation"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by raysgremlin on 2008-07-14
I understand that to use a wireless USB not support by Ubuntu 8.04 use something called NDISwrapper and use the "windows driver"(*.inf file) provided by manufacturer. All well and good, but those nice people at NETGEAR provide a Self Installing wizard. Can`t find this (*.inf) file after it has run.:confused:

---

### Post by OffAxis on 2008-07-14
you don't use the windows installer. This should help:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by raysgremlin on 2008-07-14
Thanks. But have now run into another problem. When i have edited the Blacklist file as the article suggests. I am informed I do not have root permissions.

---

### Post by braddcadd on 2008-07-14
add "sudo" in front of any command in the terminal to execute the command as a root user, it will ask for a password then execute the command

---

### Post by raysgremlin on 2008-07-18
I am trying to edit the file blacklist, in the folder etc\modprobe.d.

To add the required entrys 
blacklist b43
blacklist b43legacy
blacklist ssb
 so I can try and install this USB driver.

The sudo command is in the terminal application. 

What is the whole command I require to open this file, with admin rights ?

---

### Post by raysgremlin on 2008-07-18
Found this in another forum

ffahog to thank

open terminal and type:

gksudo nautilus <return>

this opens nautilus and allows editing  files and directories as a root user.

---

### Post by raysgremlin on 2008-07-18
chipset ID 
After running lsusb command, got the following

Bus 001 Device 003:  ID 0846:9000 NetGear, Inc.

Can`t find this exact chipset ID at NDISWrapper

What do I do now ?

---

### Post by Skulled on 2008-07-27
Sorry for my english.... I'm a french guy....

I've got the same Usb key so try this... :
download the driver file [here]("http://www.mediafire.com/?2d0ndtxzlye")
untar it, open a terminal and go in the folder that you untar
In the console write this :
```
sudo ndiswrapper -i netmw245.inf

```
then watch if your driver is installed :
```
ndiswrapper -l
```
you have to see that :
```
netmw245 : driver installed
	device (0846:9000) present
```
then, still on the terminal write this
```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

and now you've got the wifi....:D

to start ndiswrapper on the startup,write this still on the terminal :
```
 echo "ndiswrapper"|sudo tee -a /etc/modules 
```

and here we go...

N.B : you don't have to edit the blacklist modules, because there isn't a module for this usb key on linux...
So, no conflict, and reason to edit this file....

---

### Post by raysgremlin on 2008-08-03
Thanks for the simple instructions. which I followed... HOWEVER

I have a wireless connection to my Draytek 2820. When I start a web connection, firefox hangs.


Any more ideas ??

---

### Post by hornetster on 2008-11-19
I'm 'sort of' re-opening an old thread here, but I have a VERY similar adaptor (it IS a WN111, but it is a V2) and the result from lsusb is:
*Bus 002 Device 005: ID 0846:9001 NetGear, Inc.*
I 'took the liberty' to change the ID in the inf file from 9000 to 9001 (innocently hoping it would work - well, no smoke! :) )but this didn't work, driver loaded, but still getting:

[I]Nov 19 21:10:45 boss kernel: [ 4497.293340] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Nov 19 21:10:46 boss kernel: [ 4497.421321] usb 2-2: reset full speed USB device using uhci_hcd and address 5
Nov 19 21:10:46 boss kernel: [ 4497.619811] ndiswrapper: driver netmw245 (Netgear,11/19/2007,1.0.7.3) loaded
Nov 19 21:10:46 boss kernel: [ 4498.144896] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
Nov 19 21:10:46 boss kernel: [ 4498.144907] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
Nov 19 21:10:46 boss kernel: [ 4498.144921] ndiswrapper (mp_halt:262): device f638d480 is not initialized - not halting
Nov 19 21:10:46 boss kernel: [ 4498.144924] ndiswrapper: device eth%d removed
Nov 19 21:10:46 boss kernel: [ 4498.145882] ndiswrapper: probe of 2-2:1.0 failed with error -22
Nov 19 21:10:46 boss kernel: [ 4498.146115] usbcore: registered new interface driver ndiswrapper[/I]

When I run modprobe....
Any assistance greatly appreciated...

---

### Post by cokeonice on 2008-12-01
I had been working on this for three days!!

I have a PC that I was running WinXP Pro on, connected to my 42" LCD to watch movies from the 'net and play DVD's, blah, blah, blah.

I decided I wanted to try the new Ubuntu 8.10 since it said it supported wireless.

I got Ubuntu installed, got my Logitech bluetooth mouse and keyboard configured no prob.  I could not get wireless to work!

I poured through countless forums, tried the suggestions in this forum (I had the WN111 driver but I am using the netmw245 as suggested above).  

I thought, there has to be some other hardware interfering with this.  Perhaps in the BIOS?  I rebooted, entered BIOS, noticed that the 'AC97 Modem was "enabled", hmmmm, that was not "enabled" before when I was running WinXP, I must have accidently re-enabled it.  I "disabled" it, rebooted, and VOILA!  My wireless USB WN111 is working!  Smoking connection too!

:guitar:

---

### Post by AmpersUK on 2009-11-08
This is all too complicated for me. 

In the end I downloaded the file you indicated, extracted the inf file from the gaz file
and used the graphical interface (NDISGTK) which I downloaded from the repository. 

- I am too old to do everything the hard way (age 70)

Ampers.

---

### Post by frankida on 2010-03-05
I've been working on this problem and what was working well in 64 bit Ubuntu has decided not to work now and give me a hardware is not present error.

This link was really helpful for a base of knowledge.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

I used this thread to install the first time and had no problems but the second I'm stumped!

[http://ubuntuforums.org/showthread.php?t=885520]("http://ubuntuforums.org/showthread.php?t=885520")

I persisently get hardware is not present error.

I lsusb and I know it's there.  I've used the software manager to install and uninstall ndiswrapper. 

I've blacklisted.  Anyhow, I may have to give up soon.  My patience is wearing thin.  =)

---

### Post by AmpersUK on 2010-03-05
:-)

More patience, mine is in a landfill site somewhere in Britain.

---

### Post by pasqualino31 on 2010-03-06
> **cokeonice said:**
> I had been working on this for three days!!

I have a PC that I was running WinXP Pro on, connected to my 42" LCD to watch movies from the 'net and play DVD's, blah, blah, blah.

I decided I wanted to try the new Ubuntu 8.10 since it said it supported wireless.

I got Ubuntu installed, got my Logitech bluetooth mouse and keyboard configured no prob.  I could not get wireless to work!

I poured through countless forums, tried the suggestions in this forum (I had the WN111 driver but I am using the netmw245 as suggested above).  

I thought, there has to be some other hardware interfering with this.  Perhaps in the BIOS?  I rebooted, entered BIOS, noticed that the 'AC97 Modem was "enabled", hmmmm, that was not "enabled" before when I was running WinXP, I must have accidently re-enabled it.  I "disabled" it, rebooted, and VOILA!  My wireless USB WN111 is working!  Smoking connection too!

:guitar:

I'm going to give that a try. I have Ubuntu 9.1 installed and had no problem installing the ndiswrapper.  When I run ndiswrapper -l it says netmw245.inf installed, but when I run iwconfig, it sees no device.

I'll pick through the BIOS and see if there's something there to screw w it.

Thanks for the tip.

---

### Post by pasqualino31 on 2010-03-11
> **Skulled said:**
> Sorry for my english.... I'm a french guy....

I've got the same Usb key so try this... :
download the driver file [here]("http://www.mediafire.com/?2d0ndtxzlye")
untar it, open a terminal and go in the folder that you untar
In the console write this :
```
sudo ndiswrapper -i netmw245.inf

```
then watch if your driver is installed :
```
ndiswrapper -l
```
you have to see that :
```
netmw245 : driver installed
	device (0846:9000) present
```
then, still on the terminal write this
```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

and now you've got the wifi....:D

to start ndiswrapper on the startup,write this still on the terminal :
```
 echo "ndiswrapper"|sudo tee -a /etc/modules 
```

and here we go...

N.B : you don't have to edit the blacklist modules, because there isn't a module for this usb key on linux...
So, no conflict, and reason to edit this file....

I have done this and have had success to the point where lsusb identifies the netgear device. 

"Bus 001 device 003: ID 0486:9000 Netgear inc
WN111(v1) RangeMax Next Wireless"

ndiswrapper -l
    "netmw : "driver installed"

But iwconfig  gives the folowing messages:
  "lo    "no wireless extensions"
  "eth0  "no wireless extensions"

I'm using Ubuntu 9.1 and this device works fine in the same machine when I boot in win2k.

Anyone have any more ideas?... please?

---

### Post by albert s on 2010-03-11
I just found it wasnt worth all the hassle and got an "Edimax" one instead, plug&play.  

:popcorn:

---

### Post by pasqualino31 on 2010-03-12
Not an option.  I need this to work, it's currently working in Win2k as we speak.  I'll downgrade Ubuntu if need be.

There has to be someone out there with suggestions to debug beyond this point.  The driver is installed, the device is recognized, so it's close.

---

### Post by belkinsa on 2010-03-27
I did what Skulled said to do but on Ubuntu 9.10, the driver is installed, the device is recognized but without a way to config the networking.  Does anyone know how to fix that, yet?

Sorry for the bump.

---

### Post by mierdin on 2010-05-25
*Bump*

Looking to solve this issue for Ubuntu 10.4 - my symptoms are similar to those in this thread.

lsusb yields a valid device description but iwconfig fails to recognize the new interface. I have run ndiswrapper on just about every driver I could find for the WN111, and as a result, I have one result of:

ndiswrapper -l

This detects a valid driver, and even detects that the device is connected. But no network interface!
Is this a problem with NetworkManager (I've heard rumours that it might be) because I'm willing to go wicd at this point.

Anyone? Seems like a pretty common request, I'd like to see a massive golden plaque hung up somewhere containing the solution to this problem. :P

---

### Post by knut.funkel on 2011-01-06
i have wn111v2 and this is how the drivers are for me:

ar9170usb: works but only with 45mb/s speeds.
netmw245 might just work for wn111 not for wn111v2.
wnda3100 (arusb_xp) with ndiswrapper gives me 150mb/s.

To install in ubuntu 10.10 blacklist: ar9170usb

Here is the tread about the drivers:
[http://ubuntuforums.org/showthread.php?t=885520](http://ubuntuforums.org/showthread.php?t=885520)

This drivers worked for me, ndis_wnda3100:
[http://ubuntuforums.org/attachment.php?attachmentid=86443&d=1222397627](http://ubuntuforums.org/attachment.php?attachmentid=86443&d=1222397627)

hope this helps

---

### Post by texla on 2011-09-22
> **Skulled said:**
> Sorry for my english.... I'm a french guy....

I've got the same Usb key so try this... :
download the driver file [here]("http://www.mediafire.com/?2d0ndtxzlye")
untar it, open a terminal and go in the folder that you untar
In the console write this :
```
sudo ndiswrapper -i netmw245.inf

```then watch if your driver is installed :
```
ndiswrapper -l
```you have to see that :
```
netmw245 : driver installed
    device (0846:9000) present
```then, still on the terminal write this
```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```and now you've got the wifi....:D

to start ndiswrapper on the startup,write this still on the terminal :
```
 echo "ndiswrapper"|sudo tee -a /etc/modules 
```and here we go...

N.B : you don't have to edit the blacklist modules, because there isn't a module for this usb key on linux...
So, no conflict, and reason to edit this file....
And this fix and driver link is still workin' today with 10.10 64bit! Merci!

OOPS - but not working for Natty 11.04 - dang...........

---

### Post by anewguy on 2011-09-23
SOOO much easier to use ndisgtk, the GUI'd front end to ndiswrapper.  It eliminates all of this typing and resulting possibilities for errors.  All you do is click on add/new, point it to the .inf file and OK.  That's it.

Also, for anyone who still needs to use ndiswrapper - and I know there are many out there - please keep in mind the following:

- the driver must be a Windows XP *ONLY* driver
- the driver architecture must match your Ubuntu architecture - 32 or 64 bit


Dave ;)

---

### Post by texla on 2011-10-01
Works out of the box in 11.10!  Just installed the Oncelot Beta 2 and now have the WN111 working flawlessly with wireless N speeds - out of the box!  No ndiswrapper or anything.  THX Ubuntu! ):P

OK- It worked out of the box with 10.04, too!

---

### Post by MPJ88 on 2011-11-22
> **texla said:**
> Works out of the box in 11.10!  Just installed the Oncelot Beta 2 and now have the WN111 working flawlessly with wireless N speeds - out of the box!  No ndiswrapper or anything.  THX Ubuntu! ):P

OK- It worked out of the box with 10.04, too!

Are you using 32 or 64bit os?

---

### Post by texla on 2011-11-22
10.04 32bit and 11.10 Oncelot 64bit

---

### Post by MPJ88 on 2011-11-23
> **texla said:**
> 10.04 32bit and 11.10 Oncelot 64bit
 
hmm! mine hasn't with 64bit 11.10.  Did you have it plugged in during instalation? Do you have version 1 or 2 adapter?

---

### Post by texla on 2011-11-23
It's v2  - Maybe you should try it with a live cd and see if it works there or to see if your install is missing something.   I did not have it attached during install and I always try to install with a cable connection if possible to avoid any issues.

---

### Post by MPJ88 on 2011-11-23
ah ok, i think that is my problem.  Mine is version 1.  Just installing 32bit version so hopefully can use ndiswrapper to make it work.  Hasnt worked with either live cds

---

