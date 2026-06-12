---
title: "Unstable wireless connection"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by waldurp on 2011-10-19
I am new to Ubuntu and not a computer whizz. I downloaded Xtra drivers and got connected but the connection drops off and then re-connects every 10 - 15 seconds. I read about blacklisting things but do not really understand how to go about it.
Any help would be appreciated.
Thanks

---

### Post by collisionystm on 2011-10-19
> **waldurp said:**
> I am new to Ubuntu and not a computer whizz. I downloaded Xtra drivers and got connected but the connection drops off and then re-connects every 10 - 15 seconds. I read about blacklisting things but do not really understand how to go about it.
Any help would be appreciated.
Thanks

Open terminal

type

lspci

post the output

---

### Post by waldurp on 2011-10-19
> **collisionystm said:**
> Open terminal

type

lspci

post the output

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
03:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)

---

### Post by collisionystm on 2011-10-19
try this

Open Terminal

sudo apt-get install firmware-b43-installer

---

### Post by waldurp on 2011-10-19
> **collisionystm said:**
> try this

Open Terminal

sudo apt-get install firmware-b43-installer

Thanks for your reply

When I press enter after entering the above I get
 [sudo]password for ----- and can't get passed this??

---

### Post by collisionystm on 2011-10-19
> **waldurp said:**
> Thanks for your reply

When I press enter after entering the above I get
 [sudo]password for ----- and can't get passed this??

Put in your password

It will not show anything being typed ( for security purposes )

Just hit enter after putting in your password.

---

### Post by waldurp on 2011-10-19
> **collisionystm said:**
> Put in your password

It will not show anything being typed ( for security purposes )

Just hit enter after putting in your password.

Ahhh didn't know that. It is still disconnecting and this is what it said after doing the above

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 10 not upgraded.
Need to get 19.8 kB of archives.
After this operation, 139 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric/main b43-fwcutter i386 1:014-9 [16.5 kB]
Get:2 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric/multiverse firmware-b43-installer all 1:014-9 [3,272 B]
Fetched 19.8 kB in 0s (48.9 kB/s)               
Selecting previously deselected package b43-fwcutter.
(Reading database ... 125003 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a014-9_i386.deb) ...
Selecting previously deselected package firmware-b43-installer.
Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a014-9_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:014-9) ...
Setting up firmware-b43-installer (1:014-9) ...
An unsupported BCM4312 Low-Power (LP-PHY) device was found.
Use b43 LP-PHY firmware (firmware-b43-lpphy-installer package) instead.
Aborting.

---

### Post by collisionystm on 2011-10-19
sudo apt-get install firmware-b43-lpphy-installer

---

### Post by irv on 2011-10-19
Go to this link [http://ubuntuforums.org/showthread.php?p=11366865#post11366865]("http://ubuntuforums.org/showthread.php?p=11366865#post11366865") and follow the instructions in post 48. It should work. make sure you are plug in on the wire and you need to reboot afterward.

---

### Post by waldurp on 2011-10-19
> **irv said:**
> Go to this link [http://ubuntuforums.org/showthread.php?p=11366865#post11366865](http://ubuntuforums.org/showthread.php?p=11366865#post11366865) and follow the instructions in post 48. It should work. make sure you are plug in on the wire and you need to reboot afterward.

Tried sudo apt-get remove bcm-kernal-source and get the following

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcm-kernal-source

Where to from here??

---

### Post by irv on 2011-10-19
> **waldurp said:**
> Tried sudo apt-get remove bcm-kernal-source and get the following

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcm-kernel-source

Where to from here??
Sorry this changed. try bcmwl-kernel-source
Edit: I changed this on the other post also.

---

### Post by waldurp on 2011-10-19
> **irv said:**
> Sorry this changed. try bcmwl-kernal-source
Edit: I changed this on the other post also.

Sorry. Same message.--  Unable to locate package bcmwl-kernal-source.

I think I will call it quits. Do a complete install and start over.

---

### Post by irv on 2011-10-19
> **waldurp said:**
> Sorry. Same message.--  Unable to locate package bcmwl-kernal-source.

I think I will call it quits. Do a complete install and start over.

Sorry again I miss spelled kernel. It should have been bcmwl-kernel-source.

---

### Post by Sef on 2011-10-19
> 01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

I have this exact card. I got my wireless working this way:

System Settings > Hardware > Additional Drivers.

Have you tried that?

---

