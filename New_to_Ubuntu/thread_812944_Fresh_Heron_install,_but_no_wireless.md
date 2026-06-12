---
title: "Fresh Heron install, but no wireless"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by TalioGladius on 2008-05-30
Fresh install of Heron, but I have no wireless.

Dell XPS M1710 laptop. Intel PRO/Wireless 3945ABG. That's R171131 from dell.
2.6.24-16-generic


ifconfig only shows eth0, lo, and my two vmware networks.  The network manager only shows wired network.

Help.

---

### Post by ukripper on 2008-05-30
> **TalioGladius said:**
> Fresh install of Heron, but I have no wireless.

Dell XPS M1710 laptop. Intel PRO/Wireless 3945ABG. That's R171131 from dell.
2.6.24-16-generic


ifconfig only shows eth0, lo, and my two vmware networks.  The network manager only shows wired network.

Help.

can you post output of following :

```
lspci
```

---

### Post by TalioGladius on 2008-05-30
> **ukripper said:**
> can you post output of following :

```
lspci
```00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by ukripper on 2008-05-30
Also,

```
iwconfig
```

---

### Post by TalioGladius on 2008-05-30
> **ukripper said:**
> Also,

```
iwconfig
```lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

---

### Post by ukripper on 2008-05-30
this is strange because in Hardy's kernel you have iwl3945 driver which i am currently using within gutsy. It should have been working out of the box for you in hardy. Can you do the folowing so that i know what kernel version you are using:

```
uname -a
```

---

### Post by TalioGladius on 2008-05-30
> **ukripper said:**
> this is strange because in Hardy's kernel you have iwl3945 driver which i am currently using within gutsy. It should have been working out of the box for you in hardy. Can you do the folowing so that i know what kernel version you are using:

```
uname -a
```That's what I keep reading, and it doesn't make sense.  It also worked just fine out of the box for the past 3 versions, I was just forced to go to windows for a couple months before going to 8.04.

2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

---

### Post by ukripper on 2008-05-30
> **TalioGladius said:**
> That's what I keep reading, and it doesn't make sense.  It also worked just fine out of the box for the past 3 versions, I was just forced to go to windows for a couple months before going to 8.04.

2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

Have you tried using new kernel update available recently from update manager? 
2.6.24-17

Have you got wired connection you can connect your laptop to and do updates and let's see if new kernel revision does anything for your lappy?

---

### Post by stchman on 2008-05-30
I had a laptop with a 3945ABG and it worked..... kind of.

The 4965AGN works better in Hardy than the older 3945ABG.

---

### Post by TalioGladius on 2008-05-30
> **ukripper said:**
> Have you tried using new kernel update available recently from update manager? 
2.6.24-17

Have you got wired connection you can connect your laptop to and do updates and let's see if new kernel revision does anything for your lappy?yes.  -17 didn't work and caused me issues with every application working for about 3 seconds and freezing for 10-15 seconds.  Booting to -16 resolves that issue.  All other updates are installed.

I hate to try and reimage....especially if it doesn't help it.

---

### Post by ukripper on 2008-05-30
> **TalioGladius said:**
> yes.  -17 didn't work and caused me issues with every application working for about 3 seconds and freezing for 10-15 seconds.  Booting to -16 resolves that issue.  All other updates are installed.

I hate to try and reimage....especially if it doesn't help it.

Ok can you do this :

```
sudo echo iwl3945 >> /etc/modules
```

and reboot and let see if this fixes it for you.

i have done this in gutsy to use iwl3945 instead of ipw

---

### Post by TalioGladius on 2008-05-30
> **ukripper said:**
> Ok can you do this :

```
sudo echo iwl3945 >> /etc/modules
```

and reboot and let see if this fixes it for you.

i have done this in gutsy to use iwl3945 instead of ipwsudo echo iwl3945 >> /etc/modules
bash: /etc/modules: Permission denied

---

### Post by TalioGladius on 2008-05-30
I had to use gedit to add it, echo was denied.  Anyhow, no dice.  Nothing has changed, it didn't help a thing...

---

### Post by TalioGladius on 2008-05-30
I also booted to the cd to see if I could get wireless off of that, and no dice.


Apparently 8.04 isn't going to work for this laptop currently if I want wireless.  I do have a nintendo wifi usb connector....any ideas on how I could set this thing up?

---

### Post by TalioGladius on 2008-05-30
Looks like nvidia driver for fedora 9 was released.  Maybe I should go that route instead.

---

### Post by ukripper on 2008-05-30
Give 7.10  a go instead of Hardy. 7.10 is supported till April 2009 and is very stable. I have only one machine running hardy and rest others are all 7.10

---

### Post by WRDN on 2008-05-30
You could try installing ndiswrapper and using the Windows driver.

---

### Post by Zorael on 2008-06-05
TalioGladius, I recognize what you're describing all too well.

With the -16 kernel, I got mine to work by adding a file to /etc/modprobe.d/ to disable HW scanning. This made it work, out of the (repainted) box.

With the -17 kernel, I got the delays at which all programs stop and everything just chugs along. It happens everytime it scans for available networks, quite reproducible. At each time it spammed "Microcode SW error"-like messages in dmesg; there are numerous launchpad and intellinuxwireless.org bugtracker bugs regarding this. One off the top of my head: [http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1650](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1650).

My solution that seems to work on both kernels (haven't tried the -18 one yet, laptop hasn't returned from Acer repair center in Germany), is to find and compile a driver manually. This needs to be done after a kernel upgrade, of course. See [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) for links and installation how-tos.

Some snapshots plain didn't compile for me, but the golden one I found was the one released at 2008-05-07. Later snapshots may, of course, compile for you.

The disable_hw_scan method:
```
$ sudo su
# rmmod iwl3945
# echo alias wlan0 iwl3945 >> iwl3945 && echo options iwl3945 disable_hw_scan=1 hwcrypto=1 >> iwl3945
# mv iwl3945 /etc/modprobe.d/
# modprobe iwl3945
# iwlist scan
```

It still takes 10 seconds to complete a scan, but it works. Give it a shot.

---

### Post by Golem XIV on 2008-06-05
Have you tried this?

[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/](http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/)

---

### Post by Zorael on 2008-06-05
Backports did nothing for me, not the -16 nor the -17 ones, though I imagine it may solve others' issues.

---

