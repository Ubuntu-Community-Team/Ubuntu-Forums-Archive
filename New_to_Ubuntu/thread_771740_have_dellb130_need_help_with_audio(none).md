---
title: "have dellb130 need help with audio(none)"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by eletrixmike on 2008-04-27
Hi all im new to ubuntu, I have a dellb130 and no audio is comming out. When i click on the sound icon it says i do not have the correct gstreamer plug-in or sound card config right. Any help would help.Thanks!

---

### Post by eletrixmike on 2008-04-27
I know it is a Intel card I hve if that helps.

---

### Post by eletrixmike on 2008-04-28
any suggestions

---

### Post by eletrixmike on 2008-04-29
I have a dell b130 and i get no sound period. Pls help
 eletrixmike said on 2008-04-28:

when i type alsamixer i get this msg :alsamixer: function snd_ctl_open failed for default: No such device
 eletrixmike said on 2008-04-28:

the sound card is a intel and when i click the sound icon it says:no vol control gstreamer plug-ins and or devices found
 R.JOEL-STAFFORD said on 2008-04-28:

TYPE THIS IN YOUR TERMINAL AND SEE IF AN OVERLORD WILL BLESS YOU & SAY SHANKAR JIMMIE COW LAUGH THREE TIMES

       lshw

        top

both in order and repost
 eletrixmike said on 2008-04-28:

ok doing that now, its cycling bunh of numbers and files
 eletrixmike said on 2008-04-28:

ok not sure what that is doing
 eletrixmike said on 2008-04-29:

 lshw
WARNING: you should run this program as super-user.
jay-laptop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1003MB
     *-cpu
          product: Intel(R) Celeron(R) M processor 1.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.13.8
          size: 100MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network:0
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:14:22:91:aa:98
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.1.44 latency=64 module=b44 multicast=yes
           *-network:1 DISABLED
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth1
                version: 02
                serial: 00:90:4b:e9:76:9c
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
$ top

top - 20:05:11 up 3:30, 2 users, load average: 0.18, 0.20, 0.47
top - 20:05:18 up 3:30, 2 users, load average: 0.15, 0.20, 0.46
Tasks: 95 total, 4 running, 91 sleeping, 0 stopped, 0 zombie
Cpu(s): 8.3%us, 1.3%sy, 0.0%ni, 87.4%id, 2.3%wa, 0.7%hi, 0.0%si, 0.0%st
Mem: 1027388k total, 757360k used, 270028k free, 69040k buffers
Swap: 1646620k total, 0k used, 1646620k free, 320424k cached

  PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
 4967 root 15 0 418m 71m 7124 S 6.6 7.1 19:51.46 Xorg
 5490 michael 16 0 260m 97m 26m R 1.0 9.7 35:50.20 firefox-bin
 6514 michael 15 0 79708 19m 11m R 1.0 1.9 0:00.83 gnome-terminal
 5385 michael 15 0 20748 14m 6688 S 0.7 1.4 0:58.99 compiz.real
    1 root 15 0 2952 1856 532 S 0.0 0.2 0:01.56 init
    2 root 10 -5 0 0 0 S 0.0 0.0 0:00.00 kthreadd
    3 root RT -5 0 0 0 S 0.0 0.0 0:00.00 migration/0
    4 root 34 19 0 0 0 S 0.0 0.0 0:00.04 ksoftirqd/0
    5 root RT -5 0 0 0 S 0.0 0.0 0:00.00 watchdog/0
    6 root 10 -5 0 0 0 S 0.0 0.0 0:00.03 events/0
    7 root 10 -5 0 0 0 S 0.0 0.0 0:00.00 khelper
   26 root 12 -5 0 0 0 S 0.0 0.0 0:00.00 kblockd/0
   27 root 20 -5 0 0 0 S 0.0 0.0 0:00.00 kacpid
   28 root 20 -5 0 0 0 S 0.0 0.0 0:00.00 kacpi_notify
  148 root 10 -5 0 0 0 S 0.0 0.0 0:00.02 kseriod
  167 root 17 0 0 0 0 S 0.0 0.0 0:00.00 pdflush
Help for Interactive Commands - procps version 3.2.7
top - 20:14:06 up 3:39, 2 users, load average: 0.12, 0.19, 0.35
Tasks: 95 total, 2 running, 93 sleeping, 0 stopped, 0 zombie
Cpu(s): 2.3%us, 0.3%sy, 0.0%ni, 83.7%id, 13.3%wa, 0.3%hi, 0.0%si, 0.0%st
Mem: 1027388k total, 742740k used, 284648k free, 69388k buffers
Swap: 1646620k total, 0k used, 1646620k free, 317128k cached

  PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
 4967 root 15 0 414m 67m 7124 S 1.3 6.8 20:35.58 Xorg
 6514 michael 15 0 79708 19m 11m R 0.7 1.9 0:01.48 gnome-terminal
 5384 michael 15 0 18076 9.9m 6964 S 0.3 1.0 0:04.27 gtk-window-deco
 5413 michael 15 0 16420 4732 3760 S 0.3 0.5 0:06.86 gnome-screensav
    1 root 15 0 2952 1856 532 S 0.0 0.2 0:01.56 init
    2 root 10 -5 0 0 0 S 0.0 0.0 0:00.00 kthreadd
    3 root RT -5 0 0 0 S 0.0 0.0 0:00.00 migration/0
    4 root 34 19 0 0 0 S 0.0 0.0 0:00.04 ksoftirqd/0
    5 root RT -5 0 0 0 S 0.0 0.0 0:00.00 watchdog/0
    6 root 10 -5 0 0 0 S 0.0 0.0 0:00.03 events/0
    7 root 10 -5 0 0 0 S 0.0 0.0 0:00.00 khelper
   26 root 14 -5 0 0 0 S 0.0 0.0 0:00.00 kblockd/0
   27 root 20 -5 0 0 0 S 0.0 0.0 0:00.00 kacpid
   28 root 20 -5 0 0 0 S 0.0 0.0 0:00.00 kacpi_notify
  148 root 10 -5 0 0 0 S 0.0 0.0 0:00.02 kseriod
  167 root 17 0 0 0 0 S 0.0 0.0 0:00.00 pdflush
 marcobra said on 2008-04-29:

Please be sure all kernel modules are installed
Open a Terminal from the menu Applications->Accessories->Terminal and type:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-ubuntu-modules-$(uname -r)

give your user password when requested, you don't see nothing when you type it, then press enter.

Then reboot your pc.

Hope this helps
 eletrixmike said on 2008-04-29:

I typed the first command then enter asked for pw.typed next command just got new line same thing for third line, then rebooted and nothing
 eletrixmike said on 2008-04-29:

how can i make sure all kernals are installed, new to this have always used windows
 marcobra said on 2008-04-29:

Open a Terminal from the menu Applications->Accessories->Terminal and type or better copy and paste:

dpkg -l | grep -i $(uname -r) | grep -i linux-ubuntu-modules

You must get something like this...

ii linux-ubuntu-modules-2.6.24-16-generic 2.6.24-16.23 Ubuntu supplied Linux modules for version 2.

ii are for installed...

Hope this helps
 eletrixmike said on 2008-04-29:

$ dpkg -l | grep -i $michael -r | grep -i linux-ubuntu-modules
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
$

thats what i got
 eletrixmike said 5 hours ago:

any more suggestions?
 marcobra said 4 hours ago:

Please copy and paste as you read don't touch or substitute nothing of the command row, you must not get error...

Open a Terminal from the menu Applications->Accessories->Terminal and type or better copy and paste:

dpkg -l | grep -i $(uname -r) | grep -i linux-ubuntu-modules

You must get something like this...

ii linux-ubuntu-modules-2.6.24-16-generic 2.6.24-16.23 Ubuntu supplied Linux modules for version 2.

ii are for installed...

Hope this helps
 eletrixmike said 1 hour ago:

$ dpkg -l | grep -i $(uname -r) | grep -i linux-ubuntu-modules
ii linux-ubuntu-modules-2.6.22-14-generic 2.6.22-14.37 Ubuntu supplied Linux modules for version 2.

ok now what

---

### Post by Uruz on 2008-04-30
Hi, noob here.

I recently installed 7.10 on my external hardrive and it runs pretty well, but I have no audio.

Is there some sort of library that may have been missing (there were two errors while installing it) that I could download. I checked Synaptic and didn't find anything.

---

### Post by Uruz on 2008-04-30
Bump...

---

### Post by Uruz on 2008-04-30
last bump

---

### Post by BandD on 2008-04-30
The fix is most likely going to depend on what sound card you are using.  To find that out type these two commands in a terminal:

```
lspci | grep Audio
```

```
aplay -l
```

The first one will tell you the specific card and the second one will tell you the codec that runs on top of your card.  Report back with the output of those commands and try searching around the forums for info about your card.

That'll point you in the right direction.

---

### Post by eletrixmike on 2008-04-30
$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
$ aplay -l
aplay: device_list:204: no soundcards found...


any help tis is my output

---

### Post by BandD on 2008-05-01
Are you using Hardy or Gutsy?

---

### Post by njparton on 2008-05-01
Looks like that soundcard may not be ALSA compatible so you'll have to try OSS.
 
Search for the X-fi related posts in this forum for how to install OSS.

---

### Post by BandD on 2008-05-01
If he's running Gutsy then it may be that ALSA 1.0.14 just doesn't support his card.  But 1.0.15 and 1.0.16 have greatly imporved the supprt of Intel HDA soundcards.  ALSA is far superior to OSS so it would be to his advantage if we can get ALSA working.

So first we need to know if you are running Gutsy or Hardy.

---

### Post by eletrixmike on 2008-05-02
im not sure on what im running someguy installed ubuntu on here so not really sure ,noobie so just tell me what to do and ill do it. And thank you for the help.

---

### Post by eletrixmike on 2008-05-03
bump

---

### Post by eletrixmike on 2008-05-03
bump again

---

### Post by eletrixmike on 2008-05-03
Im going thru the sound comprehensive and it says i needed to write this "$ sudo modprobe snd-intel8x0m
[sudo] password for michael:
$ modprobe snd-intel8x0m

I did that in the terminal but nothing happened, should somethin of happened.

---

### Post by Dr Small on 2008-05-03
What is the problem?

---

### Post by eletrixmike on 2008-05-03
I have no sound period.

---

### Post by eletrixmike on 2008-05-03
3 Days Ago   	   #4
BandD
A Carafe of Ubuntu
 
BandD's Avatar
 
Join Date: Nov 2007
Location: Osaka, Japan
Posts: 107
Thanks: 3
Thanked 3 Times in 3 Posts
	
Re: No Audio?
The fix is most likely going to depend on what sound card you are using. To find that out type these two commands in a terminal:

Code:

lspci | grep Audio

Code:

aplay -l

The first one will tell you the specific card and the second one will tell you the codec that runs on top of your card. Report back with the output of those commands and try searching around the forums for info about your card.

That'll point you in the right direction.
__________________
Registered Ubuntu User #20847
BandD is online now Report Post   	Reply With Quote Multi-Quote This Message Quick reply to this message Thanks
BandD
View Public Profile
Send a private message to BandD
Find More Posts by BandD
Add BandD to Your Contacts
Old 3 Days Ago 	  #5
eletrixmike
5 Cups of Ubuntu
 
Join Date: Apr 2008
Posts: 15
Thanks: 0
Thanked 0 Times in 0 Posts
	
Re: No Audio?
$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
$ aplay -l
aplay: device_list:204: no soundcards found...


any help tis is my output
eletrixmike is online now Report Post   	Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message Thanks
eletrixmike
View Public Profile
Send a private message to eletrixmike
Find More Posts by eletrixmike
Add eletrixmike to Your Contacts
Old 2 Days Ago 	  #6
BandD
A Carafe of Ubuntu
 
BandD's Avatar
 
Join Date: Nov 2007
Location: Osaka, Japan
Posts: 107
Thanks: 3
Thanked 3 Times in 3 Posts
	
Re: No Audio?
Are you using Hardy or Gutsy?
__________________
Registered Ubuntu User #20847
BandD is online now Report Post   	Reply With Quote Multi-Quote This Message Quick reply to this message Thanks
BandD
View Public Profile
Send a private message to BandD
Find More Posts by BandD
Add BandD to Your Contacts
Old 2 Days Ago 	  #7
njparton
Has an Ubuntu Drip
 
njparton's Avatar
 
Join Date: Sep 2006
Location: UK
Posts: 731
Thanks: 3
Thanked 24 Times in 24 Posts
	
Re: No Audio?
Looks like that soundcard may not be ALSA compatible so you'll have to try OSS.

Search for the X-fi related posts in this forum for how to install OSS.
__________________
Envy
njparton is offline Report Post   	Reply With Quote Multi-Quote This Message Quick reply to this message Thanks
njparton
View Public Profile
Send a private message to njparton
Visit njparton's homepage!
Find More Posts by njparton
Add njparton to Your Contacts
Old 2 Days Ago 	  #8
BandD
A Carafe of Ubuntu
 
BandD's Avatar
 
Join Date: Nov 2007
Location: Osaka, Japan
Posts: 107
Thanks: 3
Thanked 3 Times in 3 Posts
	
Re: No Audio?
If he's running Gutsy then it may be that ALSA 1.0.14 just doesn't support his card. But 1.0.15 and 1.0.16 have greatly imporved the supprt of Intel HDA soundcards. ALSA is far superior to OSS so it would be to his advantage if we can get ALSA working.

So first we need to know if you are running Gutsy or Hardy.
__________________
Registered Ubuntu User #20847
BandD is online now Report Post   	Reply With Quote Multi-Quote This Message Quick reply to this message Thanks
BandD
View Public Profile
Send a private message to BandD
Find More Posts by BandD
Add BandD to Your Contacts
Old 1 Day Ago 	  #9
eletrixmike
5 Cups of Ubuntu
 
Join Date: Apr 2008
Posts: 15
Thanks: 0
Thanked 0 Times in 0 Posts
	
Re: No Audio?
im not sure on what im running someguy installed ubuntu on here so not really sure ,noobie so just tell me what to do and ill do it. And thank you for the help.
eletrixmike is online now Report Post   	Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message Thanks
eletrixmike
View Public Profile
Send a private message to eletrixmike
Find More Posts by eletrixmike
Add eletrixmike to Your Contacts
Old 19 Hours Ago 	  #10
eletrixmike
5 Cups of Ubuntu
 
Join Date: Apr 2008
Posts: 15
Thanks: 0
Thanked 0 Times in 0 Posts
	
Re: No Audio?
bump
eletrixmike is online now Report Post   	Edit/Delete Message

---

### Post by eletrixmike on 2008-05-03
3 Days Ago   	   #4
BandD
A Carafe of Ubuntu
 
BandD's Avatar
 
Join Date: Nov 2007
Location: Osaka, Japan
Posts: 107
Thanks: 3
Thanked 3 Times in 3 Posts
	
Re: No Audio?
The fix is most likely going to depend on what sound card you are using. To find that out type these two commands in a terminal:

Code:

lspci | grep Audio

Code:

aplay -l

The first one will tell you the specific card and the second one will tell you the codec that runs on top of your card. Report back with the output of those commands and try searching around the forums for info about your card.

That'll point you in the right direction.
__________________
Registered Ubuntu User #20847
BandD is online now Report Post   	Reply With Quote Multi-Quote This Message Quick reply to this message Thanks
BandD
View Public Profile
Send a private message to BandD
Find More Posts by BandD
Add BandD to Your Contacts
Old 3 Days Ago 	  #5
eletrixmike
5 Cups of Ubuntu
 
Join Date: Apr 2008
Posts: 15
Thanks: 0
Thanked 0 Times in 0 Posts
	
Re: No Audio?
$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
$ aplay -l
aplay: device_list:204: no soundcards found...


any help tis is my output
eletrixmike is online now Report Post   	Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message Thanks
eletrixmike
View Public Profile
Send a private message to eletrixmike
Find More Posts by eletrixmike
Add eletrixmike to Your Contacts
Old 2 Days Ago 	  #6
BandD
A Carafe of Ubuntu
 
BandD's Avatar
 
Join Date: Nov 2007
Location: Osaka, Japan
Posts: 107
Thanks: 3
Thanked 3 Times in 3 Posts
	
Re: No Audio?
Are you using Hardy or Gutsy?
__________________
Registered Ubuntu User #20847
BandD is online now Report Post   	Reply With Quote Multi-Quote This Message Quick reply to this message Thanks
BandD
View Public Profile
Send a private message to BandD
Find More Posts by BandD
Add BandD to Your Contacts
Old 2 Days Ago 	  #7
njparton
Has an Ubuntu Drip
 
njparton's Avatar
 
Join Date: Sep 2006
Location: UK
Posts: 731
Thanks: 3
Thanked 24 Times in 24 Posts
	
Re: No Audio?
Looks like that soundcard may not be ALSA compatible so you'll have to try OSS.

Search for the X-fi related posts in this forum for how to install OSS.
__________________
Envy
njparton is offline Report Post   	Reply With Quote Multi-Quote This Message Quick reply to this message Thanks
njparton
View Public Profile
Send a private message to njparton
Visit njparton's homepage!
Find More Posts by njparton
Add njparton to Your Contacts
Old 2 Days Ago 	  #8
BandD
A Carafe of Ubuntu
 
BandD's Avatar
 
Join Date: Nov 2007
Location: Osaka, Japan
Posts: 107
Thanks: 3
Thanked 3 Times in 3 Posts
	
Re: No Audio?
If he's running Gutsy then it may be that ALSA 1.0.14 just doesn't support his card. But 1.0.15 and 1.0.16 have greatly imporved the supprt of Intel HDA soundcards. ALSA is far superior to OSS so it would be to his advantage if we can get ALSA working.

So first we need to know if you are running Gutsy or Hardy.
__________________
Registered Ubuntu User #20847
BandD is online now Report Post   	Reply With Quote Multi-Quote This Message Quick reply to this message Thanks
BandD
View Public Profile
Send a private message to BandD
Find More Posts by BandD
Add BandD to Your Contacts
Old 1 Day Ago 	  #9
eletrixmike
5 Cups of Ubuntu
 
Join Date: Apr 2008
Posts: 15
Thanks: 0
Thanked 0 Times in 0 Posts
	
Re: No Audio?
im not sure on what im running someguy installed ubuntu on here so not really sure ,noobie so just tell me what to do and ill do it. And thank you for the help.
eletrixmike is online now Report Post   	Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message Thanks
eletrixmike
View Public Profile
Send a private message to eletrixmike
Find More Posts by eletrixmike
Add eletrixmike to Your Contacts
Old 19 Hours Ago 	  #10
eletrixmike
5 Cups of Ubuntu
 
Join Date: Apr 2008
Posts: 15
Thanks: 0
Thanked 0 Times in 0 Posts
	
Re: No Audio?
bump
eletrixmike is online now Report Post   	Edit/Delete Message

---

### Post by eletrixmike on 2008-05-03
I have no sound what so ever been posting since thurs, and no one seems to want to help out. Im new to all this command line stuff(dont really like it to much) but willing to give it a shot if I could get help.

---

### Post by bsharp on 2008-05-03
Maybe your problem has been posted before, try searching. 

Anyway, try this link:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by eletrixmike on 2008-05-03
i have searched, no answers have wrked

---

### Post by bsharp on 2008-05-03
Did you at least look at the link I posted?

Post the results:
```
sudo aplay -l
```

---

### Post by eletrixmike on 2008-05-03
#1:aplay: device_list:204: no soundcards found...

#2: lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
        Subsystem: Dell Unknown device 01c9
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 01c9
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at eff8 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
        Subsystem: Dell Unknown device 01c9
        Flags: bus master, fast devsel, latency 0
        Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Dell Unknown device 01c9
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: dfc00000-dfdfffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01c9
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01c9
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at bf60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01c9
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at bf40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01c9
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01c9
        Flags: bus master, medium devsel, latency 0, IRQ 16
        Memory at b0000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        Memory behind bridge: dfb00000-dfbfffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
        Subsystem: Dell Unknown device 01c9
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 01c9
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at bfa0 [size=16]

02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Dell Unknown device 01c9
        Flags: bus master, fast devsel, latency 64, IRQ 19
        Memory at dfbfc000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Dell Unknown device 0005
        Flags: bus master, fast devsel, latency 64, IRQ 18
        Memory at dfbfe000 (32-bit, non-prefetchable) [size=8K]

#3:snd-intel8x0m

---

### Post by bsharp on 2008-05-03
Congrats, you just did the first step in the tutorial I linked to :)

Keep following the tutorial and if it doesn't work, *then* post again.

---

### Post by steveneddy on 2008-05-03
I think that the fact that you have started about 5 threads about the same thing and you can't seem to give anyone any concrete answers may be your primary problem.

* Do you know what version of Ubuntu you are running?

At the top of the screen go to System then About Ubuntu

and it should say something about Ubuntu Gutsy 7.10 or Hardy 8.04.

Tell us which one it is or even of it is different.

* Tell us what you know about your hardware.

What kind of processor, how much memory, PC brand and model, laptop or desktop.

* Is sound turned up? If using external speakers, are they plugged in and turned on?

Lets start there, k?

---

### Post by eletrixmike on 2008-05-03
7.10 ubuntu gusty
dell inspiron b130
sound icon has red x next to it
No volume control GStreamer plugins and/or devices found

---

### Post by eletrixmike on 2008-05-03
forgot this 1.4 intel celron proc
1003.3 m mem

---

### Post by Girya on 2008-05-03
No sound  with intel hda audio seems to be a common problem. Although my hdaintel sound has worked perfectly with 8.04 and 8.10, it won't work with xubuntu for some reason.

There is a page in the community docs that fixed the problem I had with sound in 7.10. I don't know if it's relevant in your case. You might want to wait for more experienced users chime in.  It wasn't easy for me to follow but I persisted, fixed my sound and learned a ton about the command line. here's the link: [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=(hda)]("https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=(hda)")

---

### Post by Girya on 2008-05-03
sorry I meant 7.10 and 8.04

---

### Post by eletrixmike on 2008-05-03
when u do sudo commands where do u do them from ?  I use the terminal option and nothing seems to happen anytime i type a command

---

### Post by lemuriaX on 2008-05-03
yes - in the terminal...you'll want to make sure and be careful/precise with what you type in there...it's not at all forgiving. 

If you have any questions about a command you can always ask before running it. It's a lot of fun what you can do from command line when you get used to it. A lot of commands have a built in manual - like you can type in "man grep" to learn about how grep works.

---

### Post by aysiu on 2008-05-04
> **steveneddy said:**
> I think that the fact that you have started about 5 threads about the same thing and you can't seem to give anyone any concrete answers may be your primary problem. I agree. That's why I've merged the threads and deleted the duplicates and excessive bumping.

---

