---
title: "broadcom STA driver ubuntu on dell inspiron 1545"
date: 2013-08-11
forum: New to Ubuntu
---

### Post by ryan9 on 2013-08-11
the other day i dual boot installed ubuntu alongside my windows 7, i connected the laptop via ethernet cable to my router to download the additional broadcom STA driver but it just said it couldnt install it, the log is below, any help would be appreciated thanks 



```
2013-08-11 13:37:25,617 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758>
2013-08-11 13:37:28,234 DEBUG: reading modalias file /lib/modules/3.5.0-23-generic/modules.alias
2013-08-11 13:37:28,418 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-08-11 13:37:28,418 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-08-11 13:37:28,469 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-08-11 13:37:28,480 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96


2013-08-11 13:37:28,485 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-08-11 13:37:28,486 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-08-11 13:37:28,486 DEBUG: NVIDIA accelerated graphics driver not available
2013-08-11 13:37:28,490 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current


2013-08-11 13:37:28,496 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-08-11 13:37:28,497 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-08-11 13:37:28,497 DEBUG: NVIDIA accelerated graphics driver not available
2013-08-11 13:37:28,502 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates


2013-08-11 13:37:28,509 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-08-11 13:37:28,510 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-08-11 13:37:28,510 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-08-11 13:37:28,516 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates


2013-08-11 13:37:28,523 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-08-11 13:37:28,525 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-08-11 13:37:28,525 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-08-11 13:37:28,531 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates


2013-08-11 13:37:28,539 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-08-11 13:37:28,540 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-08-11 13:37:28,540 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-08-11 13:37:28,546 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173


2013-08-11 13:37:28,554 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-08-11 13:37:28,555 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-08-11 13:37:28,555 DEBUG: NVIDIA accelerated graphics driver not available
2013-08-11 13:37:28,561 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310


2013-08-11 13:37:28,588 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package nvidia-experimental-310 does not exist
2013-08-11 13:37:28,609 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304


2013-08-11 13:37:28,630 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package nvidia-experimental-304 does not exist
2013-08-11 13:37:28,631 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-08-11 13:37:28,639 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci


2013-08-11 13:37:28,640 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-08-11 13:37:28,640 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-08-11 13:37:28,640 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-08-11 13:37:28,651 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates


2013-08-11 13:37:28,658 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-08-11 13:37:28,659 DEBUG: fglrx.available: falling back to default
2013-08-11 13:37:28,908 DEBUG: XorgDriverHandler(fglrx_updates, fglrx-updates, None): Disabling as package is not compatible with Q-LTS X.org
2013-08-11 13:37:28,908 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) not available
2013-08-11 13:37:28,912 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9


2013-08-11 13:37:28,934 DEBUG: Could not instantiate Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package fglrx-experimental-9 does not exist
2013-08-11 13:37:28,939 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx


2013-08-11 13:37:28,944 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-08-11 13:37:28,945 DEBUG: fglrx.available: falling back to default
2013-08-11 13:37:29,080 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-08-11 13:37:29,080 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-08-11 13:37:29,081 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-08-11 13:37:29,085 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet


2013-08-11 13:37:29,086 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-08-11 13:37:29,099 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-08-11 13:37:29,100 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-08-11 13:37:29,105 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx


2013-08-11 13:37:29,105 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-08-11 13:37:29,105 DEBUG: cdv.available: falling back to default
2013-08-11 13:37:29,246 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-08-11 13:37:29,247 DEBUG: Intel Cedarview graphics driver not available
2013-08-11 13:37:29,247 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-08-11 13:37:29,254 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr


2013-08-11 13:37:29,259 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-08-11 13:37:29,392 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-08-11 13:37:29,392 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-08-11 13:37:29,392 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-08-11 13:37:29,398 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2013-08-11 13:37:29,411 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-08-11 13:37:29,412 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-08-11 13:37:29,412 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-08-11 13:37:29,532 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-08-11 13:37:29,533 DEBUG: Firmware for DVB cards not available
2013-08-11 13:37:29,533 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-08-11 13:37:29,557 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-08-11 13:37:29,571 DEBUG: Software modem not available
2013-08-11 13:37:29,572 DEBUG: all custom handlers loaded
2013-08-11 13:37:29,572 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2013-08-11 13:37:29,875 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k71,72,73,94,CA,E0,E1,E3,EC,F0,ram4,lsfw')
2013-08-11 13:37:29,880 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:37:30,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:37:30,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,213 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-08-11 13:37:30,214 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:37:30,214 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,214 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:37:30,214 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,214 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-08-11 13:37:30,214 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:37:30,218 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2013-08-11 13:37:30,221 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-08-11 13:37:30,221 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,221 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-08-11 13:37:30,222 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'platform:dell-laptop')
2013-08-11 13:37:30,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2013-08-11 13:37:30,251 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-08-11 13:37:30,251 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-08-11 13:37:30,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-08-11 13:37:30,251 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:37:30,251 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,252 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'usb:v7392p7811d0200dc00dsc00dp00icFFiscFFipFF')
2013-08-11 13:37:30,256 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rtl8192cu'}
2013-08-11 13:37:30,257 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rtl8192cu', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,257 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-08-11 13:37:30,257 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2013-08-11 13:37:30,257 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-08-11 13:37:30,257 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'platform:dcdbas')
2013-08-11 13:37:30,258 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-08-11 13:37:30,258 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:37:30,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,258 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:37:30,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,258 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'platform:gpio_ich')
2013-08-11 13:37:30,259 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich'}
2013-08-11 13:37:30,259 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2013-08-11 13:37:30,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:37:30,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'usb:v05CAp180Ad8730dcEFdsc02dp01ic0Eisc02ip00')
2013-08-11 13:37:30,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2013-08-11 13:37:30,263 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi'}
2013-08-11 13:37:30,263 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-08-11 13:37:30,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'acpi:PNP0303:')
2013-08-11 13:37:30,264 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2013-08-11 13:37:30,267 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2013-08-11 13:37:30,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:37:30,270 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'acpi:PNP0800:')
2013-08-11 13:37:30,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2013-08-11 13:37:30,274 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-08-11 13:37:30,274 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2013-08-11 13:37:30,274 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-08-11 13:37:30,275 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,275 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-08-11 13:37:30,275 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2013-08-11 13:37:30,290 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ums_realtek'}
2013-08-11 13:37:30,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ums_realtek', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,291 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-08-11 13:37:30,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,291 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:0017:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003D,0068,006B,006C,006D,006F,0070,0072,0074,007C,0080,0082,0083,0084,0087,0088,0089,008D,008E,008F,009A,009B,00C0,00E7')
2013-08-11 13:37:30,296 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-08-11 13:37:30,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,296 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-08-11 13:37:30,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,3,k110,111,112,145,14A,ra0,1,18,mlsfw')
2013-08-11 13:37:30,296 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:37:30,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,297 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-08-11 13:37:30,297 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,297 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-08-11 13:37:30,297 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,297 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:37:30,297 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2013-08-11 13:37:30,297 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:37:30,298 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,298 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:37:30,298 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,298 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-08-11 13:37:30,306 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-08-11 13:37:30,306 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,306 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-08-11 13:37:30,306 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,306 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-08-11 13:37:30,307 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:37:30,307 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-08-11 13:37:30,307 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:37:30,307 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'acpi:PNP0F13:')
2013-08-11 13:37:30,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd000002AAbc06sc04i01')
2013-08-11 13:37:30,311 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'input:b0003v05CAp180Ae8730-e0,1,kD4,ramlsfw')
2013-08-11 13:37:30,311 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:37:30,311 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,311 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:37:30,311 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,311 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'platform:microcode')
2013-08-11 13:37:30,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'acpi:PNP0100:')
2013-08-11 13:37:30,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'platform:regulatory')
2013-08-11 13:37:30,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA14:bd12/07/2009:svnDellInc.:pnInspiron1545:pvr:rvnDellInc.:rn:rvr:cvnDellInc.:ct8:cvr:')
2013-08-11 13:37:30,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-08-11 13:37:30,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2013-08-11 13:37:30,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:37:30,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2013-08-11 13:37:30,333 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-08-11 13:37:30,333 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,333 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-08-11 13:37:30,333 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2013-08-11 13:37:30,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2013-08-11 13:37:30,337 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-08-11 13:37:30,337 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2013-08-11 13:37:30,380 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2013-08-11 13:37:30,380 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:37:30,380 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-08-11 13:37:30,384 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2013-08-11 13:37:30,385 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:37:30,385 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-08-11 13:37:30,385 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2013-08-11 13:37:30,385 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,386 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'b43', 'package': 'firmware-b43-lpphy-installer'}
2013-08-11 13:37:30,386 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b43', 'jockey_handler': 'KernelModuleHandler', 'package': 'firmware-b43-lpphy-installer'}
2013-08-11 13:37:30,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2013-08-11 13:37:30,386 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:37:30,386 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,387 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:37:30,387 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,387 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'acpi:PNP0000:')
2013-08-11 13:37:30,387 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2013-08-11 13:37:30,391 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'platform:coretemp')
2013-08-11 13:37:30,391 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-08-11 13:37:30,391 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-08-11 13:37:30,392 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'usb:v05CAp180Ad8730dcEFdsc02dp01ic0Eisc01ip00')
2013-08-11 13:37:30,392 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-08-11 13:37:30,392 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,393 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'acpi:PNP0200:')
2013-08-11 13:37:30,393 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:37:30,396 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'hid:b0003g0001v0000413Cp00008161')
2013-08-11 13:37:30,443 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic'}
2013-08-11 13:37:30,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2013-08-11 13:37:30,444 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-08-11 13:37:30,444 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,444 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'wmi:77BD0728-2E34-478C-B625-67F02A7E4897')
2013-08-11 13:37:30,444 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'platform:pcspkr')
2013-08-11 13:37:30,444 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-08-11 13:37:30,445 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,445 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-08-11 13:37:30,445 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,445 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2013-08-11 13:37:30,448 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-08-11 13:37:30,449 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,449 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2013-08-11 13:37:30,471 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sky2'}
2013-08-11 13:37:30,471 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2013-08-11 13:37:30,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2013-08-11 13:37:30,475 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-08-11 13:37:30,475 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:37:30,475 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,475 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:37:30,475 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,475 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2013-08-11 13:37:30,475 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-08-11 13:37:30,476 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:37:30,476 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,476 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:37:30,476 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:37:30,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:37:30,479 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-08-11 13:37:30,480 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2cd7758> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2013-08-11 13:37:30,480 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2013-08-11 13:37:30,480 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k71,72,73,94,CA,E0,E1,E3,EC,F0,ram4,lsfw')
2013-08-11 13:37:30,480 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-08-11 13:37:30,480 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-08-11 13:37:30,480 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:37:30,480 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2013-08-11 13:37:30,480 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'platform:dell-laptop')
2013-08-11 13:37:30,481 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2013-08-11 13:37:30,481 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-08-11 13:37:30,481 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-08-11 13:37:30,481 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'usb:v7392p7811d0200dc00dsc00dp00icFFiscFFipFF')
2013-08-11 13:37:30,481 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-08-11 13:37:30,481 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2013-08-11 13:37:30,481 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-08-11 13:37:30,481 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'platform:dcdbas')
2013-08-11 13:37:30,481 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-08-11 13:37:30,481 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'platform:gpio_ich')
2013-08-11 13:37:30,481 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2013-08-11 13:37:30,482 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:37:30,482 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'usb:v05CAp180Ad8730dcEFdsc02dp01ic0Eisc02ip00')
2013-08-11 13:37:30,482 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2013-08-11 13:37:30,482 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-08-11 13:37:30,482 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'acpi:PNP0303:')
2013-08-11 13:37:30,482 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2013-08-11 13:37:30,482 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:37:30,482 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'acpi:PNP0800:')
2013-08-11 13:37:30,482 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2013-08-11 13:37:30,482 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2013-08-11 13:37:30,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2013-08-11 13:37:30,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:0017:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003D,0068,006B,006C,006D,006F,0070,0072,0074,007C,0080,0082,0083,0084,0087,0088,0089,008D,008E,008F,009A,009B,00C0,00E7')
2013-08-11 13:37:30,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,3,k110,111,112,145,14A,ra0,1,18,mlsfw')
2013-08-11 13:37:30,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2013-08-11 13:37:30,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-08-11 13:37:30,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-08-11 13:37:30,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-08-11 13:37:30,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'acpi:PNP0F13:')
2013-08-11 13:37:30,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd000002AAbc06sc04i01')
2013-08-11 13:37:30,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'input:b0003v05CAp180Ae8730-e0,1,kD4,ramlsfw')
2013-08-11 13:37:30,483 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'platform:microcode')
2013-08-11 13:37:30,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'acpi:PNP0100:')
2013-08-11 13:37:30,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'platform:regulatory')
2013-08-11 13:37:30,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA14:bd12/07/2009:svnDellInc.:pnInspiron1545:pvr:rvnDellInc.:rn:rvr:cvnDellInc.:ct8:cvr:')
2013-08-11 13:37:30,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-08-11 13:37:30,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2013-08-11 13:37:30,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:37:30,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2013-08-11 13:37:30,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2013-08-11 13:37:30,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2013-08-11 13:37:30,484 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2013-08-11 13:37:30,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2013-08-11 13:37:30,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'acpi:PNP0000:')
2013-08-11 13:37:30,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2013-08-11 13:37:30,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'platform:coretemp')
2013-08-11 13:37:30,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-08-11 13:37:30,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-08-11 13:37:30,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'usb:v05CAp180Ad8730dcEFdsc02dp01ic0Eisc01ip00')
2013-08-11 13:37:30,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'acpi:PNP0200:')
2013-08-11 13:37:30,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:37:30,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'hid:b0003g0001v0000413Cp00008161')
2013-08-11 13:37:30,485 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2013-08-11 13:37:30,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'wmi:77BD0728-2E34-478C-B625-67F02A7E4897')
2013-08-11 13:37:30,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'platform:pcspkr')
2013-08-11 13:37:30,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2013-08-11 13:37:30,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2013-08-11 13:37:30,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2013-08-11 13:37:30,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2013-08-11 13:37:30,486 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-08-11 13:37:30,487 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2013-08-11 13:37:30,487 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-08-11 13:37:30,487 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:37:30,487 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-08-11 13:37:30,487 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x309b3f8> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2013-08-11 13:37:30,512 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:37:30,682 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:37:30,705 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:38:39,604 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:38:42,145 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2013-08-11 13:38:42,146 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-08-11 13:38:42,355 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:38:43,831 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:38:43,850 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:38:43,874 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:38:44,667 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:38:44,978 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2013-08-11 13:38:44,979 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-08-11 13:38:45,017 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:38:47,186 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:38:47,214 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:38:47,251 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:38:56,298 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:38:56,609 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2013-08-11 13:38:56,610 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-08-11 13:38:56,657 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:38:57,758 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:38:57,776 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:38:57,802 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:39:11,993 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:39:12,303 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2013-08-11 13:39:12,303 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-08-11 13:39:12,354 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:39:13,673 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:39:13,696 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:39:13,720 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:39:15,025 DEBUG: Shutting down
2013-08-11 13:39:19,157 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758>
2013-08-11 13:39:21,919 DEBUG: reading modalias file /lib/modules/3.5.0-23-generic/modules.alias
2013-08-11 13:39:22,027 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-08-11 13:39:22,028 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-08-11 13:39:22,079 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-08-11 13:39:22,089 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96


2013-08-11 13:39:22,097 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-08-11 13:39:22,099 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-08-11 13:39:22,099 DEBUG: NVIDIA accelerated graphics driver not available
2013-08-11 13:39:22,105 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current


2013-08-11 13:39:22,114 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-08-11 13:39:22,116 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-08-11 13:39:22,116 DEBUG: NVIDIA accelerated graphics driver not available
2013-08-11 13:39:22,122 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates


2013-08-11 13:39:22,130 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-08-11 13:39:22,131 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-08-11 13:39:22,131 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-08-11 13:39:22,140 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates


2013-08-11 13:39:22,148 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-08-11 13:39:22,149 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-08-11 13:39:22,149 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-08-11 13:39:22,156 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates


2013-08-11 13:39:22,164 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-08-11 13:39:22,165 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-08-11 13:39:22,165 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-08-11 13:39:22,172 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173


2013-08-11 13:39:22,180 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-08-11 13:39:22,181 DEBUG: Disabling Nvidia driver on intel/hybrid system
2013-08-11 13:39:22,181 DEBUG: NVIDIA accelerated graphics driver not available
2013-08-11 13:39:22,188 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310


2013-08-11 13:39:22,216 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package nvidia-experimental-310 does not exist
2013-08-11 13:39:22,225 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304


2013-08-11 13:39:22,253 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package nvidia-experimental-304 does not exist
2013-08-11 13:39:22,254 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-08-11 13:39:22,262 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci


2013-08-11 13:39:22,263 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-08-11 13:39:22,263 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-08-11 13:39:22,263 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-08-11 13:39:22,274 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates


2013-08-11 13:39:22,282 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-08-11 13:39:22,282 DEBUG: fglrx.available: falling back to default
2013-08-11 13:39:22,429 DEBUG: XorgDriverHandler(fglrx_updates, fglrx-updates, None): Disabling as package is not compatible with Q-LTS X.org
2013-08-11 13:39:22,429 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) not available
2013-08-11 13:39:22,433 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9


2013-08-11 13:39:22,458 DEBUG: Could not instantiate Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 972, in get_handlers
    desc = inst.name()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 108, in name
    self._package_defaults()
  File "/usr/lib/python2.7/dist-packages/jockey/handlers.py", line 93, in _package_defaults
    (distro_name, distro_desc) = OSLib.inst.package_description(self.package)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 216, in package_description
    raise ValueError('package %s does not exist' % package)
ValueError: package fglrx-experimental-9 does not exist
2013-08-11 13:39:22,465 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx


2013-08-11 13:39:22,473 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-08-11 13:39:22,473 DEBUG: fglrx.available: falling back to default
2013-08-11 13:39:22,619 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-08-11 13:39:22,620 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-08-11 13:39:22,620 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-08-11 13:39:22,627 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet


2013-08-11 13:39:22,627 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-08-11 13:39:22,649 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-08-11 13:39:22,649 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-08-11 13:39:22,657 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx


2013-08-11 13:39:22,658 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-08-11 13:39:22,658 DEBUG: cdv.available: falling back to default
2013-08-11 13:39:22,804 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-08-11 13:39:22,804 DEBUG: Intel Cedarview graphics driver not available
2013-08-11 13:39:22,805 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-08-11 13:39:22,811 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr


2013-08-11 13:39:22,816 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-08-11 13:39:22,950 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-08-11 13:39:22,950 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-08-11 13:39:22,951 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-08-11 13:39:22,956 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2013-08-11 13:39:22,969 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-08-11 13:39:22,970 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-08-11 13:39:22,970 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-08-11 13:39:22,989 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-08-11 13:39:22,989 DEBUG: Firmware for DVB cards not available
2013-08-11 13:39:22,989 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-08-11 13:39:23,004 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-08-11 13:39:23,013 DEBUG: Software modem not available
2013-08-11 13:39:23,014 DEBUG: all custom handlers loaded
2013-08-11 13:39:23,014 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2013-08-11 13:39:23,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k71,72,73,94,CA,E0,E1,E3,EC,F0,ram4,lsfw')
2013-08-11 13:39:23,311 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:39:23,371 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,371 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:39:23,371 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,371 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-08-11 13:39:23,372 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:39:23,372 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,372 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:39:23,372 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,372 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-08-11 13:39:23,372 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:39:23,376 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2013-08-11 13:39:23,380 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-08-11 13:39:23,380 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,380 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-08-11 13:39:23,380 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,380 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'platform:dell-laptop')
2013-08-11 13:39:23,381 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2013-08-11 13:39:23,409 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-08-11 13:39:23,409 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-08-11 13:39:23,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-08-11 13:39:23,410 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:39:23,410 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,410 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'usb:v7392p7811d0200dc00dsc00dp00icFFiscFFipFF')
2013-08-11 13:39:23,415 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rtl8192cu'}
2013-08-11 13:39:23,415 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rtl8192cu', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,415 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-08-11 13:39:23,415 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2013-08-11 13:39:23,415 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-08-11 13:39:23,415 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'platform:dcdbas')
2013-08-11 13:39:23,416 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-08-11 13:39:23,416 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:39:23,416 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,416 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:39:23,416 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'platform:gpio_ich')
2013-08-11 13:39:23,417 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich'}
2013-08-11 13:39:23,417 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'gpio_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2013-08-11 13:39:23,418 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:39:23,421 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'usb:v05CAp180Ad8730dcEFdsc02dp01ic0Eisc02ip00')
2013-08-11 13:39:23,421 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2013-08-11 13:39:23,421 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi'}
2013-08-11 13:39:23,422 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-08-11 13:39:23,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'acpi:PNP0303:')
2013-08-11 13:39:23,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2013-08-11 13:39:23,425 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2013-08-11 13:39:23,425 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,425 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:39:23,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'acpi:PNP0800:')
2013-08-11 13:39:23,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2013-08-11 13:39:23,432 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-08-11 13:39:23,432 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2013-08-11 13:39:23,433 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-08-11 13:39:23,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,433 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-08-11 13:39:23,433 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2013-08-11 13:39:23,448 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ums_realtek'}
2013-08-11 13:39:23,448 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ums_realtek', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,448 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-08-11 13:39:23,449 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,449 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:0017:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003D,0068,006B,006C,006D,006F,0070,0072,0074,007C,0080,0082,0083,0084,0087,0088,0089,008D,008E,008F,009A,009B,00C0,00E7')
2013-08-11 13:39:23,453 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-08-11 13:39:23,453 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,453 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-08-11 13:39:23,454 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,454 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,3,k110,111,112,145,14A,ra0,1,18,mlsfw')
2013-08-11 13:39:23,454 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:39:23,454 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,454 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-08-11 13:39:23,454 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,454 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-08-11 13:39:23,455 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,455 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:39:23,455 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,455 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2013-08-11 13:39:23,455 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:39:23,455 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,455 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:39:23,455 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,456 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-08-11 13:39:23,464 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-08-11 13:39:23,464 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,464 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-08-11 13:39:23,464 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,464 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-08-11 13:39:23,464 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:39:23,464 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,464 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-08-11 13:39:23,465 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:39:23,465 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,465 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'acpi:PNP0F13:')
2013-08-11 13:39:23,465 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd000002AAbc06sc04i01')
2013-08-11 13:39:23,468 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'input:b0003v05CAp180Ae8730-e0,1,kD4,ramlsfw')
2013-08-11 13:39:23,469 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:39:23,469 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,469 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:39:23,469 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'platform:microcode')
2013-08-11 13:39:23,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'acpi:PNP0100:')
2013-08-11 13:39:23,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'platform:regulatory')
2013-08-11 13:39:23,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA14:bd12/07/2009:svnDellInc.:pnInspiron1545:pvr:rvnDellInc.:rn:rvr:cvnDellInc.:ct8:cvr:')
2013-08-11 13:39:23,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-08-11 13:39:23,484 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2013-08-11 13:39:23,487 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:39:23,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2013-08-11 13:39:23,491 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-08-11 13:39:23,491 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,491 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-08-11 13:39:23,491 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,491 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2013-08-11 13:39:23,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2013-08-11 13:39:23,494 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-08-11 13:39:23,495 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2013-08-11 13:39:23,538 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2013-08-11 13:39:23,539 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:39:23,539 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-08-11 13:39:23,543 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2013-08-11 13:39:23,544 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:39:23,544 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-08-11 13:39:23,544 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2013-08-11 13:39:23,544 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,544 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'b43', 'package': 'firmware-b43-lpphy-installer'}
2013-08-11 13:39:23,545 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b43', 'jockey_handler': 'KernelModuleHandler', 'package': 'firmware-b43-lpphy-installer'}
2013-08-11 13:39:23,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2013-08-11 13:39:23,545 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:39:23,545 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,545 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:39:23,545 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'acpi:PNP0000:')
2013-08-11 13:39:23,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2013-08-11 13:39:23,549 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'platform:coretemp')
2013-08-11 13:39:23,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-08-11 13:39:23,550 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-08-11 13:39:23,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'usb:v05CAp180Ad8730dcEFdsc02dp01ic0Eisc01ip00')
2013-08-11 13:39:23,551 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-08-11 13:39:23,551 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'acpi:PNP0200:')
2013-08-11 13:39:23,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:39:23,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'hid:b0003g0001v0000413Cp00008161')
2013-08-11 13:39:23,602 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic'}
2013-08-11 13:39:23,602 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,602 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2013-08-11 13:39:23,603 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2013-08-11 13:39:23,603 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'wmi:77BD0728-2E34-478C-B625-67F02A7E4897')
2013-08-11 13:39:23,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'platform:pcspkr')
2013-08-11 13:39:23,604 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-08-11 13:39:23,604 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,604 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-08-11 13:39:23,604 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,604 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2013-08-11 13:39:23,607 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-08-11 13:39:23,608 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,608 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2013-08-11 13:39:23,630 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sky2'}
2013-08-11 13:39:23,630 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,630 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2013-08-11 13:39:23,634 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2013-08-11 13:39:23,634 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-08-11 13:39:23,634 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:39:23,634 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,634 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:39:23,635 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,635 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2013-08-11 13:39:23,635 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-08-11 13:39:23,635 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-08-11 13:39:23,635 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,635 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-08-11 13:39:23,635 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-08-11 13:39:23,636 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:39:23,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-08-11 13:39:23,639 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1e10758> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2013-08-11 13:39:23,639 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2013-08-11 13:39:23,639 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k71,72,73,94,CA,E0,E1,E3,EC,F0,ram4,lsfw')
2013-08-11 13:39:23,639 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-08-11 13:39:23,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-08-11 13:39:23,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v00008086d00002938sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:39:23,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2013-08-11 13:39:23,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'platform:dell-laptop')
2013-08-11 13:39:23,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFFiscFFipFF')
2013-08-11 13:39:23,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-08-11 13:39:23,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2013-08-11 13:39:23,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'usb:v7392p7811d0200dc00dsc00dp00icFFiscFFipFF')
2013-08-11 13:39:23,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-08-11 13:39:23,640 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2013-08-11 13:39:23,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-08-11 13:39:23,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'platform:dcdbas')
2013-08-11 13:39:23,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-08-11 13:39:23,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'platform:gpio_ich')
2013-08-11 13:39:23,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2013-08-11 13:39:23,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:39:23,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'usb:v05CAp180Ad8730dcEFdsc02dp01ic0Eisc02ip00')
2013-08-11 13:39:23,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2013-08-11 13:39:23,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-08-11 13:39:23,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'acpi:PNP0303:')
2013-08-11 13:39:23,641 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v00008086d00002A42sv00001028sd000002AAbc03sc00i00')
2013-08-11 13:39:23,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v00008086d00002934sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:39:23,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'acpi:PNP0800:')
2013-08-11 13:39:23,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2013-08-11 13:39:23,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'usb:v413Cp8161d0100dc00dsc00dp00ic03isc01ip01')
2013-08-11 13:39:23,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2013-08-11 13:39:23,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:0017:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003D,0068,006B,006C,006D,006F,0070,0072,0074,007C,0080,0082,0083,0084,0087,0088,0089,008D,008E,008F,009A,009B,00C0,00E7')
2013-08-11 13:39:23,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,3,k110,111,112,145,14A,ra0,1,18,mlsfw')
2013-08-11 13:39:23,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2013-08-11 13:39:23,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-08-11 13:39:23,642 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-08-11 13:39:23,643 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-08-11 13:39:23,643 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'acpi:PNP0F13:')
2013-08-11 13:39:23,643 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd000002AAbc06sc04i01')
2013-08-11 13:39:23,643 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'input:b0003v05CAp180Ae8730-e0,1,kD4,ramlsfw')
2013-08-11 13:39:23,643 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'platform:microcode')
2013-08-11 13:39:23,643 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'acpi:PNP0100:')
2013-08-11 13:39:23,643 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'platform:regulatory')
2013-08-11 13:39:23,643 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA14:bd12/07/2009:svnDellInc.:pnInspiron1545:pvr:rvnDellInc.:rn:rvr:cvnDellInc.:ct8:cvr:')
2013-08-11 13:39:23,643 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-08-11 13:39:23,643 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2013-08-11 13:39:23,644 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v00008086d00002935sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:39:23,644 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'usb:v413Cp8162d0100dc00dsc00dp00ic03isc01ip02')
2013-08-11 13:39:23,644 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00')
2013-08-11 13:39:23,644 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icFEisc01ip00')
2013-08-11 13:39:23,644 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Cbc02sc80i00')
2013-08-11 13:39:23,644 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2013-08-11 13:39:23,644 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'acpi:PNP0000:')
2013-08-11 13:39:23,644 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v00008086d00002A43sv00001028sd000002AAbc03sc80i00')
2013-08-11 13:39:23,644 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'platform:coretemp')
2013-08-11 13:39:23,644 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-08-11 13:39:23,644 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-08-11 13:39:23,645 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'usb:v05CAp180Ad8730dcEFdsc02dp01ic0Eisc01ip00')
2013-08-11 13:39:23,645 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'acpi:PNP0200:')
2013-08-11 13:39:23,645 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v00008086d00002937sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:39:23,645 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'hid:b0003g0001v0000413Cp00008161')
2013-08-11 13:39:23,645 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'usb:v413Cp8160d0173dcE0dsc01dp01icE0isc01ip01')
2013-08-11 13:39:23,645 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'wmi:77BD0728-2E34-478C-B625-67F02A7E4897')
2013-08-11 13:39:23,645 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'platform:pcspkr')
2013-08-11 13:39:23,645 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v00008086d00002930sv00001028sd000002AAbc0Csc05i00')
2013-08-11 13:39:23,645 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v000011ABd00004354sv00001028sd000002AAbc02sc00i00')
2013-08-11 13:39:23,645 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2013-08-11 13:39:23,645 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2013-08-11 13:39:23,646 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-08-11 13:39:23,646 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2013-08-11 13:39:23,646 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2013-08-11 13:39:23,646 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'pci:v00008086d00002936sv00001028sd000002AAbc0Csc03i00')
2013-08-11 13:39:23,646 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-08-11 13:39:23,646 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x21d43f8> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2013-08-11 13:39:23,709 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:39:23,728 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:39:23,752 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:39:27,153 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:39:30,488 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2013-08-11 13:39:30,489 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2013-08-11 13:39:30,507 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:39:32,484 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:39:32,512 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:39:32,550 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:40:18,029 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-08-11 13:40:18,339 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2013-08-11 13:40:18,340 WARNING: /sys/module/wl


```

---

### Post by oldfred on 2013-08-11
Added code tags, please use them for any long terminal output to make it easier to read & preserve formatting.

Also edited title so those who know about broadcom drivers may see your thread.

---

