---
title: "Wireless device unknown - RaLink xxx?"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by mafi01 on 2008-07-26
Hi all,

My wireless network adapter apparently has some difficulties talking to the Ubuntu OS. I've tried googling for solutions, but nothing seems to show up that works, once I've tried it.

I'm pretty new at this, so if someone would care to walk me through the steps, I'd be very, very happy :-)

---

### Post by northern lights on 2008-07-26
Can you please post the output of ```
sudo lshw -C network
```

Thank you.



P.S. Might as well add ```
iwconfig
```

---

### Post by mafi01 on 2008-07-28
Definitely!

Code: sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:e0:91:38:05:cc
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.35 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

Code: iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

Thank you.

---

### Post by northern lights on 2008-07-28
I think you need the 'rt2x00' driver, anyhoo you're wireless card does not have proper driver's assigned.

Check under "System > Administartion > Hardware Drivers" - can you enable wireless drivers?

---

### Post by mafi01 on 2008-07-28
Nope, the only device driver in there is my ATI graphics driver...

---

### Post by halitech on 2008-07-28
try```
lsusb
```

---

### Post by northern lights on 2008-07-28
I don't know why you'd want to see USB devices - you think this is a wireless dongle?

Could you rather / as well post the output of ```
lspci | grep RaLink
```in order to find out which RaLink device it is (unfortunately, lshw is not revealing that...).

---

### Post by halitech on 2008-07-28
d'oh, got too many connection threads I'm following, meant to do lsusb and lspci to see where it shows up

---

### Post by mafi01 on 2008-07-28
Hi, it's not an usb dongle, but here is the output anyway.

Code: lsusb

Bus 006 Device 003: ID 0c45:62c0 Microdia 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

And the "lspci | grep RaLink"

08:00.0 Network controller: RaLink Unknown device 0781

Thanks both.

---

### Post by northern lights on 2008-07-28
> **halitech said:**
> d'oh, got too many connection threads I'm followingyup, know how that is.

> **mafi01 said:**
> Hi, it's not an usb donglefigured.

> **mafi01 said:**
> 08:00.0 Network controller: RaLink Unknown device 0781
Crap! Again it doesn't give a model ID.
Do you know / Can you check what exact RaLink device it is?
(Most likely something like rt2400/rt2500)

---

### Post by mafi01 on 2008-07-28
Will be a couple of minutes - am going to see if my Vista partition can provide further details.

** Powering down - stay tuned **

---

### Post by mafi01 on 2008-07-28
Unfortunately it doesn't seem to provide much.

All the info I can find on it is:

"802.11n Wireless LAN Card" and that the Vista driver in use is a file named netr28.sys.

What to do..?

---

### Post by mafi01 on 2008-07-28
And some more information:

I tried uninstalling the driver in Vista and then experimented a bit with reinstalling new ones. It proved comaptible with the RT2860 driver, but halfway through the installation Vista/MS support suggested the RT2790 driver, which also did the trick.

So my best guess - it's a RT2790.

Hope this will prove useful for further guidance :-)

---

### Post by mafi01 on 2008-07-29
Okay - what to do? I've downloaded two driver packages from the RaLink homepage, so now I've got a zip- and a .tar file on my Desktop.

What's the next step in this wireless quest :-)

---

### Post by mafi01 on 2008-07-30
Seriously - no one has any ideas on what to do next?

Please don't make me revert to M$ Vista - where the wireless works...

---

### Post by Twitch6000 on 2008-07-30
Humm if the driver came with a .tar then this means with a bit of work you can compile it in ubuntu and then your wireless will work.

---

### Post by mafi01 on 2008-07-30
The thing is I'm not sure how this is done... I've downoaded the driver tarball and tried experimenting a little but it seems to generate an error message one place or another.

That's why I'd really like some step-by-step assistance :-)

Thanks

---

### Post by Twitch6000 on 2008-07-30
> **mafi01 said:**
> The thing is I'm not sure how this is done... I've downoaded the driver tarball and tried experimenting a little but it seems to generate an error message one place or another.

That's why I'd really like some step-by-step assistance :-)

Thanks

1)bunzip2 -dfv filename.tar.bz2 after extracting it will give filename.tar,
2)tar -xvf filename.tar

it should be something like that in the terminal.
If not just make a new topic about how to unpack .tar's as I am not to good with them.

---

### Post by mafi01 on 2008-07-31
Thanks a lot - I'll give it a try :-)

---

### Post by chip616 on 2008-08-23
Mafi01:

Did you ever get your wireless working with the Ralink RT2790 card?  My new eeepc 901 has one of those, and I need to know if it is going to work in Ubuntu 8.04 before I try installing it.

Frank.

---

### Post by mafi01 on 2008-08-23
Unfortunately no. I haven't had the time to look into it lately though, but please post your solution if you get it working. I'm getting more tired of Vista by the hour ;-)

Edit: If you get it working with another distro I'd be very grateful for a posting of that as well.

Thanks,
mafi01

---

### Post by jason.k.holden on 2009-01-07
Not sure if this thread is still active, but I think I was able to get this hardware to work using ndiswrapper.  In my case, I already had the ndiswrapper module installed from a previous wireless card, so I've left that particular step out.  There's plenty of posts that can better describe installing ndiswrapper than what I can describe here:

Hardware Description: Belkin N Wireless ExpressCard Adapter (Belkin F5D807)

jason@rowblue3:~$ lspci | grep RaLink
01:00.0 Network controller: RaLink Device 0781

jason@rowblue3:~$ sudo lshw -C network
  *-network                
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:1c:df:93:e7:1c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2860 driverversion=1.53+Arcadyan Technology Corpora ip=192.168.1.101 latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 92:3d:76:fa:50:a1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

// check to see if you already have an ndiswrapper installed
jason@rowblue3:~$ lsmod | grep ndiswrapper
ndiswrapper           196380  0 
usbcore               148848  4 ndiswrapper,ohci_hcd,ehci_hcd

// if you don't, do a google search for ubuntu ndiswrapper install

// Pop in the windows driver cd that came with the wireless card
// We're looking for the proper .inf file
// I found that XP2K/rt2860.rtf worked
// Your md5sum may differ if you have an older or newer version

jason@rowblue3:~$ md5sum /media/cdrom/InstallationFiles/XP2K/rt2860.inf 
6733bee5badf86da9aa5e0110ec5bbf5  /media/cdrom/InstallationFiles/XP2K/rt2860.inf

// Tell ndiswrapper about this
jason@rowblue3:~$ cd /media/cdrom/InstallationFiles/XP2K/
jason@rowblue3:/media/cdrom/InstallationFiles/XP2K$ ndiswrapper -i rt2860.inf 

// Check to see if ndiswrapper detected it
jason@rowblue3:/media/cdrom/InstallationFiles/XP2K$ ndiswrapper -l
bcmwl5 : driver installed
rt2860 : driver installed
	device (1814:0781) present
jason@rowblue3:/media/cdrom/InstallationFiles/XP2K$ 
 
// reboot and hopefully your card will now be detected

Hope this helps
-Jason

---

### Post by corncob on 2009-02-04
I finally got my wireless working after installing Intrepid on my eeepc 1000.  I went to [http://www.mediafire.com/?jfrgzemgnjz](http://www.mediafire.com/?jfrgzemgnjz) and downloaded rt2860sta-dkm_1.8LK_all.deb and opened it with the default (GDebi Package Installer).  It was easy as pie and after all the things I went through that didn't work!

---

### Post by andre_orwell on 2009-03-26
Can anybody else vote for that .deb on mediafire?  Is there not an official download site?  I'd certainly prefer it.

---

