---
title: "[SOLVED] can not get my wireless to work"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by jpease on 2008-10-31
1st time ubuntu user.
I can not get my wireless to work.  It worked flawless in xp-pro.

I installed 8.10 last night on my laptop.  Been a long time windows user I am really impressed.  I think I am really going to like it.

Wired works flawlessly.  I had the update manager perform all the updates after the install.

Wireless Infrastructure:
Linksys WAP54g Access point
Linksys WPC54g Notebook adapter (power light on, link light not blinking)
Security WEP 64 bits
SSID broadcast enabled

Laptop IBM T23

I got the little network icon upper right with an red triangle.  Message no network connection.  I tried to manually configure the network but it did not work.

Please help.

---

### Post by jpease on 2008-10-31
ps: I have another win vista laptop next to the ibm/ubuntu that is working via wireless with no problems, which is what I am using to post here.

Please help!

---

### Post by superprash2003 on 2008-10-31
in your terminal type lshw -C network and post output.. also post output of iwconfig

---

### Post by jpease on 2008-10-31
nathan@nathan-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 41
       serial: 00:d0:59:a8:f5:11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f2:d3:3e:7e:17:5e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0c:41:c4:a0:e3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
nathan@nathan-laptop:~$

---

### Post by jpease on 2008-10-31
nathan@nathan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

nathan@nathan-laptop:~$

---

### Post by jpease on 2008-10-31
> **superprash2003 said:**
> in your terminal type lshw -C network and post output.. also post output of iwconfig
when I did the lshw -c network I wasn't connected to the lan line

---

### Post by jpease on 2008-10-31
nathan@nathan-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:00.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:00.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
nathan@nathan-laptop:~$

nathan@nathan-laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046d:c030 Logitech, Inc. iFeel Mouse
Bus 002 Device 003: ID 045e:00b0 Microsoft Corp. Digital Media Pro Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
nathan@nathan-laptop:~$

---

### Post by dolman25 on 2008-10-31
have you tried checking "hardware drivers" located in system/administration?

---

### Post by jpease on 2008-10-31
> **dolman25 said:**
> have you tried checking "hardware drivers" located in system/administration?
WOW! thanks it worked.  Once activated it went right through with the appropriate security parameters.

thanks!

---

### Post by superprash2003 on 2008-11-01
glad to know you got it working..Please mark Thread as SOLVED  under Thread Tools

---

### Post by LookTJ on 2008-11-01
Did you click on the network icon to view the available networks?

edit: Nevermind didn't read thread

---

