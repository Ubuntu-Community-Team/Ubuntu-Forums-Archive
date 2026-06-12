---
title: "Ubuntu 11.10 very very slow"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by stubags on 2011-10-15
Hi there,

Was hoping someone could help me.

Totally new to linux - just fresh installed Ubuntu 11.10 onto a Dell Inspiron 6000.

Unfortunately it's running incredibly slowly - well, slower than the clogged up ancient version of Windows XP that was on it before. It takes forever to open a program, although certain ones, such as Chromium, run very quickly once they're actually open.

I've googled around and seem to be getting some sort of impression it might be something to do with the drivers?

I saw on another thread you it might be helpful to paste the jockey thingy from terminal, so will do that

any help or advice anyone can offer would be greatly appreciated
cheers,
stubags


```
2011-10-15 23:39:04,307 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 23:39:04,311 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-15 23:39:04,315 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-15 23:39:04,315 DEBUG: nvidia.available: falling back to default
2011-10-15 23:39:04,352 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-15 23:39:04,358 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-10-15 23:39:04,362 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-10-15 23:39:04,362 DEBUG: nvidia.available: falling back to default
2011-10-15 23:39:04,397 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 23:39:04,398 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-15 23:39:04,508 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-15 23:39:04,508 DEBUG: Firmware for DVB cards not available
2011-10-15 23:39:04,509 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-15 23:39:04,528 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-15 23:39:04,728 DEBUG: Software modem not available
2011-10-15 23:39:04,728 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-15 23:39:04,786 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-10-15 23:39:04,787 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-15 23:39:04,995 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-15 23:39:04,996 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-15 23:39:05,008 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-15 23:39:05,012 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-10-15 23:39:05,012 DEBUG: fglrx.available: falling back to default
2011-10-15 23:39:05,046 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 23:39:05,050 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-15 23:39:05,054 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-15 23:39:05,054 DEBUG: fglrx.available: falling back to default
2011-10-15 23:39:05,088 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-15 23:39:05,088 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-15 23:39:05,093 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-15 23:39:05,094 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-15 23:39:05,094 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-15 23:39:05,094 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-15 23:39:05,116 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-15 23:39:05,136 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-15 23:39:05,137 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-15 23:39:05,137 DEBUG: all custom handlers loaded
2011-10-15 23:39:05,137 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00008086d00002658sv00001028sd00000188bc0Csc03i00')
2011-10-15 23:39:05,566 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-15 23:39:05,572 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 23:39:05,760 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:05,760 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00008086d0000266Asv00001028sd00000188bc0Csc05i00')
2011-10-15 23:39:05,768 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-10-15 23:39:05,768 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:05,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-15 23:39:05,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-15 23:39:05,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00008086d00002659sv00001028sd00000188bc0Csc03i00')
2011-10-15 23:39:05,773 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-15 23:39:05,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'platform:pcspkr')
2011-10-15 23:39:05,775 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-10-15 23:39:05,775 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:05,775 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-10-15 23:39:05,775 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:05,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 23:39:05,806 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-15 23:39:05,807 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 23:39:05,807 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:05,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-15 23:39:05,808 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-15 23:39:05,808 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-15 23:39:05,809 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00008086d00004220sv00008086sd00002722bc02sc80i00')
2011-10-15 23:39:05,813 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ipw2200'}
2011-10-15 23:39:05,813 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ipw2200', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:05,814 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'platform:dcdbas')
2011-10-15 23:39:05,814 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00008086d00002590sv00001028sd00000188bc06sc00i00')
2011-10-15 23:39:05,819 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00008086d0000265Csv00001028sd00000188bc0Csc03i20')
2011-10-15 23:39:05,823 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-10-15 23:39:05,823 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00001002d00005460sv00001028sd00002003bc03sc00i00')
2011-10-15 23:39:06,258 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeonfb'}
2011-10-15 23:39:06,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeonfb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,258 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-10-15 23:39:06,258 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,258 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-15 23:39:06,258 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd00000188bc06sc04i01')
2011-10-15 23:39:06,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-15 23:39:06,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2011-10-15 23:39:06,263 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00001180d00000476sv00001028sd00000188bc06sc07i00')
2011-10-15 23:39:06,268 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'yenta_socket'}
2011-10-15 23:39:06,268 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'yenta_socket', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,268 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'yenta_socket'}
2011-10-15 23:39:06,269 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'yenta_socket', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,269 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00008086d00002653sv00001028sd00000188bc01sc01i80')
2011-10-15 23:39:06,273 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-10-15 23:39:06,273 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,273 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-15 23:39:06,273 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 23:39:06,274 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-10-15 23:39:06,274 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 23:39:06,274 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,274 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v000014E4d0000170Csv00001028sd00000188bc02sc00i00')
2011-10-15 23:39:06,334 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'b44'}
2011-10-15 23:39:06,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b44', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,334 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA08:bd07/22/2005:svnDellInc.:pnInspiron6000:pvr:rvnDellInc.:rn0UF414:rvr:cvnDellInc.:ct8:cvr:')
2011-10-15 23:39:06,354 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop'}
2011-10-15 23:39:06,354 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,354 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-15 23:39:06,354 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'ssb:v4243id0807rev03')
2011-10-15 23:39:06,358 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,3,k110,111,112,145,14A,ra0,1,18,mlsfw')
2011-10-15 23:39:06,358 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 23:39:06,358 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,358 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-15 23:39:06,358 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,358 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-15 23:39:06,359 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,359 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 23:39:06,359 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00008086d0000265Bsv00001028sd00000188bc0Csc03i00')
2011-10-15 23:39:06,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-15 23:39:06,364 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00008086d00002641sv00001028sd00000188bc06sc01i00')
2011-10-15 23:39:06,368 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng'}
2011-10-15 23:39:06,369 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,369 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-10-15 23:39:06,369 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,369 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00008086d0000265Asv00001028sd00000188bc0Csc03i00')
2011-10-15 23:39:06,376 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00008086d0000266Dsv000014F1sd00005423bc07sc03i00')
2011-10-15 23:39:06,381 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_intel8x0m'}
2011-10-15 23:39:06,381 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_intel8x0m', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,381 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00001180d00000552sv00001028sd00000188bc0Csc00i10')
2011-10-15 23:39:06,381 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2011-10-15 23:39:06,381 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,382 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'platform:regulatory')
2011-10-15 23:39:06,382 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-15 23:39:06,382 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 23:39:06,383 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,383 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-15 23:39:06,383 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd00000188bc08sc05i01')
2011-10-15 23:39:06,383 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2011-10-15 23:39:06,383 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,383 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci'}
2011-10-15 23:39:06,384 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,384 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'platform:eisa')
2011-10-15 23:39:06,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-15 23:39:06,398 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-15 23:39:06,398 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,398 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-10-15 23:39:06,398 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,398 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'ssb:v4243id0806rev07')
2011-10-15 23:39:06,399 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'b44'}
2011-10-15 23:39:06,399 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b44', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'pci:v00008086d0000266Esv00001028sd00000188bc04sc01i00')
2011-10-15 23:39:06,404 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_intel8x0'}
2011-10-15 23:39:06,404 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_intel8x0', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,404 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-15 23:39:06,404 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 23:39:06,404 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 23:39:06,404 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb748490c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-15 23:39:06,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00008086d00002658sv00001028sd00000188bc0Csc03i00')
2011-10-15 23:39:06,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-10-15 23:39:06,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00008086d0000266Asv00001028sd00000188bc0Csc05i00')
2011-10-15 23:39:06,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-15 23:39:06,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'acpi:PNP0303:')
2011-10-15 23:39:06,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00008086d00002659sv00001028sd00000188bc0Csc03i00')
2011-10-15 23:39:06,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-15 23:39:06,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'platform:pcspkr')
2011-10-15 23:39:06,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 23:39:06,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-10-15 23:39:06,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-15 23:39:06,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-15 23:39:06,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'platform:dell-laptop')
2011-10-15 23:39:06,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00008086d00004220sv00008086sd00002722bc02sc80i00')
2011-10-15 23:39:06,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'platform:dcdbas')
2011-10-15 23:39:06,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00008086d00002590sv00001028sd00000188bc06sc00i00')
2011-10-15 23:39:06,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00008086d0000265Csv00001028sd00000188bc0Csc03i20')
2011-10-15 23:39:06,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-10-15 23:39:06,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00001002d00005460sv00001028sd00002003bc03sc00i00')
2011-10-15 23:39:06,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-15 23:39:06,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00008086d00002448sv00001028sd00000188bc06sc04i01')
2011-10-15 23:39:06,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-15 23:39:06,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2011-10-15 23:39:06,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00001180d00000476sv00001028sd00000188bc06sc07i00')
2011-10-15 23:39:06,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00008086d00002653sv00001028sd00000188bc01sc01i80')
2011-10-15 23:39:06,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-10-15 23:39:06,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-10-15 23:39:06,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v000014E4d0000170Csv00001028sd00000188bc02sc00i00')
2011-10-15 23:39:06,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA08:bd07/22/2005:svnDellInc.:pnInspiron6000:pvr:rvnDellInc.:rn0UF414:rvr:cvnDellInc.:ct8:cvr:')
2011-10-15 23:39:06,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-15 23:39:06,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'ssb:v4243id0807rev03')
2011-10-15 23:39:06,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,3,k110,111,112,145,14A,ra0,1,18,mlsfw')
2011-10-15 23:39:06,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 23:39:06,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00008086d0000265Bsv00001028sd00000188bc0Csc03i00')
2011-10-15 23:39:06,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-15 23:39:06,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00008086d00002641sv00001028sd00000188bc06sc01i00')
2011-10-15 23:39:06,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00008086d0000265Asv00001028sd00000188bc0Csc03i00')
2011-10-15 23:39:06,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00008086d0000266Dsv000014F1sd00005423bc07sc03i00')
2011-10-15 23:39:06,408 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00001180d00000552sv00001028sd00000188bc0Csc00i10')
2011-10-15 23:39:06,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'platform:regulatory')
2011-10-15 23:39:06,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2011-10-15 23:39:06,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-15 23:39:06,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd00000188bc08sc05i01')
2011-10-15 23:39:06,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'platform:eisa')
2011-10-15 23:39:06,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-15 23:39:06,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'ssb:v4243id0806rev07')
2011-10-15 23:39:06,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'pci:v00008086d0000266Esv00001028sd00000188bc04sc01i00')
2011-10-15 23:39:06,409 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-15 23:39:06,409 DEBUG: querying driver db jockey.detection.OpenPrintingDriverDB instance at 0xb74847ac> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-15 23:40:29,160 DEBUG: Shutting down
```

---

### Post by madjr on 2011-10-15
have you tried login into **unity 2d** ?

also computer specs please

---

### Post by stubags on 2011-10-15
hi 
thanks for replying

here's the specs

just trying to work out how to access unity 2d...

```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port [8086:2591] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M22 [Mobility Radeon X300] [1002:5460]
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b3)
03:01.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 08)
03:01.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 17)
03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
```

---

### Post by stubags on 2011-10-15
hi

in unity 2d now - no difference

programmes are taking between 20 and 30 seconds to load up, as is even the home folder - is assume this linux malarkey is supposed to be faster than this, even on an oldish computer like this?

---

### Post by madjr on 2011-10-15
is this your computer?
[http://www.notebookreview.com/default.asp?newsID=2376](http://www.notebookreview.com/default.asp?newsID=2376)

what was the last distro you tried on it?

your computer probably may not to be able to handle unity, so i would try xubuntu or lubuntu to max its performance

---

### Post by sisyphus10 on 2011-10-16
I too am finding 11.10 incredibly slow. I upgraded to it yesterday from 11.04 which was snappily fast, as have been previous versions. But with this one, it takes on average about 10 seconds to open a program where before it took one second or less. "Fast" on 11.10 is 4 or 5 seconds to get a reaction.

I have tried it in Unity 3D and 2D and also installed Gnome Classic, but the reaction times are the same in all of them.

The computer is fairly old -- a Pentium IV 2.0 GHz with 2.5 GB RAM. The graphics are shown to be Gallium 0.4 on NV34 -- though I thought it was an old NVidia card (which I am guessing the NV in NV34 might be related to)... But as I say, previous versions of Ubuntu ran fine on it.

The computer is totally dedicated to Ubuntu.

---

### Post by Meelad on 2011-10-16
I'm running it on Q8400 Quadcore 2.66 GHz processor and 4 GB RAM (Ubuntu only recognizes 3.2 GB of it). Ubuntu 11.10 seems to run fairly smooth on it. The Software Centrum could take 4-5 seconds to start, but most of the programs run reasonably fast. I had 10.10 before this one and I didn't notice any loss of speed. So far it's even more stable than 10.10..

---

### Post by madjr on 2011-10-16
> **sisyphus10 said:**
> I too am finding 11.10 incredibly slow. I upgraded to it yesterday from 11.04 which was snappily fast, as have been previous versions. But with this one, it takes on average about 10 seconds to open a program where before it took one second or less. "Fast" on 11.10 is 4 or 5 seconds to get a reaction.

I have tried it in Unity 3D and 2D and also installed Gnome Classic, but the reaction times are the same in all of them.

The computer is fairly old -- a Pentium IV 2.0 GHz with 2.5 GB RAM. The graphics are shown to be Gallium 0.4 on NV34 -- though I thought it was an old NVidia card (which I am guessing the NV in NV34 might be related to)... But as I say, previous versions of Ubuntu ran fine on it.

The computer is totally dedicated to Ubuntu.

if it was an upgrade, then it may had gone bad, so try a live-cd or usb and see if performance is same.

---

### Post by jayrulez on 2011-10-20
Does it run slowly just after boot or does it get slower after a few minutes?

Check your system monitor and see how much memory the ubuntuone sync daemon process is using. Recently it I saw it using about 1.5 of the 2 GB  I have available. I have to stop tht process everytime I start up.

---

### Post by collisionystm on 2011-10-20
Looking at your computer models specs, I do not think it has the power to handle 11.10. Theoretically it should, but in the real world... no. You are on the border line. I have used that computer you have. For some reason those are just slow. I even have one here I put 10.04 on and it is still slow.

Maybe invest in something else?

---

### Post by collisionystm on 2011-10-20
or if you want to try a lightweight great linux, try crunchbang with xfce. It might be right up your ally. It is also a VERY GOOD distro.

---

### Post by Roope_T on 2011-10-20
I have 4 computers home and all have 11.10. 

Two laptops that are fairly old are very very slow with 11.10 but they were fast when they had 10.04. And from these two the lot faster is the slower one. The other two computers run very well.

So is this about some bug or? Im not going to belive that Unity is the reason for this because the symptoms are same as when the computer uses lot of swap.

---

### Post by cclements on 2011-10-20
Hey guys, posted this in a related thread, but thought I'd throw my experience in here.  

MacBook Pro 7,1 (NVidia 320M)

I was having extreme slowness in launching applications as well.  It would sometimes take firefox +4s to launch.  I was able to completely eliminate the sluggishness by:

1.  installing the latest nvidia driver from the website, 285.something
2.  in nvidia x server settings app, set "powermizer" to "prefer maximum performance"

Immediately, the sluggishness went away.  Firefox now opens in slightly over a second.  Hope this helps someone.

---

### Post by Roope_T on 2011-10-20
Thanx for the tip towards the gpu. This fixed both computers. I had ATI gpu in both.

```
sudo apt-get install fglrx
```

---

### Post by sisyphus10 on 2011-10-20
I tested it running 11.10 from the disc, and it is still slow. So I guess that is that for this computer -- though I will check out that sync daemon/Ram business. But in the end, I suppose I will need to reinstall 11.04 which ran very well and fast.

I will now try it on another computer -- a P4 3.0 GHz with 4 GB RAM, currently set up as a dual boot Ubuntu 11.04 and Windows 7...

EDIT: I wrote the above before seeing the other more recent posts on this page. Will check out the GPU driver business too.

Another piece of information: when I open something simple like a game (Mahjongg), the CPU usage in System Monitor goes up to 100% and sits there for 4 or 5 seconds, then drops down to 10%. The game opens minimized, and if I enlarge it to fit the screen, the CPU jumps back up to 100% for another 4 or 5 seconds. RAM remains constant at around 6% throughout. When using Ubuntu 11.04 and with the same game, these actions were near instantaneous.

Question: is there a way to force Ubuntu to look for an update to the GPU?

---

### Post by sisyphus10 on 2011-10-20
A real newbie question: the only appropriate (?) driver I could find on the NVidia website was for Linux 32-bit. It has the title NVIDIA-Linux-x86-173.14.31-pkg1.run Can someone please confirm if this is in fact an appropriate type of file for Ubuntu, and if so, how do I in fact "run" it. Double clicking on it produces nothing...

---

### Post by superbatlife on 2011-10-20
Install 11.04, 11.10 needs time to mature..

My gateway with a very basic duo handles it fine but my pentium 4 2.2 ghz with 1 gig of memory bogs.
11.04 on the pentium is very very fast, less then 20 seconds boot, less than 5 shutdown, programs open and close freely...

---

### Post by sisyphus10 on 2011-10-26
FWIW, I tried 11.10 on my P4 3.0 GHZ where 11.04 currently dual boots with Windows 7. I ran it from the installation disk. While a little faster, it was still unacceptably slow, though the amount of CPU used on this computer ran to a maximum of around 70% as opposed to 100% on the other one.

---

### Post by Kamikazi Xavier on 2011-10-26
i hope mine wont be too slow. i cant find how to get unity to work yet in 10.04

---

### Post by Le Bouffre on 2011-11-26
Hi all,

my first post. I have the same problem.
I recently installed Ubuntu 11.10 on a Packard Bell Imax within Vista - 2gb.
I am disappointed with the responsiveness of the system (I mainly use Firefox).
Is my computer unsuitable for this version of Linux? It is no faster under Ubuntu than under Vista where I had resorted to using GameBooster to shut down unnecessary processes and services.
I am not well  acquainted with Linux. Any help appreciated.:)
My PC:
[http://www.techradar.com/reviews/pc-mac/pc-mac-desktops/packard-bell-imax-mini-n3600-647055/review#](http://www.techradar.com/reviews/pc-mac/pc-mac-desktops/packard-bell-imax-mini-n3600-647055/review#)

update: I have uninstalled the proprietary nVidia driver to see if that helps.
update 2: now I have no sound; FF seems a bit faster
update 3: installed other "unrecommended" driver, got sound back, but will it be faster...?

---

