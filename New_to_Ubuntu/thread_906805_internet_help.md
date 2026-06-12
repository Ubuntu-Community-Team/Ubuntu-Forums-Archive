---
title: "internet help"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by dsmcginn on 2008-08-31
i'm new to ubuntu and unix in general. i just installed ubuntu on my laptop and i'm trying to get internet access through a wireless router. since i can't connect to the internet on my laptop, i tried downloading the drivers and everything needed from my desktop, and burning them to a CD, but that didn't work. 
any help would be appreciated!
=)

---

### Post by BDNiner on 2008-08-31
What wireless card do you have? not all wireless cards are compatible with linux.

---

### Post by oilchangeguy on 2008-08-31
> **dsmcginn said:**
> i'm new to ubuntu and unix in general. i just installed ubuntu on my laptop and i'm trying to get internet access through a wireless router. since i can't connect to the internet on my laptop, i tried downloading the drivers and everything needed from my desktop, and burning them to a CD, but that didn't work. 
any help would be appreciated!
=)

first, Why can't you use a wired connection on the laptop? And no, I don't mean use it all of the time.

---

### Post by falcon61102 on 2008-08-31
If you could, go to your terminal, run the following command and post the results:
```
sudo lshw -C network
```

The terminal can be found in Applications>Accessories.

Also, if you look in the upper right hand corner of your desktop you should see the Network Manager, it's the two black monitors, one on top of the other.  If you click on that, are any wireless access points listed?

---

### Post by dsmcginn on 2008-08-31
> **oilchangeguy said:**
> first, Why can't you use a wired connection on the laptop? And no, I don't mean use it all of the time.

i tried to go directly from my modem, but i would still need to download the drivers, so i figured it would be easier to just download the wireless ones. 
=)

i'm using an atheros ar5bxb63 card.

and no, no access points.

---

### Post by BDNiner on 2008-08-31
since you have an atheros card I would try installing the drivers through the restricted drivers manager. it can be found in the main menu under System > Administration > Hardware Drivers. should be listed as "atheros hardware access layer". just make sure it is enabled.

can you also paste the output of the command falcon61102 asked you to run?

---

### Post by dsmcginn on 2008-08-31
> **falcon61102 said:**
> If you could, go to your terminal, run the following command and post the results:
```
sudo lshw -C network
```

The terminal can be found in Applications>Accessories.

Also, if you look in the upper right hand corner of your desktop you should see the Network Manager, it's the two black monitors, one on top of the other.  If you click on that, are any wireless access points listed?

when i ran that command, it gave me a bunch of info...what are you looking for specifically? i don't want to type it all out...lol.

---

### Post by falcon61102 on 2008-08-31
There's quite a few people that have had problems with atheros when first setting up their system but with the right drivers it shouldn't be a probmlem.  You may need to download a set of WinXP drivers for you card and place them on a USB drive or a cd should work too and then install them using a program called ndiswrapper which you can install from your LiveCD.

---

### Post by BDNiner on 2008-08-31
> **dsmcginn said:**
> when i ran that command, it gave me a bunch of info...what are you looking for specifically? i don't want to type it all out...lol.

you don't have to type it out. Just copy and paste it into a new message.

---

### Post by falcon61102 on 2008-08-31
Ok, run this one instead and we'll work with that info instead.
```
lspci -nn
```

That's going to give you a whole list of all your hardware, we only need the one that talks about your wireless card.

If you could, copy and paste the output of the last command to a text file, save the file on a USB drive and copy to the message bored.  It has some info about your card we may need.

---

### Post by dsmcginn on 2008-08-31
> **BDNiner said:**
> you don't have to type it out. Just copy and paste it into a new message.


uhh...my laptop isnt connected to the internet...that's the whole reason why i'm here! =) i'm on my desktop right now which is running windows.

---

### Post by BDNiner on 2008-08-31
[http://ubuntuforums.org/showthread.php?t=830283](http://ubuntuforums.org/showthread.php?t=830283)

I found this other post about using ndiswrapper. Disregard my post about using the restricted drivers manager. you card is not compatible with madwifi.

Sorry i shouldn't have assumed that you were connected via ethernet and typing your messages from the laptop

---

### Post by falcon61102 on 2008-08-31
I'm not sure if you can install ndisgtk from the LiveCD but I know you can install ndiswrapper which is just the text based version that works just as well.

---

### Post by dsmcginn on 2008-08-31
doug@doug:~$ sudo lshw -C network
[sudo] password for doug: 
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:16:be:ac
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

doug@doug:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
0a:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
0a:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]



that's what i got when i entered those two codes...

does that help at all?

---

### Post by falcon61102 on 2008-09-01
Yeah, it helps.  It's going to help make sure you get the right driver for your card.  You're best bet to locate a good driver would be the manufacture's website for you laptop.  They normally have a drivers download section, just be sure to download the WinXP version of your wireless card drivers.  If you need to download them on another computer and copy them over with a USB drive, copy them to a place that easily reached like your home folder or desktop.

Also, were you able to get ndiswrapper installed?

---

### Post by dsmcginn on 2008-09-01
no...i got the files downloaded, but once i try to open them on my laptop, nothing happens.

---

### Post by falcon61102 on 2008-09-01
Yeah, they're not going to open like they would on windows.  Just copy them somewhere handy.

What files did you download?

If they are .exe or .zip files, right-click on them and click Extract Here.  That will create a folder and extract the contents into that folder.  You should now be ready to install them.

---

### Post by dsmcginn on 2008-09-01
i got the drivers for my wireless card, and i extracted a folder with ndiswrapper-1.53 into documents...it has two subfolders called driver and utils, and then some text files.

how do i install it?

---

### Post by falcon61102 on 2008-09-01
Honestly the easiest way to install ndiswrapper is to use the Synaptic Package Manager.  I've always had trouble with the downloaded version for some reason.  If you put your LiveCD in and start the package manager, go to Edit>Add Cd...  Follow the menus and select your CD.  Then search for ndiswrapper.  At least three items should come up, you want to install ndiswrapper-common and ndiswrapper-utils-1.9.

As far as the drivers go, right click on them and Extract them.  Once you get ndiswrapper installed then we'll use them.

---

### Post by dsmcginn on 2008-09-01
awesome...you're my new best friend...lol. 

what next?

---

### Post by falcon61102 on 2008-09-01
Alright, you have ndiswrapper installed and your drivers extracted?

If so, it's time to install them.  Open a terminal and using the change directory command, "cd", navigate to your folder with the drivers in them.  In that folder should be a .inf file and you can either type "dir" to see a list of files or use the nautilus file browser to examine the folder.  Either way, look for that .inf file.  Then type:
```
sudo ndiswrapper -i driver.inf
sudo ndiswrapper -l
sudo depmod - a
sudo modprobe ndiswrapper
```

Replace driver.inf with the actual .inf file that you found early.
The second command will list the driver once it installs to show that it was done correctly.
The last two commands configure and load ndiswrapper.

At this point, if all went well, you should be able to click on your Network Manager and see your wireless access points.  

If so, them you need to load ndiswrapper into the modules file so it will start every time you boot.  To do that, run:
```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```

And you should be good to go.

---

### Post by dsmcginn on 2008-09-01
ok...so i did all that and they didn't show up in network manager...
=(
i rebooted and nothing still.

---

### Post by falcon61102 on 2008-09-01
Go into your terminal and run:
```
sudo lshw -C network
```

---

### Post by dsmcginn on 2008-09-01
doug@doug:~$ sudo lshw -C network

  *-network               

       description: Ethernet interface

       product: 88E8038 PCI-E Fast Ethernet Controller

       vendor: Marvell Technology Group Ltd.

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: eth0

       version: 14

       serial: 00:1b:24:16:be:ac

       capacity: 100MB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair

  *-network UNCLAIMED

       description: Ethernet controller

       product: AR242x 802.11abg Wireless PCI Express Adapter

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:03:00.0

       version: 01

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix cap_list

       configuration: latency=0

---

### Post by falcon61102 on 2008-09-01
Alright, I've done some research and actually just got the same type of card working on a buddies computer using the following:

[http://ubuntuforums.org/showthread.php?t=865971&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=865971&highlight=AR242x)

Take a look at Post #4 and you should be good to go.

---

