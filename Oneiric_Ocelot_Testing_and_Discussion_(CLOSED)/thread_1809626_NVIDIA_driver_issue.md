---
title: "NVIDIA driver issue"
date: 2011-07-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mdhollis on 2011-07-21
I just upgraded oneiric and on the kernel 3.0.0-6 I noticed that I wasn't getting 3D acceleration and the NVIDIA driver wasn't activated. When I try to activate it I get an error that reads "Sorry, installation of this driver failed.  Please have a look at the log file for details: /var/log/jockey.log"

This is the log:

```
2011-07-21 21:37:38,596 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c>
2011-07-21 21:37:40,503 DEBUG: reading modalias file /lib/modules/3.0.0-6-generic-pae/modules.alias
2011-07-21 21:37:40,643 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-07-21 21:37:40,650 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-07-21 21:37:40,703 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-07-21 21:37:40,722 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-07-21 21:37:40,777 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-21 21:37:40,782 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-07-21 21:37:40,782 DEBUG: fglrx.available: falling back to default
2011-07-21 21:37:40,888 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-07-21 21:37:40,888 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-07-21 21:37:40,941 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-07-21 21:37:40,941 DEBUG: Firmware for DVB cards not available
2011-07-21 21:37:40,942 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-07-21 21:37:40,968 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-07-21 21:37:40,992 DEBUG: Software modem not available
2011-07-21 21:37:40,992 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-07-21 21:37:41,010 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-07-21 21:37:41,016 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-07-21 21:37:41,017 DEBUG: nvidia.available: falling back to default
2011-07-21 21:37:41,041 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-07-21 21:37:41,042 DEBUG: NVIDIA accelerated graphics driver not available
2011-07-21 21:37:41,047 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-07-21 21:37:41,053 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-07-21 21:37:41,053 DEBUG: nvidia.available: falling back to default
2011-07-21 21:37:41,105 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-21 21:37:41,105 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 957, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-07-21 21:37:41,118 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-07-21 21:37:41,124 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-07-21 21:37:41,125 DEBUG: nvidia.available: falling back to default
2011-07-21 21:37:41,174 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-21 21:37:41,174 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-07-21 21:37:41,190 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-21 21:37:41,214 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-07-21 21:37:41,214 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-07-21 21:37:41,215 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-07-21 21:37:41,221 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-07-21 21:37:41,221 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-07-21 21:37:41,222 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-07-21 21:37:41,222 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-07-21 21:37:41,259 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-07-21 21:37:41,259 DEBUG: Experimental 3D support for NVIDIA cards is available
2011-07-21 21:37:41,260 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-07-21 21:37:41,274 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-07-21 21:37:41,275 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-07-21 21:37:41,300 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-07-21 21:37:41,301 DEBUG: all custom handlers loaded
2011-07-21 21:37:41,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A66bc0Csc05i00')
2011-07-21 21:37:41,753 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:41,753 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-21 21:37:41,753 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-21 21:37:41,754 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A66bc05sc00i00')
2011-07-21 21:37:41,758 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'platform:eisa')
2011-07-21 21:37:41,759 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-07-21 21:37:41,791 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-21 21:37:41,798 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:41,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-21 21:37:41,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'platform:pcspkr')
2011-07-21 21:37:41,799 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:41,799 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:41,799 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v000010DEd000003D0sv0000103Csd00002A66bc03sc00i00')
2011-07-21 21:37:41,805 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:41,805 DEBUG: got handler xorg:nouveau([Nouveau3DHandler, free, disabled] Experimental 3D support for NVIDIA cards)
2011-07-21 21:37:41,962 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-07-21 21:37:41,968 DEBUG: nvidia.available: falling back to default
2011-07-21 21:37:42,455 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:37:42,456 DEBUG: KMH enabled: False
2011-07-21 21:37:41,994 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-07-21 21:37:42,464 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-07-21 21:37:42,476 DEBUG: nvidia.available: falling back to default
2011-07-21 21:37:42,519 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-07-21 21:37:42,581 DEBUG: NVidia(nvidia_96).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:37:42,582 DEBUG: nvidia_96 is not the alternative in use
2011-07-21 21:37:42,520 DEBUG: ignoring unavailable handler xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-07-21 21:37:42,590 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-07-21 21:37:42,601 DEBUG: nvidia.available: falling back to default
2011-07-21 21:37:42,707 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:37:42,707 DEBUG: nvidia_173 is not the alternative in use
2011-07-21 21:37:42,644 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-07-21 21:37:42,707 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'platform:regulatory')
2011-07-21 21:37:42,709 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A66bc05sc00i00')
2011-07-21 21:37:42,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v000011C1d00005811sv0000103Csd00002A66bc0Csc00i10')
2011-07-21 21:37:42,724 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:42,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-21 21:37:42,724 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A66bc06sc01i00')
2011-07-21 21:37:42,735 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-07-21 21:37:42,735 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v00008086d0000107Csv00008086sd00001376bc02sc00i00')
2011-07-21 21:37:43,169 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e1000', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-07-21 21:37:43,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-21 21:37:43,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'usb:v1058p1021d2002dc00dsc00dp00ic08isc06ip50')
2011-07-21 21:37:43,171 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,171 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,171 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v000010DEd000003ECsv0000103Csd00002A66bc01sc01i8a')
2011-07-21 21:37:43,175 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,175 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-07-21 21:37:43,185 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2011-07-21 21:37:43,202 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-07-21 21:37:43,202 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'usb:v058Fp6377d0100dc00dsc00dp00ic08isc06ip50')
2011-07-21 21:37:43,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'input:b0003v04D9p1702e0110-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,AB,AC,AD,D9,ram4,lsfw')
2011-07-21 21:37:43,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A66bc04sc03i00')
2011-07-21 21:37:43,209 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,210 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.10:bd12/11/2007:svnHP-Pavilion:pnGX615AA-ABAs3300f:pvr:rvnASUSTekComputerINC.:rnAcacia:rvr1.02:cvnHewlett-Packard:ct3:cvrChassisVersion:')
2011-07-21 21:37:43,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-07-21 21:37:43,226 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'usb:v04D9p1702d0101dc00dsc00dp00ic03isc01ip01')
2011-07-21 21:37:43,227 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,227 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,227 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'usb:v04D9p1702d0101dc00dsc00dp00ic03isc00ip00')
2011-07-21 21:37:43,227 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,228 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v000010DEd000003F3sv0000103Csd00002A66bc06sc04i01')
2011-07-21 21:37:43,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-21 21:37:43,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2011-07-21 21:37:43,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'usb:v15A9p0004d0001dc00dsc00dp00icFFiscFFipFF')
2011-07-21 21:37:43,235 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,235 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A66bc0Csc03i20')
2011-07-21 21:37:43,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2011-07-21 21:37:43,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A66bc06sc80i00')
2011-07-21 21:37:43,244 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,244 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-21 21:37:43,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'input:b0011v0002p0005e0055-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2011-07-21 21:37:43,245 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-21 21:37:43,245 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-07-21 21:37:43,246 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A66bc01sc01i85')
2011-07-21 21:37:43,250 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-21 21:37:43,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-21 21:37:43,251 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,251 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2011-07-21 21:37:43,251 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'input:b0003v04D9p1702e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-07-21 21:37:43,252 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 21:37:43,252 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9c5366c> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-07-21 21:37:43,252 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A66bc0Csc05i00')
2011-07-21 21:37:43,252 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-21 21:37:43,252 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-21 21:37:43,252 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A66bc05sc00i00')
2011-07-21 21:37:43,252 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'platform:eisa')
2011-07-21 21:37:43,252 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-07-21 21:37:43,252 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-21 21:37:43,252 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-21 21:37:43,252 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'platform:pcspkr')
2011-07-21 21:37:43,252 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v000010DEd000003D0sv0000103Csd00002A66bc03sc00i00')
2011-07-21 21:37:43,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'platform:regulatory')
2011-07-21 21:37:43,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A66bc05sc00i00')
2011-07-21 21:37:43,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v000011C1d00005811sv0000103Csd00002A66bc0Csc00i10')
2011-07-21 21:37:43,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-21 21:37:43,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A66bc06sc01i00')
2011-07-21 21:37:43,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-07-21 21:37:43,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v00008086d0000107Csv00008086sd00001376bc02sc00i00')
2011-07-21 21:37:43,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-07-21 21:37:43,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-21 21:37:43,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'usb:v1058p1021d2002dc00dsc00dp00ic08isc06ip50')
2011-07-21 21:37:43,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v000010DEd000003ECsv0000103Csd00002A66bc01sc01i8a')
2011-07-21 21:37:43,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-07-21 21:37:43,253 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2011-07-21 21:37:43,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-07-21 21:37:43,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'usb:v058Fp6377d0100dc00dsc00dp00ic08isc06ip50')
2011-07-21 21:37:43,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'input:b0003v04D9p1702e0110-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,AB,AC,AD,D9,ram4,lsfw')
2011-07-21 21:37:43,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A66bc04sc03i00')
2011-07-21 21:37:43,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.10:bd12/11/2007:svnHP-Pavilion:pnGX615AA-ABAs3300f:pvr:rvnASUSTekComputerINC.:rnAcacia:rvr1.02:cvnHewlett-Packard:ct3:cvrChassisVersion:')
2011-07-21 21:37:43,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-07-21 21:37:43,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'usb:v04D9p1702d0101dc00dsc00dp00ic03isc01ip01')
2011-07-21 21:37:43,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'usb:v04D9p1702d0101dc00dsc00dp00ic03isc00ip00')
2011-07-21 21:37:43,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v000010DEd000003F3sv0000103Csd00002A66bc06sc04i01')
2011-07-21 21:37:43,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-21 21:37:43,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2011-07-21 21:37:43,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'usb:v15A9p0004d0001dc00dsc00dp00icFFiscFFipFF')
2011-07-21 21:37:43,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A66bc0Csc03i20')
2011-07-21 21:37:43,254 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2011-07-21 21:37:43,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A66bc06sc80i00')
2011-07-21 21:37:43,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-21 21:37:43,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'input:b0011v0002p0005e0055-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2011-07-21 21:37:43,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-21 21:37:43,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-07-21 21:37:43,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A66bc01sc01i85')
2011-07-21 21:37:43,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-21 21:37:43,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-21 21:37:43,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2011-07-21 21:37:43,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'input:b0003v04D9p1702e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-07-21 21:37:43,255 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9c5342c> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-07-21 21:37:43,331 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:37:43,332 DEBUG: nvidia_173 is not the alternative in use
2011-07-21 21:37:44,467 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:37:44,467 DEBUG: KMH enabled: False
2011-07-21 21:37:45,793 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:37:45,793 DEBUG: nvidia_173 is not the alternative in use
2011-07-21 21:37:45,876 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:37:45,877 DEBUG: nvidia_173 is not the alternative in use
2011-07-21 21:37:45,937 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:37:45,938 DEBUG: KMH enabled: False
2011-07-21 21:37:51,590 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:37:51,590 DEBUG: KMH enabled: False
2011-07-21 21:37:53,451 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:37:53,451 DEBUG: KMH enabled: False
2011-07-21 21:38:00,821 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-07-21 21:38:00,821 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-07-21 21:38:37,555 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:38:37,555 DEBUG: KMH enabled: False
2011-07-21 21:38:37,596 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:38:37,596 DEBUG: KMH enabled: False
2011-07-21 21:38:40,977 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:38:40,977 DEBUG: nvidia_173 is not the alternative in use
2011-07-21 21:38:41,092 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:38:41,093 DEBUG: KMH enabled: False
2011-07-21 21:38:41,165 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:38:41,165 DEBUG: KMH enabled: False
2011-07-21 21:38:41,554 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:38:41,554 DEBUG: KMH enabled: False
2011-07-21 21:38:41,585 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:38:41,585 DEBUG: KMH enabled: False
2011-07-21 21:38:41,668 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:38:41,668 DEBUG: nvidia_173 is not the alternative in use
2011-07-21 21:38:41,729 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:38:41,729 DEBUG: KMH enabled: False
2011-07-21 21:38:41,769 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 21:38:41,769 DEBUG: KMH enabled: False
2011-07-21 21:38:45,697 DEBUG: Shutting down
2011-07-21 22:05:07,842 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c>
2011-07-21 22:05:09,803 DEBUG: reading modalias file /lib/modules/3.0.0-6-generic-pae/modules.alias
2011-07-21 22:05:09,929 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-07-21 22:05:09,937 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-07-21 22:05:09,992 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-07-21 22:05:10,013 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-07-21 22:05:10,072 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-21 22:05:10,076 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-07-21 22:05:10,076 DEBUG: fglrx.available: falling back to default
2011-07-21 22:05:10,195 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-07-21 22:05:10,195 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-07-21 22:05:10,244 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-07-21 22:05:10,244 DEBUG: Firmware for DVB cards not available
2011-07-21 22:05:10,244 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-07-21 22:05:10,262 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-07-21 22:05:10,284 DEBUG: Software modem not available
2011-07-21 22:05:10,284 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-07-21 22:05:10,301 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-07-21 22:05:10,306 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-07-21 22:05:10,306 DEBUG: nvidia.available: falling back to default
2011-07-21 22:05:10,322 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-07-21 22:05:10,322 DEBUG: NVIDIA accelerated graphics driver not available
2011-07-21 22:05:10,326 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-07-21 22:05:10,330 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-07-21 22:05:10,330 DEBUG: nvidia.available: falling back to default
2011-07-21 22:05:10,363 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-21 22:05:10,363 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 957, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-07-21 22:05:10,377 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-07-21 22:05:10,382 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-07-21 22:05:10,382 DEBUG: nvidia.available: falling back to default
2011-07-21 22:05:10,415 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-21 22:05:10,415 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-07-21 22:05:10,419 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-21 22:05:10,436 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-07-21 22:05:10,436 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-07-21 22:05:10,436 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-07-21 22:05:10,441 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-07-21 22:05:10,441 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-07-21 22:05:10,441 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-07-21 22:05:10,441 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-07-21 22:05:10,468 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-07-21 22:05:10,468 DEBUG: Experimental 3D support for NVIDIA cards is available
2011-07-21 22:05:10,468 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-07-21 22:05:10,475 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-07-21 22:05:10,476 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-07-21 22:05:10,492 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-07-21 22:05:10,492 DEBUG: all custom handlers loaded
2011-07-21 22:05:10,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A66bc0Csc05i00')
2011-07-21 22:05:10,928 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:10,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-21 22:05:10,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-21 22:05:10,928 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A66bc05sc00i00')
2011-07-21 22:05:10,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'platform:eisa')
2011-07-21 22:05:10,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-07-21 22:05:10,957 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-21 22:05:10,962 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:10,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-21 22:05:10,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'platform:pcspkr')
2011-07-21 22:05:10,963 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:10,963 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:10,963 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v000010DEd000003D0sv0000103Csd00002A66bc03sc00i00')
2011-07-21 22:05:10,967 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:10,967 DEBUG: got handler xorg:nouveau([Nouveau3DHandler, free, disabled] Experimental 3D support for NVIDIA cards)
2011-07-21 22:05:11,088 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-07-21 22:05:11,092 DEBUG: nvidia.available: falling back to default
2011-07-21 22:05:11,569 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 22:05:11,570 DEBUG: KMH enabled: False
2011-07-21 22:05:11,109 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-07-21 22:05:11,573 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-07-21 22:05:11,577 DEBUG: nvidia.available: falling back to default
2011-07-21 22:05:11,594 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-07-21 22:05:11,618 DEBUG: NVidia(nvidia_96).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 22:05:11,619 DEBUG: nvidia_96 is not the alternative in use
2011-07-21 22:05:11,594 DEBUG: ignoring unavailable handler xorg:nvidia_96([NvidiaDriver96, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-07-21 22:05:11,622 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-07-21 22:05:11,627 DEBUG: nvidia.available: falling back to default
2011-07-21 22:05:11,667 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 22:05:11,668 DEBUG: nvidia_173 is not the alternative in use
2011-07-21 22:05:11,643 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-07-21 22:05:11,668 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'platform:regulatory')
2011-07-21 22:05:11,668 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A66bc05sc00i00')
2011-07-21 22:05:11,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v000011C1d00005811sv0000103Csd00002A66bc0Csc00i10')
2011-07-21 22:05:11,674 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:11,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-21 22:05:11,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A66bc06sc01i00')
2011-07-21 22:05:11,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-07-21 22:05:11,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v00008086d0000107Csv00008086sd00001376bc02sc00i00')
2011-07-21 22:05:12,019 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e1000', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-07-21 22:05:12,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-21 22:05:12,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'usb:v1058p1021d2002dc00dsc00dp00ic08isc06ip50')
2011-07-21 22:05:12,020 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,020 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,020 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v000010DEd000003ECsv0000103Csd00002A66bc01sc01i8a')
2011-07-21 22:05:12,024 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-07-21 22:05:12,034 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,034 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2011-07-21 22:05:12,051 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-07-21 22:05:12,051 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'usb:v058Fp6377d0100dc00dsc00dp00ic08isc06ip50')
2011-07-21 22:05:12,054 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,054 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'input:b0003v04D9p1702e0110-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,AB,AC,AD,D9,ram4,lsfw')
2011-07-21 22:05:12,054 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A66bc04sc03i00')
2011-07-21 22:05:12,058 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,058 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.10:bd12/11/2007:svnHP-Pavilion:pnGX615AA-ABAs3300f:pvr:rvnASUSTekComputerINC.:rnAcacia:rvr1.02:cvnHewlett-Packard:ct3:cvrChassisVersion:')
2011-07-21 22:05:12,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-07-21 22:05:12,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'usb:v04D9p1702d0101dc00dsc00dp00ic03isc01ip01')
2011-07-21 22:05:12,075 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,075 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,075 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'usb:v04D9p1702d0101dc00dsc00dp00ic03isc00ip00')
2011-07-21 22:05:12,076 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,076 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v000010DEd000003F3sv0000103Csd00002A66bc06sc04i01')
2011-07-21 22:05:12,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-21 22:05:12,080 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2011-07-21 22:05:12,081 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'usb:v15A9p0004d0001dc00dsc00dp00icFFiscFFipFF')
2011-07-21 22:05:12,084 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,084 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A66bc0Csc03i20')
2011-07-21 22:05:12,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2011-07-21 22:05:12,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A66bc06sc80i00')
2011-07-21 22:05:12,092 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-21 22:05:12,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'input:b0011v0002p0005e0055-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2011-07-21 22:05:12,093 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-21 22:05:12,093 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-07-21 22:05:12,094 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A66bc01sc01i85')
2011-07-21 22:05:12,098 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,098 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-21 22:05:12,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-21 22:05:12,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2011-07-21 22:05:12,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'input:b0003v04D9p1702e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-07-21 22:05:12,100 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-21 22:05:12,100 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x943266c> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-07-21 22:05:12,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v000010DEd000003EBsv0000103Csd00002A66bc0Csc05i00')
2011-07-21 22:05:12,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-21 22:05:12,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-21 22:05:12,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v000010DEd000003F5sv0000103Csd00002A66bc05sc00i00')
2011-07-21 22:05:12,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'platform:eisa')
2011-07-21 22:05:12,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-07-21 22:05:12,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-21 22:05:12,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-21 22:05:12,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'platform:pcspkr')
2011-07-21 22:05:12,100 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v000010DEd000003D0sv0000103Csd00002A66bc03sc00i00')
2011-07-21 22:05:12,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'platform:regulatory')
2011-07-21 22:05:12,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v000010DEd000003EAsv0000103Csd00002A66bc05sc00i00')
2011-07-21 22:05:12,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v000011C1d00005811sv0000103Csd00002A66bc0Csc00i10')
2011-07-21 22:05:12,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-21 22:05:12,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v000010DEd000003E0sv0000103Csd00002A66bc06sc01i00')
2011-07-21 22:05:12,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-07-21 22:05:12,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v00008086d0000107Csv00008086sd00001376bc02sc00i00')
2011-07-21 22:05:12,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-07-21 22:05:12,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-21 22:05:12,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'usb:v1058p1021d2002dc00dsc00dp00ic08isc06ip50')
2011-07-21 22:05:12,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v000010DEd000003ECsv0000103Csd00002A66bc01sc01i8a')
2011-07-21 22:05:12,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-07-21 22:05:12,101 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2011-07-21 22:05:12,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-07-21 22:05:12,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'usb:v058Fp6377d0100dc00dsc00dp00ic08isc06ip50')
2011-07-21 22:05:12,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'input:b0003v04D9p1702e0110-e0,1,4,k71,72,73,74,80,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,AB,AC,AD,D9,ram4,lsfw')
2011-07-21 22:05:12,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v000010DEd000003F0sv0000103Csd00002A66bc04sc03i00')
2011-07-21 22:05:12,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr5.10:bd12/11/2007:svnHP-Pavilion:pnGX615AA-ABAs3300f:pvr:rvnASUSTekComputerINC.:rnAcacia:rvr1.02:cvnHewlett-Packard:ct3:cvrChassisVersion:')
2011-07-21 22:05:12,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-07-21 22:05:12,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'usb:v04D9p1702d0101dc00dsc00dp00ic03isc01ip01')
2011-07-21 22:05:12,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'usb:v04D9p1702d0101dc00dsc00dp00ic03isc00ip00')
2011-07-21 22:05:12,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v000010DEd000003F3sv0000103Csd00002A66bc06sc04i01')
2011-07-21 22:05:12,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-21 22:05:12,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2011-07-21 22:05:12,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'usb:v15A9p0004d0001dc00dsc00dp00icFFiscFFipFF')
2011-07-21 22:05:12,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v000010DEd000003F2sv0000103Csd00002A66bc0Csc03i20')
2011-07-21 22:05:12,102 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2011-07-21 22:05:12,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v000010DEd000003EFsv0000103Csd00002A66bc06sc80i00')
2011-07-21 22:05:12,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-21 22:05:12,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'input:b0011v0002p0005e0055-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2011-07-21 22:05:12,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-21 22:05:12,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-07-21 22:05:12,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v000010DEd000003F6sv0000103Csd00002A66bc01sc01i85')
2011-07-21 22:05:12,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-21 22:05:12,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-21 22:05:12,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2011-07-21 22:05:12,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'input:b0003v04D9p1702e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-07-21 22:05:12,103 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x943242c> about HardwareID('modalias', 'acpi:PNP0F13:')
2011-07-21 22:05:12,171 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 22:05:12,171 DEBUG: nvidia_173 is not the alternative in use
2011-07-21 22:05:13,249 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 22:05:13,249 DEBUG: KMH enabled: False
2011-07-21 22:05:14,446 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 22:05:14,447 DEBUG: nvidia_173 is not the alternative in use
2011-07-21 22:05:14,505 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 22:05:14,505 DEBUG: nvidia_173 is not the alternative in use
2011-07-21 22:05:14,546 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 22:05:14,546 DEBUG: KMH enabled: False
2011-07-21 22:05:17,521 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 22:05:17,522 DEBUG: KMH enabled: False
2011-07-21 22:05:18,880 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 22:05:18,880 DEBUG: KMH enabled: False
2011-07-21 22:05:23,856 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-07-21 22:05:23,857 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-07-21 22:06:04,430 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 22:06:04,431 DEBUG: KMH enabled: False
2011-07-21 22:06:04,496 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-07-21 22:06:04,496 DEBUG: KMH enabled: False
```

---

### Post by Sworddragon on 2011-07-21
Maybe the nvidia module wasn't build on this version of the kernel (my wasn't too and I needed to build it manually with dkms). What says "dkms status"?

---

### Post by lidex on 2011-07-21
```
ERROR: modinfo: could not find module nvidia_current
```
Worked for me to just re-install it:
```
sudo apt-get install --reinstall nvidia-current
```
**Reboot**

---

### Post by mdhollis on 2011-07-21
> **lidex said:**
> ```
ERROR: modinfo: could not find module nvidia_current
```
Worked for me to just re-install it:
```
sudo apt-get install --reinstall nvidia-current
```
**Reboot**

That was it.  Thanks.

---

### Post by mdhollis on 2011-07-21
> **Sworddragon said:**
> Maybe the nvidia module wasn't build on this version of the kernel (my wasn't too and I needed to build it manually with dkms). What says "dkms status"?

I got an error stating it was missing from the dkms tree.  But re-installing it in the terminal resolved the issue.

---

### Post by Harry33 on 2011-07-22
> **mdhollis said:**
> I got an error stating it was missing from the dkms tree.  But re-installing it in the terminal resolved the issue.

This is a known issue with the kernel 3.0.0.-6.7.
The installation is left without the file /lib/modules/3.0.0-6-generic/updates/dkms/nvidia-current.ko.
Like you said, reinstallation solves this.

---

