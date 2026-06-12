---
title: "Trouble trying to install Google Earth"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by Ymurti on 2012-08-22
Please help me! I downloaded the google earth from its homepage and when trying to install I get this error:


yajnamurti@yajnamurti-laptop:~$ sudo apt-get install lsb-core
[sudo] password for yajnamurti: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lsb-core is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lsb-base

E: Package 'lsb-core' has no installation candidate

---

### Post by Zvezdica27 on 2012-08-22
in ubuntu (version?) it is often most recommended to use software center. Find GE there and install it trough it, because it will solve all issues. I believe the .deb on Google web site and the package trough Software center are not the same, but cannot really tell.

I had the same issues on 11.04, but after purging the system and reisntalling trough SC (and using Goggle DNS), it now works flawless.

Hope it helps.

btw: same goes for Thunderbird, if you download tarballs it won't completely integrate. Trough SC, it does. Don't know why (even if you run all the scripts for integration)

zz

---

### Post by Ymurti on 2012-08-22
> **Zvezdica27 said:**
> in ubuntu (version?) it is often most recommended to use software center. Find GE there and install it trough it, because it will solve all issues. I believe the .deb on Google web site and the package trough Software center are not the same, but cannot really tell.

I had the same issues on 11.04, but after purging the system and reisntalling trough SC (and using Goggle DNS), it now works flawless.

Hope it helps.
zz

Zz thank for your help. My Ubuntu version is 12.04
When I try using the Software Center I get this:


[ATTACH]223045[/ATTACH]

---

### Post by Ymurti on 2012-08-23
So I managed to install lsb-core from this site:  [http://packages.ubuntu.com/precise/i386/lsb-core/download](http://packages.ubuntu.com/precise/i386/lsb-core/download)

And after that I was able to install Google Earth through Software Center. 

But when I tried to open Google earth it did not open and I got this crash message:

Major Version 6
Minor Version 2
Build Number 0002
Build Date Apr 14 2012
Build Time 01:09:37
OS Type 3
OS Major Version 3
OS Minor Version 2
OS Build Version 0
OS Patch Version 0
Crash Signal 11
Crash Time 1345694049
Up Time 4.45656

Stacktrace from glibc:
./libgoogleearth_free.so(+0xc645b)[0x1d645b]
./libgoogleearth_free.so(+0xc66a3)[0x1d66a3]
[0x2b1400]

Please help!

---

### Post by alphacrucis2 on 2012-08-23
Now that you have lsb-core installed. Just download and install the latest version of google-earth from google. I recall the fonts look a bit weird but you can fix that by installing msttcorefonts.

---

### Post by Ymurti on 2012-08-23
> **alphacrucis2 said:**
> Now that you have lsb-core installed. Just download and install the latest version of google-earth from google. I recall the fonts look a bit weird but you can fix that by installing msttcorefonts.

Dear Alpha, I have installed Google earth but when I try to launch it through the terminal I got this:


yajnamurti@yajnamurti-laptop:~$ google-earth
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/yajnamurti/.googleearth/crashlogs/crashlog-5035ed5f.txt

Please include this file if you submit a bug report to Google.
yajnamurti@yajnamurti-laptop:~$

---

### Post by alphacrucis2 on 2012-08-23
Maybe something to do with your graphics driver OpenGL support

[http://productforums.google.com/forum/#!category-topic/earth/linux/io2PeV9hirI](http://productforums.google.com/forum/#!category-topic/earth/linux/io2PeV9hirI)

What graphics card/driver are you using.

GE 6.2.2.6613 works fine here with 12.04 and nvidia proprietary driver

---

### Post by Ymurti on 2012-08-23
> **alphacrucis2 said:**
> Maybe something to do with your graphics driver OpenGL support

[http://productforums.google.com/forum/#!category-topic/earth/linux/io2PeV9hirI](http://productforums.google.com/forum/#!category-topic/earth/linux/io2PeV9hirI)

What graphics card/driver are you using.

How can I find out???

---

### Post by Hadaka on 2012-08-23
Hi, to display graphics card

```
lspci | grep -i vga
#or
lspci | grep -i graphics 
```

---

### Post by Ymurti on 2012-08-23
> **Hadaka said:**
> Hi, to display graphics card

```
lspci | grep -i vga
#or
lspci | grep -i graphics 
```

yajnamurti@yajnamurti-laptop:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series]
yajnamurti@yajnamurti-laptop:~$ lspci | grep -i graphics
yajnamurti@yajnamurti-laptop:~$

---

### Post by Hadaka on 2012-08-23
hi, try this...it will give you more info on your card, including the driver.

```
 lspci -v | grep -iA12 vga[CODE]
``` [/CODE]

---

### Post by alphacrucis2 on 2012-08-24
> **Ymurti said:**
> yajnamurti@yajnamurti-laptop:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series]
yajnamurti@yajnamurti-laptop:~$ lspci | grep -i graphics
yajnamurti@yajnamurti-laptop:~$

Did you try installing the proprietary AMD driver? If not, click the icon on the far right end of the indicator bar. Click System Settings, then in the hardware section, click "Additional drivers"

---

### Post by Ymurti on 2012-08-24
> **alphacrucis2 said:**
> Did you try installing the proprietary AMD driver? If not, click the icon on the far right end of the indicator bar. Click System Settings, then in the hardware section, click "Additional drivers"

Dear Alpha, I tried to install the proprietary AMD driver but I got this message:

[ATTACH]223108[/ATTACH]


And here it is the jockey.log:
```

2012-08-24 11:50:04,784 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c>
2012-08-24 11:50:06,774 DEBUG: reading modalias file /lib/modules/3.2.0-29-generic/modules.alias
2012-08-24 11:50:06,901 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-08-24 11:50:06,915 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-08-24 11:50:06,996 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-08-24 11:50:07,093 DEBUG: Could not instantiate Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 215, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package linux-firmware-nonfree does not exist
2012-08-24 11:50:07,109 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-08-24 11:50:07,117 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-08-24 11:50:07,139 DEBUG: Could not instantiate Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 215, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package bcmwl-kernel-source does not exist
2012-08-24 11:50:07,139 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-08-24 11:50:07,146 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-08-24 11:50:07,146 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-08-24 11:50:07,171 DEBUG: VMWare Client Tools not available
2012-08-24 11:50:07,172 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-08-24 11:50:07,242 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-08-24 11:50:07,269 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-08-24 11:50:07,269 DEBUG: fglrx.available: falling back to default
2012-08-24 11:50:07,389 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) not available
2012-08-24 11:50:07,394 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-08-24 11:50:07,401 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-08-24 11:50:07,402 DEBUG: fglrx.available: falling back to default
2012-08-24 11:50:07,452 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-08-24 11:50:07,452 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-08-24 11:50:07,481 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-08-24 11:50:07,488 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-08-24 11:50:07,537 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-08-24 11:50:07,538 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2012-08-24 11:50:07,545 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2012-08-24 11:50:07,547 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2012-08-24 11:50:07,547 DEBUG: cdv.available: falling back to default
2012-08-24 11:50:07,596 DEBUG: Intel Cedarview graphics driver not available
2012-08-24 11:50:07,596 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-08-24 11:50:07,606 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-08-24 11:50:07,607 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-08-24 11:50:07,607 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-08-24 11:50:07,607 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-08-24 11:50:07,636 DEBUG: Could not instantiate Handler subclass __builtin__.SlModem from name SlModem
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 215, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package sl-modem-daemon does not exist
2012-08-24 11:50:07,637 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-08-24 11:50:07,659 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-08-24 11:50:07,664 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-08-24 11:50:07,681 DEBUG: nvidia.available: falling back to default
2012-08-24 11:50:07,713 DEBUG: NVIDIA accelerated graphics driver not available
2012-08-24 11:50:07,717 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-08-24 11:50:07,726 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-08-24 11:50:07,728 DEBUG: nvidia.available: falling back to default
2012-08-24 11:50:07,776 DEBUG: NVIDIA accelerated graphics driver not available
2012-08-24 11:50:07,780 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-08-24 11:50:07,786 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-08-24 11:50:07,788 DEBUG: nvidia.available: falling back to default
2012-08-24 11:50:07,833 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-08-24 11:50:07,841 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-08-24 11:50:07,847 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-08-24 11:50:07,849 DEBUG: nvidia.available: falling back to default
2012-08-24 11:50:07,894 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-08-24 11:50:07,902 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-08-24 11:50:07,911 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-08-24 11:50:07,911 DEBUG: nvidia.available: falling back to default
2012-08-24 11:50:07,955 DEBUG: NVIDIA accelerated graphics driver not available
2012-08-24 11:50:07,961 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-08-24 11:50:07,971 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-08-24 11:50:07,973 DEBUG: nvidia.available: falling back to default
2012-08-24 11:50:08,018 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-08-24 11:50:08,018 DEBUG: all custom handlers loaded
2012-08-24 11:50:08,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00001002d0000AA68sv0000104Dsd00009071bc04sc03i00')
2012-08-24 11:50:08,311 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-08-24 11:50:08,450 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,450 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-08-24 11:50:08,454 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-24 11:50:08,454 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,454 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00008086d00002D10sv0000104Dsd00009071bc06sc00i00')
2012-08-24 11:50:08,719 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00008086d00002C62sv0000104Dsd00009071bc06sc00i00')
2012-08-24 11:50:08,723 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-08-24 11:50:08,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-08-24 11:50:08,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00008086d00003B64sv0000104Dsd00009071bc07sc80i00')
2012-08-24 11:50:08,726 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-08-24 11:50:08,727 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,727 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-08-24 11:50:08,727 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-24 11:50:08,727 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,727 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-24 11:50:08,727 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,727 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'platform:regulatory')
2012-08-24 11:50:08,728 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-08-24 11:50:08,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00008086d00002D11sv0000104Dsd00009071bc06sc00i00')
2012-08-24 11:50:08,743 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,2,k112,r8,amlsfw')
2012-08-24 11:50:08,743 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-24 11:50:08,743 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,743 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-24 11:50:08,743 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,744 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-08-24 11:50:08,744 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00008086d00002D12sv0000104Dsd00009071bc06sc00i00')
2012-08-24 11:50:08,746 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'platform:eisa')
2012-08-24 11:50:08,747 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00008086d00003B34sv0000104Dsd00009071bc0Csc03i20')
2012-08-24 11:50:08,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'platform:sony-laptop')
2012-08-24 11:50:08,751 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00008086d00002D01sv0000104Dsd00009071bc06sc00i00')
2012-08-24 11:50:08,755 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00008086d00000044sv0000104Dsd00009071bc06sc00i00')
2012-08-24 11:50:08,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'usb:v1BCFp0005d0013dc00dsc00dp00ic03isc01ip02')
2012-08-24 11:50:08,758 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-08-24 11:50:08,758 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,758 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2012-08-24 11:50:08,758 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-08-24 11:50:08,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-08-24 11:50:08,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00001002d000068E0sv0000104Dsd00009071bc03sc00i00')
2012-08-24 11:50:08,763 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-08-24 11:50:08,897 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-08-24 11:50:08,897 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-08-24 11:50:08,763 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-08-24 11:50:08,902 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-08-24 11:50:08,906 DEBUG: fglrx.available: falling back to default
2012-08-24 11:50:08,939 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-08-24 11:50:08,939 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-08-24 11:50:08,919 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-08-24 11:50:08,940 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-08-24 11:50:08,940 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,940 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'acpi:INT0800:')
2012-08-24 11:50:08,940 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00008086d00003B56sv0000104Dsd00009071bc04sc03i00')
2012-08-24 11:50:08,949 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-08-24 11:50:08,949 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,949 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-08-24 11:50:08,950 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-08-24 11:50:08,950 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'usb:v0A81p0101d0110dc00dsc00dp00ic03isc01ip01')
2012-08-24 11:50:08,950 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-08-24 11:50:08,951 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,951 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2012-08-24 11:50:08,951 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,951 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00001180d0000E822sv0000104Dsd00009071bc08sc05i00')
2012-08-24 11:50:08,960 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-08-24 11:50:08,960 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,960 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2012-08-24 11:50:08,960 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,961 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'input:b0003v0A81p0101e0110-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,AD,D1,D9,ram4,lsfw')
2012-08-24 11:50:08,961 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-24 11:50:08,961 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,961 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-24 11:50:08,962 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00008086d00003B30sv0000104Dsd00009071bc0Csc05i00')
2012-08-24 11:50:08,967 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-08-24 11:50:08,967 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,4,k71,72,73,8A,94,95,9E,A1,B7,B8,B9,CA,CB,CD,D4,E0,E1,E2,E3,ED,EE,121,168,174,1A2,1A3,1D0,1D1,1D2,1D3,1D9,1DA,1DC,1E0,1E1,1E2,1E3,1E4,ram4,lsfw')
2012-08-24 11:50:08,968 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-24 11:50:08,968 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,968 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-24 11:50:08,968 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-08-24 11:50:08,968 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-24 11:50:08,968 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'usb:v05E3p0608d7764dc09dsc00dp01ic09isc00ip00')
2012-08-24 11:50:08,970 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'input:b0003v0A81p0101e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2012-08-24 11:50:08,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-24 11:50:08,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-24 11:50:08,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-08-24 11:50:08,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-24 11:50:08,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,971 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-24 11:50:08,971 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,971 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000105Bsd0000E017bc02sc80i00')
2012-08-24 11:50:08,980 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2012-08-24 11:50:08,980 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrR1100Y8:bd08/17/2010:svnSonyCorporation:pnVPCEB34EN:pvrC606JGKX:rvnSonyCorporation:rnVAIO:rvrN/A:cvnSonyCorporation:ct10:cvrN/A:')
2012-08-24 11:50:08,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-08-24 11:50:08,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-08-24 11:50:08,994 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-24 11:50:08,994 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,995 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-24 11:50:08,995 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:08,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00')
2012-08-24 11:50:08,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'usb:v0C45p6464d0102dcEFdsc02dp01ic0Eisc01ip00')
2012-08-24 11:50:09,022 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-08-24 11:50:09,022 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,022 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'acpi:SNY5001:')
2012-08-24 11:50:09,022 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-08-24 11:50:09,022 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-24 11:50:09,022 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,022 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'acpi:SNYALP0012:PNP0F13:')
2012-08-24 11:50:09,022 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00008086d00003B29sv0000104Dsd00009071bc01sc06i01')
2012-08-24 11:50:09,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'usb:v0A81p0101d0110dc00dsc00dp00ic03isc00ip00')
2012-08-24 11:50:09,025 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2012-08-24 11:50:09,026 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00008086d00003B3Csv0000104Dsd00009071bc0Csc03i20')
2012-08-24 11:50:09,030 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00008086d00003B09sv0000104Dsd00009071bc06sc01i00')
2012-08-24 11:50:09,034 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-08-24 11:50:09,034 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,035 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00001180d0000E230sv0000104Dsd00009071bc08sc80i00')
2012-08-24 11:50:09,035 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'platform:pcspkr')
2012-08-24 11:50:09,035 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-08-24 11:50:09,035 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,035 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-08-24 11:50:09,036 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,036 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-08-24 11:50:09,036 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-24 11:50:09,036 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,036 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-24 11:50:09,036 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,036 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-08-24 11:50:09,036 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'usb:v0C45p6464d0102dcEFdsc02dp01ic0Eisc02ip00')
2012-08-24 11:50:09,037 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v000011ABd00004381sv0000104Dsd00009071bc02sc00i00')
2012-08-24 11:50:09,056 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sky2'}
2012-08-24 11:50:09,057 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-08-24 11:50:09,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00008086d00002D13sv0000104Dsd00009071bc06sc00i00')
2012-08-24 11:50:09,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'input:b0003v1BCFp0005e0110-e0,1,2,4,k110,111,112,113,114,r0,1,6,8,am4,lsfw')
2012-08-24 11:50:09,060 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-24 11:50:09,060 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,060 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-24 11:50:09,060 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-08-24 11:50:09,068 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-08-24 11:50:09,068 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,068 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-08-24 11:50:09,068 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,068 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-08-24 11:50:09,069 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-24 11:50:09,069 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'pci:v00008086d00002448sv0000104Dsd00009071bc06sc04i01')
2012-08-24 11:50:09,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'input:b0011v0002p0008e7326-e0,1,3,k110,111,112,145,14A,ra0,1,18,mlsfw')
2012-08-24 11:50:09,072 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-24 11:50:09,072 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,072 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-08-24 11:50:09,072 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,072 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-08-24 11:50:09,072 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,072 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-24 11:50:09,072 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,072 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'input:b0003v0C45p6464e0102-e0,1,kD4,ramlsfw')
2012-08-24 11:50:09,072 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-08-24 11:50:09,073 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,073 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-08-24 11:50:09,073 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-08-24 11:50:09,073 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb7660d0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-08-24 11:50:09,073 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00001002d0000AA68sv0000104Dsd00009071bc04sc03i00')
2012-08-24 11:50:09,073 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-08-24 11:50:09,073 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00008086d00002D10sv0000104Dsd00009071bc06sc00i00')
2012-08-24 11:50:09,073 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00008086d00002C62sv0000104Dsd00009071bc06sc00i00')
2012-08-24 11:50:09,073 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-08-24 11:50:09,073 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-08-24 11:50:09,073 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00008086d00003B64sv0000104Dsd00009071bc07sc80i00')
2012-08-24 11:50:09,073 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-08-24 11:50:09,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'platform:regulatory')
2012-08-24 11:50:09,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-08-24 11:50:09,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00008086d00002D11sv0000104Dsd00009071bc06sc00i00')
2012-08-24 11:50:09,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,2,k112,r8,amlsfw')
2012-08-24 11:50:09,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-08-24 11:50:09,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00008086d00002D12sv0000104Dsd00009071bc06sc00i00')
2012-08-24 11:50:09,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'platform:eisa')
2012-08-24 11:50:09,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00008086d00003B34sv0000104Dsd00009071bc0Csc03i20')
2012-08-24 11:50:09,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'platform:sony-laptop')
2012-08-24 11:50:09,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00008086d00002D01sv0000104Dsd00009071bc06sc00i00')
2012-08-24 11:50:09,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00008086d00000044sv0000104Dsd00009071bc06sc00i00')
2012-08-24 11:50:09,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'usb:v1BCFp0005d0013dc00dsc00dp00ic03isc01ip02')
2012-08-24 11:50:09,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-08-24 11:50:09,074 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-08-24 11:50:09,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00001002d000068E0sv0000104Dsd00009071bc03sc00i00')
2012-08-24 11:50:09,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'acpi:INT0800:')
2012-08-24 11:50:09,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00008086d00003B56sv0000104Dsd00009071bc04sc03i00')
2012-08-24 11:50:09,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-08-24 11:50:09,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-08-24 11:50:09,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'usb:v0A81p0101d0110dc00dsc00dp00ic03isc01ip01')
2012-08-24 11:50:09,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00001180d0000E822sv0000104Dsd00009071bc08sc05i00')
2012-08-24 11:50:09,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'input:b0003v0A81p0101e0110-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,9B,9C,9E,9F,A3,A4,A5,A6,AB,AC,AD,D1,D9,ram4,lsfw')
2012-08-24 11:50:09,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00008086d00003B30sv0000104Dsd00009071bc0Csc05i00')
2012-08-24 11:50:09,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'input:b0010v104Dp0000e0000-e0,1,4,k71,72,73,8A,94,95,9E,A1,B7,B8,B9,CA,CB,CD,D4,E0,E1,E2,E3,ED,EE,121,168,174,1A2,1A3,1D0,1D1,1D2,1D3,1D9,1DA,1DC,1E0,1E1,1E2,1E3,1E4,ram4,lsfw')
2012-08-24 11:50:09,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-08-24 11:50:09,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'usb:v05E3p0608d7764dc09dsc00dp01ic09isc00ip00')
2012-08-24 11:50:09,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'input:b0003v0A81p0101e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2012-08-24 11:50:09,075 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-08-24 11:50:09,076 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv0000105Bsd0000E017bc02sc80i00')
2012-08-24 11:50:09,076 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrR1100Y8:bd08/17/2010:svnSonyCorporation:pnVPCEB34EN:pvrC606JGKX:rvnSonyCorporation:rnVAIO:rvrN/A:cvnSonyCorporation:ct10:cvrN/A:')
2012-08-24 11:50:09,076 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-08-24 11:50:09,076 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-08-24 11:50:09,076 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00')
2012-08-24 11:50:09,076 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'usb:v0C45p6464d0102dcEFdsc02dp01ic0Eisc01ip00')
2012-08-24 11:50:09,076 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'acpi:SNY5001:')
2012-08-24 11:50:09,076 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-08-24 11:50:09,076 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'acpi:SNYALP0012:PNP0F13:')
2012-08-24 11:50:09,076 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00008086d00003B29sv0000104Dsd00009071bc01sc06i01')
2012-08-24 11:50:09,076 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'usb:v0A81p0101d0110dc00dsc00dp00ic03isc00ip00')
2012-08-24 11:50:09,076 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00008086d00003B3Csv0000104Dsd00009071bc0Csc03i20')
2012-08-24 11:50:09,076 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00008086d00003B09sv0000104Dsd00009071bc06sc01i00')
2012-08-24 11:50:09,077 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00001180d0000E230sv0000104Dsd00009071bc08sc80i00')
2012-08-24 11:50:09,077 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'platform:pcspkr')
2012-08-24 11:50:09,077 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-08-24 11:50:09,077 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-08-24 11:50:09,077 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'usb:v0C45p6464d0102dcEFdsc02dp01ic0Eisc02ip00')
2012-08-24 11:50:09,077 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v000011ABd00004381sv0000104Dsd00009071bc02sc00i00')
2012-08-24 11:50:09,077 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-08-24 11:50:09,077 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00008086d00002D13sv0000104Dsd00009071bc06sc00i00')
2012-08-24 11:50:09,077 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'input:b0003v1BCFp0005e0110-e0,1,2,4,k110,111,112,113,114,r0,1,6,8,am4,lsfw')
2012-08-24 11:50:09,077 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-08-24 11:50:09,077 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-08-24 11:50:09,077 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'pci:v00008086d00002448sv0000104Dsd00009071bc06sc04i01')
2012-08-24 11:50:09,077 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'input:b0011v0002p0008e7326-e0,1,3,k110,111,112,145,14A,ra0,1,18,mlsfw')
2012-08-24 11:50:09,077 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'input:b0003v0C45p6464e0102-e0,1,kD4,ramlsfw')
2012-08-24 11:50:09,078 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb745984c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-08-24 11:50:09,155 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-08-24 11:50:09,155 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-08-24 11:50:09,231 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-08-24 11:50:09,232 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-08-24 11:50:09,286 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-08-24 11:50:09,286 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-08-24 11:50:33,658 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-08-24 11:50:33,659 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-08-24 11:50:39,960 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-08-24 11:50:39,961 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2012-08-24 11:50:39,961 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2012-08-24 11:51:35,608 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-08-24 11:51:35,608 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-08-24 11:51:35,623 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-08-24 11:51:35,624 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
```

---

### Post by Ymurti on 2012-08-24
> **Hadaka said:**
> hi, try this...it will give you more info on your card, including the driver.

```
 lspci -v | grep -iA12 vga[CODE]
``` [/CODE]

```
yajnamurti@yajnamurti-laptop:~$  lspci -v | grep -iA12 vga
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series] (prog-if 00 [VGA controller])
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0020000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at d000 [size=256]
	Expansion ROM at f0000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeon

01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series]
	Subsystem: Sony Corporation Device 9071
	Flags: bus master, fast devsel, latency 0, IRQ 45
yajnamurti@yajnamurti-laptop:~$ 

```

---

### Post by alphacrucis2 on 2012-08-24
You could try installing the fglrx driver manually. Seems that someone else had a similar problem.

See this thread:

[http://ubuntuforums.org/showthread.php?t=2026897](http://ubuntuforums.org/showthread.php?t=2026897)


Also:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

start at the section titled :

Manually installing Catalyst 12.6

Note that the name of the driver installer you obtain from AMD will be named slightly differently to what is mentioned in the howto as it will now be a later version. They release a new Catalyst fglrx driver every month.

---

### Post by Ymurti on 2012-08-24
> **alphacrucis2 said:**
> You could try installing the fglrx driver manually. Seems that someone else had a similar problem.

See this thread:

[http://ubuntuforums.org/showthread.php?t=2026897](http://ubuntuforums.org/showthread.php?t=2026897)


Also:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

start at the section titled :

Manually installing Catalyst 12.6

Note that the name of the driver installer you obtain from AMD will be named slightly differently to what is mentioned in the howto as it will now be a later version. They release a new Catalyst fglrx driver every month.

Dear Alpha, and everybody that has answered my thread. Thank you a lot for your help. Now Google earth is working!!!  :D

---

### Post by aquariusmediaaamar on 2012-08-24
Hi,
What are the benefits of Google Earth. Is it a product of Google.

---

### Post by Ymurti on 2012-08-24
> **aquariusmediaaamar said:**
> Hi,
What are the benefits of Google Earth. Is it a product of Google.

Dear Aquarius, It is a product of Google. Google earth is a very fancy map of the world. You can learn more about it going to their site. [www.google.com](www.google.com)  then type:  Google earth.

):P

---

