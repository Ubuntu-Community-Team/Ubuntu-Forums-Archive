---
title: "strange behavior for 8.04-wireless"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by akkad on 2008-05-14
i have 2 laptops dell and lenovo, both have a fresh installation of 8.04, both have intel wireless card, since 8.04 installed, the WIFI LED on both laptops have no light any more (starnge !!!), the dell wifi is working but lenovo is not, any idea ???

---

### Post by wjp.reg on 2008-05-14
[It's a bug]("https://bugs.launchpad.net/ubuntu/+bug/217889")

---

### Post by balagosa on 2008-05-14
> **akkad said:**
> i have 2 laptops dell and lenovo, both have a fresh installation of 8.04, both have intel wireless card, since 8.04 installed, the WIFI LED on both laptops have no light any more (starnge !!!), the dell wifi is working but lenovo is not, any idea ???

the Dell WiFi worked out of the box. while the Lenovo will need some tweaking.

so, can you post the outcome of:

```
lspci
``` on your Lenovo?

---

### Post by akkad on 2008-05-14
here is it :

[COLOR="DarkOrange"]00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)[/COLOR]

---

### Post by balagosa on 2008-05-14
hmmm....you got the same lspci (Network) as mine. so have you tried your Lenovo wifi? as previous poster has said, it is a bug? Light if off, but WiFi access is on?

if the prob is concerning your WiFi driver, i can not help you with that. because i am also configuring my WiFi at the moment.

but you know one thing that is weird, my Asus Details listed [**3945ABG Wireless**]("http://www.sulit.com.ph/index.php/view+classifieds/id/309315/ASUS+A8LE+-+Centrino+Duo+Pentium+M+1.66Ghz+1GB+RAM+120GB+HDD") as it's Wireless Description. but my lspci dished out:
03:00.0 Network controller: a certain Atheros 5007EG (rev 02)

---

### Post by akkad on 2008-05-14
actually when switch on/off the wifi it looks like it is working on the tray netwrok notification manager but no such one access point appears.

---

### Post by Stefan Stryjecki on 2008-05-14
Try installing linux-backport-modules. It solved the problem for me and many others:

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/181255]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/181255")

---

### Post by akkad on 2008-05-14
i tried this but useless :
sudo apt-get install linux-backports-modules-hardy
sudo rmmod iwl3945; sudo modprobe iwl3945

by the way at the boot time there is a message appears in the command line it tells about some error, at the time it appears the LED flashes only once, may be this can help the developers to identify it.

---

### Post by balagosa on 2008-05-14
> **akkad said:**
> i tried this but useless :
sudo apt-get install linux-backports-modules-hardy
sudo rmmod iwl3945; sudo modprobe iwl3945

by the way at the boot time there is a message appears in the command line it tells about some error, at the time it appears the LED flashes only once, may be this can help the developers to identify it.

you say during boot time?? try logging on recovery mode and posting that error here. it might be useful.

---

### Post by akkad on 2008-05-15
it sounds crazy but yes i was waiting the error to appear while boot then take the attached screen shot (i dont know how to get it from recovery mode) :) , u dont know how hard was that, any way this screen shot error appears for a second at the same time the WIFI led flashes for 2 -3 seconds.

---

