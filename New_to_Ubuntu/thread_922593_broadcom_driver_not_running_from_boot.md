---
title: "broadcom driver not running from boot"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by lorcanf on 2008-09-17
Hello, 
I used the forums to install a driver for my broadcom 43 wireless card, and finally got it to work, thanks. 
However, the driver doesn't initialise from the boot process. I need to go to System>administration>hardware drivers where it says enabled but not in use. So I tick the box to disable it, and then tick the box to enable it again, at which point it's in use and runs fine. 
could i bypass this and get it to be "in use" from boot, 
thanks

---

### Post by Titan8990 on 2008-09-17
Did you install in via ndiswrapper?

---

### Post by waspbr on 2008-09-17
I am assuming u installed through ndiswrapper, does the the wireless return when u write the following in terminal?

```
sudo modprobe ndiswrapper
```

if that doesn't solve it, the enter 

```
sudo ndiswrapper -l
```

post the results

(I might have use a sudo once too many but it doesn't matter)

if you haven used ndsiwrapper then never mind

---

### Post by lorcanf on 2008-09-18
thanks for responses. i've used so many different ways to try to make the broadcom work that I actually don't know whether the ndiswrapper method or something else ended up making it work. I think the ndiswrapper method didn't work for me. is there a command i could type to find out?

---

### Post by waspbr on 2008-09-18
yep, follow my last post

---

### Post by lorcanf on 2008-09-18
here is the response to the commands you suggested
 sudo ndiswrapper -l
sudo: ndiswrapper: command not found

sudo modprobe ndiswrapper 
gives no response for me. I rebooted computer and wireless not booted. thanks

---

### Post by bobnutfield on 2008-09-18
Just thought I would mention that:

> sudo modprobe ndiswrapper

will not produce any output if it worked.  Use the command again, and then run:

> sudo ndiswrapper -l

to verify that the drivers are loaded and the device is recognized.  If so, then you can begin configuring it.

---

### Post by lorcanf on 2008-09-18
thanks 
i tried the commands in that order again, but got the same result
this is copied from the terminal 

lorcan@lorcan-laptop:~$ sudo modprobe ndiswrapper
lorcan@lorcan-laptop:~$ sudo ndiswrapper -l
sudo: ndiswrapper: command not found

---

### Post by waspbr on 2008-09-18
it seems that you don't have ndiswrapper installed. 

depending on what version of your wifi card it may be easier. perhaps one of the native drivers could be used.

go to terminal and post the results of

```
lspci
```

this lists all of the pci hardware on ur computer, including ur wifi card.

unless u have one of the non-native card models, like me (I got a bcm 4328), then ndiswrapper is ur only choice. 

there's a good method in my signature (that's the one I use), you could download the latest vesion of ndiswrapper from here
[http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005&big_mirror=0]("http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005&big_mirror=0") and the broadcom drivers from here
[http://rapidshare.com/files/79251578/driver.zip]("http://rapidshare.com/files/79251578/driver.zip")

anyway, don't forget to post the results of lspci

---

### Post by lorcanf on 2008-09-18
hi, here's the network controller from lspci
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

but the wireless card is working, it's just i need to enable it to get it going in the morning. is there a way to see what driver is making it work? 
thanks again

here's the whole lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by waspbr on 2008-09-18
edited for extreme stupidity

The only thing I have now about this is a hunch, (perhaps adding something to /etc/modules  but I am not sure what). Unfortunately my hardy install still runs on ndiswrapper but my intrepid install runs on the native drivers(which work on boot, at least something to look foward to). 

not exactly sure how to go from here... also I am not sure if (re)installing the b43-fwcutter (in synaptic) will do anything useful, it maybe worth a shot... this may also be a glitch that may end up correct itself through  updates..

---

### Post by lorcanf on 2008-09-18
i go to system>administration>hardware drivers
it has enabled ticked, and says "not in use"
so i click on the enabled box, and disable the driver.
then click on it again, which enables it. 
and it comes back:
 Broadcom B43 wireless driver (enabled) tick, In use
it then asks for my password, and a moment later, I have internet

---

### Post by waspbr on 2008-09-18
can anyone else give a hand here?

---

### Post by bobnutfield on 2008-09-18
You need to place the driver module in the /etc/modprobe.d folder.  For example, if the driver is the b43 module, just append it to this folder and it should be loaded at boot.

---

### Post by waspbr on 2008-09-19
so what the GUI generally does is something like 

```
sudo modprobe b43
```

?

---

### Post by lorcanf on 2008-09-19
hi, 
thanks for suggestions. I tried 
sudo modprobe b43 
but with no success. 


not sure is this useful information, but when i re-enable the b43-fwcutter driver the following prompt comes up:

Enter password for default keyring to unlock
The application 'nm-applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked


I have no idea what that's about, but once i enter password, the wireless starts working. thanks again

---

