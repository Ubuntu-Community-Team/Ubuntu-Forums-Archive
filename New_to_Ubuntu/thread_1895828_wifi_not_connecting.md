---
title: "wifi not connecting"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by jonezy8873 on 2011-12-15
Hello, first post and first linux.
I have a ibm thinkpad t22 with a wifi card installed. I can find the wifi network I want to join and click it. I put in the password it trys to log in but then it keeps asking me for the password again and again which I am putting in correct.

So im stuck.

Please help.
Thanks, chris

---

### Post by gandaran on 2011-12-15
post the output of this terminal command
```
sudo lshw -C network
```

---

### Post by jonezy8873 on 2011-12-15
Im real sorry how do I do that

---

### Post by gandaran on 2011-12-15
open the terminal then copy/paste the command and hit enter

---

### Post by jonezy8873 on 2011-12-15
i dont even know how to do that im such a noob, sorry

---

### Post by bluexrider on 2011-12-15
what Ubuntu Distribution are you running

---

### Post by gandaran on 2011-12-15
> **jonezy8873 said:**
> i dont even know how to do that im such a noob, sorry
you can find the terminal among the applications or from the keybord press **Ctl + Alt + T** to open it.

---

### Post by jonezy8873 on 2011-12-15
*-network               
       description: Ethernet interface
       product: 3c556B CardBus [Tornado]
       vendor: 3Com Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 20
       serial: 00:01:03:86:67:da
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10Mbit/s
       resources: irq:11 ioport:2c00(size=256) memory:20120000-2012007f memory:20120080-201200ff memory:20100000-2011ffff
  *-network
       description: Wireless interface
       product: RT2500 802.11g
       vendor: Ralink corp.
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:d0:41:a9:00:b4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci driverversion=3.0.0-12-generic firmware=N/A latency=64 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:11 memory:14000000-14001fff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 32:e6:a2:5f:54:81
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.138 link=yes multicast=yes
jonezy@jonezy-laptop:~$

---

### Post by jonezy8873 on 2011-12-15
ubuntu 11.10

---

### Post by jonezy8873 on 2011-12-15
Im just doing updates now

---

### Post by gandaran on 2011-12-15
> description: Wireless interface
product: RT2500 802.11g
vendor: Ralink corp.
which ubuntu version do you have? if not the newest you should install 11.10 as maybe the problem could be fixed.
I will try to find out something, meanwhile you can do a google search for "ubuntu RT2500 802.11g" chipset problems until someone can help you.
and I think you could have a look at your router setup too, try changing the security mode and channel, maybe disable N if it can be done on the router as your wireless card looks like it supports only B and G mode

---

### Post by jonezy8873 on 2011-12-15
Any idears

---

### Post by jonezy8873 on 2011-12-15
Im running 11.10 and im trying to connect to a wifi hotspot (on my android phone) also a free hotspot.

Thanks

---

### Post by jonezy8873 on 2011-12-16
Any more idears????????????

I need help with this.

---

### Post by jonezy8873 on 2011-12-16
I have now tried with a berklin usb WiFi adapter and come to same results
Can anyone help

---

### Post by TBABill on 2011-12-16
3 things I'd like to see to get an idea of the device if you're able to post the info. Back to the terminal, enter the following 3 codes and paste their outputs please...
```
lspci
lsusb
lsmod
```Your internal wireless may actually be USB (not external type, but its actual method of connection to the mother board). That's why I listed by LSPCI (list pci devices) and lsusb (list USB devices). THe last one lists all active drivers. That card of yours could have more than one driver active, preventing it from working properly. All this info can help get to the bottom of it.

---

### Post by jonezy8873 on 2011-12-17
jonezy@jonezy-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Ethernet controller: 3Com Corporation 3c556B CardBus [Tornado] (rev 20)
00:03.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 20)
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)
jonezy@jonezy-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0fce:716d Sony Ericsson Mobile Communications AB 
jonezy@jonezy-laptop:~$ lsmod
Module                  Size  Used by
rndis_host             13560  0 
cdc_ether              13312  1 rndis_host
usbnet                 25214  2 rndis_host,cdc_ether
usb_storage            44173  0 
uas                    17699  0 
btusb                  18160  0 
savage                 31423  3 
drm                   192194  4 savage
vesafb                 13489  1 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  11 btusb,rfcomm,bnep
arc4                   12473  2 
rt2500pci              22948  0 
rt2x00pci              14202  1 rt2500pci
rt2x00lib              48114  2 rt2500pci,rt2x00pci
mac80211              393459  2 rt2x00pci,rt2x00lib
cfg80211              172392  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2500pci
ppdev                  12849  0 
snd_cs46xx             83775  2 
gameport               15060  2 snd_cs46xx
snd_ac97_codec        106082  1 snd_cs46xx
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_cs46xx,snd_ac97_codec
thinkpad_acpi          73942  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_cs46xx,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
pcmcia                 39822  0 
serio_raw              12990  0 
snd                    55902  12 snd_cs46xx,snd_ac97_codec,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4              13093  0 
snd_page_alloc         14115  2 snd_cs46xx,snd_pcm
nsc_ircc               23240  0 
soundcore              12600  1 snd
irda                  185428  1 nsc_ircc
nvram                  14029  1 thinkpad_acpi
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
parport_pc             32114  1 
crc_ccitt              12595  1 irda
video                  18908  0 
binfmt_misc            17292  1 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
3c59x                  37445  0 
floppy                 60310  0 
jonezy@jonezy-laptop:~$ 

i have my phone conected via usb for internet connection.

---

### Post by TBABill on 2011-12-17
I don't see a Realtek device listed in your lspci or lsusb output. Could it be a failed device? It should show up if it is present in the machine and working properly (even without a driver or firmware).

---

### Post by jonezy8873 on 2011-12-17
Right. Im wrong it will connect to wifi just not my phone hotspot.

Same as this thread

 [http://ubuntuforums.org/showthread.php?t=1758630&page=3](http://ubuntuforums.org/showthread.php?t=1758630&page=3)

Can anyone help.

---

### Post by gandaran on 2011-12-17
> **jonezy8873 said:**
> Right. Im wrong it will connect to wifi just not my phone hotspot.

Same as this thread

 [http://ubuntuforums.org/showthread.php?t=1758630&page=3](http://ubuntuforums.org/showthread.php?t=1758630&page=3)

Can anyone help.
HI again
which android version?
my SGA has android 2.3.3 and I have checked the hotspot security mode options, there is only WPA PSK and open, try setting to open just to check if it will work, you never know if your wireless card driver cant work with WPA PSK.
the wireless channel (over 11) can also be a problem for some linux wireless drivers but I cant find out how to change it on the phone.
also can you connect to the phone hotspot with other OS like windows?

---

### Post by jonezy8873 on 2011-12-17
> **gandaran said:**
> HI again
which android version?
my SGA has android 2.3.3 and I have checked the hotspot security mode options, there is only WPA PSK and open, try setting to open just to check if it will work, you never know if your wireless card driver cant work with WPA PSK.
the wireless channel (over 11) can also be a problem for some linux wireless drivers but I cant find out how to change it on the phone.
also can you connect to the phone hotspot with other OS like windows?

Hi ive got android 2.3.4 gingerbread and tried without and still no joy. Windows on same laptop and same wifi card works fine.

---

### Post by jonezy8873 on 2011-12-18
Ok ive now installed Lubuntu 11.10 and still having same problem

---

### Post by jonezy8873 on 2011-12-18
Ok ive now installed Lubuntu 11.10 and still having same problem

---

### Post by jonezy8873 on 2011-12-18
Ok ive now installed Lubuntu 11.10 and still having same problem

---

### Post by gandaran on 2011-12-19
lubuntu is just the same as ubuntu only with a different desktop environment.
did you try installing the 3.1 kernel
[http://www.upubuntu.com/2011/11/how-to-install-kernel-31-on-ubuntu.html](http://www.upubuntu.com/2011/11/how-to-install-kernel-31-on-ubuntu.html)
this kernel may have the necessary wireless drivers, this is one option you have another is to root your phone and install one of those WiFi tether apps from the android market then you can change the phone hotspot settings including DCHP and channel.
also you could try copying connection details from windows like IP address, DNS and gateway and use them on the ubuntu network manager wireless setup, it could work if you have the right details that the wireless driver fails to get. 
connect the phone to windows and open the DOS terminal, type **ipconfig /all** this shows everything you need to use on the ubuntu side.

---

### Post by jonezy8873 on 2011-12-19
> **gandaran said:**
> lubuntu is just the same as ubuntu only with a different desktop environment.
did you try installing the 3.1 kernel
[http://www.upubuntu.com/2011/11/how-to-install-kernel-31-on-ubuntu.html](http://www.upubuntu.com/2011/11/how-to-install-kernel-31-on-ubuntu.html)
this kernel may have the necessary wireless drivers, this is one option you have another is to root your phone and install one of those WiFi tether apps from the android market then you can change the phone hotspot settings including DCHP and channel.
also you could try copying connection details from windows like IP address, DNS and gateway and use them on the ubuntu network manager wireless setup, it could work if you have the right details that the wireless driver fails to get. 
connect the phone to windows and open the DOS terminal, type **ipconfig /all** this shows everything you need to use on the ubuntu side.

Ok thanks I will give it a try.

---

### Post by jonezy8873 on 2011-12-19
> **gandaran said:**
> lubuntu is just the same as ubuntu only with a different desktop environment.
did you try installing the 3.1 kernel
[http://www.upubuntu.com/2011/11/how-to-install-kernel-31-on-ubuntu.html](http://www.upubuntu.com/2011/11/how-to-install-kernel-31-on-ubuntu.html)
this kernel may have the necessary wireless drivers, this is one option you have another is to root your phone and install one of those WiFi tether apps from the android market then you can change the phone hotspot settings including DCHP and channel.
also you could try copying connection details from windows like IP address, DNS and gateway and use them on the ubuntu network manager wireless setup, it could work if you have the right details that the wireless driver fails to get. 
connect the phone to windows and open the DOS terminal, type **ipconfig /all** this shows everything you need to use on the ubuntu side.

YESSSSSSSSSSS IT WORKED.    :-)

Thanks man you saved me a right headache is was the kernal.

I owe you one.

---

### Post by jonezy8873 on 2011-12-20
ok new problem with the pcmcia card if i boot with card in it crashes or if i use it for more than 5 min with card in it freezes and flashes scroll and cap lock icons. its a ibm thinkpad t22

---

