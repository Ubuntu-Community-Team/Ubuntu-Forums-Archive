---
title: "Won't connect to internet"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by Arendyl on 2012-10-24
I just did a fresh install of ubuntu 12.10, and when I go to connect to the internet, the applet say "disconnected" in faded letters and won't give me the option to connect to a network. I also cannot connect via a physical line, with the same issue. How do I resolve this problem?
I have an old HP mini, if you were wondering.

---

### Post by newb85 on 2012-10-24
What are the results of
```
sudo lshw -c network
```

(The above won't modify your system; it will only grab some info about your networking card and drivers.)

---

### Post by Arendyl on 2012-10-25
> **newb85 said:**
> What are the results of
```
sudo lshw -c network
```

(The above won't modify your system; it will only grab some info about your networking card and drivers.)

PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 00:25:b3:6a:39:43
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:febc0000-febfffff ioport:ec80(size=128)

---

### Post by Arendyl on 2012-10-26
Can anybody help me out?

---

### Post by Sowndefex on 2012-10-26
Same for me.

---

### Post by newb85 on 2012-10-26
@Arendyl,
Try this:
```
sudo apt-get purge firmware-b43-installer
sudo apt-get install firmware-b43-lpphy-installer
```

@Sowndefex,
does the output of
```
sudo lshw -C network
```
also return a line
```
product: BCM4312 802.11b/g LP-PHY
```
for you?

---

### Post by Arendyl on 2012-10-26
> **newb85 said:**
> @Arendyl,
Try this:
```
sudo apt-get purge firmware-b43-installer
sudo apt-get install firmware-b43-lpphy-installer
```

@Sowndefex,
does the output of
```
sudo lshw -C network
```
also return a line
```
product: BCM4312 802.11b/g LP-PHY
```
for you?

No cigar. Unable to locate package error

---

### Post by newb85 on 2012-10-26
Unless it has been removed between 12.04 and 12.10, it should be in the multiverse repository.  Do you have multiverse enabled?

---

### Post by Arendyl on 2012-10-27
> **newb85 said:**
> Unless it has been removed between 12.04 and 12.10, it should be in the multiverse repository.  Do you have multiverse enabled?

I have no idea. How do I check that?

---

### Post by newb85 on 2012-10-27
In Software Center, Edit>Software Sources.  
There should be an option like "Software restricted by copyright or legal issues (multiverse)".  Make sure it's checked.

Then,
```
sudo apt-get update
sudo apt-get install firmware-b43-lpphy-installer
```

---

### Post by Arendyl on 2012-10-27
Mulitverse was checked before. It failed to update, I think because I'm not connected to the internet. The ```
 sudo apt-get install firmware-b43-lpphy-installer 
``` failed as well, unable to locate package

---

### Post by newb85 on 2012-10-27
Yeah...it's trying to locate the package in an online repository, so of course it's going to fail if you're not connected.  ;)

Edit:Wow, again, I should start drinking coffee earlier.  You're not connected to the internet because you wireless isn't working, right?

---

### Post by newb85 on 2012-10-27
Okay, I think you can download the .deb for the package using Windows/your other machine/however you're accessing the forums.

[http://archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43-lpphy-installer_015-14_all.deb]("http://archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43-lpphy-installer_015-14_all.deb")

Then, try opening the file with Software Center and installing it.

---

### Post by Arendyl on 2012-10-29
> **newb85 said:**
> Okay, I think you can download the .deb for the package using Windows/your other machine/however you're accessing the forums.

[http://archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43-lpphy-installer_015-14_all.deb]("http://archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43-lpphy-installer_015-14_all.deb")

Then, try opening the file with Software Center and installing it.

When I open the .deb file with the Software Center, it comes up as normal but the install button is grayed out and I can't click on it.

---

### Post by Hadaka on 2012-10-29
Hi, here ya go..a chili555 fix for b-43 lpphy...try post #6 or #8

load the zip file first, drag to desk top..chose..open here
then load the other code, hope this helps

[http://ubuntuforums.org/showthread.php?t=2076976](http://ubuntuforums.org/showthread.php?t=2076976)

copy via windows to a usb or disc to transfer to the linux box

this is for loading the driver offline.

---

### Post by newb85 on 2012-10-29
> **Hadaka said:**
> Hi, here ya go..a chili555 fix for b-43 lpphy...try post #6 or #8

load the zip file first, drag to desk top..chose..open here
then load the other code, hope this helps

[http://ubuntuforums.org/showthread.php?t=2076976](http://ubuntuforums.org/showthread.php?t=2076976)

copy via windows to a usb or disc to transfer to the linux box

this is for loading the driver offline.

Hadaka, can you help me understand why my advice didn't pan out?

---

### Post by Arendyl on 2012-10-29
I'm sorry, I am still new to ubuntu, and I don't understand the instructions presented in that thread. I am not getting the same result as the OP of that thread. Could somebody give me a step-by-step? Thank you in advance.

---

### Post by Hadaka on 2012-10-29
Hi, do you have a usb stick or cd you can load a file to?

---

### Post by Hadaka on 2012-10-29
@Newb
When I open the .deb file with the Software Center, it comes up as  normal but the install button is grayed out and I can't click on it.

i think the reason it didnt pan out was an attempt to access the software center
with a machine that had no internet connection.

---

### Post by Arendyl on 2012-10-30
> **Hadaka said:**
> Hi, do you have a usb stick or cd you can load a file to?

Yes, of course.

---

### Post by Arendyl on 2012-11-01
Can anybody help me?

---

### Post by Arendyl on 2012-11-06
Do bumps work on this site?

---

### Post by wildmanne39 on 2012-11-06
Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thanks

---

### Post by newb85 on 2012-11-07
Wild Man, don't know if you noticed this from the first page,

> **Arendyl said:**
> PCI (sysfs)  
  *-network               
       description: Network controller
       product: **BCM4312 802.11b/g LP-PHY**

I believe this means they need the lpphy firmware.

---

### Post by wildmanne39 on 2012-11-07
Yes it does and it is included in the zip file I attached.
Thanks

---

