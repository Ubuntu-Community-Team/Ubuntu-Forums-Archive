---
title: "wireless driver help much appreciated"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by bjgar on 2012-02-26
I had the broadcom sta wireless driver but when i tried to use aircrack i was told i needed the b43 driver, so after alot of confusion i got it. now neither seems to work, please help i dont want to mess anything up. when i try to activate the old driver it says Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

the log says: 
```
2012-02-26 11:20:52,186 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c>
2012-02-26 11:20:52,189 DEBUG: reading modalias file /lib/modules/2.6.32-38-generic/modules.alias
2012-02-26 11:20:52,412 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2012-02-26 11:20:52,424 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-02-26 11:20:52,494 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2012-02-26 11:20:52,504 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2012-02-26 11:20:52,513 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2012-02-26 11:20:52,531 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2012-02-26 11:20:52,562 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-02-26 11:20:53,013 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-02-26 11:20:53,070 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-02-26 11:20:53,110 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-02-26 11:20:53,111 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-02-26 11:20:53,111 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-02-26 11:20:53,117 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-02-26 11:20:53,117 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-02-26 11:20:53,117 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-02-26 11:20:53,118 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-02-26 11:20:53,202 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-02-26 11:20:53,222 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-02-26 11:20:53,268 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-02-26 11:20:53,275 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-02-26 11:20:53,276 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-02-26 11:20:53,301 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-02-26 11:20:53,302 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-02-26 11:20:53,330 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-02-26 11:20:53,331 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-02-26 11:20:53,359 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-02-26 11:20:53,359 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-02-26 11:20:53,410 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-02-26 11:20:53,638 DEBUG: Software modem not available
2012-02-26 11:20:53,639 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-02-26 11:20:53,647 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-02-26 11:20:53,648 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-02-26 11:20:53,663 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-02-26 11:20:53,663 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2012-02-26 11:20:53,766 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2012-02-26 11:20:53,767 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2012-02-26 11:20:53,797 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2012-02-26 11:20:53,798 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2012-02-26 11:20:53,798 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-02-26 11:20:53,980 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-02-26 11:20:53,981 DEBUG: Firmware for DVB cards not available
2012-02-26 11:20:53,982 DEBUG: all custom handlers loaded
2012-02-26 11:20:53,982 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v00008086d000027A6sv00001028sd000001BDbc03sc80i00')
2012-02-26 11:20:54,355 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2012-02-26 11:20:54,720 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v00008086d000027B9sv00001028sd000001BDbc06sc01i00')
2012-02-26 11:20:54,726 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rng', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,726 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,726 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd000001BDbc08sc80i00')
2012-02-26 11:20:54,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-02-26 11:20:54,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'acpi:device:')
2012-02-26 11:20:54,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001028sd000001BDbc04sc03i00')
2012-02-26 11:20:54,735 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,735 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-02-26 11:20:54,736 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,736 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'platform:dcdbas')
2012-02-26 11:20:54,736 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-02-26 11:20:54,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v00008086d000027DAsv00001028sd000001BDbc0Csc05i00')
2012-02-26 11:20:54,772 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,772 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-02-26 11:20:54,772 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,772 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-02-26 11:20:54,772 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-02-26 11:20:54,773 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001028sd000001BDbc0Csc03i20')
2012-02-26 11:20:54,777 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'platform:regulatory')
2012-02-26 11:20:54,777 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd000001BDbc08sc80i00')
2012-02-26 11:20:54,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v00008086d000027A0sv00001028sd000001BDbc06sc00i00')
2012-02-26 11:20:54,782 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-02-26 11:20:54,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-02-26 11:20:54,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v00008086d000027A2sv00001028sd000001BDbc03sc00i00')
2012-02-26 11:20:54,787 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,787 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,787 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-02-26 11:20:54,787 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-02-26 11:20:54,787 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-02-26 11:20:54,787 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-02-26 11:20:54,787 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'ssb:v4243id0807rev03')
2012-02-26 11:20:54,791 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001028sd000001BDbc0Csc03i00')
2012-02-26 11:20:54,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd000001BDbc08sc05i01')
2012-02-26 11:20:54,796 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,796 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,796 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-02-26 11:20:54,796 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,797 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-02-26 11:20:54,797 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,797 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2012-02-26 11:20:54,797 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,797 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,798 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'ssb:v4243id0806rev07')
2012-02-26 11:20:54,798 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b44', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001028sd000001BDbc0Csc03i00')
2012-02-26 11:20:54,802 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA08:bd07/28/2006:svnDellInc.:pnMM061:pvr:rvnDellInc.:rn0KD882:rvr:cvnDellInc.:ct8:cvr:')
2012-02-26 11:20:54,820 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,821 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_laptop', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,821 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-02-26 11:20:54,821 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'ssb:v4243id0817rev04')
2012-02-26 11:20:54,821 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-02-26 11:20:54,821 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,821 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-02-26 11:20:54,822 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'usb:v0BB4p0C02d0226dc00dsc00dp00ic08isc06ip50')
2012-02-26 11:20:54,928 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-02-26 11:20:54,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-02-26 11:20:54,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd000001BDbc0Csc00i10')
2012-02-26 11:20:54,929 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,929 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,929 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v000014E4d00004328sv00001028sd00000009bc02sc80i00')
2012-02-26 11:20:54,990 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,994 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-02-26 11:20:54,995 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: enabled, b43: enabled, b43legacy: enabled
2012-02-26 11:20:54,994 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-02-26 11:20:54,995 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v000014E4d0000170Csv00001028sd000001AFbc02sc00i00')
2012-02-26 11:20:54,996 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b44', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:54,996 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001028sd000001BDbc0Csc03i00')
2012-02-26 11:20:55,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'platform:pcspkr')
2012-02-26 11:20:55,002 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:55,002 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:55,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2012-02-26 11:20:55,003 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:55,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'acpi:PNP0F13:')
2012-02-26 11:20:55,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'usb:v0BB4p0C02d0226dc00dsc00dp00icFFisc42ip01')
2012-02-26 11:20:55,005 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001028sd000001BDbc0Csc03i00')
2012-02-26 11:20:55,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'platform:eisa')
2012-02-26 11:20:55,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-02-26 11:20:55,023 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:55,023 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:55,023 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'ssb:v4243id0812rev0B')
2012-02-26 11:20:55,023 DEBUG: got handler firmware:b43([B43Handler, free, enabled] Broadcom B43 wireless driver)
2012-02-26 11:20:55,223 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2012-02-26 11:20:55,228 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-02-26 11:20:55,228 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-02-26 11:20:55,228 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8604c6c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-02-26 11:20:55,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v00008086d000027A6sv00001028sd000001BDbc03sc80i00')
2012-02-26 11:20:55,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2012-02-26 11:20:55,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v00008086d000027B9sv00001028sd000001BDbc06sc01i00')
2012-02-26 11:20:55,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd000001BDbc08sc80i00')
2012-02-26 11:20:55,229 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-02-26 11:20:55,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'acpi:device:')
2012-02-26 11:20:55,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v00008086d000027D8sv00001028sd000001BDbc04sc03i00')
2012-02-26 11:20:55,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-02-26 11:20:55,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'platform:dcdbas')
2012-02-26 11:20:55,230 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-02-26 11:20:55,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v00008086d000027DAsv00001028sd000001BDbc0Csc05i00')
2012-02-26 11:20:55,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-02-26 11:20:55,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-02-26 11:20:55,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-02-26 11:20:55,231 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v00008086d000027CCsv00001028sd000001BDbc0Csc03i20')
2012-02-26 11:20:55,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'platform:regulatory')
2012-02-26 11:20:55,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd000001BDbc08sc80i00')
2012-02-26 11:20:55,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v00008086d000027A0sv00001028sd000001BDbc06sc00i00')
2012-02-26 11:20:55,232 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-02-26 11:20:55,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-02-26 11:20:55,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v00008086d000027A2sv00001028sd000001BDbc03sc00i00')
2012-02-26 11:20:55,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-02-26 11:20:55,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-02-26 11:20:55,233 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-02-26 11:20:55,234 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-02-26 11:20:55,234 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'ssb:v4243id0807rev03')
2012-02-26 11:20:55,234 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v00008086d000027C9sv00001028sd000001BDbc0Csc03i00')
2012-02-26 11:20:55,234 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd000001BDbc08sc05i01')
2012-02-26 11:20:55,234 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-02-26 11:20:55,235 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-02-26 11:20:55,235 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,14D,14E,ra0,1,18,1C,mlsfw')
2012-02-26 11:20:55,235 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'ssb:v4243id0806rev07')
2012-02-26 11:20:55,235 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v00008086d000027C8sv00001028sd000001BDbc0Csc03i00')
2012-02-26 11:20:55,235 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA08:bd07/28/2006:svnDellInc.:pnMM061:pvr:rvnDellInc.:rn0KD882:rvr:cvnDellInc.:ct8:cvr:')
2012-02-26 11:20:55,236 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-02-26 11:20:55,236 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'ssb:v4243id0817rev04')
2012-02-26 11:20:55,236 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-02-26 11:20:55,236 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-02-26 11:20:55,236 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'usb:v0BB4p0C02d0226dc00dsc00dp00ic08isc06ip50')
2012-02-26 11:20:55,237 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-02-26 11:20:55,237 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-02-26 11:20:55,237 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd000001BDbc0Csc00i10')
2012-02-26 11:20:55,237 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v000014E4d00004328sv00001028sd00000009bc02sc80i00')
2012-02-26 11:20:55,237 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v000014E4d0000170Csv00001028sd000001AFbc02sc00i00')
2012-02-26 11:20:55,238 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v00008086d000027CAsv00001028sd000001BDbc0Csc03i00')
2012-02-26 11:20:55,238 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'platform:pcspkr')
2012-02-26 11:20:55,238 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C0,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')
2012-02-26 11:20:55,238 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'acpi:PNP0F13:')
2012-02-26 11:20:55,238 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'usb:v0BB4p0C02d0226dc00dsc00dp00icFFisc42ip01')
2012-02-26 11:20:55,239 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v00008086d000027CBsv00001028sd000001BDbc0Csc03i00')
2012-02-26 11:20:55,239 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'platform:eisa')
2012-02-26 11:20:55,239 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-02-26 11:20:55,239 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'ssb:v4243id0812rev0B')
2012-02-26 11:20:55,240 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2012-02-26 11:20:55,240 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-02-26 11:20:55,240 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89f3c2c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-02-26 11:20:55,639 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: enabled, b43: enabled, b43legacy: enabled
2012-02-26 11:20:56,169 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: enabled, b43: enabled, b43legacy: enabled
2012-02-26 11:21:02,466 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: enabled, b43: enabled, b43legacy: enabled
2012-02-26 11:21:03,691 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: enabled, b43: enabled, b43legacy: enabled
2012-02-26 11:21:10,386 DEBUG: Installing package: bcmwl-kernel-source
2012-02-26 11:21:12,167 DEBUG: install progress statusChange dpkg-exec 0.000000
2012-02-26 11:21:15,696 DEBUG: install progress statusChange bcmwl-kernel-source 0.000000
2012-02-26 11:21:15,697 DEBUG: install progress statusChange bcmwl-kernel-source 20.000000
2012-02-26 11:21:17,011 DEBUG: install progress statusChange bcmwl-kernel-source 40.000000
2012-02-26 11:21:17,083 DEBUG: install progress statusChange bcmwl-kernel-source 60.000000
2012-02-26 11:21:17,311 DEBUG: install progress statusChange dpkg-exec 60.000000
2012-02-26 11:21:17,420 DEBUG: install progress statusChange bcmwl-kernel-source 60.000000
2012-02-26 11:21:17,502 DEBUG: install progress statusChange bcmwl-kernel-source 80.000000
2012-02-26 11:21:56,069 DEBUG: install progress statusChange bcmwl-kernel-source 100.000000
2012-02-26 11:21:56,262 DEBUG: install progress statusChange initramfs-tools 100.000000
2012-02-26 11:22:12,416 DEBUG: Selecting previously deselected package bcmwl-kernel-source.
(Reading database ... 218357 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb) ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-38-generic
Building for architecture i686
Building initial module for 2.6.32-38-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-38-generic/updates/dkms/

depmod.........

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-38-generic

2012-02-26 11:22:13,013 DEBUG: unbind/rebind on driver /sys/module/wl/drivers/pci:wl: device 0000:0b:00.0
2012-02-26 11:22:13,191 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-02-26 11:22:13,310 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-02-26 11:22:20,212 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-02-26 11:22:20,323 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-02-26 11:22:20,356 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-02-26 11:22:20,463 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-02-26 11:22:20,660 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-02-26 11:22:20,767 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
```

---

