---
title: "How to upgrade from 10.04 to 10.10 without internet"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by anujtripathi on 2011-09-27
Hi

I am someone who has used ubuntu in the past and have done installation through a CD or Wubi. It has been a breeze.

Right now I am facing a problem where I installed 10.04 through USB with a dual boot. The install went fine but 10.04 doesn't have driver's for my network cards hence no network for me. Moreover, I am not sure how to delete the Linux install as I do not have the install CD (Install done by the company) for the other OS. I have tried to boot through the 10.10 OS but there are no upgrade options there. I checked in many forums but haven't been able to find an ISO image which has upgrade option.

Please suggest what can I do here ? I am open to deleting current Linux installation if that doesn't mess with my other OS. If there are any easier ways to upgrade, please let me know. I have tried to look for upgrade option from images available on the ubuntu site.

Any help will be golden. Thank you

---

### Post by anewguy on 2011-09-27
What are the network cards?

For now, just post the output of  the following back here and it will get us started:

lspci

lsusb

You do these from the terminal - Applications/Accessories/Terminal


Dave ;)

---

### Post by anewguy on 2011-09-28
I know my answer may seem counter to what you asked, but if we see what you have for network/wireless controllers we might be able to get your network connection(s) working, at which point you could do the upgrade WITH internet.

Dave ;)

---

### Post by anujtripathi on 2011-09-28
Posting the outputs after login through the USB based 10.10 ubuntu.

The Wired network works but the wireless is still not detected.

Following are the outputs
00:00.0 Host bridge: Intel Corporation Sandy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 6 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation 6000 Series Gen2 (rev 34)
0a:00.0 SD Host controller: O2 Micro, Inc. Device 8221 (rev 05)
0a:00.1 Mass storage controller: O2 Micro, Inc. Device 8231 (rev 03)

lsusb

Bus 002 Device 004: ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor
Bus 002 Device 003: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 04b3:3025 IBM Corp. 
Bus 001 Device 006: ID 046d:c063 Logitech, Inc. 
Bus 001 Device 005: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 001 Device 004: ID 413c:2513 Dell Computer Corp. 
Bus 001 Device 003: ID 413c:2513 Dell Computer Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Both the commands were run as su.

As I said, any help is golden, so let me know what ever your suggestion is.

By the way will using Lilo to clear the MBR as suggested on some forum help. Through that I can remove the ubuntu partition and reinstall a new fresh 10.10 or 11.04 ubuntu.

I would be more inclined to make the hardware working in the current install and then upgrade through network

---

### Post by wildmanne39 on 2011-09-28
Hi, that information doesn't tell us all the information on the wireless card that you have but I believe from what I saw that this will get it working.
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```
if not post the results of this command please:
```
lspci -nnk | grep -iA2 net
```

If you plan on doing a network upgrade I would use the wired connection and not the wireless to do it.

Sine you say you have a wired connection I would download the livecd of the version of ubuntu that you want to use and test it first and make sure it runs on your computer good.

Also  since you plan on upgrading when you do you will have to get your wireless working all over again.

You can reformat your ubuntu partitions using the livecd you do not need to use Lilo or some third party program.
Thank you

---

### Post by westie457 on 2011-09-28
> **anujtripathi said:**
> Hi

I am someone who has used ubuntu in the past and have done installation through a CD or Wubi. It has been a breeze.

Right now I am facing a problem where I installed 10.04 through USB with a dual boot. The install went fine but 10.04 doesn't have driver's for my network cards hence no network for me. Moreover, I am not sure how to delete the Linux install as I do not have the install CD (Install done by the company) for the other OS. I have tried to boot through the 10.10 OS but there are no upgrade options there. I checked in many forums but haven't been able to find an ISO image which has upgrade option.

Please suggest what can I do here ? I am open to deleting current Linux installation if that doesn't mess with my other OS. If there are any easier ways to upgrade, please let me know. I have tried to look for upgrade option from images available on the ubuntu site.

Any help will be golden. Thank you

Hello, if I have read your posts correctly and understand them properly, you already have 10.04 LTS installed and you have 10.10 on a USB stick and you want to upgrade to 10.10.

One way I have used to upgrade from an older to a newer is 

Boot into the older Desktop (10.04) then plug the in USB stick(10.10). The system finds the new software and asks if you want to install. You can either say yes or no. If you say yes it should upgrade for you.

@ anewguy The suggestion above is to help the OP upgrade. I have no idea if his network connectivity problems will be solved doing it this way because I have different chips in my box.

            ______________________________________________________________________________

Beaten by wildemanne39 again. Damn sometimes my knowledge lets me down.

---

### Post by anujtripathi on 2011-09-28
Hi wildmanne39

The wired connection here works with the USB boot and not with 10.04 install. Basically I have no internet connectivity in 10.04.

Following is the output you requested:
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Dell Device [1028:0493]
    Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Intel Corporation 6000 Series Gen2 [8086:0082] (rev 34)
    Subsystem: Intel Corporation Device [8086:1321]
0a:00.0 SD Host controller [0805]: O2 Micro, Inc. Device [1217:8221] (rev 05)


Please note that this has been obtained from a 10.10 USB boot and not the 10.04 install which in on my laptop. I need to enable both these controllers on 10.04. From other forums it seems 10.10 and 11.04 have the drivers for both, hence I would like to upgrade to one of them

---

### Post by anujtripathi on 2011-09-28
Hi Westie

As suggested by you,
"Boot into the older Desktop (10.04) then plug the in USB stick(10.10).  The system finds the new software and asks if you want to install. You  can either say yes or no. If you say yes it should upgrade for you."

This doesn't work. On plugging the USB stick the autorun doesn't happen. I looked into the autorun.inf but it points to wubi.exe which cannot be run on Linux.

---

### Post by bcbc on 2011-09-28
You need the alternate CD to do an offline upgrade - not the desktop CD ISO.


[https://help.ubuntu.com/community/MaverickUpgrades#Upgrading_Using_the_Alternate_CD.2BAC8-DVD](https://help.ubuntu.com/community/MaverickUpgrades#Upgrading_Using_the_Alternate_CD.2BAC8-DVD)

---

### Post by wildmanne39 on 2011-09-28
Hi, so did you install ubuntu using wubi?

The driver for your wired connection is installed but I have done some research and it just does not work a lot of times with your network card, and I am pretty sure the command I gave in my previous post will work to get your wireless working but you need the wired connection to do it.
Thank you

---

