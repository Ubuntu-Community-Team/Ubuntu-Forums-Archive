---
title: "WiFi Problems"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by DRS5193 on 2012-09-22
I am on Ubuntu 12.04 and upgraded from 11.10.  I am currently dual booting with windows 7.

I can't connect to my colleges WiFi.  I have never been able to connect on boot up, and have had to be connected via ethernet first before I can connect wireless.  This has not been a problem because I've always been near an ethernet jack when I needed to use the internet so it hasn't been a concern until now, where I can't connect to the WiFi at all.  I've toggled the F2 key on and off, so that's not the issue.

Any help would be greatly appreciated!

---

### Post by titanSavior on 2012-09-22
It would help to know what you are running it on. Especially your wireless device.

---

### Post by Hadaka on 2012-09-22
Hi, please post the output of..

```
lspci -nnk | grep -iA2 0280 
```

---

### Post by Bucky Ball on 2012-09-22
*Thread moved to **Networking & Wireless***


And also the output of:

```
sudo lshw -C network
```... please. What is in 'Additional Drivers'? Nothing disabled for wireless?

PS: Does the wireless light go on and off when you toggle? Obvious, but make sure you know it is the 'on' position. ;)

---

### Post by DRS5193 on 2012-09-23
> **Hadaka said:**
> Hi, please post the output of..

```
lspci -nnk | grep -iA2 0280 
```

When doing this I get the following:

> 03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel modules: bcma, brcmsmac

---

### Post by DRS5193 on 2012-09-23
> **Bucky Ball said:**
> *Thread moved to **Networking & Wireless***


And also the output of:

```
sudo lshw -C network
```

When I do this I get the following:

 ```
*-network UNCLAIMED     
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c1
       serial: f0:4d:a2:67:b8:00
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=atl1c  driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=161.115.25.6  latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:f0400000-f043ffff ioport:2000(size=128)

```

> ... please. What is in 'Additional Drivers'? Nothing disabled for wireless?

PS: Does the wireless light go on and off when you toggle? Obvious, but make sure you know it is the 'on' position. ;)


My computer doesn't have a wireless light.  But I've tried to connect when it's is both on and off (I don't which is which, since I don't have the light).

I did however, note that my wireless card driver (Broadcom STA Wireless Driver) is not activated so I attempted to activate it.  It told me it couldn't and to consult /var/log/jockey/log for more info.  I would like to upload it here, but I can not upload .log files apparently :(  Is there something in the file specifically I should copy and paste here?

Thank you all for your help and support!

---

### Post by Bucky Ball on 2012-09-23
Ah, that is a package to do with the Additional Drivers app. 

Make sure you have jockey-gtk and jockey-common installed and try again.

Other thing to do is post the contents of the file  /var/log/jockey/log, the jockey log file, and that will give us more clues as to what the error is.

---

### Post by sandyd on 2012-09-23
Please post the output of
```

cat /var/log/jockey.log
```

---

### Post by Hadaka on 2012-09-23
Hi, your card broadcom 4313..4727 requires the sta driver.
use the chili555 fix-it method.

```
 sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
 
```

that should work for you.

---

### Post by DRS5193 on 2012-09-23
> **sandyd said:**
> Please post the output of
```

cat /var/log/jockey.log
```

It's really long.... but here it is

```
2012-09-23 16:53:14,161 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-09-23 16:53:14,162 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,162 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'acpi:DLL0457:PNP0F13:')
2012-09-23 16:53:14,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00003B0Bsv00001028sd00000457bc06sc01i00')
2012-09-23 16:53:14,165 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-09-23 16:53:14,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2012-09-23 16:53:14,166 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,166 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2012-09-23 16:53:14,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA09:bd10/20/2010:svnDellInc.:pnInspironN7010:pvrA09:rvnDellInc.:rn08VFX1:rvrA09:cvnDellInc.:ct8:cvrA09:')
2012-09-23 16:53:14,180 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop'}
2012-09-23 16:53:14,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00002D01sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-09-23 16:53:14,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00003B30sv00001028sd00000457bc0Csc05i00')
2012-09-23 16:53:14,189 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-09-23 16:53:14,189 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-09-23 16:53:14,190 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,190 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,190 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,190 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2012-09-23 16:53:14,190 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-09-23 16:53:14,191 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00')
2012-09-23 16:53:14,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2012-09-23 16:53:14,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00002D12sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,197 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00003B56sv00001028sd00000457bc04sc03i00')
2012-09-23 16:53:14,200 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-09-23 16:53:14,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00002D10sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,203 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-09-23 16:53:14,203 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,203 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,203 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,203 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,203 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-0800200C9A66')
2012-09-23 16:53:14,203 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-09-23 16:53:14,203 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,204 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,204 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,204 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'acpi:PNP0303:')
2012-09-23 16:53:14,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'platform:pcspkr')
2012-09-23 16:53:14,204 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-09-23 16:53:14,204 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,205 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-09-23 16:53:14,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2012-09-23 16:53:14,205 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-09-23 16:53:14,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-09-23 16:53:14,206 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,206 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,206 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-09-23 16:53:14,206 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,206 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-09-23 16:53:14,206 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,206 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-09-23 16:53:14,206 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,206 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,206 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,206 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2012-09-23 16:53:14,207 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2012-09-23 16:53:14,207 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-09-23 16:53:14,207 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,207 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-09-23 16:53:14,207 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,207 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2012-09-23 16:53:14,207 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'platform:dcdbas')
2012-09-23 16:53:14,208 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00003B32sv00001028sd00000457bc11sc80i00')
2012-09-23 16:53:14,211 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intel_ips'}
2012-09-23 16:53:14,211 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_ips', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,211 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001028sd00000010bc02sc80i00')
2012-09-23 16:53:14,249 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2012-09-23 16:53:14,250 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:14,250 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-09-23 16:53:14,254 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-09-23 16:53:14,255 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:14,255 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-09-23 16:53:14,256 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2012-09-23 16:53:14,256 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,256 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2012-09-23 16:53:14,256 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd00000457bc06sc04i01')
2012-09-23 16:53:14,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-09-23 16:53:14,272 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-09-23 16:53:14,272 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,272 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-09-23 16:53:14,272 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-09-23 16:53:14,273 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,273 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,273 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-09-23 16:53:14,273 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,273 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,273 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,273 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,273 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00003B34sv00001028sd00000457bc0Csc03i20')
2012-09-23 16:53:14,276 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'acpi:PNP0200:')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:PNP0100:')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00003B3Csv00001028sd00000457bc0Csc03i20')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'platform:dell-laptop')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v0C45p6480d9A07dcEFdsc02dp01ic0Eisc01ip00')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:INT0800:')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'platform:regulatory')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00000046sv00001028sd00000457bc03sc00i00')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v0C45p6480d9A07dcEFdsc02dp01ic0Eisc02ip00')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00002D13sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:PNP0103:')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00003B64sv00001028sd00000457bc07sc80i00')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00001969d00002060sv00001028sd00000457bc02sc00i00')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:PNP0000:')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00002C62sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00003B2Fsv00001028sd00000457bc01sc06i01')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00002D11sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0003v0C45p6480e9A07-e0,1,kD4,ramlsfw')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:DLL0457:PNP0F13:')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00003B0Bsv00001028sd00000457bc06sc01i00')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA09:bd10/20/2010:svnDellInc.:pnInspironN7010:pvrA09:rvnDellInc.:rn08VFX1:rvrA09:cvnDellInc.:ct8:cvrA09:')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00002D01sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00003B30sv00001028sd00000457bc0Csc05i00')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00002D12sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00003B56sv00001028sd00000457bc04sc03i00')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00002D10sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-0800200C9A66')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:PNP0303:')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'platform:pcspkr')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'platform:dcdbas')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00003B32sv00001028sd00000457bc11sc80i00')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001028sd00000010bc02sc80i00')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd00000457bc06sc04i01')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-09-23 16:53:14,282 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00003B34sv00001028sd00000457bc0Csc03i20')
2012-09-23 16:53:14,282 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2012-09-23 16:53:14,282 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:PNP0200:')
2012-09-23 16:53:14,332 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:14,351 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:14,389 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:17,722 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:21,585 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-09-23 16:53:21,586 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-09-23 16:53:21,645 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:24,106 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:24,133 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:24,174 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:25,857 DEBUG: Shutting down

```

---

### Post by DRS5193 on 2012-09-23
> **Bucky Ball said:**
> Ah, that is a package to do with the Additional Drivers app. 

Make sure you have jockey-gtk and jockey-common installed and try again.

Other thing to do is post the contents of the file  /var/log/jockey/log, the jockey log file, and that will give us more clues as to what the error is.

The installation app thing didn't work.  But just to make sure, I'm not a complete idiot, could you post the directions for how to post those?

These are the contents of jockey.log

```
2012-09-23 11:01:25,674 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170>
2012-09-23 11:01:27,857 DEBUG: reading modalias file /lib/modules/3.2.0-31-generic/modules.alias
2012-09-23 11:01:27,938 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-09-23 11:01:27,938 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-09-23 11:01:28,001 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-09-23 11:01:28,011 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-09-23 11:01:28,017 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-09-23 11:01:28,017 DEBUG: fglrx.available: falling back to default
2012-09-23 11:01:28,141 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-09-23 11:01:28,148 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-09-23 11:01:28,154 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-09-23 11:01:28,154 DEBUG: fglrx.available: falling back to default
2012-09-23 11:01:28,210 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-09-23 11:01:28,210 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2012-09-23 11:01:28,218 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2012-09-23 11:01:28,219 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2012-09-23 11:01:28,219 DEBUG: cdv.available: falling back to default
2012-09-23 11:01:28,272 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2012-09-23 11:01:28,273 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-09-23 11:01:28,280 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-09-23 11:01:28,308 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-09-23 11:01:28,309 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-09-23 11:01:28,309 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-09-23 11:01:28,316 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-09-23 11:01:28,317 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-09-23 11:01:28,344 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-09-23 11:01:28,344 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-09-23 11:01:28,372 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-09-23 11:01:28,383 DEBUG: Software modem not available
2012-09-23 11:01:28,383 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-09-23 11:01:28,416 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-09-23 11:01:28,417 DEBUG: Firmware for DVB cards not available
2012-09-23 11:01:28,418 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-09-23 11:01:28,427 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-09-23 11:01:28,434 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-09-23 11:01:28,478 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-09-23 11:01:28,478 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-09-23 11:01:28,485 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-09-23 11:01:28,486 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-09-23 11:01:28,486 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-09-23 11:01:28,487 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-09-23 11:01:28,498 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-09-23 11:01:28,505 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-09-23 11:01:28,508 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-09-23 11:01:28,508 DEBUG: NVIDIA accelerated graphics driver not available
2012-09-23 11:01:28,513 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-09-23 11:01:28,520 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-09-23 11:01:28,521 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-09-23 11:01:28,521 DEBUG: NVIDIA accelerated graphics driver not available
2012-09-23 11:01:28,527 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-09-23 11:01:28,534 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-09-23 11:01:28,536 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-09-23 11:01:28,536 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-09-23 11:01:28,542 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-09-23 11:01:28,549 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-09-23 11:01:28,551 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-09-23 11:01:28,551 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-09-23 11:01:28,557 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-09-23 11:01:28,564 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-09-23 11:01:28,566 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-09-23 11:01:28,566 DEBUG: NVIDIA accelerated graphics driver not available
2012-09-23 11:01:28,572 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-09-23 11:01:28,579 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-09-23 11:01:28,580 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-09-23 11:01:28,581 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-09-23 11:01:28,581 DEBUG: all custom handlers loaded
2012-09-23 11:01:28,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'acpi:PNP0100:')
2012-09-23 11:01:28,581 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-09-23 11:01:28,592 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 11:01:28,680 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:28,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-09-23 11:01:28,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-09-23 11:01:28,680 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00008086d00003B3Csv00001028sd00000457bc0Csc03i20')
2012-09-23 11:01:28,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'platform:dcdbas')
2012-09-23 11:01:28,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-09-23 11:01:28,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2012-09-23 11:01:28,933 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 11:01:28,933 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:28,933 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 11:01:28,934 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:28,934 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-09-23 11:01:28,943 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-09-23 11:01:28,943 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:28,943 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-09-23 11:01:28,943 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:28,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'usb:v0C45p6480d9A07dcEFdsc02dp01ic0Eisc01ip00')
2012-09-23 11:01:28,970 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-09-23 11:01:28,970 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:28,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'acpi:INT0800:')
2012-09-23 11:01:28,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'platform:dell-laptop')
2012-09-23 11:01:28,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-09-23 11:01:28,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 11:01:28,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:28,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-09-23 11:01:28,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-09-23 11:01:28,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00008086d00000046sv00001028sd00000457bc03sc00i00')
2012-09-23 11:01:28,974 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2012-09-23 11:01:28,974 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:28,974 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'usb:v0C45p6480d9A07dcEFdsc02dp01ic0Eisc02ip00')
2012-09-23 11:01:28,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2012-09-23 11:01:28,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-09-23 11:01:28,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00008086d00002D13sv00008086sd00008086bc06sc00i00')
2012-09-23 11:01:28,978 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'acpi:PNP0103:')
2012-09-23 11:01:28,978 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00008086d00003B64sv00001028sd00000457bc07sc80i00')
2012-09-23 11:01:28,980 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-09-23 11:01:28,980 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:28,981 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00001969d00002060sv00001028sd00000457bc02sc00i00')
2012-09-23 11:01:28,984 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'atl1c'}
2012-09-23 11:01:28,984 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:28,984 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'acpi:PNP0000:')
2012-09-23 11:01:28,984 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00008086d00002C62sv00008086sd00008086bc06sc00i00')
2012-09-23 11:01:28,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00008086d00003B2Fsv00001028sd00000457bc01sc06i01')
2012-09-23 11:01:28,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00008086d00002D11sv00008086sd00008086bc06sc00i00')
2012-09-23 11:01:28,991 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2012-09-23 11:01:29,003 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-09-23 11:01:29,003 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,003 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-09-23 11:01:29,004 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,004 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2012-09-23 11:01:29,004 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-09-23 11:01:29,004 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,004 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-09-23 11:01:29,004 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 11:01:29,004 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,005 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2012-09-23 11:01:29,005 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi'}
2012-09-23 11:01:29,005 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,005 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'input:b0003v0C45p6480e9A07-e0,1,kD4,ramlsfw')
2012-09-23 11:01:29,005 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 11:01:29,005 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,005 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 11:01:29,005 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,005 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-09-23 11:01:29,005 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 11:01:29,006 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,006 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 11:01:29,006 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,006 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'acpi:DLL0457:PNP0F13:')
2012-09-23 11:01:29,006 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00008086d00003B0Bsv00001028sd00000457bc06sc01i00')
2012-09-23 11:01:29,009 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-09-23 11:01:29,009 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2012-09-23 11:01:29,009 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 11:01:29,009 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,009 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 11:01:29,009 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2012-09-23 11:01:29,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA09:bd10/20/2010:svnDellInc.:pnInspironN7010:pvrA09:rvnDellInc.:rn08VFX1:rvrA09:cvnDellInc.:ct8:cvrA09:')
2012-09-23 11:01:29,022 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop'}
2012-09-23 11:01:29,022 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,022 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00008086d00002D01sv00008086sd00008086bc06sc00i00')
2012-09-23 11:01:29,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-09-23 11:01:29,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00008086d00003B30sv00001028sd00000457bc0Csc05i00')
2012-09-23 11:01:29,028 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-09-23 11:01:29,028 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-09-23 11:01:29,028 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 11:01:29,028 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,028 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 11:01:29,028 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2012-09-23 11:01:29,029 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-09-23 11:01:29,029 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,029 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00')
2012-09-23 11:01:29,029 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2012-09-23 11:01:29,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00008086d00002D12sv00008086sd00008086bc06sc00i00')
2012-09-23 11:01:29,035 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00008086d00003B56sv00001028sd00000457bc04sc03i00')
2012-09-23 11:01:29,038 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-09-23 11:01:29,038 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,038 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00008086d00002D10sv00008086sd00008086bc06sc00i00')
2012-09-23 11:01:29,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-09-23 11:01:29,041 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 11:01:29,041 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,041 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 11:01:29,041 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-0800200C9A66')
2012-09-23 11:01:29,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-09-23 11:01:29,042 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 11:01:29,042 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,042 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 11:01:29,042 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'acpi:PNP0303:')
2012-09-23 11:01:29,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2012-09-23 11:01:29,043 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-09-23 11:01:29,043 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,043 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-09-23 11:01:29,043 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 11:01:29,043 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,043 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-09-23 11:01:29,043 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,043 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-09-23 11:01:29,043 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,043 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-09-23 11:01:29,044 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,044 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 11:01:29,044 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,044 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2012-09-23 11:01:29,044 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2012-09-23 11:01:29,044 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-09-23 11:01:29,044 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,045 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-09-23 11:01:29,045 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2012-09-23 11:01:29,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'platform:pcspkr')
2012-09-23 11:01:29,045 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-09-23 11:01:29,045 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,045 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-09-23 11:01:29,046 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,046 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00008086d00003B32sv00001028sd00000457bc11sc80i00')
2012-09-23 11:01:29,048 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intel_ips'}
2012-09-23 11:01:29,049 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_ips', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,049 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001028sd00000010bc02sc80i00')
2012-09-23 11:01:29,085 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2012-09-23 11:01:29,085 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 11:01:29,085 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-09-23 11:01:29,090 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-09-23 11:01:29,090 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 11:01:29,090 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-09-23 11:01:29,090 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2012-09-23 11:01:29,091 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,091 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2012-09-23 11:01:29,091 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,091 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd00000457bc06sc04i01')
2012-09-23 11:01:29,095 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-09-23 11:01:29,104 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-09-23 11:01:29,104 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,104 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-09-23 11:01:29,104 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,104 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-09-23 11:01:29,104 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 11:01:29,105 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,105 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-09-23 11:01:29,105 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 11:01:29,105 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,105 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 11:01:29,105 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 11:01:29,105 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'pci:v00008086d00003B34sv00001028sd00000457bc0Csc03i20')
2012-09-23 11:01:29,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2012-09-23 11:01:29,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x25f6170> about HardwareID('modalias', 'acpi:PNP0200:')
2012-09-23 11:01:29,108 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'acpi:PNP0100:')
2012-09-23 11:01:29,108 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-09-23 11:01:29,108 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-09-23 11:01:29,108 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-09-23 11:01:29,108 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00008086d00003B3Csv00001028sd00000457bc0Csc03i20')
2012-09-23 11:01:29,108 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'platform:dcdbas')
2012-09-23 11:01:29,109 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-09-23 11:01:29,109 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2012-09-23 11:01:29,109 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-09-23 11:01:29,109 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'usb:v0C45p6480d9A07dcEFdsc02dp01ic0Eisc01ip00')
2012-09-23 11:01:29,109 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'acpi:INT0800:')
2012-09-23 11:01:29,109 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'platform:dell-laptop')
2012-09-23 11:01:29,109 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-09-23 11:01:29,109 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-09-23 11:01:29,109 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-09-23 11:01:29,109 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00008086d00000046sv00001028sd00000457bc03sc00i00')
2012-09-23 11:01:29,109 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'usb:v0C45p6480d9A07dcEFdsc02dp01ic0Eisc02ip00')
2012-09-23 11:01:29,109 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2012-09-23 11:01:29,109 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-09-23 11:01:29,109 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00008086d00002D13sv00008086sd00008086bc06sc00i00')
2012-09-23 11:01:29,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'acpi:PNP0103:')
2012-09-23 11:01:29,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00008086d00003B64sv00001028sd00000457bc07sc80i00')
2012-09-23 11:01:29,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00001969d00002060sv00001028sd00000457bc02sc00i00')
2012-09-23 11:01:29,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'acpi:PNP0000:')
2012-09-23 11:01:29,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00008086d00002C62sv00008086sd00008086bc06sc00i00')
2012-09-23 11:01:29,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00008086d00003B2Fsv00001028sd00000457bc01sc06i01')
2012-09-23 11:01:29,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00008086d00002D11sv00008086sd00008086bc06sc00i00')
2012-09-23 11:01:29,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2012-09-23 11:01:29,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2012-09-23 11:01:29,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-09-23 11:01:29,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2012-09-23 11:01:29,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'input:b0003v0C45p6480e9A07-e0,1,kD4,ramlsfw')
2012-09-23 11:01:29,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-09-23 11:01:29,110 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'acpi:DLL0457:PNP0F13:')
2012-09-23 11:01:29,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00008086d00003B0Bsv00001028sd00000457bc06sc01i00')
2012-09-23 11:01:29,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2012-09-23 11:01:29,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2012-09-23 11:01:29,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA09:bd10/20/2010:svnDellInc.:pnInspironN7010:pvrA09:rvnDellInc.:rn08VFX1:rvrA09:cvnDellInc.:ct8:cvrA09:')
2012-09-23 11:01:29,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00008086d00002D01sv00008086sd00008086bc06sc00i00')
2012-09-23 11:01:29,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-09-23 11:01:29,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00008086d00003B30sv00001028sd00000457bc0Csc05i00')
2012-09-23 11:01:29,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-09-23 11:01:29,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2012-09-23 11:01:29,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00')
2012-09-23 11:01:29,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2012-09-23 11:01:29,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00008086d00002D12sv00008086sd00008086bc06sc00i00')
2012-09-23 11:01:29,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00008086d00003B56sv00001028sd00000457bc04sc03i00')
2012-09-23 11:01:29,111 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00008086d00002D10sv00008086sd00008086bc06sc00i00')
2012-09-23 11:01:29,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-09-23 11:01:29,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-0800200C9A66')
2012-09-23 11:01:29,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-09-23 11:01:29,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'acpi:PNP0303:')
2012-09-23 11:01:29,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2012-09-23 11:01:29,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-09-23 11:01:29,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2012-09-23 11:01:29,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2012-09-23 11:01:29,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2012-09-23 11:01:29,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'platform:pcspkr')
2012-09-23 11:01:29,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00008086d00003B32sv00001028sd00000457bc11sc80i00')
2012-09-23 11:01:29,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001028sd00000010bc02sc80i00')
2012-09-23 11:01:29,112 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd00000457bc06sc04i01')
2012-09-23 11:01:29,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-09-23 11:01:29,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-09-23 11:01:29,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-09-23 11:01:29,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'pci:v00008086d00003B34sv00001028sd00000457bc0Csc03i20')
2012-09-23 11:01:29,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2012-09-23 11:01:29,113 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x29b7d40> about HardwareID('modalias', 'acpi:PNP0200:')
2012-09-23 11:01:29,170 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 11:01:29,182 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 11:01:29,203 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 11:08:19,192 DEBUG: Shutting down
2012-09-23 16:53:10,547 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8>
2012-09-23 16:53:12,933 DEBUG: reading modalias file /lib/modules/3.2.0-31-generic/modules.alias
2012-09-23 16:53:13,019 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-09-23 16:53:13,019 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-09-23 16:53:13,081 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-09-23 16:53:13,092 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-09-23 16:53:13,099 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-09-23 16:53:13,100 DEBUG: fglrx.available: falling back to default
2012-09-23 16:53:13,218 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-09-23 16:53:13,224 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-09-23 16:53:13,233 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-09-23 16:53:13,233 DEBUG: fglrx.available: falling back to default
2012-09-23 16:53:13,298 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-09-23 16:53:13,298 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2012-09-23 16:53:13,306 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2012-09-23 16:53:13,307 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2012-09-23 16:53:13,307 DEBUG: cdv.available: falling back to default
2012-09-23 16:53:13,365 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2012-09-23 16:53:13,366 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-09-23 16:53:13,371 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-09-23 16:53:13,393 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-09-23 16:53:13,394 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-09-23 16:53:13,394 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-09-23 16:53:13,402 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-09-23 16:53:13,403 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-09-23 16:53:13,433 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-09-23 16:53:13,434 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-09-23 16:53:13,465 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-09-23 16:53:13,481 DEBUG: Software modem not available
2012-09-23 16:53:13,481 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-09-23 16:53:13,524 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-09-23 16:53:13,525 DEBUG: Firmware for DVB cards not available
2012-09-23 16:53:13,525 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-09-23 16:53:13,535 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-09-23 16:53:13,543 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-09-23 16:53:13,591 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-09-23 16:53:13,592 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-09-23 16:53:13,599 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-09-23 16:53:13,600 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-09-23 16:53:13,601 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-09-23 16:53:13,601 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-09-23 16:53:13,616 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-09-23 16:53:13,622 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-09-23 16:53:13,625 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-09-23 16:53:13,625 DEBUG: NVIDIA accelerated graphics driver not available
2012-09-23 16:53:13,630 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-09-23 16:53:13,637 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-09-23 16:53:13,639 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-09-23 16:53:13,639 DEBUG: NVIDIA accelerated graphics driver not available
2012-09-23 16:53:13,650 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-09-23 16:53:13,656 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-09-23 16:53:13,658 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-09-23 16:53:13,658 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-09-23 16:53:13,661 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-09-23 16:53:13,666 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-09-23 16:53:13,667 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-09-23 16:53:13,667 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-09-23 16:53:13,673 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-09-23 16:53:13,680 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-09-23 16:53:13,682 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-09-23 16:53:13,682 DEBUG: NVIDIA accelerated graphics driver not available
2012-09-23 16:53:13,691 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-09-23 16:53:13,700 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-09-23 16:53:13,702 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-09-23 16:53:13,702 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-09-23 16:53:13,702 DEBUG: all custom handlers loaded
2012-09-23 16:53:13,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'acpi:PNP0100:')
2012-09-23 16:53:13,702 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-09-23 16:53:13,714 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:13,804 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:13,804 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-09-23 16:53:13,804 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-09-23 16:53:13,804 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00003B3Csv00001028sd00000457bc0Csc03i20')
2012-09-23 16:53:14,068 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'platform:dell-laptop')
2012-09-23 16:53:14,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-09-23 16:53:14,081 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2012-09-23 16:53:14,081 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,081 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,082 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,082 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-09-23 16:53:14,092 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-09-23 16:53:14,092 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,092 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-09-23 16:53:14,092 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,092 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'usb:v0C45p6480d9A07dcEFdsc02dp01ic0Eisc01ip00')
2012-09-23 16:53:14,120 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-09-23 16:53:14,121 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'acpi:INT0800:')
2012-09-23 16:53:14,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-09-23 16:53:14,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-09-23 16:53:14,121 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,122 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'platform:regulatory')
2012-09-23 16:53:14,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-09-23 16:53:14,122 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00000046sv00001028sd00000457bc03sc00i00')
2012-09-23 16:53:14,125 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2012-09-23 16:53:14,125 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'usb:v0C45p6480d9A07dcEFdsc02dp01ic0Eisc02ip00')
2012-09-23 16:53:14,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2012-09-23 16:53:14,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-09-23 16:53:14,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00002D13sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'acpi:PNP0103:')
2012-09-23 16:53:14,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00003B64sv00001028sd00000457bc07sc80i00')
2012-09-23 16:53:14,132 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-09-23 16:53:14,132 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00001969d00002060sv00001028sd00000457bc02sc00i00')
2012-09-23 16:53:14,136 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'atl1c'}
2012-09-23 16:53:14,136 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'acpi:PNP0000:')
2012-09-23 16:53:14,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00002C62sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00003B2Fsv00001028sd00000457bc01sc06i01')
2012-09-23 16:53:14,142 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00002D11sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,147 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2012-09-23 16:53:14,159 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-09-23 16:53:14,160 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,160 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-09-23 16:53:14,160 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2012-09-23 16:53:14,160 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-09-23 16:53:14,160 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-09-23 16:53:14,161 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,161 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2012-09-23 16:53:14,161 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi'}
2012-09-23 16:53:14,161 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0003v0C45p6480e9A07-e0,1,kD4,ramlsfw')
2012-09-23 16:53:14,161 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,161 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,161 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-09-23 16:53:14,162 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,162 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'acpi:DLL0457:PNP0F13:')
2012-09-23 16:53:14,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00003B0Bsv00001028sd00000457bc06sc01i00')
2012-09-23 16:53:14,165 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-09-23 16:53:14,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2012-09-23 16:53:14,166 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,166 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2012-09-23 16:53:14,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA09:bd10/20/2010:svnDellInc.:pnInspironN7010:pvrA09:rvnDellInc.:rn08VFX1:rvrA09:cvnDellInc.:ct8:cvrA09:')
2012-09-23 16:53:14,180 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop'}
2012-09-23 16:53:14,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00002D01sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-09-23 16:53:14,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00003B30sv00001028sd00000457bc0Csc05i00')
2012-09-23 16:53:14,189 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-09-23 16:53:14,189 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-09-23 16:53:14,190 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,190 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,190 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,190 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2012-09-23 16:53:14,190 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-09-23 16:53:14,191 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00')
2012-09-23 16:53:14,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2012-09-23 16:53:14,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00002D12sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,197 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00003B56sv00001028sd00000457bc04sc03i00')
2012-09-23 16:53:14,200 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-09-23 16:53:14,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00002D10sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,203 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-09-23 16:53:14,203 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,203 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,203 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,203 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,203 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-0800200C9A66')
2012-09-23 16:53:14,203 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-09-23 16:53:14,203 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,204 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,204 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,204 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'acpi:PNP0303:')
2012-09-23 16:53:14,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'platform:pcspkr')
2012-09-23 16:53:14,204 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-09-23 16:53:14,204 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,205 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-09-23 16:53:14,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2012-09-23 16:53:14,205 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-09-23 16:53:14,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-09-23 16:53:14,206 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,206 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,206 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-09-23 16:53:14,206 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,206 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-09-23 16:53:14,206 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,206 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-09-23 16:53:14,206 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,206 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,206 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,206 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2012-09-23 16:53:14,207 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2012-09-23 16:53:14,207 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-09-23 16:53:14,207 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,207 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-09-23 16:53:14,207 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,207 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2012-09-23 16:53:14,207 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'platform:dcdbas')
2012-09-23 16:53:14,208 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00003B32sv00001028sd00000457bc11sc80i00')
2012-09-23 16:53:14,211 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intel_ips'}
2012-09-23 16:53:14,211 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_ips', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,211 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001028sd00000010bc02sc80i00')
2012-09-23 16:53:14,249 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2012-09-23 16:53:14,250 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:14,250 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-09-23 16:53:14,254 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-09-23 16:53:14,255 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:14,255 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-09-23 16:53:14,256 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2012-09-23 16:53:14,256 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,256 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2012-09-23 16:53:14,256 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd00000457bc06sc04i01')
2012-09-23 16:53:14,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-09-23 16:53:14,272 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-09-23 16:53:14,272 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,272 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-09-23 16:53:14,272 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-09-23 16:53:14,273 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,273 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,273 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-09-23 16:53:14,273 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-09-23 16:53:14,273 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,273 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-09-23 16:53:14,273 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-09-23 16:53:14,273 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'pci:v00008086d00003B34sv00001028sd00000457bc0Csc03i20')
2012-09-23 16:53:14,276 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x140e1b8> about HardwareID('modalias', 'acpi:PNP0200:')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:PNP0100:')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00003B3Csv00001028sd00000457bc0Csc03i20')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'platform:dell-laptop')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v093Ap2510d0100dc00dsc00dp00ic03isc01ip02')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v0C45p6480d9A07dcEFdsc02dp01ic0Eisc01ip00')
2012-09-23 16:53:14,277 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:INT0800:')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'platform:regulatory')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00000046sv00001028sd00000457bc03sc00i00')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v0C45p6480d9A07dcEFdsc02dp01ic0Eisc02ip00')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00002D13sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:PNP0103:')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00003B64sv00001028sd00000457bc07sc80i00')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00001969d00002060sv00001028sd00000457bc02sc00i00')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:PNP0000:')
2012-09-23 16:53:14,278 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00002C62sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00003B2Fsv00001028sd00000457bc01sc06i01')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00002D11sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0003v0C45p6480e9A07-e0,1,kD4,ramlsfw')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:DLL0457:PNP0F13:')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00003B0Bsv00001028sd00000457bc06sc01i00')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'wmi:ABBC0F6D-8EA1-11D1-00A0-C90629100000')
2012-09-23 16:53:14,279 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA09:bd10/20/2010:svnDellInc.:pnInspironN7010:pvrA09:rvnDellInc.:rn08VFX1:rvrA09:cvnDellInc.:ct8:cvrA09:')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00002D01sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00003B30sv00001028sd00000457bc0Csc05i00')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00002D12sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00003B56sv00001028sd00000457bc04sc03i00')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00002D10sv00008086sd00008086bc06sc00i00')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'wmi:DD8C7670-1CB5-11DB-A98B-0800200C9A66')
2012-09-23 16:53:14,280 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0003v093Ap2510e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:PNP0303:')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'platform:pcspkr')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'platform:dcdbas')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00003B32sv00001028sd00000457bc11sc80i00')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001028sd00000010bc02sc80i00')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd00000457bc06sc04i01')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-09-23 16:53:14,281 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-09-23 16:53:14,282 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'pci:v00008086d00003B34sv00001028sd00000457bc0Csc03i20')
2012-09-23 16:53:14,282 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'wmi:ABBC0F6C-8EA1-11D1-00A0-C90629100000')
2012-09-23 16:53:14,282 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x17cdd88> about HardwareID('modalias', 'acpi:PNP0200:')
2012-09-23 16:53:14,332 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:14,351 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:14,389 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:17,722 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:21,585 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-09-23 16:53:21,586 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-09-23 16:53:21,645 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:24,106 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:24,133 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:24,174 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-09-23 16:53:25,857 DEBUG: Shutting down
```

---

### Post by DRS5193 on 2012-09-23
> **Hadaka said:**
> Hi, your card broadcom 4313..4727 requires the sta driver.
use the chili555 fix-it method.

```
 sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
 
```that should work for you.

It did not :(

---

### Post by Bucky Ball on 2012-09-23
Try this  in a terminal just to make sure you have everything installed:

```
sudo apt-get install jockey-gtk
sudo apt-get install jockey-common
```

You probably won't need the second command as jockey-gtk should drag in jockey-common.

What happened?

---

### Post by DRS5193 on 2012-09-23
> **Bucky Ball said:**
> Try this  in a terminal just to make sure you have everything installed:

```
sudo apt-get install jockey-gtk
sudo apt-get install jockey-common
```You probably won't need the second command as jockey-gtk should drag in jockey-common.

What happened?

For both commands I got the following:```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
jockey-gtk is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 rhythmbox-mozilla : Depends: rhythmbox (= 2.96-0ubuntu4.2) but 2.96-0ubuntu4.1 is to be installed
 rhythmbox-plugin-cdrecorder : Depends: rhythmbox (= 2.96-0ubuntu4.2) but 2.96-0ubuntu4.1 is to be installed
 rhythmbox-plugin-magnatune : Depends: rhythmbox (= 2.96-0ubuntu4.2) but 2.96-0ubuntu4.1 is to be installed
 rhythmbox-plugin-zeitgeist : Depends: rhythmbox (>= 2.96-0ubuntu4.2) but 2.96-0ubuntu4.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

I tried the 'apt-get -f install' like it recommended and got this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gir1.2-rb-3.0 librhythmbox-core5 rhythmbox rhythmbox-plugins
The following packages will be upgraded:
  gir1.2-rb-3.0 librhythmbox-core5 rhythmbox rhythmbox-plugins
4 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
6 not fully installed or removed.
Need to get 0 B/1,069 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 340025 files and directories currently installed.)
Preparing to replace rhythmbox 2.96-0ubuntu4.1 (using .../rhythmbox_2.96-0ubuntu4.2_amd64.deb) ...
Unpacking replacement rhythmbox ...
Preparing to replace rhythmbox-plugins 2.96-0ubuntu4.1 (using .../rhythmbox-plugins_2.96-0ubuntu4.2_amd64.deb) ...
Unpacking replacement rhythmbox-plugins ...
Preparing to replace librhythmbox-core5 2.96-0ubuntu4.1 (using .../librhythmbox-core5_2.96-0ubuntu4.2_amd64.deb) ...
Unpacking replacement librhythmbox-core5 ...
Preparing to replace gir1.2-rb-3.0 2.96-0ubuntu4.1 (using .../gir1.2-rb-3.0_2.96-0ubuntu4.2_amd64.deb) ...
Unpacking replacement gir1.2-rb-3.0 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Processing triggers for man-db ...
Setting up whoopsie (0.1.32) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /nonexistent -g whoopsie -s /bin/false -u 118 whoopsie' returned error code 1. Exiting.
dpkg: error processing whoopsie (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up librhythmbox-core5 (2.96-0ubuntu4.2) ...
Setting up gir1.2-rb-3.0 (2.96-0ubuntu4.2) ...
Setting up rhythmbox (2.96-0ubuntu4.2) ...
Setting up rhythmbox-plugin-magnatune (2.96-0ubuntu4.2) ...
Setting up rhythmbox-plugin-zeitgeist (2.96-0ubuntu4.2) ...
Setting up rhythmbox-plugin-cdrecorder (2.96-0ubuntu4.2) ...
Setting up rhythmbox-mozilla (2.96-0ubuntu4.2) ...
Setting up rhythmbox-plugins (2.96-0ubuntu4.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 whoopsie
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The update manager then appeared on it's  own, so I ran updates.  I then tried to run the commands you gave me and got this for the jockey-gtk

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gir1.2-rb-3.0 librhythmbox-core5 rhythmbox rhythmbox-plugins
The following packages will be upgraded:
  gir1.2-rb-3.0 librhythmbox-core5 rhythmbox rhythmbox-plugins
4 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
6 not fully installed or removed.
Need to get 0 B/1,069 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 340025 files and directories currently installed.)
Preparing to replace rhythmbox 2.96-0ubuntu4.1 (using .../rhythmbox_2.96-0ubuntu4.2_amd64.deb) ...
Unpacking replacement rhythmbox ...
Preparing to replace rhythmbox-plugins 2.96-0ubuntu4.1 (using .../rhythmbox-plugins_2.96-0ubuntu4.2_amd64.deb) ...
Unpacking replacement rhythmbox-plugins ...
Preparing to replace librhythmbox-core5 2.96-0ubuntu4.1 (using .../librhythmbox-core5_2.96-0ubuntu4.2_amd64.deb) ...
Unpacking replacement librhythmbox-core5 ...
Preparing to replace gir1.2-rb-3.0 2.96-0ubuntu4.1 (using .../gir1.2-rb-3.0_2.96-0ubuntu4.2_amd64.deb) ...
Unpacking replacement gir1.2-rb-3.0 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Processing triggers for man-db ...
Setting up whoopsie (0.1.32) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /nonexistent -g whoopsie -s /bin/false -u 118 whoopsie' returned error code 1. Exiting.
dpkg: error processing whoopsie (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up librhythmbox-core5 (2.96-0ubuntu4.2) ...
Setting up gir1.2-rb-3.0 (2.96-0ubuntu4.2) ...
Setting up rhythmbox (2.96-0ubuntu4.2) ...
Setting up rhythmbox-plugin-magnatune (2.96-0ubuntu4.2) ...
Setting up rhythmbox-plugin-zeitgeist (2.96-0ubuntu4.2) ...
Setting up rhythmbox-plugin-cdrecorder (2.96-0ubuntu4.2) ...
Setting up rhythmbox-mozilla (2.96-0ubuntu4.2) ...
Setting up rhythmbox-plugins (2.96-0ubuntu4.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 whoopsie
E: Sub-process /usr/bin/dpkg returned an error code (1)
danny@Ubuntu-Danny:~$ 
```

and for jockey-common I got this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
jockey-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up whoopsie (0.1.32) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /nonexistent -g whoopsie -s /bin/false -u 118 whoopsie' returned error code 1. Exiting.
dpkg: error processing whoopsie (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 whoopsie
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I then checked the additional drivers and it said that the wireless card was on.  But still no wi-fi.

---

### Post by DRS5193 on 2012-09-23
Scratch that!  Restarted computer and we're now all systems go!  Thank you all so, so much!

:guitar:

---

### Post by Bucky Ball on 2012-09-24
Fantastic news and no probs. It is persistent? Wireless still up after restart? Then all good; enjoy the OS and the learning curve. ;)

I suggest:

```
sudo apt-get update
sudo apt-get upgrade
```

That will not upgrade the OS but all packages with an available upgrades. If there are any errors from that perhaps post another thread. Good luck.

Please mark as 'Solved' from 'Thread Tools' to help others.

---

