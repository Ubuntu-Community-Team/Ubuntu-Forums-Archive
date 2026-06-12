---
title: "Can't activate additional driver"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by carolin3 on 2013-04-22
I try to activate it then it says look in /var/log/jockey.log

this is the log
```
2013-04-22 11:21:29,330 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c>2013-04-22 11:21:35,916 DEBUG: reading modalias file /lib/modules/3.5.0-27-generic/modules.alias
2013-04-22 11:21:36,436 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-04-22 11:21:36,450 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-04-22 11:21:36,826 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-04-22 11:21:37,010 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96


2013-04-22 11:21:37,020 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2013-04-22 11:21:37,026 DEBUG: nvidia.available: falling back to default
2013-04-22 11:21:37,747 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-22 11:21:37,748 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-22 11:21:37,756 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current


2013-04-22 11:21:37,768 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2013-04-22 11:21:37,769 DEBUG: nvidia.available: falling back to default
2013-04-22 11:21:38,302 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2013-04-22 11:21:38,312 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates


2013-04-22 11:21:38,329 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2013-04-22 11:21:38,333 DEBUG: nvidia.available: falling back to default
2013-04-22 11:21:38,869 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-04-22 11:21:38,878 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates


2013-04-22 11:21:38,893 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2013-04-22 11:21:38,896 DEBUG: nvidia.available: falling back to default
2013-04-22 11:21:39,378 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-22 11:21:39,378 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2013-04-22 11:21:39,387 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates


2013-04-22 11:21:39,403 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2013-04-22 11:21:39,405 DEBUG: nvidia.available: falling back to default
2013-04-22 11:21:39,963 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2013-04-22 11:21:39,972 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173


2013-04-22 11:21:39,982 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2013-04-22 11:21:39,984 DEBUG: nvidia.available: falling back to default
2013-04-22 11:21:40,475 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-22 11:21:40,477 DEBUG: NVIDIA accelerated graphics driver not available
2013-04-22 11:21:40,486 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310


2013-04-22 11:21:40,553 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2013-04-22 11:21:40,554 DEBUG: nvidia.available: falling back to default
2013-04-22 11:21:41,013 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-04-22 11:21:41,023 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304


2013-04-22 11:21:41,084 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2013-04-22 11:21:41,086 DEBUG: nvidia.available: falling back to default
2013-04-22 11:21:41,560 DEBUG: XorgDriverHandler(nvidia_experimental_304, nvidia-experimental-304, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-22 11:21:41,561 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2013-04-22 11:21:41,561 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-04-22 11:21:41,583 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates


2013-04-22 11:21:41,601 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2013-04-22 11:21:41,602 DEBUG: fglrx.available: falling back to default
2013-04-22 11:21:42,147 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2013-04-22 11:21:42,156 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9


2013-04-22 11:21:42,222 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2013-04-22 11:21:42,223 DEBUG: fglrx.available: falling back to default
2013-04-22 11:21:42,698 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) availability undetermined, adding to pool
2013-04-22 11:21:42,708 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx


2013-04-22 11:21:42,725 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2013-04-22 11:21:42,726 DEBUG: fglrx.available: falling back to default
2013-04-22 11:21:43,200 DEBUG: XorgDriverHandler(fglrx, fglrx, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-22 11:21:43,201 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2013-04-22 11:21:43,201 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-04-22 11:21:43,216 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr


2013-04-22 11:21:43,230 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-04-22 11:21:43,697 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-22 11:21:43,698 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-04-22 11:21:43,698 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-04-22 11:21:43,710 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet


2013-04-22 11:21:43,711 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-04-22 11:21:43,787 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-04-22 11:21:43,788 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-04-22 11:21:43,800 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl


2013-04-22 11:21:43,860 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-04-22 11:21:43,861 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-04-22 11:21:43,861 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2013-04-22 11:21:43,872 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx


2013-04-22 11:21:43,873 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2013-04-22 11:21:43,873 DEBUG: cdv.available: falling back to default
2013-04-22 11:21:44,338 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package is not compatible with Q-LTS X.org
2013-04-22 11:21:44,338 DEBUG: Intel Cedarview graphics driver not available
2013-04-22 11:21:44,339 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-04-22 11:21:44,349 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci


2013-04-22 11:21:44,351 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-04-22 11:21:44,351 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-04-22 11:21:44,351 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-04-22 11:21:44,400 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-04-22 11:21:44,534 DEBUG: Software modem not available
2013-04-22 11:21:44,535 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-04-22 11:21:44,669 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-04-22 11:21:44,670 DEBUG: Firmware for DVB cards not available
2013-04-22 11:21:44,671 DEBUG: all custom handlers loaded
2013-04-22 11:21:44,671 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'pci:v00008086d00000BF1sv00001043sd000084A9bc06sc00i00')
2013-04-22 11:21:45,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2013-04-22 11:21:45,898 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-22 11:21:46,204 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,204 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-22 11:21:46,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,205 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-22 11:21:46,206 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,206 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-22 11:21:46,206 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,207 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-22 11:21:46,207 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,207 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-22 11:21:46,208 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'pci:v0000168Cd00000032sv000011ADsd00006627bc02sc80i00')
2013-04-22 11:21:46,246 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ath9k'}
2013-04-22 11:21:46,246 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'pci:v00001969d00002062sv00001043sd00008468bc02sc00i00')
2013-04-22 11:21:46,264 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'atl1c'}
2013-04-22 11:21:46,265 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'platform:regulatory')
2013-04-22 11:21:46,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,8B,94,98,AB,AC,B8,B9,BF,D4,E3,EE,F0,F4,215,216,217,218,219,21A,ram4,lsfw')
2013-04-22 11:21:46,268 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-22 11:21:46,268 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,269 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-22 11:21:46,269 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,269 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'usb:v046Dp0A29d7657dc00dsc00dp00ic03isc00ip00')
2013-04-22 11:21:46,415 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-04-22 11:21:46,415 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,416 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-04-22 11:21:46,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-22 11:21:46,417 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-22 11:21:46,418 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,418 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'platform:microcode')
2013-04-22 11:21:46,420 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-22 11:21:46,420 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'platform:eisa')
2013-04-22 11:21:46,423 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'platform:eeepc-wmi')
2013-04-22 11:21:46,425 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'wmi:ABBC0F72-8EA1-11D1-00A0-C90629100000')
2013-04-22 11:21:46,425 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'eeepc_wmi'}
2013-04-22 11:21:46,426 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'eeepc_wmi', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,426 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001043sd000083ADbc0Csc03i20')
2013-04-22 11:21:46,442 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2013-04-22 11:21:46,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'pci:v00008086d000027BCsv00001043sd000083ADbc06sc01i00')
2013-04-22 11:21:46,458 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2013-04-22 11:21:46,459 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,459 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'pci:v00008086d000027C1sv00001043sd000083ADbc01sc06i01')
2013-04-22 11:21:46,475 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2013-04-22 11:21:46,475 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,476 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2013-04-22 11:21:46,476 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001043sd00008516bc04sc03i00')
2013-04-22 11:21:46,492 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-22 11:21:46,493 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,493 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-04-22 11:21:46,493 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-04-22 11:21:46,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'pci:v00008086d000027DAsv00001043sd000083ADbc0Csc05i00')
2013-04-22 11:21:46,510 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2013-04-22 11:21:46,510 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-22 11:21:46,511 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'pci:v00008086d00000BE1sv00001043sd000084A9bc03sc00i00')
2013-04-22 11:21:46,526 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'gma500_gfx'}
2013-04-22 11:21:46,527 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'gma500_gfx', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,527 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'cedarview_gfx', 'package': 'cedarview-drm'}
2013-04-22 11:21:46,536 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx


2013-04-22 11:21:46,591 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx


2013-04-22 11:21:46,592 DEBUG: got handler kmod:cedarview_gfx([KernelModuleHandler, nonfree, disabled] Cedar Trail drm driver in DKMS format.)
2013-04-22 11:21:46,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'usb:v04F2pB26Fd6253dcEFdsc02dp01ic0Eisc02ip00')
2013-04-22 11:21:46,609 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2013-04-22 11:21:46,609 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'input:b0003v046Dp0A29e0111-e0,1,3,4,k71,72,73,77,A3,A4,A5,A6,A8,CF,D0,ra28,29,2A,2B,2C,2D,2E,2F,30,31,32,33,34,35,36,37,38,39,3A,3B,3C,3D,3E,m4,lsfw')
2013-04-22 11:21:46,610 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-22 11:21:46,610 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,611 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-22 11:21:46,611 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,611 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-22 11:21:46,612 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,612 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-04-22 11:21:46,612 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,613 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-22 11:21:46,613 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,613 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-22 11:21:46,614 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-22 11:21:46,614 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,615 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-22 11:21:46,615 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,615 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'input:b0003v04F2pB26Fe6253-e0,1,kD4,ramlsfw')
2013-04-22 11:21:46,616 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-22 11:21:46,616 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,617 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-22 11:21:46,617 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,617 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-04-22 11:21:46,618 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrX101CH.0701:bd03/08/2012:svnASUSTeKCOMPUTERINC.:pnX101CH:pvrx.x:rvnASUSTeKCOMPUTERINC.:rnX101CH:rvrx.xx:cvnASUSTeKCOMPUTERINC.:ct10:cvrx.x:')
2013-04-22 11:21:46,664 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001043sd000083ADbc0Csc03i00')
2013-04-22 11:21:46,681 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-04-22 11:21:46,682 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-22 11:21:46,682 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,682 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-22 11:21:46,683 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,683 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'usb:v04F2pB26Fd6253dcEFdsc02dp01ic0Eisc01ip00')
2013-04-22 11:21:46,684 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2013-04-22 11:21:46,685 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,685 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'usb:v046Dp0A29d7657dc00dsc00dp00ic01isc01ip00')
2013-04-22 11:21:46,687 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio'}
2013-04-22 11:21:46,688 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,688 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'pci:v00008086d00002448sv00001043sd000083ADbc06sc04i01')
2013-04-22 11:21:46,704 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-04-22 11:21:46,704 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-22 11:21:46,705 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,705 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-22 11:21:46,705 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,706 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001043sd000083ADbc0Csc03i00')
2013-04-22 11:21:46,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-22 11:21:46,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001043sd000083ADbc0Csc03i00')
2013-04-22 11:21:46,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'acpi:SYN0A13:PNP0F13:')
2013-04-22 11:21:46,738 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-22 11:21:46,741 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001043sd000083ADbc0Csc03i00')
2013-04-22 11:21:46,756 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'hid:b0003g0001v0000046Dp00000A29')
2013-04-22 11:21:46,914 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic'}
2013-04-22 11:21:46,914 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'usb:v046Dp0A29d7657dc00dsc00dp00ic01isc02ip00')
2013-04-22 11:21:46,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'wmi:466747A0-70EC-11DE-8A39-0800200C9A66')
2013-04-22 11:21:46,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'platform:pcspkr')
2013-04-22 11:21:46,919 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-04-22 11:21:46,920 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,920 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-04-22 11:21:46,920 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'platform:coretemp')
2013-04-22 11:21:46,923 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:0036:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,0066,0068,006B,006C,006D,0072,0078,007C,0080,0082,0083,0084,0087,0088,0089,008E,008F,0096,00C0,00E1,00E7')
2013-04-22 11:21:46,943 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-04-22 11:21:46,944 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,944 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2013-04-22 11:21:46,944 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,945 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-22 11:21:46,974 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-04-22 11:21:46,974 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,975 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-04-22 11:21:46,975 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-22 11:21:46,976 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-22 11:21:46,976 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-22 11:21:46,977 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-22 11:21:46,978 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,978 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-22 11:21:46,978 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-04-22 11:21:46,979 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,979 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-04-22 11:21:46,980 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-04-22 11:21:46,980 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9e5ba0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-04-22 11:21:46,980 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'pci:v00008086d00000BF1sv00001043sd000084A9bc06sc00i00')
2013-04-22 11:21:46,981 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2013-04-22 11:21:46,981 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-04-22 11:21:46,981 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'pci:v0000168Cd00000032sv000011ADsd00006627bc02sc80i00')
2013-04-22 11:21:46,981 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'pci:v00001969d00002062sv00001043sd00008468bc02sc00i00')
2013-04-22 11:21:46,982 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'platform:regulatory')
2013-04-22 11:21:46,982 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,14,k71,72,73,8B,94,98,AB,AC,B8,B9,BF,D4,E3,EE,F0,F4,215,216,217,218,219,21A,ram4,lsfw')
2013-04-22 11:21:46,982 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'usb:v046Dp0A29d7657dc00dsc00dp00ic03isc00ip00')
2013-04-22 11:21:46,982 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-04-22 11:21:46,983 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2013-04-22 11:21:46,983 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'platform:microcode')
2013-04-22 11:21:46,983 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-04-22 11:21:46,983 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'platform:eisa')
2013-04-22 11:21:46,984 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'platform:eeepc-wmi')
2013-04-22 11:21:46,984 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'wmi:ABBC0F72-8EA1-11D1-00A0-C90629100000')
2013-04-22 11:21:46,984 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001043sd000083ADbc0Csc03i20')
2013-04-22 11:21:46,984 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'wmi:97845ED0-4E6D-11DE-8A39-0800200C9A66')
2013-04-22 11:21:46,985 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'pci:v00008086d000027BCsv00001043sd000083ADbc06sc01i00')
2013-04-22 11:21:46,985 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'pci:v00008086d000027C1sv00001043sd000083ADbc01sc06i01')
2013-04-22 11:21:46,985 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001043sd00008516bc04sc03i00')
2013-04-22 11:21:46,986 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-04-22 11:21:46,986 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'pci:v00008086d000027DAsv00001043sd000083ADbc0Csc05i00')
2013-04-22 11:21:46,986 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'acpi:INT0800:')
2013-04-22 11:21:46,986 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'pci:v00008086d00000BE1sv00001043sd000084A9bc03sc00i00')
2013-04-22 11:21:46,987 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'usb:v04F2pB26Fd6253dcEFdsc02dp01ic0Eisc02ip00')
2013-04-22 11:21:46,987 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2013-04-22 11:21:46,987 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'input:b0003v046Dp0A29e0111-e0,1,3,4,k71,72,73,77,A3,A4,A5,A6,A8,CF,D0,ra28,29,2A,2B,2C,2D,2E,2F,30,31,32,33,34,35,36,37,38,39,3A,3B,3C,3D,3E,m4,lsfw')
2013-04-22 11:21:46,987 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2013-04-22 11:21:46,988 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'input:b0003v04F2pB26Fe6253-e0,1,kD4,ramlsfw')
2013-04-22 11:21:46,988 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2013-04-22 11:21:46,988 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrX101CH.0701:bd03/08/2012:svnASUSTeKCOMPUTERINC.:pnX101CH:pvrx.x:rvnASUSTeKCOMPUTERINC.:rnX101CH:rvrx.xx:cvnASUSTeKCOMPUTERINC.:ct10:cvrx.x:')
2013-04-22 11:21:46,988 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001043sd000083ADbc0Csc03i00')
2013-04-22 11:21:46,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2013-04-22 11:21:46,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'usb:v04F2pB26Fd6253dcEFdsc02dp01ic0Eisc01ip00')
2013-04-22 11:21:46,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'usb:v046Dp0A29d7657dc00dsc00dp00ic01isc01ip00')
2013-04-22 11:21:46,989 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'pci:v00008086d00002448sv00001043sd000083ADbc06sc04i01')
2013-04-22 11:21:46,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2013-04-22 11:21:46,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001043sd000083ADbc0Csc03i00')
2013-04-22 11:21:46,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-04-22 11:21:46,990 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001043sd000083ADbc0Csc03i00')
2013-04-22 11:21:46,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'acpi:SYN0A13:PNP0F13:')
2013-04-22 11:21:46,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-04-22 11:21:46,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001043sd000083ADbc0Csc03i00')
2013-04-22 11:21:46,991 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'hid:b0003g0001v0000046Dp00000A29')
2013-04-22 11:21:46,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'usb:v046Dp0A29d7657dc00dsc00dp00ic01isc02ip00')
2013-04-22 11:21:46,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'wmi:466747A0-70EC-11DE-8A39-0800200C9A66')
2013-04-22 11:21:46,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'platform:pcspkr')
2013-04-22 11:21:46,992 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'platform:coretemp')
2013-04-22 11:21:46,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:0036:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,0034,0066,0068,006B,006C,006D,0072,0078,007C,0080,0082,0083,0084,0087,0088,0089,008E,008F,0096,00C0,00E1,00E7')
2013-04-22 11:21:46,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-04-22 11:21:46,993 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2013-04-22 11:21:46,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-04-22 11:21:46,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-04-22 11:21:46,994 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa0f4cac> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2013-04-22 11:22:05,032 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx


2013-04-22 11:22:05,033 WARNING: /sys/module/cedarview_gfx/drivers does not exist, cannot rebind cedarview_gfx driver
2013-04-22 11:23:45,980 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx


2013-04-22 11:23:45,982 WARNING: /sys/module/cedarview_gfx/drivers does not exist, cannot rebind cedarview_gfx driver
2013-04-22 11:24:01,167 DEBUG: Shutting down
```

My computer is eeepc x101ch

---

### Post by duanedesign on 2013-04-22
PLease try the following If you have a similar issue, your results may vary.

    Go into Synaptic (you may need to install Synaptic. It might be possible to accomplish this without Synaptic, have not tried)  and completely remove all Nvidia related packages, plus Jockey. Make sure to "completely remove", not just uninstall. You do this by right clicking on the green box and select 'completelt remove'.

    Re-install only jockey-common, jockey-gtk, nvidia-common, nvidia-current, and nvidia-settings. If it tries to auto-select any other packages, unmark them. Seriously.

    This is critical: After Synaptic has installed the selected packages, reboot once. Not rebooting at this point will cause failure later. At least, it did for me.

    After rebooting, open System Settings->Additional Drivers. At this point, you should have different options under Additional Drivers. I went with the one marked "Recommended". Select activate, and reboot again..

My graphics now seem to be working as they should.

---

### Post by abhich on 2013-04-22
i had the same problem with me. even when i download the additional driver it says 'not currently in use'

---

