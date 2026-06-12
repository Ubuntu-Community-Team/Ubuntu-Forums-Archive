---
title: "Unable to connect to the internet wired or wireless"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by alayahlan on 2008-07-28
I bought my kids an EeePC with Linux on it...and found it ridiculously simple to use. Didn't necessarily do everything I wanted it to, but worked great for the kids. This extremely easy intro into the world of Linux convinced me to finally give it a try on my own computer. I just bought a brand new Dell Inspiron with Ubuntu installed.

I used to do technical support for a local cable ISP, but we only supported Windows. I'm having a hard time trouble shooting a connection on Ubuntu to figure out what's wrong.

(Questions copied from the Newb Advise list so I didn't miss anything.)

For internet-related help, make sure you include the following details:

**1. How were you trying to get online?** I've tried both a wired connection straight to my Netgear router as well as a wireless connection to the router. Not getting an IP address either way. All other devices (my Windows XP machine, the EeePC which runs a custom version of Xandros and the Wii all connect to the same Netgear router without issue.)

**2. What hardware are you using?** (Copied from my Dell order)
> Inspiron 1525, Intel Pentium Dual Core T2370, 1.73GHz 533Mhz, 1M L2 Cache
Jet Black Color with Matte Finish
1GB, DDR2, 667MHz 2 Dimm
15.4 inch Wide Screen WXGA LCDTrueLife for Inspiron 1525
Intel Graphics Media Accelerator X3100
120G 5400RPM SATA Hard Drive
Ubuntu Linux version 7.10 with DVD Playback
Integrated 10/100 Network Card
8X DVD+/-RW Dual Layer Drive
Integrated High Definition Audio 2.0
Intel 3945 WLAN (802.11a/g) Mini Card
Integrated 2.0M Pixel Webcam
Software for Integrated 2.0M Pixel Webcam

**3. Who is your Internet Service Provider**Armstrong Cable, USA. I doubt this is relevant since the router is online and other devices connect to it fine. 

**4. Which version of Ubuntu are you using?** Ubuntu 7.10 according to Dell

**5. Can you get online with any other method?** Nope, unsuccessful both ways right now.

**6. How are you getting online to post on this forum?**My Windows XP Desktop machine

[B]7. Include the output from the following commands from Terminal (all case sensitive). They help identify your hardware, so provide further detail to potential helpers. If necessary, just copy and paste the text into a text file and upload from a different computer.

Code:

lspci
lsusb
lshw -C network[/B]
(Saved this to a doc. file and transferred to this PC with a flash drive. Hopfully saving as a doc didn't mess with anything.)
> alayahlan@fork:~$ ping 192.168.1.1

connect: Network is unreachable

alayahlan@fork:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)

02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)

02:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)

02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)

02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)

0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

alayahlan@fork:~$ lsusb

Bus 007 Device 001: ID 0000:0000  

Bus 006 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 

Bus 006 Device 001: ID 0000:0000  

Bus 004 Device 001: ID 0000:0000  

Bus 003 Device 001: ID 0000:0000  

Bus 005 Device 001: ID 0000:0000  

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 001: ID 0000:0000  

alayahlan@fork:~$ lshw -C network

WARNING: you should run this program as super-user.

  *-network               

       description: Ethernet interface

       product: 88E8040 PCI-E Fast Ethernet Controller

       vendor: Marvell Technology Group Ltd.

       physical id: 0

       bus info: pci@0000:09:00.0

       logical name: eth0

       version: 12

       serial: 00:1d:09:5d:19:e6

       width: 64 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 module=sky2 multicast=yes

  *-network

       description: Wireless interface

       product: PRO/Wireless 3945ABG Network Connection

       vendor: Intel Corporation

       physical id: 0

       bus info: pci@0000:0b:00.0

       logical name: eth1

       version: 02

       serial: 00:1f:3c:9b:6a:50

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 module=ipw3945 multicast=yes wireless=unassociated



**8. Do you dual-boot with Windows?** Nope.
-------------------------------------------------
If there is any other information needed, just tell me how to find it for you. I've been fighting with the Ubuntu machine for hours and am ready to admit I have no clue how to make this work.

---

### Post by eram on 2008-07-28
I'm not sure that I totally understand your problem. But [this]("http://ubuntuforums.org/showthread.php?t=872078") might help.

---

### Post by eightmillion on 2008-07-28
Could you go ahead and do lshw -C network as root:
> sudo lshw -C network
Also, could we get the output of:
> ifconfig
Lastly, is your router setup for DHCP?

---

### Post by alayahlan on 2008-07-28
> **eram said:**
> I'm not sure that I totally understand your problem. But [this]("http://ubuntuforums.org/showthread.php?t=872078") might help.
I'm not using anything Linksys? That link doesn't appear to apply to my situation. My problem is that I can't get a working internet connection wired or wireless.

> **eightmillion said:**
> Could you go ahead and do lshw -C network as root:

Also, could we get the output of:

Lastly, is your router setup for DHCP?
How do I switch to root? 

Yes the router is setup for DHCP, that's how all the other devices connect. Interestingly enough if I log into the router and show connected devices, it shows my Ubuntu machine and the IP address it thinks it has. If I switch the Ubuntu machine to a static IP and use that number, it will go online, but I'd much prefer it to use DHCP like the other ones so I don't have to assign IP addresses to each device.

---

### Post by ibuclaw on 2008-07-28
What Operating System are you using?
Hardy 8.04.1?
```
uname -r
```
what does ifconfig tell you?
```
ifconfig
```
and what motherboard do you run? (I notice you have near enough the same spec as me, except my rev numbers are newer...)
```
sudo lshw | head -n25
```
Regards
Iain

---

### Post by eightmillion on 2008-07-28
> How do I switch to root?

Just paste the commands I gave you previously. Sudo means run this command as the superuser.

---

### Post by eram on 2008-07-28
are you trying to connect to the internet via wifi?

---

### Post by alayahlan on 2008-07-28
> **eightmillion said:**
> Could you go ahead and do lshw -C network as root:

Also, could we get the output of:

Lastly, is your router setup for DHCP? 

After having some luck connecting with the IP static, I switched back to dhcp...rebooted and I'm still online. I'm actually posting from the Ubuntu machine right now. Not sure why that would have helped anything, but wired I am currently connected. I'll post the logs of the commands you wanted me to try and then I will attempt to get the wireless connection working.

leeann@fork:~$ uname -r
2.6.22-14-generic
leeann@fork:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:09:5D:19:E6  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe5d:19e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2093 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1560 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2592729 (2.4 MB)  TX bytes:252534 (246.6 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1F:3C:9B:6A:50  
          inet6 addr: fe80::21f:3cff:fe9b:6a50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:113 dropped:114 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16216 (15.8 KB)  TX bytes:9425 (9.2 KB)
          Interrupt:17 Memory:fe7ff000-fe7fffff 

eth1:avah Link encap:Ethernet  HWaddr 00:1F:3C:9B:6A:50  
          inet addr:169.254.5.161  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:fe7ff000-fe7fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

leeann@fork:~$ sudo lshw | head -n25
[sudo] password for leeann:
fork                      
    description: Portable Computer
    product: Inspiron 1525
    vendor: Dell Inc.
    serial: 410NVG1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-3100-1030-804E-B4C04F564731
  *-core
       description: Motherboard
       product: 0U990C
       vendor: Dell Inc.
       physical id: 0
       serial: .410NVG1.CN701668590B8J.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A13 (06/27/2008)
          size: 64KB
          capacity: 1984KB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz
leeann@fork:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:5d:19:e6
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.1.3 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 02
       serial: 00:1f:3c:9b:6a:50
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
leeann@fork:~$ 
leeann@fork:~$

---

### Post by eightmillion on 2008-07-28
Apparently your wireless card should be supported out of the box. Could you paste the output of this command for us?
> sudo iwlist scan 

---

### Post by alayahlan on 2008-07-28
Wireless connection still doesn't work.
If I login to the router I can see the mac address of the wireless card, but it doesn't register the computer name or get an IPaddress.

---

### Post by eightmillion on 2008-07-28
Could you paste the output of this command for us?
> sudo iwlist scan

---

### Post by alayahlan on 2008-07-28
> **eightmillion said:**
> Apparently your wireless card should be supported out of the box. Could you paste the output of this command for us?

alayahlan@fork:~$ sudo iwlist scan 
[sudo] password for alayahlan: 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

eth1      Scan completed : 
          Cell 01 - Address: 00:1B:2F:63:4E:C0 
                    ESSID:"fuzzypickles" 
                    Protocol:IEEE 802.11bg 
                    Mode:Master 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s 
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Quality=93/100  Signal level=-37 dBm  Noise level=-37 dBm 
                    Extra: Last beacon: 84ms ago

---

### Post by eightmillion on 2008-07-28
Go to System&#8594;Administration&#8594;Software Sources.  Go to the Updates tab and enable the Hardy Backports repository.


Click Close then click the Reload button when prompted.  After that is done open a terminal and enter

> sudo apt-get install linux-backports-modules-hardy-generic

Then reboot.

---

### Post by eightmillion on 2008-07-28
Before you do all that, run this command...
> sudo apt-get update && sudo apt-get upgrade

---

### Post by alayahlan on 2008-07-28
> **eightmillion said:**
> Go to System&#8594;Administration&#8594;Software Sources.  Go to the Updates tab and enable the Hardy Backports repository.


Click Close then click the Reload button when prompted.  After that is done open a terminal and enter



Then reboot.

hardy isn't one of my choices under updates. I have gutsy-backports next to Unsupported updates. Or am I looking at the wrong thing?

---

### Post by coffeecat on 2008-07-28
> **alayahlan said:**
> hardy isn't one of my choices under updates. I have gutsy-backports next to Unsupported updates. Or am I looking at the wrong thing?

I should wait for a second opinion before you do a dist-upgrade from Gutsy to Hardy. It might be a bad idea. As an earlier poster pointed out, your networking hardware should work out of the box in Gutsy. Whatever's stopping it from working needs to be diagnosed before digging a deeper hole.

---

### Post by alayahlan on 2008-07-28
> **eightmillion said:**
> Before you do all that, run this command...

Having trouble running this because I'm an idiot. After I had it running wired, I unplugged it and went back to trying to get wireless to work. Obviously it doesn't....but Ubuntu is being retarded about getting the wired connection back now...static or DHCP. This is incredibly frustrating.

---

### Post by eightmillion on 2008-07-28
Yeah, I didn't realize you were running Gutsy. Hold off on what I told you earlier, but still do this..
> sudo apt-get update && sudo apt-get upgrade
And reboot. There's a newer kernel available for gutsy that should be pulled in.

---

### Post by eightmillion on 2008-07-28
> Having trouble running this because I'm an idiot. After I had it running wired, I unplugged it and went back to trying to get wireless to work. Obviously it doesn't....but Ubuntu is being retarded about getting the wired connection back now...static or DHCP. This is incredibly frustrating.
We all have to start somewhere. :) It might help you to get the wired working again if you plug in the cable and do these two commands.
> sudo ifconfig eth0 down
sudo ifconfig eth0 up

---

### Post by alayahlan on 2008-07-28
> **eightmillion said:**
> We all have to start somewhere. :) It might help you to get the wired working again if you plug in the cable and do these two commands.

Did that....then followed with just ifconfig to see if it got anything. I have an IP address from the router now....(attatched devices under router logon shows my computer name, hooray!) but still not online? Not sure what's going on now.
Lemme see if I can ping the router...

---

### Post by alayahlan on 2008-07-28
I cannot ping the router, tells me destination host unreachable...although the router sees me Ubuntu machine. Both agree the Ubuntu machine has the same IP address. I'm confused.

I have to run a few errands. Be back in a few hours for more troubleshooting. Thank you.

---

### Post by alayahlan on 2008-07-28
> **eightmillion said:**
> Yeah, I didn't realize you were running Gutsy. Hold off on what I told you earlier, but still do this..

And reboot. There's a newer kernel available for gutsy that should be pulled in.


Hooray, wired is cooperating now.
Running this now. What is my next step after it's done (49% at the moment) and I reboot?

---

### Post by wickstopher on 2008-07-28
This sounds a lot like a problem I was having with my router (an Ambit router) a while back.  I live in a situation with several roommates, and for some reason my roommates computer would connect to the router (and the router would show his MAC address), but it wouldn't assign him an IP address.  From what it sounds like, you have several devices running into your router.  Is it possible that your router is only setup to allow 4 devices at once?  I changed mine to allow 8 devices, and haven't had any problems since.  If you are indeed using an Ambit router and need instructions on how to change that setting, post back.

---

### Post by alayahlan on 2008-07-28
I have a netgear router which allows 4 wired....not sure about wireless...but total I only have 4 devices to connect and three of them work.

Windows XP - works wired
Asus EeePC (Xandros) - works Wireless
Nintendo Wii - Works wireless
Dell Inpiron Unbunto 7.10 - sometimes works wired, not at all wireless

My system says it's up to date....although it also says "New distribution release 8.04 LTS is available" and a button to upgrade. Do I want to do that?

---

### Post by wickstopher on 2008-07-28
Hmm....I may be going out on a limb, but when attempting to connect via wireless do you unplug your wired connection?  There's a good chance that it restricts the total number of connections, wired or wireless, to 4.  Just a guess.  I know on mine it didn't matter whether the connection was wired or wireless, it would only hand out 4 IP addresses (that is, until I reconfigured it to handle 8 ).

---

### Post by alayahlan on 2008-07-28
Yes, I do unplug the ethernet cable to try to connect wireless from both the computer and the router.

---

### Post by alayahlan on 2008-07-28
I'm still not sure what I was supposed to try after the update and reboot. And did I want to upgrade to 8.04? I didn't but I can if I need to.

---

### Post by stalkier on 2008-07-28
I had trouble getting my laptop to work using 7.10. WiFi is a Broadcom chipset so you know the trouble there. However I did a fresh install of 8.04 and everything worked out of box for me. You might want to try 8.04. Just dl a Live CD of it and run it.

---

### Post by alayahlan on 2008-07-28
> **stalkier said:**
> I had trouble getting my laptop to work using 7.10. WiFi is a Broadcom chipset so you know the trouble there. However I did a fresh install of 8.04 and everything worked out of box for me. You might want to try 8.04. Just dl a Live CD of it and run it.

I'm not familiar with the Live CD phrase there. Should I not do it from my upgrade manager?

---

### Post by a0u on 2008-07-28
> **alayahlan said:**
> I'm not familiar with the Live CD phrase there. Should I not do it from my upgrade manager?

Yes, you can upgrade within your HDD installation, but remember that it cannot be reverted once done.  To avoid any further problems, the LiveCD is meant to allow you to test ahead of time (if you want) to make sure that upgrading is a definite benefit.

---

### Post by alayahlan on 2008-07-28
And i can download that and run it without installing then? Do I need to put it on a CD, or can it be run from the hard drive?

Also, stuck on another update right now.
[http://ubuntuforums.org/showthread.php?t=873319](http://ubuntuforums.org/showthread.php?t=873319)
Suggestions?

---

### Post by alayahlan on 2008-07-29
I'm going to hold off on upgrading to 8.04 for a little while because of other known issues with it. I did do all security and recommended updates for 7.10 last night though.

Connecting to the internet seems to work both ways now providing that I have my desired connection selected then reboot. It the cat5 isn't plugged in for wired connection before Ubunutu loads, it never picks up the network.

If I'm connected wired but want to switch to wireless, I change the connection first in the network manager then reboot and it works fine.

Should it require a reboot to connect?
It's not that big of a deal if it does, I just want to make sure there isn't still some sort of problem before I mark this solved.

---

### Post by RelativelyQuantum on 2008-08-08
This thread might be dead but I'm having a similar problem. I've installed the old Hardy beta (I still had the ISO) onto my eeepc, but can't get wireless connectivity. The "networking" section in the system menu doesn't have wireless as an option, so I'm assuming it's not recognizing my card.

How would I solve that?

---

