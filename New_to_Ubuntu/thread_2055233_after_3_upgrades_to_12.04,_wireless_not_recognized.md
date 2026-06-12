---
title: "after 3 upgrades to 12.04, wireless not recognized"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by jarymo on 2012-09-08
so, I was using whatever came before Natty the other day, wireless working fine, so I decided to upgrade.  After 3 upgrades, I'm now at 12.04, but wireless doesn't work, in fact, it's not even recognized.  I have Broadcom 4322AG on hp Pavillion laptop.  Don't recall having this problem with the version before natty.

I have searched for hours and find nothing that helps solve my problem, so I'm posting a new thread.

any ideas??

---

### Post by uRock on 2012-09-08
Did you upgrade or clean install? Can you enter the following into a terminal the paste the output here?```
lspci
```

---

### Post by cortman on 2012-09-08
Try running

```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by anewguy on 2012-09-09
If possible, temporarily hard-wire connect your PC to your router.  Then go to Additional Drivers.  It will run for a while.  Hopefully it will show a driver that needs to be activated - if so - activate it and then reboot.

---

### Post by jarymo on 2012-09-09
> **anewguy said:**
> If possible, temporarily hard-wire connect your PC to your router.  Then go to Additional Drivers.  It will run for a while.  Hopefully it will show a driver that needs to be activated - if so - activate it and then reboot.

Drivers were not installed, so I tried to install.  Here is /var/log/jockey.log

```
2012-09-08 23:02:21,348 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7215d0c>
2012-09-08 23:02:26,265 DEBUG: reading modalias file /lib/modules/3.2.0-30-generic-pae/modules.alias
2012-09-08 23:02:26,402 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-09-08 23:02:26,411 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-09-08 23:02:26,480 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-09-08 23:02:26,577 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-09-08 23:02:26,583 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-09-08 23:02:26,583 DEBUG: fglrx.available: falling back to default
2012-09-08 23:02:26,875 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-09-08 23:02:26,880 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-09-08 23:02:26,886 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-09-08 23:02:26,887 DEBUG: fglrx.available: falling back to default
2012-09-08 23:02:26,937 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-09-08 23:02:26,937 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-09-08 23:02:26,960 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-09-08 23:02:26,960 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-09-08 23:02:26,998 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-09-08 23:02:26,999 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-09-08 23:02:27,005 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-09-08 23:02:27,006 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-09-08 23:02:27,006 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-09-08 23:02:27,006 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-09-08 23:02:27,077 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-09-08 23:02:27,077 DEBUG: Firmware for DVB cards not available
2012-09-08 23:02:27,078 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-09-08 23:02:27,084 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-09-08 23:02:27,109 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-09-08 23:02:27,109 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-09-08 23:02:27,109 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py

2012-09-08 23:02:27,109 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2012-09-08 23:02:27,116 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2012-09-08 23:02:27,117 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2012-09-08 23:02:27,117 DEBUG: cdv.available: falling back to default
2012-09-08 23:02:27,162 DEBUG: Intel Cedarview graphics driver availability undetermined, adding to pool
2012-09-08 23:02:27,162 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-09-08 23:02:27,170 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-09-08 23:02:27,177 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-09-08 23:02:27,218 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-09-08 23:02:27,218 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-09-08 23:02:27,243 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-09-08 23:02:27,249 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-09-08 23:02:27,251 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-09-08 23:02:27,251 DEBUG: NVIDIA accelerated graphics driver not available
2012-09-08 23:02:27,256 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-09-08 23:02:27,262 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-09-08 23:02:27,263 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-09-08 23:02:27,263 DEBUG: NVIDIA accelerated graphics driver not available
2012-09-08 23:02:27,268 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-09-08 23:02:27,274 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-09-08 23:02:27,276 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-09-08 23:02:27,276 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-09-08 23:02:27,281 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-09-08 23:02:27,287 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-09-08 23:02:27,288 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-09-08 23:02:27,288 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
 
2012-09-08 23:02:27,972 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7215d0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-09-08 23:02:27,972 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7215d0c> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2012-09-08 23:02:27,976 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7215d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-09-08 23:02:27,976 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7215d0c> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2012-09-08 23:02:27,986 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-09-08 23:02:27,986 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-09-08 23:02:27,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7215d0c> about HardwareID('modalias', 'platform:hp-wmi')
2012-09-08 23:02:27,987 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7215d0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-09-08 23:02:27,987 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7215d0c> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2012-09-08 23:02:27,990 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2012-09-08 23:02:27,991 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2012-09-08 23:02:27,991 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7215d0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-09-08 23:02:27,991 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7215d0c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2012-09-08 23:02:28,005 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-09-08 23:02:28,005 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-09-08 23:02:28,005 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7215d0c> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2012-09-08 23:02:28,005 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7215d0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-09-08 23:02:28,005 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7215d0c> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2012-09-08 23:02:28,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7215d0c> about HardwareID('modalias', 'acpi:PNP0B00:')
```

*****************
Decided to tackle the 'could not find module fglrx_updates' and have been googling for an hour, cannot find out what I need to do.

appreciate the help!

---

### Post by jarymo on 2012-09-09
uRock, I think this is answered in the subject line, LOL

results of lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

---

### Post by jarymo on 2012-09-09
thanks, cortman, newest version is already installed.

---

### Post by jarymo on 2012-09-09
omg, I fixed it!  Found another post on the wireless forum and all I had to do was **reinstall** bcmwl-kernel-source.

I'm now a happy camper!  :):)

Thanks to you who tried to help me!!


sudo apt-get install --reinstall bcmwl-kernel-source

Seems strange that when I installed it a while ago, it said newest driver already installed, but when I REinstalled, it fixed the problem???

---

### Post by jarymo on 2012-09-09
Guess I spoke too soon.  I am connected with 5 bars, but cannot access any webpage.

What now?:confused:

---

### Post by jarymo on 2012-09-09
Problem finally solved, hope this will help someone else!

Checked the MTU in my Linksys router config and it was set at 1492.

Back to ubuntu, it was set at 1500.

sudo ifconfig eth0 mtu 1492   (to change MTU in ifconfig)

$ ifconfig | grep MTU   (to verify changes were made)
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1

in addition, changed MTU setting in Network Manager from [automatic] to 1492.

viola, it's fixed.

---

### Post by cortman on 2012-09-09
> **jarymo said:**
> Problem finally solved, hope this will help someone else!

Checked the MTU in my Linksys router config and it was set at 1492.

Back to ubuntu, it was set at 1500.

sudo ifconfig eth0 mtu 1492   (to change MTU in ifconfig)

$ ifconfig | grep MTU   (to verify changes were made)
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1

in addition, changed MTU setting in Network Manager from [automatic] to 1492.

viola, it's fixed.

Thanks for sharing your solution!

Good work! :)

---

