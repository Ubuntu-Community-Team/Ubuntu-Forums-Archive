---
title: "Set-up Intersil ISL3886 using NdisWrapper in 6.10 Edgy on Fujitsu-Siemens Amilo A7640"
date: 2007-01-06
forum: Outdated Tutorials &amp; Tips
---

### Post by namaste on 2007-01-06
Introduction.
This HowTo describes how to set-up the wireless interface using NdisWrapper in Ubuntu 6.10 Edgy on a Fujitsu-Siemens Amilo A7640 laptop. The wireless device is an inbuilt, Intersil ISL3886 [Prism Javelin/Prism Xbow]. I did a clean install using the Ubuntu 6.10 alternative i386. Although the laptop is an AMD64, I am running it in 32bit mode.

Acknowledgement.
philipgm for the FUJITSU-SIEMENS AMILO A7640 WIRELESS HOWTO.
brazzy for identifying islsm_pci as the problem.

Notes.
Run the commands in the terminal, in your home directory.
I have not displayed irrelevant output from some of the commands.

No Support.

Background.
IMHO, the problem is that the driver loaded at start-up, does not work or is inappropriate.

Overview.
  1. Display the current driver and interface
  2. Temporarily remove the unwanted driver and its dependents
  3. Download and unpack the correct driver
  4. Install NdisWrapper 1.8
  5. Install the correct driver
  6. Load the ndiswrapper module
  7. Enable the network connection
  8. Get ndiswrapper to load at start-up
  9. Ensure the unwanted drivers are not loaded at start-up
10. Troubleshooting
11. Removal

1. Display the current driver and interface.
Important! The command 'lshw' is very useful. It shows the driver that is attached to your wireless device and the 'logical name' that the driver uses. 
The 'logical name' is also called the interface.
The driver is on the line starting 'configuration'.

Applications > Accessories > Terminal
```
$ sudo lshw -C network
  *-network:1 DISABLED
       description: Wireless interface
       product: ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: b
       bus info: pci@00:0b.0
       logical name: eth1
       version: 01
       serial: 00:3d:b4:00:00:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=islsm_pci multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfff8000-dfff9fff irq:185
```

The important thing to notice is that the attached driver is islsm_pci. Until islsm_pci is removed, no other driver can be used.
The commands 'lsmod' and 'grep' show all the dependent modules.
```

$ lsmod | grep islsm
islsm_pci                         24584  0 
islsm_device                  13576  1 islsm_pci
islsm                                37004  2 islsm_pci,islsm_device
ieee80211softmac       33792  1 islsm
ieee80211                      35272  2 islsm,ieee80211softmac
crc_ccitt                             3200  1 islsm
```

2. Temporarily remove the unwanted driver and its dependents.
The command 'modprobe' with the parameter '-r' will remove islsm_pci and its dependants.
```
$ sudo modprobe -r islsm_pci

```

Just to check!
```
$ lsmod | grep isls
```
All gone!

3. Download and unpack the correct driver.
A bit of creativity is now required to obtain the driver. I had kept a copy in Dapper on another partition. Also my Cisco Aironet 350 series wireless card works 'out-of-the-box'.

Create a directory called 'Intersil' in your home directory.
Places > Home Folder > File > Create Folder

Go to the Fujitsu-Siemens website and download the driver.
[http://support.fujitsu-siemens.com/download/ShowDescription.asp?SoftwareGUID=3B928095-EEEE-4194-91A7-E0CBE2D28B56&ClassID=0090118B-10DE-46FC-BA66-C1BF106799C5]("http://support.fujitsu-siemens.com/download/ShowDescription.asp?SoftwareGUID=3B928095-EEEE-4194-91A7-E0CBE2D28B56&ClassID=0090118B-10DE-46FC-BA66-C1BF106799C5")
Accept the license conditions and 'Download software'.

Extract the driver.
Open with 'file-roller' > select PRISMA00.inf and PRISMA00.sys
> Extract > extract in folder 'Intersil' > selected files > Extract

4. Install NdisWrapper 1.8.
The package is on the installation CD.
System > Administration > Synaptic Package Manager > [Search] ndiswrapper [Search]
Important! Install ndiswrapper-common and ndiswrapper-utils-1.8 > [Mark for Installation]
[Apply] > [Apply] > insert CD > [OK]

5. Install the correct driver.
Run NdisWrapper to 'install' the driver. Important! ndiswrapper-1.8
```
$ sudo ndiswrapper-1.8 -i Intersil/PRISMA00.inf
Installing prisma00

```

List the driver.
```
$ sudo ndiswrapper -l
Installed drivers:
prisma00                driver installed, hardware present 

```

6. Load the ndiswrapper module.
```
$ sudo modprobe ndiswrapper

```

Check the driver and the interface. Important! wlan0 is the correct interface for NdisWrapper.
```
$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:2 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

7. Enable the network connection.
System > Administration > Networking > click on: Wireless connection > [Properties] > click on: Enable this connection > type in your Network name (ESSID) > [OK] > click on the box on the left hand side of the Wireless connection icon.
The system will now search and connect to your wireless router.
[Close]

Add the Network Monitor applet to the top panel. It makes it easy to see if the wireless is working correctly.
In the top panel, right click > + Add to Panel... > System & Hardware / click on: Network Monitor > [+Add] > [Close]

The interface connection should be configured automatically.
If not, use the Network Monitor to Select the wlan0 interface.
Left click on the Network Monitor > In Name over type 'lo' with wlan0 > [Close]
The wireless will now be working. Signal Strength 100% and a green stack on the right hand side of the Network Monitor.

8. Get NdisWrapper to load at start-up.
```
$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
```

Take a security copy of /etc/modules.
```
$ sudo cp /etc/modules /etc/modules.orig
```

Add ndiswrapper to /etc/modules.
```
$ sudo gedit /etc/modules
```
Add this line to the end of the file, [Save] and Close document.
```
ndiswrapper
```

9. Ensure the unwanted drivers are not loaded at start-up.
Important! prism54 must also not be loaded.

Take a security copy of /etc/modprobe.d/blacklist.
```
$ sudo cp /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.orig
```

Blacklist prism54 and islsm_pci.
```
$ sudo gedit /etc/modprobe.d/blacklist
```
Add these two lines to the end of the file, [Save] and Close document.
```
blacklist prism54
blacklist islsm_pci

```

Shut Down the computer. Important! Restart does not seem to re-activate the wireless correctly.
Start the computer. Completed! 

10. Troubleshooting
Check that you have followed the instructions correctly.
A good starting point is to run lshw, see above. Check that the logical name is wlan0 and the driver is ndiswrapper.

Also see [URL="https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"]https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide
[/URL]
I have had trouble with corrupt installs. It may not be obvious that the install has not been completely successful. The symptoms have been the system locking after a few minutes and applications/desktop/panel acting strange. After a complete re-install this HowTo worked and the other problems disappeared.

11. Removal
Remove the driver using
```
$ sudo ndiswrapper -e prisma00
```

Remove NdisWrapper using Synaptic Package Manager.

---

### Post by philc on 2007-01-28
Really good and useful Howto.

One thing to add, which had me stumped for a couple of hours, was that my wireless adaptor is not on WLAN0. It's on ETH1.

Basically, I followed all the steps up to iwconfig in step 6, where WLAN0 No Device Errors became my bane. I searched the forums but no real answers....

I skipped through all the next steps up to blacklisting Prism34 and islsm on startup. Did this, shut down, powered up and everything is auto-detected with correct drivers on ETH1.

I have my wireless connection back! Really happy.

Thank you. :D

---

### Post by Liph on 2007-08-15
This was a great help. I am a linux noob and setting up my WG511 to work with WPA was driving me nuts.

Then When I finally did get it to work I shutdown the computer and it was gone again.

I followed you advice and now it works fine, I just had to add "prism54pci" to the blacklist so that it would work on Feisty Fawn

---

### Post by gyyug78fg87ogguiioioioioi on 2011-02-26
hi i just installed ubuntu 10.10...
how do it: 
1. Display the current driver and interface
  2. Temporarily remove the unwanted driver and its dependents
?

---

### Post by typhoon_tip on 2011-03-09
Resuming an old thread. Works fantastic with Ubuntu 10.10 and ndiswrapper-1.9 as well, same procedure as above. The driver is not anymore in the same place as it was before, so you can look it up here:
[http://support.ts.fujitsu.com/Download/ShowDescription.asp?SoftwareGUID=3B928095-EEEE-4194-91A7-E0CBE2D28B56&OSID=665F4A20-6E31-43C3-82C2-D98CE773007C&Status=False&Component=Gemtek%20WL-850FJx%20(Conexant](http://support.ts.fujitsu.com/Download/ShowDescription.asp?SoftwareGUID=3B928095-EEEE-4194-91A7-E0CBE2D28B56&OSID=665F4A20-6E31-43C3-82C2-D98CE773007C&Status=False&Component=Gemtek%20WL-850FJx%20(Conexant))

(accept and download as indicated)

If you have a fresh install, there is no need to remove any driver as no driver is being hooked to the unrecognized Wireless card.

:popcorn:

---

