---
title: "Ubuntu install failing at &quot;Loading module usb-storage&quot;"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by number2301 on 2008-11-28
Hi all, I've recently decided to give Linux a go after thinking about it for many years and my computer needing a reformat anyway. So I ran the live CD for a while and everything worked just fine as far as I can tell. But when I tried to install it to the hard drive, it got stuck at 90% (Loading module 'usb-storage' for 'usb storage'). I left it sat at this for about half an hour and it didn't move so I had to shut the machine down.

I had wondered if it had any relation to the messages I get when loading the live CD, I get several iterations of something to the effect of - rt2x00 USB_vendor_request: Error... and on the next line 'error -110'. Apologies for the vagueness but I was copying it down onto paper and it's not up for very long!

I get the above message roughly 10 times before the system boots up and Ubuntu works with my USB wireless stick just fine. I've not actually tried it with a memory stick but I'm sure there'd be some solution for that if I could get it to install!

Thanks in advance!

---

### Post by Michael.Godawski on 2008-11-28
So you mean the Live Session works after the error messages, and the installation get stuck forever during the loading of the module usb-storage?

I suggest unplugging all unnecessary USB devices during install.

---

### Post by number2301 on 2008-11-28
Yes that was what I meant, between posting this thread and now I tried to install a second time, this time from the Live CD as opposed to straight from the CD before loading Ubuntu, it installed fine but I still get the error messages and start up takes quite a long time.

I've now tested it with my memory stick and both that and my USB wireless stick work fine from the front USB ports.

Is there anything to be worried about with the error messages?

EDIT - I've just noticed, it comes under "*Starting Bluetooth" which doesn't have an ok next to it like the other "*Starting whatever" lines do, it's a desktop computer which doesn't have bluetooth.

---

### Post by Michael.Godawski on 2008-11-28
So when you installed Ubuntu successfully and you are able to login, let's have a closer look at the ominous error messages:),

Run ```
dmesg
``` in terminal and post here the error message under suspicion.

Also have a look at the system logs in System > Administration > System Log.

---

### Post by number2301 on 2008-11-28
The below is I believe the relevant section, I've highlighted the error messages which it shows me during boot up in bold and attached the full dmesg, xorg and syslog outputs as text files.

> [  198.286893] Bluetooth: Core ver 2.13
[  198.287554] NET: Registered protocol family 31
[  198.287560] Bluetooth: HCI device and connection manager initialized
[  198.287564] Bluetooth: HCI socket layer initialized
[  198.407699] Bluetooth: L2CAP ver 2.11
[  198.407707] Bluetooth: L2CAP socket layer initialized
[  198.436205] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  198.436213] Bluetooth: BNEP filters: protocol multicast
[  198.479184] Bridge firewalling registered
[  198.479958] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  198.505512] Bluetooth: SCO (Voice Link) ver 0.6
[  198.505520] Bluetooth: SCO socket layer initialized
[B][  291.172054] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x09 failed for offset 0x0000 with error -110.
[  293.672057] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x04d0 with error -110.
[  296.172064] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x04d0 with error -110.
[  298.672071] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x04d0 with error -110.
[  301.172263] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x04d0 with error -110.
[  303.672086] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x04d0 with error -110.
[  303.672281] phy1 -> rt2500usb_bbp_read: Error - PHY_CSR8 register busy. Read failed.
[  306.172093] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0400 with error -110.[/B]
[  306.172187] phy1 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[  306.172271] phy1 -> rt2x00lib_probe_dev: Error - Failed to allocate device.


Thanks for the speedy response!

---

### Post by Michael.Godawski on 2008-11-28
> I've now tested it with my memory stick and both that and my USB wireless stick work fine from the front USB ports.

So your wlan connection is working fine?

Please post also the results of these commands:

```
lsusb
iwconfig
sudo lshw -C network
```

When nothing more happens than this error messages which seemingly do not any harm...then we are lucky.:)

---

### Post by number2301 on 2008-11-28
Wlan is working fine, commands give -

> curtis@desktop:~$ lsusb
Bus 005 Device 002: ID 050d:7051 Belkin Components F5D7051 54g USB Network Adapter
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
curtis@desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE802.11bg  ESSID:"Albert"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:74:95:49:4C   
          Bit Rate=18 Mb/s   Tx-Power=14 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Link Quality=45/100  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

curtis@desktop:~$ sudo lshw -C network
[sudo] password for curtis: 
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:15:f2:2e:46:fe
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fa:20:44:bd:e8:6f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:50:c2:de:6d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rndis_wlan driverversion=22-Aug-2005 firmware=Wireless RNDIS device ip=192.168.0.6 link=yes multicast=yes wireless=IEEE802.11bg
curtis@desktop:~$ sudo lshw -C network


I've now tested the rear USB ports which are working fine, so as far as I can tell the only problem I'm getting is the error messages themselves and slow booting.

---

