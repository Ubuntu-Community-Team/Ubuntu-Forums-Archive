---
title: "Broadcom 4322 wireless card driver"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by nksjolinder on 2011-09-17
Hey guys,

I am just now learning the ropes in linux, trying to figure out even the simplest of tasks, and in this case i am trying to install drivers for the broadcom wirless card detected with lshw below:

*-network
                description: Network controller
                product: BCM4322 802.11a/b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:17 memory:f6cfc000-f6cfffff

I downloaded the 64 bit driver from this site : [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

My issue now (assuming that is the correct driver) is that i am not sure how to use the tar.gz file as i am used to the pre-compiled .exe's in windows. Any help would be greatly appreciated and keep in mind that i am very new in your explanation :P

---

### Post by Megaptera on 2011-09-17
Have you tried using the menu bar on the top panel?
System > Adminstration > Hardware drivers  clicking on that gets me the Broadcom drivers I need and installs them - no other intervention on my part.
Worth a try if not already done?

---

### Post by gandaran on 2011-09-17
broadcom drivers are included in the software packages already (USC or synaptic) find which one is the right one and install
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by blade4 on 2011-09-17
Hi and welcome to ubuntu . I might be able to help you out here . I had similar problems with my broadcom adapter . Here's what I did : 

Note : These instructions work for ubuntu 10.04 LTS and broadcom 43xx packages . They may or may not work for you . Use at your own risk . 


You will have to install b43-fwcutter and patch packages. After that you will need to setup firmware manually (without the firmware automatically downloading and being set up).

b43-fwcutter is located on the Ubuntu install cd under ../pool/main/b/b43-fwcutter/ and patch is located under ../pool/main/p/patch/ or both in the official repositories online.

Double click on the package to install or in a terminal navigate to the folder containing the package and issue the following command:

:/b43-fwcutter/$ sudo dpkg -i b43-fwcutter*

Step 1.

On a computer with Internet access, download the required firmware files from [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Step 2.

Copy the downloaded files to your home folder and execute the following commands consecutively in a terminal to extract and install the firmware:

~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

Note: A computer restart may be required before using the wifi card.

Hope this helps ..

Cheers :)

---

### Post by nksjolinder on 2011-09-17
> **Megaptera said:**
> Have you tried using the menu bar on the top panel?
System > Adminstration > Hardware drivers  clicking on that gets me the Broadcom drivers I need and installs them - no other intervention on my part.
Worth a try if not already done?

  This worked perfectly! thanks a lot! and thank you all for the other posts you put up

---

### Post by Megaptera on 2011-09-17
You're welcome! Glad it helped.

---

