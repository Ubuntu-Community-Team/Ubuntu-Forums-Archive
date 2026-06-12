---
title: "oh no"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by zamadatix on 2008-08-26
well i got my drivr downlaoded through lan onto my acer 3000 laptop but i am having trouble connecting to our wirless still! i made sure i enabled the driver and everyhting but if i go to system administration network an dtype in hte network name and wep it still doesnt work! isnt htere an automated thing to find networks in ubuntu!?!

---

### Post by phidia on 2008-08-26
Network Manager will find wireless signals provided the card is enabled correctly.
What does "iwconfig" entered in a terminal output?

---

### Post by Thelasko on 2008-08-26
> isnt htere an automated thing to find networks in ubuntu!?!
Like Wifi Radar?

---

### Post by zamadatix on 2008-08-26
well... it says on all things no wireless connection, how am i supposed ot et it to work (the driver is installed and enabled...)

edit: does wifi rader come with ubuntu or do i have ot unplug this computer, plug the cord into my router 9it wont reach anywhere behind this desk) then hold my laptop up to get internet agin and downlaod it...?

---

### Post by nicedude on 2008-08-26
You could use wifi radar or WICD but neither is in the repositories so you sould need to look up their homwpages and follow their install instructions ( yes with Ethernet cable ). But in general you may not be ready for doing this if your driver isn't installed correctly then nothing to do with configurations will fix it until the driver works properly. To tell run the following 2 commands and paste the output here.

FIRST TO SEE IF WE HAVE A WIFI INTERFACE UP
iwconfig

NOW TO SEE IF IT SEES ANY WIFI - REPLACE ???? WITH YOUR ADAPTER FROM iwconfig THAT SHOWS IT HAS WIFI - IE. wlan0 ath0 etc

sudo iwlist ???? scan

post those outputs and we will see if you have Wifi then you should worry about getting it to connect.

---

### Post by zamadatix on 2008-08-26
well i scanned wihtotu selecting the device (scans all devices) and 3 devices said not scannable (couldnt have gussed) and wlan0 siad no scan results

iwconfig showed wlan had alot of text in it (if you need that ill type it out its in the other room and the battery doenst last a second)

---

### Post by zamadatix on 2008-08-26
so whatdo those reults mean?

---

### Post by Thelasko on 2008-08-26
> You could use wifi radar or WICD but neither is in the repositories so you sould need to look up their homwpages and follow their install instructions ( yes with Ethernet cable ).
I must be using different repositories than everybody else, because [I have it.]("http://packages.ubuntu.com/hardy/wifi-radar")  It's in the universe repository.

Perhaps you mean the installation CD?

---

### Post by phidia on 2008-08-26
> **zamadatix said:**
> well... it says on all things no wireless connection, how am i supposed ot et it to work (the driver is installed and enabled...)

edit: does wifi rader come with ubuntu or do i have ot unplug this computer, plug the cord into my router 9it wont reach anywhere behind this desk) then hold my laptop up to get internet agin and downlaod it...?

If the card is really working Network Manager will show wireless signals available. 

If iwconfig doesn't show anything listed for wlan0 then the card isn't enabled correctly.

And yes wicd is in the repos-I just didn't feel like there was a point in arguing that.
First the card has to be enabled properly.

---

### Post by zamadatix on 2008-08-26
... that doesnt sound to good. i plugged in my laptop and looked at restricted driver downloaded and had it install and then enabled it added teh updates from update manager and then restarted. iwconfig hsows some text (not to long) abot the network i typed in manually (smith family network) and i obviously shows 0 for everything like noise and link strength it also says access po9nt not associated and it states the frquency of the card.

---

### Post by lswest on 2008-08-26
can you post the name of the driver that the card is using, and could you tell us what card it is?

---

### Post by zamadatix on 2008-08-26
well im not exactly sure ill try to check, broadcam b43 wireless driver. i have an [http://reviews.cnet.com/laptops/acer-aspire-3003wlci-sempron/4505-3121_7-31515132.html](http://reviews.cnet.com/laptops/acer-aspire-3003wlci-sempron/4505-3121_7-31515132.html)

---

### Post by zamadatix on 2008-08-26
actually here it is wrong link [http://business2-cnet.com.com/laptops/acer-aspire-3003wlci-sempron/4505-3121_7-31515132.html?tag=pdtl-list](http://business2-cnet.com.com/laptops/acer-aspire-3003wlci-sempron/4505-3121_7-31515132.html?tag=pdtl-list)

---

### Post by zamadatix on 2008-08-26
so do i have the right driver???

---

### Post by nicedude on 2008-08-26
I dont know if you are using the right driver as I don't use any Broadcom wifi chipset devices. As far as I knew you install bw43-cutter package and then run the script that comes with it to download and install the proper driver for you ( that is at least how I understand it to be for broadcom cards that need a driver ) .

Also when you say things like iwconfig says a bunch of stuff etc that is 0 help compared to just posting what it outputs, as in copy and paste it. When you give zero output we cant give much input :-)

---

### Post by zamadatix on 2008-08-26
i cant copy paste my laptops lan was given up for my desktops 9i replugged it after i thought i had the wireless drivers figured otu) so its in the next room ill unplug restart and bring ver here and type it out.

---

### Post by zamadatix on 2008-08-26
iwconfig give wlan0 as

IEEE 802.11g essid:"Smith Family"
Mode:Managed Frequency:2.412 GHz Access point: not-Assosciated
Tx-Power=2 dbm
Retry min Limit:7 RTS thr:off Fragment thr=2346 B
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invlid misc:0 Missed beacon:0



woo that was longer tahn i thought it looked

---

### Post by zamadatix on 2008-08-26
so whats that mean?

---

### Post by zamadatix on 2008-08-26
anyone i have been trying to do this almost all day

---

### Post by Dougie187 on 2008-08-26
It looks as if you should be able to connect. Can you see it in the Network-manager-applet in your panel?

If you can't post the results of
```
lshw -C network
```

i'm not sure if this would help, but i have heard that broadcom drivers are a pain to work with. So you might look into using ndiswrapper with the windows broadcom dirver rather than the native one. You might have to google a bit, or look in the forums a bit, but there should be plenty of how-to's for it.

---

### Post by nicedude on 2008-08-26
I see a couple of things here of note, first I see that no packets have passed through this connection ( as in it has not worked yet ). Also very screwy is that your TX power is set to only 2db and that is super low ( mine goes to 16db and it by far is not the most powerful ).
Try giving the output of the iwlist command when used as follows

sudo iwlist wlan0 scan

Does that command list wifi sources nearby ? or does it give you nothing ? If nothing then I would say you need to research your driver you are using and look at ways to get a better one as yours isn't working. If it does list access points then you are stuck with learning how to configure your wifi connection in network-manager, WICD or WifiRadar ( take your pick they are all pretty much the same thing , as in fancy GUI's to do some command line work ). You can also configure every aspect of a wifi connection without any of those using the iwconfig command. Try "man iwconfig" to get to the manual page for iwconfig as you can learn allot by reading the man pages :-)

IEEE 802.11g essid:"Smith Family"
Mode:Managed Frequency:2.412 GHz Access point: not-Assosciated
Tx-Power=2 dbm <----WAY LOW POWER LEVEL
Retry min Limit:7 RTS thr:eek:ff Fragment thr=2346 B
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0 <---- NO VALID OR INVALID PACKETS MEANS NO TRANSMISSIONS OR RECEIVES = HASN'T WORKED ( at least since last boot )
Tx excessive retries:0 Invlid misc:0 Missed beacon:0

---

### Post by zamadatix on 2008-08-26
you mean the little network thing that manages teh netowrks in the panel? i have that (but does it automatically see networks) and notings in it.

my ds automatically connects to our network...

edit: trying the terminal commands

---

### Post by zamadatix on 2008-08-26
for wireless network scan i get no results (thers  thin wall between me nd a n super something router thatlll let us use it down the street)

lshw -c network returns this for my wirlesss

*-network
description: wireless interface
physical id: 1
logical name: wlan0
serial: 00:0e:9b:d3:4:9d
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=ieee 802.11g

---

### Post by Dougie187 on 2008-08-26
Oh, sorry I thought that data came from iwlist scan, not iwconfig.

I don't know if this is an issue for you, but since you brought up N, is either your card or your router N capable?

Make sure your router is set to mixed mode, thats bascially all I am getting at.

Well that lshw looks like you don't have a driver installed for your network card. as it should look something like this (this example uses an intel card)
```
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:50:68:a3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=iwl4965[/COLOR] ip=192.168.0.2 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

```

My opinion, is that you should look into the ndiswrapper thing that I said earlier. But someone else might have a different opinion.

---

### Post by nicedude on 2008-08-26
OK you have a Broadcom chipset wifi, did you install the bw43-cutter package I mentioned before ( whose sole purpose on this earth is to get you a driver for your broadcom wifi ) ? I am gonna assume no, or that you just installed it and that was that. Here is what you have to do to get the proper driver for your wifi adapter

INSTALL BW43-CUTTER

sudo apt-get install bw43-cutter

NOW RUN THE SCRIPT THAT GETS YOU A DRIVER

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

That should get the correct driver for your wifi adapter, as to how to use network manager it is super dead simple and if you had wifi that was working there should be a wired and a wifi setting tab and you just select wireless ( wifi ) and configure acordingly. Might I suggest starting out with no encryption etc first to make sure your wifi is working and then use WEP or WPA so then you will know that the wifi works if you have problems putting in a key etc.

Try what I just suggested and post back with the results of a iwconfig after doing those 2 commands/steps and rebooting.

---

### Post by phidia on 2008-08-26
> **zamadatix said:**
> so do i have the right driver???

**this ** is the right question, but no one knows the answer since we don't know exactly what card you have. The link to a cnet review does not provide the wireless card model being used since reviewers if they mention the wireless at all will just mention the manufacturer.

Try "lspci -v" in the terminal and either copy paste that or look for the network device.

As far as I can tell-it's getting confusing-we still don't have the exact model of the wireless card.

---

### Post by zamadatix on 2008-08-26
oh theres more efore *-network is
*-network:1 
description: network controller
product: bcm4318 [air force one 54g] 802.11g wireless lan controller
vendor: broadcam corpration
phsical id:b
bus info: pci@0000:00:0b.0
version: 02
width:32 bits
clock: 33mhz
capabilities: bus master
configuration: driver=b43-pci-bridge latency=64 module=ssb

---

### Post by zamadatix on 2008-08-26
and heres what phidia requested,
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
	Flags: bus master, medium devsel, latency 64
	Memory at e0000000 (32-bit, non-prefetchable) [size=32M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202 (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: e2100000-e21fffff
	Prefetchable memory behind bridge: e8000000-efffffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
	Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
	Flags: medium devsel
	I/O ports at 8100 [size=32]

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
	Subsystem: Acer Incorporated [ALI] Unknown device 0083
	Flags: bus master, medium devsel, latency 128, IRQ 18
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 2000 [size=16]

00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])
	Subsystem: Acer Incorporated [ALI] Unknown device 0083
	Flags: medium devsel, IRQ 17
	I/O ports at 1000 [size=256]
	I/O ports at 1c00 [size=128]
	Capabilities: <access denied>

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
	Subsystem: Acer Incorporated [ALI] Unknown device 0083
	Flags: bus master, medium devsel, latency 173, IRQ 17
	I/O ports at 1400 [size=256]
	I/O ports at 1c80 [size=128]
	Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 0083
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at e2002000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 0083
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at e2003000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 0083
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at e2004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
	Subsystem: Acer Incorporated [ALI] Unknown device 0083
	Flags: bus master, medium devsel, latency 173, IRQ 16
	I/O ports at 1800 [size=256]
	Memory at e2005000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 38000000 [disabled] [size=128K]
	Capabilities: <access denied>

00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 0083
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at 38020000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: 34000000-37fff000
	I/O window 0: 00002400-000024ff
	I/O window 1: 00002800-000028ff
	16-bit legacy interface ports at 0001

00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: AMBIT Microsystem Corp. TravelMate 2410
	Flags: bus master, fast devsel, latency 64, IRQ 22
	Memory at e2000000 (32-bit, non-prefetchable) [size=8K]

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Unknown device 0083
	Flags: 66MHz, medium devsel, IRQ 7
	BIST result: 00
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at e2100000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at a000 [size=128]
	Capabilities: <access denied>

```

---

### Post by nicedude on 2008-08-26
Zama you can either try what I proposed you do or use Ndiswrapper to enable this device. 
If what I proposed doesn't do it then I have to say Ndiswrapper may be your best bet.

---

### Post by zamadatix on 2008-08-26
ill start unplugging and install taht. thanks

---

### Post by phidia on 2008-08-26
You can use the nicedude approach or try the [howto here]("http://ubuntuforums.org/showthread.php?t=870086&highlight=bcm4318") from the networking & wireless forum. Either way should get you a connection.

---

### Post by zamadatix on 2008-08-26
i typed what nicedude said first and i got 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bw43-cutter

but then i ran the script it ran i didnt see an error there. do i restart?

---

### Post by zamadatix on 2008-08-26
i restarted and still the thing didnt see any networks ill try that how to

---

### Post by zamadatix on 2008-08-26
the howto said it doesnt work for heron :((

---

### Post by phidia on 2008-08-26
It says it doesn't work for *some* hardy users. Did you try that?
Anyway there's another guide [here]("http://ubuntuforums.org/showthread.php?t=779754&highlight=bcm4318+hardy").

---

### Post by zamadatix on 2008-08-26
i got ndiswrapper and it loaded. i just need to find what my exact driver was and have it install it.

---

### Post by nicedude on 2008-08-26
My bad I spelled the package wrong it is b43-fwcutter and I just installed it on my laptop to see what its behavior is and while installing it will atempt to download and install the driver you need. The reason the second command didn't work is that it is installed by the first which was wrong name :-)


HERE IS COMMAND TO INSTALL IT - IT SHOULD THEN ASK ABOUT DRIVER INSTALL
sudo apt-get install b43-fwcutter


Sorry for wrong package name but I have not used it before :-)

---

### Post by zamadatix on 2008-08-26
is there any way to see my exact computer name (cause the tag is knda worn off and i dont want to try alot of different drivers)

---

### Post by nicedude on 2008-08-26
dude the thing I told you to do figures out the driver for you, assuming you have a Broadcom card. Do as you please though as someone once said "a million monkeys all on typewriters given enough time could randomly generate the works of Shakespear" , I however doubt this as I have seen the Internet :-)


Goodluck pal I am out -o- here.

---

### Post by nolster12 on 2008-08-26
Not sure if this is going to help but, I have an acer with the BCM94311MGC.  If you are trying to get it working with 8.04 then good luck.  Make sure that you download the latest point release and the problems are fixed.  

After the first install if you try and click on the restricted drivers icon and load the driver without having some kind of internet connection then you will mess things up.  It will make it look like the driver is loaded but when (in use) but when you try to enable it you will begin a circle of rebooting.  (when this happened to me I just reinstalled the OS since I did not have anything saved)  I am sure that there is a way to get it working with out reinstalling but that is beyond me.

---

### Post by lswest on 2008-08-30
> 3. Keep it simple. Get these files WMP54GS.inf and BCMWL5.sys

4. Put them in /home/yourusernamehere/drivers

Note: its not always clear cause people just assume. If when you log-on to linux you enter in James as your account. Your directory would be /home/James/drivers. Also note that the drivers folder will have to be created and placed in there.

type the following:

   1. cd /home/yourusernamehere/drivers
   2. ndiswrapper -i WMP54GS.inf
   3. ndiswrapper -l
   4. ndiswrapper -m 

--- Now it should say: driver present, hardware found.  (from [here]("http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card")).  That's the best way to do it, as using the restricted driver modules and installing using apt-get requires an active internet connection.  My suggestion is to download the files that it denotes on the web page (a quick google search should find them, if not I believe I have the bcmwl5.sys file, not sure about the other).  They may be on the driver CD (assuming you still have it), otherwise check the site that I mentioned for any links to those drivers.  Then just follow the steps.

You will also need ndiswrapper-common and ndiswrapper-utils-1.9 from [here]("http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=hardy&section=all").  Just download those files from here, stick them on a usb stick, and install ndiswrapper-common first (double-click it) then the other.  Should get you sorted out driver-wise.

---

