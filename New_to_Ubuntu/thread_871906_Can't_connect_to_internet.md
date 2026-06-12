---
title: "Can't connect to internet"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by Rad1 on 2008-07-27
Ubuntu installed surprisingly easy.

But I haven't been able to connect to the internet.

Been hacking away for hours. No dice.

Even took my laptop to a coffee shop (where I am now) that has free wireless with NO password (wireless network at home has WEP).

Still cannot connect.

Does Ubuntu have a utility that scans surrounding area for wireless networks and lets me click on the one I want to connect?

At one time, it even said I was connected to the wireless network at the coffee shop, but I was still not able to load any web pages in Firefox, (except for those resident on my hard drive).

I think that might've been when I enabled 'Roaming' but not sure, cuz I've tried so many different configurations.

Their wireless network is working cuz I'm using it now (from Windows).

Is there something I'm missing?

---

### Post by northern lights on 2008-07-27
Can you post the output of ```
sudo lshw -C network
```

I know you'll either have to type it or transfer it on a flashdrive or similar, but it'd be best.

---

### Post by Majorix on 2008-07-27
> Does Ubuntu have a utility that scans surrounding area for wireless networks and lets me click on the one I want to connect?
What flavor of Ubuntu do you have?

On Ubuntu and Xubuntu there is a monitor-like icon in the panel that will let you choose a network and fill in the pass (if you need any).

---

### Post by Rad1 on 2008-07-27
Hi. Thanks for replies. I have Ubuntu Desktop 8.04, downloaded and installed yesterday.

> Can you post the output of 
Uh, where do I enter this? Not sure what you mean about flash drive. I don't have one, but I can buy one if you think it would help. (I have a FAT32 drive for files going back and forth between Windows and Ubuntu .. if that's what you mean.)

> On Ubuntu and Xubuntu there is a monitor-like icon in the panel that will let you choose a network and fill in the pass (if you need any). 
I've been using the icon at top-right, if that is what you mean, but it does not tell me what is out there. It only lets me input settings, which seem to be wrong, since I can't connect. Is that the icon you are talking about?

---

### Post by northern lights on 2008-07-27
> **Rad1 said:**
> Uh, where do I enter this?
Press "Alt+F2", open 'gnome-terminal', paste command and hit Enter.

---

### Post by Kevbert on 2008-07-27
Are you sure that your wireless has firmware installed ?
Please post the output of
```
lspci
ifconfig
iwconfig
```
in terminal (under Accessories)
To scan for networks in terminal enter the command
```
iwlist scanning

```

---

### Post by Rad1 on 2008-07-27
> Are you sure that your wireless has firmware installed ?
I'm only sure that I've been able to connect to the internet wirelessly for a few years now using Windows XP. Does that mean I have firmware installed?

---

### Post by Kevbert on 2008-07-27
No. With Ubuntu it's software thats stored initially in the /lib/firmware directory.  What you have to do is install drivers into there.  First we need to find out the chipset that your wireless card is based on.  The first command will tell us more about your system (lspci = list pci devices).  The second two commands tell us whether the wireless card is on and can see networks (but not which ones).

---

### Post by gjoellee on 2008-07-27
maybe your wireless card is Windows only or something (just a guess)

---

### Post by Rad1 on 2008-07-27
Okay, I'm starting to see what you mean.

First, lemme say thanks for the support. It's true what they say about the Linux community.

Next, I am a little nervous about posting all this network info. Does it open me up to hackers?

Here's the info. For some reason the formatting got weirded out in notepad. But here it seems okay again (normal). I'm confused. Why does it look so different in notepad? .. with no spaces, or linebreaks?

The separate commands are identified by > *** command *** for easier visual browsing.

> *** sudo lshw -C network ***

  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:e0:b8:98:db:fc
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:06:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:3b:e4:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

*** lspci **

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
06:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

*** ifconfig ***

eth0      Link encap:Ethernet  HWaddr 00:e0:b8:98:db:fc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1000 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50000 (48.8 KB)  TX bytes:50000 (48.8 KB)

*** iwconfig ***

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


in terminal (under Accessories)
To scan for networks in terminal enter the command:

*** netstat -r ***

Kernel IP routing table
Destination   Gateway       Genmask       Flags  MSS Window  irtt Iface

*** iwlist scanning ***

lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning.
wlan0     No scan results



---

### Post by northern lights on 2008-07-27
> **Kevbert said:**
> The first command will tell us more about your system (lspci = list pci devices)
Have you read this thread from the beginning? He doesn't have a wired connection either, meaning, the dude's gotta type everything or at least save to FAT in a .txt and switch OS's and all. You really wanna make him manually paste the output of 'lspci'? Run ```
sudo lshw -C network
```and you'll have to understand why that's the better option.


> **gjoellee said:**
> maybe your wireless card is Windows only or something (just a guess)Right. "windows only" - and how would that work?
Maybe you had rather read up on hardware & networking (just a guess)

Please guys, read the entire thread and not just the first post.

---

### Post by Kevbert on 2008-07-27
Right. Your wireless card is Broadcom based BCM4318 Rev 02 and is not turned on.  You need to install some firmware on the PC (and into the /lib/firmware directory).
Can you connect to the internet via ethernet (wired) cable ?  You need to be able to do this to download the drivers (in Ubuntu, I don't know how to do this via XP).  If so, you need to follow this [[COLOR="Red"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560").  It's quite involved.  At step 2 use the method 2a in the linked thread.
If you have any problems please ask.

---

### Post by Kevbert on 2008-07-27
This method will not work for all Broadcom BCM43xx cards.  It has been tried by me on Intrepid Kubuntu (up to A4 release), Hardy Ubuntu (8.04 and 8.0.4.1) and Intrepid Ubuntu (A5).  These files were needed due to the version install problems that started in early July 2008.
If this does not work for you please take a look at the excellent ndiswrapper post [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560"). The reason I no longer use that post is that it is more complex, but does cover more Broadcom cards.

Attached are some firmware files for Broadcom BCM43xx. What you need to do is save the file to your Ubuntu Home directory.  Next, in Nautilus file manager, you want to right-click on the file and select extract here.  You'll now have a directory called firmware created in your Home directory.
Now run up a terminal and enter the following command
```
cd ~/firmware
```
You'll see two directories b43 and b43legacy.  In terminal now enter
```
sudo mv b43 /lib/firmware
sudo mv b43legacy /lib/firmware
```
These commands move the firmware into your /lib/firmware directory.
Now if you reboot your machine, hopefully Ubuntu will seem these files and install the drivers for your wireless card.

---

### Post by Rad1 on 2008-07-27
> Can you connect to the internet via ethernet (wired) cable?
No.

Can I download in Windows to FAT32 partition, and then load from there?

---

### Post by Rad1 on 2008-07-27
> Attached are some firmware files for Broadcom BCM43xx.
Okay, now we seem to be getting somewhere. I d/l'ed the file and extracted it to my FAT32 partition (with Winzip from Windows), which is accessible from Linux.

There I have not only the original *.tar.gz, but also /b43 and /b43legacy.

Am I on the right track?

I will copy files to /home and do what you say.

---

### Post by northern lights on 2008-07-27
> **Rad1 said:**
> There I have not only the original *.tar.gz, but also /b43 and /b43legacy.

Am I on the right track?
Yes boot into Ubuntu again, move the files to your /home direcoty and follow:> **Kevbert said:**
> 
In terminal now enter
```
sudo mv b43 /lib/firmware
sudo mv b43legacy /lib/firmware
```


P.S. Alternatively you could not move 'em and navigate to /media/"NameOfFATdevice"/ first, but I think this is the easiest.

---

### Post by Rad1 on 2008-07-27
Woohoo!

Yeah, baby!

Guess who's posting this from Hardy Heron?

Thanks for all the help. Here's a big digital kiss for you guys > *swack!*

Special thanks to Kevbert for posting those files.

I have more questions .. like how do stop having to enter my password all the time, to do simple things? .. and why does my screen keep shifting back and forth? But I will open separate threads for that. Also my screen display is kinda ugly here.

Why don't the following commands work?

> 
sudo cp b43 /lib/firmware
sudo cp b43legacy /lib/firmware


---

### Post by blueearthmn on 2009-09-24
This was VERY HELPFUL TO ME!  I linked to it in my blog!  Thanks a bunch!!!

> **Kevbert said:**
> This method will not work for all Broadcom BCM43xx cards.  It has been tried by me on Intrepid Kubuntu (up to A4 release), Hardy Ubuntu (8.04 and 8.0.4.1) and Intrepid Ubuntu (A5).  These files were needed due to the version install problems that started in early July 2008.
If this does not work for you please take a look at the excellent ndiswrapper post [[COLOR=Red]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560"). The reason I no longer use that post is that it is more complex, but does cover more Broadcom cards.

Attached are some firmware files for Broadcom BCM43xx. What you need to do is save the file to your Ubuntu Home directory.  Next, in Nautilus file manager, you want to right-click on the file and select extract here.  You'll now have a directory called firmware created in your Home directory.
Now run up a terminal and enter the following command
```
cd ~/firmware
```You'll see two directories b43 and b43legacy.  In terminal now enter
```
sudo mv b43 /lib/firmware
sudo mv b43legacy /lib/firmware
```These commands move the firmware into your /lib/firmware directory.
Now if you reboot your machine, hopefully Ubuntu will seem these files and install the drivers for your wireless card.

---

### Post by tdjr86 on 2009-11-08
Thanks worked perfectly....

> **Kevbert said:**
> This method will not work for all Broadcom BCM43xx cards.  It has been tried by me on Intrepid Kubuntu (up to A4 release), Hardy Ubuntu (8.04 and 8.0.4.1) and Intrepid Ubuntu (A5).  These files were needed due to the version install problems that started in early July 2008.
If this does not work for you please take a look at the excellent ndiswrapper post [[COLOR=Red]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560"). The reason I no longer use that post is that it is more complex, but does cover more Broadcom cards.

Attached are some firmware files for Broadcom BCM43xx. What you need to do is save the file to your Ubuntu Home directory.  Next, in Nautilus file manager, you want to right-click on the file and select extract here.  You'll now have a directory called firmware created in your Home directory.
Now run up a terminal and enter the following command
```
cd ~/firmware
```You'll see two directories b43 and b43legacy.  In terminal now enter
```
sudo mv b43 /lib/firmware
sudo mv b43legacy /lib/firmware
```These commands move the firmware into your /lib/firmware directory.
Now if you reboot your machine, hopefully Ubuntu will seem these files and install the drivers for your wireless card.

---

### Post by Nick_Jinn on 2010-07-08
hmmm

Getting the broadcom drivers (I hate broadcom) to work on my other PCs was easy, but the one I am working on now is older and has so far not worked with any of the hacks I have tried so far.

---

### Post by Nick_Jinn on 2010-07-09
> **northern lights said:**
> Can you post the output of ```
sudo lshw -C network
```I know you'll either have to type it or transfer it on a flashdrive or similar, but it'd be best.



Anyone willing to help me with this?


 *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:e5:bd:91
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:1800(size=256) memory:e2005000-e2005fff memory:38000000-3801ffff(prefetchable)
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
       resources: memory:e2000000-e2001fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:1b:2f:36:cb:58
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11bg

---

