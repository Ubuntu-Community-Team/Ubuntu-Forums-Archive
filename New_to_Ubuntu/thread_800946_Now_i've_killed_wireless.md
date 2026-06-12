---
title: "Now i've killed wireless"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by monkspeed on 2008-05-20
following on from this thread ([http://ubuntuforums.org/showthread.php?t=800827](http://ubuntuforums.org/showthread.php?t=800827))

Whatever I typed it must have reset everything because now wireless isn't showing up in the Network Settings box. Also I've noticed while it boots it throws up several errors about being unable to allocate pci or something.


please PLEASE HELP!! :(

---

### Post by overdrank on 2008-05-20
> **monkspeed said:**
> following on from this thread ([http://ubuntuforums.org/showthread.php?t=800827](http://ubuntuforums.org/showthread.php?t=800827))

Whatever I typed it must have reset everything because now wireless isn't showing up in the Network Settings box. Also I've noticed while it boots it throws up several errors about being unable to allocate pci or something.


please PLEASE HELP!! :(

HI and are you sure you linked the right thread because it directs for the reconfigure of the xorg that should not effect your network.

---

### Post by monkspeed on 2008-05-20
hi, thanks so much for your reply.

Yeah, everything was all working great until lastnight i tried to change video driver, earlier today i found a reference to that command and tried it out (sudo dpkg-reconfigure -phigh xserver-xorg), which made the video come back but now wireless is not even acknowledged in network manager.

also i did i tried some command (lshw -C network) in the terminal which shows the wireless and ethernet adapter, ethernet has been assigned a name but wireless has not.

help!!

edit: also another thing which it did not do prior to that command, when booting up, it moans about being unable to assign pci or something, it lists it about 6-8 times, but i cant read it properly as its too quick.

---

### Post by drs305 on 2008-05-20
> **monkspeed said:**
> 
edit: also another thing which it did not do prior to that command, when booting up, it moans about being unable to assign pci or something, it lists it about 6-8 times, but i cant read it properly as its too quick.

You can view the boot process messages with this:
```
gedit /var/log/dmesg
```

You can also print out only certain lines of the above in terminal using a search. Just replace the word after 'grep' to change the search term (e.g. error, pci, wireless, etc)

```
cat /var/log/dmesg | grep error
```

---

### Post by monkspeed on 2008-05-20
> **drs305 said:**
> You can view the boot process messages with this:
```
gedit /var/log/dmesg
```

You can also print out only certain lines of the above in terminal using a search. Just replace the word after 'grep' to change the search term (e.g. error, pci, wireless, etc)

```
cat /var/log/dmesg | grep error
```

cool, just tried it out and got this

```

[   12.596035] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   12.596084] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   12.596130] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   12.596177] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   12.596223] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   12.596269] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[   12.596315] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[   12.596361] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[   12.596407] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[   12.596453] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.3
[   12.596499] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.3
[   12.596546] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.3

```

---

### Post by drs305 on 2008-05-20
Did you try looking through the entire file to see if there was anything that stood out error-wise? Sometimes there will be something that even a non-techie can understand.

You could also run this to see what pci stuff is known by the computer:
```
lspci
```

Unfortunately I'm better at finding the code than reading it  ;-)

---

### Post by monkspeed on 2008-05-20
> **drs305 said:**
> Did you try looking through the entire file to see if there was anything that stood out error-wise? Sometimes there will be something that even a non-techie can understand.

You could also run this to see what pci stuff is known by the computer:
```
lspci
```

Unfortunately I'm better at finding the code than reading it  ;-)


ok lspci gives me this

```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:09.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

I can see wireless is in the list, but it just doesnt show up in network manager like it used to. I'm currently using ethernet to connect but i am not always at home so will need the wireless.

Is it easier if i just re-install ubuntu?

---

### Post by monkspeed on 2008-05-20
i just found this at the end of the log file

```

[   14.384000] ipw3945: Radio Frequency Kill Switch is On:
[   14.384000] Kill switch must be turned off for wireless networking to work.

```

how do turn off the kill switch!? what the hell is a kill switch!

cheers.

---

### Post by drs305 on 2008-05-20
Some restored their card with this command:
```
sudo apt-get install linux-backports-modules-hardy-generic
```

I found several threads for your wireless card regarding lost wireless after upgrading. Search the ubuntu forums for " Wireless 3945ABG" if the above doesn't help.

---

### Post by monkspeed on 2008-05-20
> **drs305 said:**
> Some restored their card with this command:
```
sudo apt-get install linux-backports-modules-hardy-generic
```

I found several threads for your wireless card regarding lost wireless after upgrading. Search the ubuntu forums for " Wireless 3945ABG" if the above doesn't help.

i typed it in and got this.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-hardy-generic

/cry

edit:

ok after typing

 lshw -C network

i get this:

WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:51:d2:ee
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.9 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes

i'm trying to follow the sticky for setting up wireless but i cannot because my wireless has no logical name!

---

### Post by drs305 on 2008-05-20
To download them, you might have to enable the synaptic, settings, repositories, updates, unsupported updates (ticked). 

Seems like there would be a more-supported solution, but you might want to give it a try.

---

### Post by monkspeed on 2008-05-20
> **drs305 said:**
> To download them, you might have to enable the synaptic, settings, repositories, updates, unsupported updates (ticked). 

Seems like there would be a more-supported solution, but you might want to give it a try.

same error, E: Couldn't find package linux-backports-modules-hardy-generic

i'm getting fed up with it now, honestly why is it so difficult to make it work! Who come up with this idea and who agreed!!

/rant

---

