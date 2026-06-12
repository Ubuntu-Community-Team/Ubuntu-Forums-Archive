---
title: "How do you find attached hardware?"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-07-12
I am blowed if I can find out what hardware is attached to what port! I know my phone is attached because sakis found it, but cannot find any place where it tells me what is in what port?????:confused:J (Surely if I attach something something should say so somewhere?)

---

### Post by puntigamer on 2012-07-12
What are you searching for? USB? PCI?

Try 'lsusb' or 'lspci' etc :)

---

### Post by Jackalyn on 2012-07-12
> **puntigamer said:**
> What are you searching for? USB? PCI?

USB I think I may need to ask for two posts to be merged. My phone is plugged in and as USB I think, (thanks to the help of someone answering the phone post,) this means it should act like a flash drive. 



Try 'lsusb' or 'lspci' etc :)
I don't understand what you mean? Sorry too new to all this and need a ubuntudictionary and an UBUNTU ABC!!!  Is it some magic thing I type into the terminal?

---

### Post by puntigamer on 2012-07-12
yes, you need to type them into the terminal, and maybe post it here, so we can see what could be wrong with your hardware ;) the command 'lsusb' listst your USB ports and devices, the 'lspci' your pci devices and so on...

---

### Post by jmfal on 2012-07-12
Are you trying to download pictures from your phone to your pc?

Open file manager and top left is devices see if it is listed there and click ont to open

---

### Post by mastablasta on 2012-07-12
> **Jackalyn said:**
>  Is it some magic thing I type into the terminal?
 
yes it's magic words... :-)
 
ls = list
lspci = list all pci connected devices
lsusb = list all USB devices
lshw = list all detected hardware with some additional info

---

### Post by Jackalyn on 2012-07-12
> **mastablasta said:**
> yes it's magic words... :-)
 
ls = list
lspci = list all pci connected devices
lsusb = list all USB devices
lshw = list all detected hardware with some additional info

OOOOH that makes sense

But what does all this stuff mean?

jacky@jacky-Aspire-6930G:~$ 'lsusb' listst your USB ports and devices4
Usage: lsusb [options]...
List USB devices
  -v, --verbose
      Increase verbosity (show descriptors)
  -s [[bus]:][devnum]
      Show only devices with specified device and/or
      bus numbers (in decimal)
  -d vendor:[product]
      Show only devices with the specified vendor and
      product ID numbers (in hexadecimal)
  -D device
      Selects which device lsusb will examine
  -t
      Dump the physical USB device hierarchy as a tree
  -V, --version
      Show version of program
jacky@jacky-Aspire-6930G:~$ lspci your pci devices
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
jacky@jacky-Aspire-6930G:~$ H
H: command not found
jacky@jacky-Aspire-6930G:~$ 1
1: command not found
jacky@jacky-Aspire-6930G:~$ 2
2: command not found
jacky@jacky-Aspire-6930G:~$

jacky@jacky-Aspire-6930G:~$ ls
AB.zip                                   META-INF
ÀM?@H                                    mods.d
audacity tests                           modules
C:\nppdf32Log\debuglog.txt               Music
Desktop                                  Office
Documents                                Pictures
Don Pegg storymaking with children.pdf   pkg-desc
Downloads                                Public
Dropbox                                  registration
examples.desktop                         sakis3g
eyfs statutory framework march 2012.pdf  seamonkey
firedance final.pdf                      Templates
fonts                                    Ubuntu One
icons                                    Videos
Kindlegen                                will
jacky@jacky-Aspire-6930G:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 9300M GS] (rev a1)
07:00.0 Network controller: Intel Corporation WiFi Link 5100
09:00.0 Ethernet controller: Atheros Communications Inc. AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
jacky@jacky-Aspire-6930G:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 004: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 004 Device 002: ID 147e:1000 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 002 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem
Bus 002 Device 003: ID 19d2:0010 ZTE WCDMA Technologies MSM 
jacky@jacky-Aspire-6930G:~$ lshw

So the phone shows up as ZTE WCDMA how do I get the pics out? Sorry mods, I seem to have ended up with two threads that are somehow linked though the original question was different.

---

### Post by plucky on 2012-07-12
> But what does all this stuff mean?


The commands are ```
ls
lspci
lsusb
lshw
```

Don't put anything else in the line except the <enter> key for each entry.

Good Luck

---

### Post by Jackalyn on 2012-07-12
> **plucky said:**
> The commands are ```
ls
lspci
lsusb
lshw
```Don't put anything else in the line except the <enter> key for each entry.

Good Luck
OK that does show my phone..not how on earth do I get the pictures off of it

jacky@jacky-Aspire-6930G:~$ ls
AB.zip                                   META-INF
ÀM?@H                                    mods.d
audacity tests                           modules
C:\nppdf32Log\debuglog.txt               Music
Desktop                                  Office
Documents                                Pictures
Don Pegg storymaking with children.pdf   pkg-desc
Downloads                                Public
Dropbox                                  registration
examples.desktop                         sakis3g
eyfs statutory framework march 2012.pdf  seamonkey
firedance final.pdf                      Templates
fonts                                    Ubuntu One
icons                                    Videos
Kindlegen                                will
jacky@jacky-Aspire-6930G:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 9300M GS] (rev a1)
07:00.0 Network controller: Intel Corporation WiFi Link 5100
09:00.0 Ethernet controller: Atheros Communications Inc. AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
jacky@jacky-Aspire-6930G:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 004: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 004 Device 002: ID 147e:1000 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 002 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem
Bus 002 Device 003: ID 19d2:0010 ZTE WCDMA Technologies MSM 
jacky@jacky-Aspire-6930G:~$ lshw

I guess that also answers my question about bluetooth???

---

