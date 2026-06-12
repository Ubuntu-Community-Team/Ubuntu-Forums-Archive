---
title: "Super Noob - Identifing Wireless Card"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by bull205 on 2008-09-19
Alrightly...so how do I go about identifing what kind of wireless card I have installed.  I have a new Sony vaio, SR-165E.  It came with crap OS that I couldn't stand and I have been messing with the idea of installing Ubuntu for a long time, so now was my chance.

I have installed and i am connected to the internet via ethernet, but I am getting nowhere on the wireless side.

1. How do I find out what kind of card i have?
2. How do I get drivers or enable it?
3. How do I surf the net wirelessly?

---

### Post by k33bz on 2008-09-19
> **bull205 said:**
> Alrightly...so how do I go about identifing what kind of wireless card I have installed.  I have a new Sony vaio, SR-165E.  It came with crap OS that I couldn't stand and I have been messing with the idea of installing Ubuntu for a long time, so now was my chance.

I have installed and i am connected to the internet via ethernet, but I am getting nowhere on the wireless side.

1. How do I find out what kind of card i have?
2. How do I get drivers or enable it?
3. How do I surf the net wirelessly?

run this in your terminal
```
lspci
```

and post the output here

---

### Post by bull205 on 2008-09-19
I am guessing it is the intel unknown device 4232...

00:00.0 Host bridge: Intel Corporation Cantiga Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Cantiga Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Cantiga Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
04:00.0 Network controller: Intel Corporation Unknown device 4232
06:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
06:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
06:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

---

### Post by northern lights on 2008-09-19
Most likely it is. Can you please also post the output of ```
sudo lshw -C network
```Thank you.

---

### Post by bull205 on 2008-09-19
*-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:ba:19:8a:a1
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=10.0.1.3 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

---

### Post by MockY on 2008-09-19
So the card is not listed in the Restricted Drivers Manager? System - Administration - Restricted Drivers Manager. 
Sitting on Feisty right now so the name might be a bit different in the release you are currently using, but something similar should be there.

---

### Post by bull205 on 2008-09-19
It says "no proprietary drivers are in use on this system"

---

### Post by anewguy on 2008-09-19
According to the sonystyle website:

Wireless LAN : Intel® WiFi Link 5100AGN (802.11a/b/g/n)

You can find the Windows XP driver (you'll need it) at:

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2963&OSFullName=Windows*+XP+Home+Edition&lang=eng&strOSs=45&submit=Go!]("http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2963&OSFullName=Windows*+XP+Home+Edition&lang=eng&strOSs=45&submit=Go!")

Then you need to be sure ndiswrapper is installed.  You can check this simply by opening a terminal window and typing the following:

ndiswrapper -l <enter> where that's a lower case "L" for "List"

If it just returns nothing, you're okay.  If it says ndiswrapper not found, you'll need to install ndiswrapper.

So, download the XP driver via the above link and save it to a new folder, then do ndiswrapper -l in a terminal window and copy/paste the output back here and we can go from there.

Dave:)

---

### Post by bull205 on 2008-09-19
I downloaded the driver...mucked my way around the synaptic package manager and the terminal, managing to get ndiswrapper on my machine, I think.

When I type "ndiswrapper -l" in the terminal, nothing shows on the next command line. So now, I guess I just need to figure out if i have 32 or 64 driver to unzip and install. Am I on the right track?

---

### Post by Ripfox on 2008-09-19
I find that sometimes if you hook up to a wired connection, open all repos and update your system sometimes a restricted driver will be then available.

---

### Post by bull205 on 2008-09-19
Nada...I am on the wired ubuntu laptop as we speak (type).  It says that there's nothing to update.

---

### Post by bull205 on 2008-09-19
i downloaded the drivers and can't seem to install them with ndiswrapper.  More specifically, not of them are "valid" drivers.

1. How do I identify the correct driver from the download that I got from the intel website?

2. How do I install?

Edit:  Ok so I downloaded the driver and installed using ndiswrapper.  The terminal result from running 'lspci -l' gives me:

netw5x32 : driver installed
	device (8086:4232) present


However, when i open network settings, there is no option for selecting wireless.  Thoughts on where I go from here?

---

### Post by arron on 2008-09-19
To the best of my memory, it should be a .inf file.  There is a good gui to help with the install, it really should be included with the base Ubuntu install

[http://ubuntuforums.org/showthread.php?t=50607](http://ubuntuforums.org/showthread.php?t=50607)

Try the gui.  Is your drivers a exe file, zip or what?  Have you extracted them if needed.  If its a exe file you can even try to unzip it with unzip driverfile.exe, or run it with wine (install wine, then rune wine driverfile.exe).

Hope it helps, wifi and laptops can be tricky to figure out but once you do get it, its easy to repeat.

---

### Post by lswest on 2008-09-19
please run the following commands:
```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
``` if the wireless networks are now available (give it a moment or two to initialize) all is well, and you just need to add ndiswrapper to the file /etc/modules by doing this:
```
sudo nano /etc/modules
``` and append ndiswrapper to the end of the file, hit ctrl+x to exit, y to agree to overwrite, and enter to accept the filename.  It should then initialize at every boot.

---

### Post by bull205 on 2008-09-19
When I run 'ndiswrapper -m' it returns a long page of:

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

Then when I enter "sudo modprobe ndiswrapper' nothing happens. Is this what is supposed to happen?

---

### Post by lswest on 2008-09-19
sudo modprobe ndiswrapper will not give output, but it will load the driver.  After doing so check the wireless connections.  (the output from ndiswrapper -m means the command was either run before, or it was already configured).

if there is no accessible wireless, post the output of ```
lshw -C network
``` again please.

---

### Post by bull205 on 2008-09-19
OK, so I ran the two commands then enter the third "sudo nano /etc/modules and got an output, but you lost me at 

> and append ndiswrapper to the end of the file, hit ctrl+x to exit, y to agree to overwrite, and enter to accept the filename. It should then initialize at every boot.

---

### Post by lswest on 2008-09-19
> **bull205 said:**
> OK, so I ran the two commands then enter the third "sudo nano /etc/modules and got an output, but you lost me at

Nano is a text editor based in the terminal.  Therefore, enter ndiswrapper at the end of whatever is already present (on a new line).  Then to save those changes, hit ctrl + x (the keys) and it will begin to exit.  It will then ask you if you want to save and overwrite the changes.  Hit the y key.  Then hit enter, as it will prompt you for the name of the file, since we want to overwrite the present one, don't change the name.

Hopefully that clears it up.

And I assume that means ndiswrapper got your wireless working?

---

### Post by bull205 on 2008-09-19
negative.  ndiswrapper says that I have the drivers installed, but the network doesn't show any wireless option.  I have the XP drivers but no joy with them.

---

### Post by lswest on 2008-09-19
> **bull205 said:**
> negative.  ndiswrapper says that I have the drivers installed, but the network doesn't show any wireless option.  I have the XP drivers but no joy with them.

Then could you post the output of ```
lshw -C network
``` again?

---

### Post by bull205 on 2008-09-19
*-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:ba:19:8a:a1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=10.0.1.3 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

---

### Post by anewguy on 2008-09-19
Please do as lswest just requested, but also check under system/administration/network - it should show an area called wireless, and if so, it should also say roaming enabled.  If the wireless area shows but doesn't say roaming enabled you will need to enable roaming there.

EDIT:  You beat me to it.  The device is showing now.  Check the network as per above and post back.

---

### Post by lswest on 2008-09-19
I see a slight problem with the network adapter.  There's no driver displayed in the configuration line.  I don't know the exact chipset, but in my experience that means there's no driver being used for it.  (Possibly the wrong driver, or a driver conflict?).  I'll google around to see if there are any pre-installed drivers in ubuntu that might be conflicting.

could you post the output of ```
dmesg | grep wlan0 
``` it seems your card may not be detected at boot.  Similar issue [here]("http://sudan.ubuntuforums.com/showthread.php?t=909031") (not sure if it was resolved, still reading)

Found some more info here: [http://sudan.ubuntuforums.com/showpost.php?p=5726363&postcount=16](http://sudan.ubuntuforums.com/showpost.php?p=5726363&postcount=16) and here: [http://ubuntuforums.org/showthread.php?t=879134](http://ubuntuforums.org/showthread.php?t=879134) from the last link [this post]("http://ubuntuforums.org/showpost.php?p=5754065&postcount=62") seems to be the one you need

Hopefully those will help you.

---

### Post by anewguy on 2008-09-19
> **lswest said:**
> I see a slight problem with the network adapter.  There's no driver displayed in the configuration line.  I don't know the exact chipset, but in my experience that means there's no driver being used for it.  (Possibly the wrong driver, or a driver conflict?).  I'll google around to see if there are any pre-installed drivers in ubuntu that might be conflicting.

I missed that!  Also wondering - if the wrong file (correct driver set, just the wrong driver selected) was used with ndiswrapper it might still show the device but with no driver - checking the actual Windows file downloaded (the .inf  *IF* I remember correctly - it's been a long time!) may indicate the exact filename needed to be included.

Dave :)

---

### Post by lswest on 2008-09-19
> **anewguy said:**
> I missed that!  Also wondering - if the wrong file (correct driver set, just the wrong driver selected) was used with ndiswrapper it might still show the device but with no driver - checking the actual Windows file downloaded (the .inf  *IF* I remember correctly - it's been a long time!) may indicate the exact filename needed to be included.

Dave :)

Yup, the .inf is what you need! Also, I posted a few links above to a solution that seemed to work for someone earlier on.  It seems to be a linux driver too, so I recommend we try that one first.

---

### Post by bull205 on 2008-09-21
When I run 
"dmesg | grep wlan0"
in the terminal, nothing happens....nothing to post.

---

