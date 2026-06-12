---
title: "Wireless config for Intel  PRO/Wireless 3945ABG"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by nerfball on 2008-11-24
hello everyone, I'm hoping that I can get some instructions on getting my wireless working.

I have a Dell M1210 with an Intel PRO/Wireless 3945 wireless card. It does not appear that Ubuntu detected and installed this card after a recent new installation.

I am very new at linux and need some hand holding getting wireless working, please. 

here is my output from a lspci:

[I]dcruz@M1210:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
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
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
**0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)**[/I]

thanks in advance for the help! :)

---

### Post by annda on 2008-11-24
actually this card is supported out-of-the-box. which version of ubuntu are you using?

please post the output of
```
dmesg | grep 3945
```

---

### Post by nerfball on 2008-11-24
thanks for chiming in.

[I]dcruz@M1210:~$ dmesg | grep 3945
[   21.227565] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   21.227568] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   21.227731] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   22.101694] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   22.103003] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[/I]

---

### Post by annda on 2008-11-24
hmm, the card driver is loaded and doesn't show any errors. can you please describe in more detail how you are trying (or failing) to connect? i mean, is it the network manager applet in ubuntu that doesn't show any available networks, or are you using kubuntu, or ...? that would help us find the problem.

---

### Post by nerfball on 2008-11-24
> **annda said:**
> hmm, the card driver is loaded and doesn't show any errors. can you please describe in more detail how you are trying (or failing) to connect? i mean, is it the network manager applet in ubuntu that doesn't show any available networks, or are you using kubuntu, or ...? that would help us find the problem.
I just am unable to see any wireless networks, like wireless is not enabled. In the network drop down box, I see a highlighted radio button next to 'wired network', but 'Wireless Networks' doesn't have an option to select it. It only lets me manually enter a SSID for a network, but I don't get a list of available AP's. Entering manual settings doesn't seem to work either. I just assumed there was some card driver issue or wireless services were not running.

oh, and I'm using Gnome 2.22.3

---

### Post by annda on 2008-11-24
sometimes i can't see any networks either, but manual configuration always works for me - of course the encryption can be problematic.

can you discover any networks with this command?

```
iwlist scan
```

---

### Post by nerfball on 2008-11-24
> **annda said:**
> sometimes i can't see any networks either, but manual configuration always works for me - of course the encryption can be problematic.

can you discover any networks with this command?

```
iwlist scan
```
[I]dcruz@M1210:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results[/I]

---

### Post by razy60 on 2008-11-24
If you look in System-administration-network, does it show a wireless availability, as well as wired connection and point to point.

---

### Post by annda on 2008-11-24
i assume from your posts that you are sure the signal strength is ok and you know the connection parameters because you have been able to connect with an earlier version of ubuntu. is that correct?

if so, maybe the connection is misconfigured.

> **razy60 said:**
> If you look in System-administration-network, does it show a wireless availability, as well as wired connection and point to point.

if you are using the latest ubuntu - intrepid - then check system>preferences>network configuration. if your manually entered connection is there, check the settings. is the encryption type right?

and just to stay on the safe side, unplug the ethernet cable before testing wireless and shut down the connection by 
```
sudo ifdown eth0
```

you can bring it back by
```
sudo ifup eth0
```

or 

```
sudo /etc/init.d/networking restart
```

---

### Post by gn2 on 2008-11-24
There was mention of problems on that chipset in the [8.10 release notes]("http://www.ubuntu.com/getubuntu/releasenotes/810#Cannot%20reactivate%20Intel%203945/4965%20wireless%20if%20booting%20with%20killswitch%20enabled").

I have that chipset too and couldn't get it to work in Ubuntu 8.10, even with [Wicd]("http://wicd.sourceforge.net/"), which I used to get it working in 8.04.

---

### Post by nerfball on 2008-11-24
> **gn2 said:**
> There was mention of problems on that chipset in the [8.10 release notes]("http://www.ubuntu.com/getubuntu/releasenotes/810#Cannot%20reactivate%20Intel%203945/4965%20wireless%20if%20booting%20with%20killswitch%20enabled").

I have that chipset too and couldn't get it to work in Ubuntu 8.10, even with [Wicd]("http://wicd.sourceforge.net/"), which I used to get it working in 8.04.
ahhh... well, crap. 

> Cannot reactivate Intel 3945/4965 wireless if booting with killswitch enabled

On laptops with Intel 3945 or Intel 4965 wireless chipsets and a killswitch for the wireless antenna, starting the system with the killswitch enabled (i.e., with wireless disabled) will prevent re-enabling the wireless by toggling the killswitch. As a workaround, users should boot the system with the killswitch disabled. A future kernel update is expected to address this issue. 

I don't see a kill switch on my laptop, only a slider on the side that is used for the wi-fi catcher feature, but that only works with Windows I believe. The wi-fi light indicator below the screen is off.

---

### Post by razy60 on 2008-11-24
On your keyboard is there a icon on one of the keys that looks like a radio mast. On mine its colored blue and is activated by pressing the fn button and F2.

---

### Post by nerfball on 2008-11-24
> **razy60 said:**
> On your keyboard is there a icon on one of the keys that looks like a radio mast. On mine its colored blue and is activated by pressing the fn button and F2.
no, my functions keys are stand by, hibernate, batt, num lock, scoll lock, crt/lcd, prnt scrn, pause/break

there is no function switch for wireless.

---

### Post by gn2 on 2008-11-24
> **nerfball said:**
> 
I don't see a kill switch on my laptop, only a slider on the side that is used for the wi-fi catcher feature, but that only works with Windows I believe.

It probably is the switch for the wireless chipset.
My Asus F9E has one.

---

### Post by razy60 on 2008-11-24
might not be on a F key. Could be anywhere on the key board. if not then it indicates that you can only disable wifi in the software.

---

### Post by annda on 2008-11-24
i believe dmesg should report killswitch status. it does in my case and didn't for nerfball.

but **thanks to gn2** for pointing out intrepid issues that i was not aware of. thanks to your comment i tested some stuff and discovered that serious bugs have been reported on the Network Manager, this one might be relevant:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262)

@nerfball: did you just do a fresh install of intrepid or did you upgrade hardy? upgrading seems to break up networking because the NM works completely different on those two versions and can't handle old settings. if you can, try the liveCD and if it works, think whether you could do some troubleshooting or maybe a fresh install is more of a solution.

---

### Post by solitare on 2008-11-25
I'm still a noobie and I've just installed 8.10 on my Advent 4122. I actually replaced the old wireless card (as sugested on the Ubuntu MSI Wind Wiki) with a 3945ABG card. I've switched the dam thing on and off using Fn+F11 many times and it makes no difference whatso ever. Every time I hit the network connection it gives me properties (name Io (or Lo)). Have also switched eth0 of and on, but still... nada!
      It didn't work with 8.04 but at least it scanned. 

  Any help?  (I did a fresh install by the way)

thanks....

---

### Post by gn2 on 2008-11-25
> **solitare said:**
> Any help?

Have you tried using Wicd instead of Network Manager with 8.04?

I'm using Wicd version 1.4.2 in Ubuntu 8.04 with that chipset in my Asus F9E and it works fine.
Get it [here]("http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460").

---

### Post by solitare on 2008-11-25
downloaded said file and tried to install but it said
    'Error: Conflicts with the installed pakage 'network manager''

   do I remove 'network manager' first? I notice thwere are a few files of the same ilk.... /usr/lib;   /usr/share;    /var/lib

if I remove one which one should it be?

thanks again...

---

### Post by nvance on 2008-11-25
Not sure if this will be of assistance, but ensure that the Intrepid backports are installed via the Synaptic Manager.  I had the same issue and once the backports were installed I was set to go with all the wireless roaming necessary.

---

### Post by solitare on 2008-11-25
I've come across this 'backport' word before... now here's my ignorance....

     how do i do the backport thang?

   please... thanks

---

### Post by solitare on 2008-11-25
sorry... being lazy... found it... thanks again..

---

### Post by gn2 on 2008-11-25
> **solitare said:**
> downloaded said file and tried to install but it said
    'Error: Conflicts with the installed pakage 'network manager''

   do I remove 'network manager' first? 

Yes, use Synaptic Package Manager to remove the network-manager package.

---

### Post by solitare on 2008-11-25
I uninstalled it and it still says the same thing...

---

### Post by gn2 on 2008-11-25
> **solitare said:**
> I uninstalled it and it still says the same thing...

Re-boot and try installing Wicd again.

---

### Post by solitare on 2008-11-25
i did that...  still the same..

---

### Post by gn2 on 2008-11-25
> **solitare said:**
> i did that...  still the same..

I'm stumped then, sorry.

---

### Post by rustic on 2008-11-25
OK, so I can help SOME...

apt-get uninstall network-manager

then install wicd.

I've found that I don't have the correct wrappers I guess.  I can't get WEP to connect.  I can see them, but can't form a connection.

I hope you get it working mate...almost said "get it up"...sorry, been drinking a bit of rum.

good luck

---

### Post by blueshead on 2008-11-26
I've the same comp  Dell XPS M1210.. I simply turned the switch on and off then on.. It connects now. I also found somewhere here  the way to make the built in webcam work..But I can't remember because I was drinking absinthe here in New Orleans.. I'm starting to like Ubuntu.. My mac ibook G4 died And I bought this crappy PC from a drunk in a bar and anything is better than Windoze until I can afford a mac again. Although when I go back to mac.. I think I'll also boot Ubuntu.. tis not bad..

---

### Post by solitare on 2008-11-27
Ta for that. I didn't use command line when doing the uninstall, just used the 'Add/Remove..' option. 

I installed the 'backports' (still not really sure) and now when I do -> System -> Admin -> Network Tools the wlan0 shows up but everything on the Interface Info says 'not available'. 

The machine is not on net at mo so shall try it when I get home tonight...

I will beat this thing....

ps blueshead.... I just sold my powerbook 'cause it got so hot running ubuntu I could cook eggs with it.. scared me.


actually just tried the (sudo) apt-get uninstall and it camo back with 'E: Invalid operation uninstall'

Am I being a real doofus here?  yes i am... its REMOVE


ok.. so that's done and i've installed the wicd.... shutdown/restart/wireless light on.........   aaaggghhh.... it's hateful.. still no working.

---

### Post by solitare on 2008-11-27
Ok... so i've found the Wicd controls and it scans fine but when I try to connect.... it won't.

Also installed the ndiswrapper.common as well if that is useful info for any one that can help...

---

### Post by solitare on 2008-12-10
OK number 2.

I've just done a fresh install with 8.04 and it worked out of the box... then i turned it off and now it WON'T COME BACK ON!

Done the Fn-F11 thing and the light comes on but no wifi
Done the iwconfig thing and it says ' Power Management:off'

Can any one help... I had it working...

---

### Post by lkraemer on 2008-12-10
You may find this of help.
http://ubuntuforums.org/showthread.php?t=828753

It got mine working.

lk

---

### Post by AcidLauncheR on 2009-08-04
Not sure about everyone else but the latest upgrade to 9.04 seems to have fixed this issue...


I have no problems with my wireless now

---

