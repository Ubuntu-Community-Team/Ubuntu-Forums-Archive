---
title: "jockey fails to install drivers"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by z3nhakr on 2012-07-24
im trying to update my graphics driver (amd proprietary fglrx) but i get this message:
```
Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log
```here's the log. i read it but i still have no idea what went wrong :S

```
2012-07-24 23:31:39,811 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60>
2012-07-24 23:31:41,519 DEBUG: reading modalias file /lib/modules/3.2.0-27-generic/modules.alias
2012-07-24 23:31:41,578 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-07-24 23:31:41,584 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-07-24 23:31:41,638 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-07-24 23:31:41,658 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-07-24 23:31:41,694 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-07-24 23:31:41,694 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-07-24 23:31:41,695 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-07-24 23:31:41,703 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-07-24 23:31:41,703 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-07-24 23:31:41,735 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-07-24 23:31:41,735 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-07-24 23:31:41,791 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-07-24 23:31:41,793 DEBUG: Firmware for DVB cards not available
2012-07-24 23:31:41,793 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-07-24 23:31:41,841 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-07-24 23:31:41,852 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-07-24 23:31:41,853 DEBUG: fglrx.available: falling back to default
2012-07-24 23:31:41,972 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-24 23:31:41,979 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-07-24 23:31:41,990 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-07-24 23:31:41,990 DEBUG: fglrx.available: falling back to default
2012-07-24 23:31:42,052 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-07-24 23:31:42,053 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-07-24 23:31:42,087 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-07-24 23:31:42,113 DEBUG: Software modem not available
2012-07-24 23:31:42,114 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-07-24 23:31:42,128 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-07-24 23:31:42,139 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-07-24 23:31:42,142 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-07-24 23:31:42,142 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-24 23:31:42,149 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-07-24 23:31:42,161 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-07-24 23:31:42,162 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-07-24 23:31:42,162 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-24 23:31:42,169 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-07-24 23:31:42,180 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-07-24 23:31:42,182 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-07-24 23:31:42,182 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-24 23:31:42,188 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-07-24 23:31:42,199 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-07-24 23:31:42,201 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-07-24 23:31:42,201 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-24 23:31:42,208 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-07-24 23:31:42,219 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-07-24 23:31:42,220 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-07-24 23:31:42,220 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-24 23:31:42,227 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-07-24 23:31:42,238 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-07-24 23:31:42,240 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-07-24 23:31:42,240 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-24 23:31:42,240 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-07-24 23:31:42,261 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-07-24 23:31:42,262 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-07-24 23:31:42,263 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-07-24 23:31:42,263 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-07-24 23:31:42,270 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-07-24 23:31:42,282 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-07-24 23:31:42,336 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-07-24 23:31:42,336 DEBUG: all custom handlers loaded
2012-07-24 23:31:42,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-07-24 23:31:42,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-24 23:31:42,350 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:31:42,419 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,419 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-24 23:31:42,419 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,419 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-24 23:31:42,419 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-24 23:31:42,419 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-07-24 23:31:42,577 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-07-24 23:31:42,577 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,577 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'platform:ideapad')
2012-07-24 23:31:42,577 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-24 23:31:42,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,D4,D9,E0,E1,E2,F5,F7,ram4,l0,1,2,sfw')
2012-07-24 23:31:42,585 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:31:42,585 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,585 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-24 23:31:42,585 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-07-24 23:31:42,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-24 23:31:42,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-24 23:31:42,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'platform:acer-wmi')
2012-07-24 23:31:42,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'wmi:431F16ED-0C2B-444C-B267-27DEB140CF9C')
2012-07-24 23:31:42,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'pci:v00001002d00006760sv000017AAsd00003976bc03sc00i00')
2012-07-24 23:31:42,757 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-07-24 23:31:42,779 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:31:42,779 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:31:42,757 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-24 23:31:42,785 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-07-24 23:31:42,796 DEBUG: fglrx.available: falling back to default
2012-07-24 23:31:42,854 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:31:42,854 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:31:42,829 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-24 23:31:42,855 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-07-24 23:31:42,880 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:31:42,880 DEBUG: fglrx is not the alternative in use
2012-07-24 23:31:42,855 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-24 23:31:42,887 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-07-24 23:31:42,898 DEBUG: fglrx.available: falling back to default
2012-07-24 23:31:42,956 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:31:42,957 DEBUG: fglrx is not the alternative in use
2012-07-24 23:31:42,930 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-24 23:31:42,957 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-07-24 23:31:42,958 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,958 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'pci:v00008086d0000008Bsv00008086sd00005315bc02sc80i00')
2012-07-24 23:31:42,967 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi'}
2012-07-24 23:31:42,967 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-24 23:31:42,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-24 23:31:42,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-24 23:31:42,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'pci:v00008086d00000126sv000017AAsd00003976bc03sc00i00')
2012-07-24 23:31:42,974 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2012-07-24 23:31:42,974 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-07-24 23:31:42,976 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-24 23:31:42,976 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,976 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-24 23:31:42,976 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-24 23:31:42,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-07-24 23:31:42,978 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'usb:v5986p030Cd1402dcEFdsc02dp01ic0Eisc02ip00')
2012-07-24 23:31:42,978 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-07-24 23:31:42,979 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:31:42,979 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,979 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-07-24 23:31:42,979 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:31:42,979 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,979 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'acpi:PNP0303:')
2012-07-24 23:31:42,979 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-07-24 23:31:42,981 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-07-24 23:31:42,981 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,981 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-07-24 23:31:42,981 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:31:42,981 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,981 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-24 23:31:42,981 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,981 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-24 23:31:42,981 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr57CN30WW:bd12/05/2011:svnLENOVO:pn09932TU:pvrLenovoIdeaPadU400:rvnLENOVO:rnEmeraldLake:rvrFAB1:cvnLENOVO:ct10:cvr0.1:')
2012-07-24 23:31:42,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-24 23:31:42,990 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-07-24 23:31:42,992 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-07-24 23:31:42,992 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,992 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-07-24 23:31:42,992 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:31:42,992 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,992 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-24 23:31:42,992 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,992 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-07-24 23:31:42,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-07-24 23:31:42,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2012-07-24 23:31:42,997 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-07-24 23:31:42,997 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,997 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'pci:v00008086d00001503sv000017AAsd00003975bc02sc00i00')
2012-07-24 23:31:42,999 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'e1000e'}
2012-07-24 23:31:42,999 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e1000e', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'input:b0003v5986p030Ce1402-e0,1,kD4,ramlsfw')
2012-07-24 23:31:42,999 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:31:42,999 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,999 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-24 23:31:42,999 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:42,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'acpi:CYS0001:PNP0F13:PNP0F03:PNP0F0E:PNP0F0B:PNP0F12:')
2012-07-24 23:31:42,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'wmi:D9F41781-F633-4400-9355-601770BEC510')
2012-07-24 23:31:42,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'acpi:VPC2004:')
2012-07-24 23:31:42,999 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'platform:pcspkr')
2012-07-24 23:31:43,000 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-07-24 23:31:43,000 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:43,000 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-07-24 23:31:43,000 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:43,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-07-24 23:31:43,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2012-07-24 23:31:43,000 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:31:43,000 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:43,000 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-24 23:31:43,000 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:43,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-24 23:31:43,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'usb:v5986p030Cd1402dcEFdsc02dp01ic0Eisc01ip00')
2012-07-24 23:31:43,001 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-07-24 23:31:43,001 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:43,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'wmi:67C3371D-95A3-4C37-BB61-DD47B491DAAB')
2012-07-24 23:31:43,001 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2012-07-24 23:31:43,001 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:43,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'platform:regulatory')
2012-07-24 23:31:43,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-07-24 23:31:43,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-07-24 23:31:43,005 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-07-24 23:31:43,009 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-07-24 23:31:43,009 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:43,009 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-07-24 23:31:43,009 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:43,009 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,E3,EE,F0,ram4,lsfw')
2012-07-24 23:31:43,009 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:31:43,009 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:43,010 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-24 23:31:43,010 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'pci:v00001033d00000194sv000017AAsd00003975bc0Csc03i30')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'wmi:40D1BF71-A82D-4E59-A168-3985E03B2E87')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf91e60> about HardwareID('modalias', 'acpi:INT0800:')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'platform:ideapad')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,D4,D9,E0,E1,E2,F5,F7,ram4,l0,1,2,sfw')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'platform:acer-wmi')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'wmi:431F16ED-0C2B-444C-B267-27DEB140CF9C')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'pci:v00001002d00006760sv000017AAsd00003976bc03sc00i00')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'pci:v00008086d0000008Bsv00008086sd00005315bc02sc80i00')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-24 23:31:43,010 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'pci:v00008086d00000126sv000017AAsd00003976bc03sc00i00')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'usb:v5986p030Cd1402dcEFdsc02dp01ic0Eisc02ip00')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'acpi:PNP0303:')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr57CN30WW:bd12/05/2011:svnLENOVO:pn09932TU:pvrLenovoIdeaPadU400:rvnLENOVO:rnEmeraldLake:rvrFAB1:cvnLENOVO:ct10:cvr0.1:')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'pci:v00008086d00001503sv000017AAsd00003975bc02sc00i00')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'input:b0003v5986p030Ce1402-e0,1,kD4,ramlsfw')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'acpi:CYS0001:PNP0F13:PNP0F03:PNP0F0E:PNP0F0B:PNP0F12:')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'wmi:D9F41781-F633-4400-9355-601770BEC510')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'acpi:VPC2004:')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'platform:pcspkr')
2012-07-24 23:31:43,011 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-07-24 23:31:43,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2012-07-24 23:31:43,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-24 23:31:43,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'usb:v5986p030Cd1402dcEFdsc02dp01ic0Eisc01ip00')
2012-07-24 23:31:43,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'wmi:67C3371D-95A3-4C37-BB61-DD47B491DAAB')
2012-07-24 23:31:43,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'platform:regulatory')
2012-07-24 23:31:43,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-07-24 23:31:43,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-07-24 23:31:43,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-07-24 23:31:43,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,E3,EE,F0,ram4,lsfw')
2012-07-24 23:31:43,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'pci:v00001033d00000194sv000017AAsd00003975bc0Csc03i30')
2012-07-24 23:31:43,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'wmi:40D1BF71-A82D-4E59-A168-3985E03B2E87')
2012-07-24 23:31:43,012 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x13024d0> about HardwareID('modalias', 'acpi:INT0800:')
2012-07-24 23:31:43,101 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:31:43,101 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:31:43,141 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:31:43,141 DEBUG: fglrx is not the alternative in use
2012-07-24 23:31:43,226 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:31:43,227 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:31:43,262 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:31:43,262 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:31:43,277 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:31:43,278 DEBUG: fglrx is not the alternative in use
2012-07-24 23:31:51,615 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:31:51,615 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:31:56,271 DEBUG: _check_polkit_privilege: sender :1.93 on connection <dbus._dbus.SystemBus (system) at 0xed0bf0> pid 9820 is not authorized for com.ubuntu.devicedriver.install: dbus.Dictionary({dbus.String(u'polkit.retains_authorization_after_challenge'): dbus.String(u'true'), dbus.String(u'polkit.dismissed'): dbus.String(u'true')}, signature=dbus.Signature('ss'))
2012-07-24 23:31:59,255 DEBUG: Shutting down
2012-07-24 23:36:41,707 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60>
2012-07-24 23:36:43,445 DEBUG: reading modalias file /lib/modules/3.2.0-27-generic/modules.alias
2012-07-24 23:36:43,517 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-07-24 23:36:43,532 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-07-24 23:36:43,589 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-07-24 23:36:43,630 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-07-24 23:36:43,665 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-07-24 23:36:43,665 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-07-24 23:36:43,665 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-07-24 23:36:43,673 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-07-24 23:36:43,674 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-07-24 23:36:43,715 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-07-24 23:36:43,715 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-07-24 23:36:43,792 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-07-24 23:36:43,793 DEBUG: Firmware for DVB cards not available
2012-07-24 23:36:43,793 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-07-24 23:36:43,843 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-07-24 23:36:43,854 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-07-24 23:36:43,854 DEBUG: fglrx.available: falling back to default
2012-07-24 23:36:44,029 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-07-24 23:36:44,036 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-07-24 23:36:44,046 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-07-24 23:36:44,047 DEBUG: fglrx.available: falling back to default
2012-07-24 23:36:44,109 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-07-24 23:36:44,110 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-07-24 23:36:44,169 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-07-24 23:36:44,204 DEBUG: Software modem not available
2012-07-24 23:36:44,204 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-07-24 23:36:44,249 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-07-24 23:36:44,259 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-07-24 23:36:44,262 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-07-24 23:36:44,263 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-24 23:36:44,269 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-07-24 23:36:44,280 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-07-24 23:36:44,282 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-07-24 23:36:44,282 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-24 23:36:44,289 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-07-24 23:36:44,300 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-07-24 23:36:44,301 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-07-24 23:36:44,301 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-24 23:36:44,308 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-07-24 23:36:44,319 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-07-24 23:36:44,320 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-07-24 23:36:44,321 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-24 23:36:44,327 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-07-24 23:36:44,338 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-07-24 23:36:44,340 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-07-24 23:36:44,340 DEBUG: NVIDIA accelerated graphics driver not available
2012-07-24 23:36:44,346 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-07-24 23:36:44,357 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-07-24 23:36:44,359 DEBUG: Disabling Nvidia driver on intel/hybrid system
2012-07-24 23:36:44,359 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-07-24 23:36:44,359 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-07-24 23:36:44,369 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-07-24 23:36:44,370 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-07-24 23:36:44,371 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-07-24 23:36:44,371 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-07-24 23:36:44,382 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-07-24 23:36:44,394 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-07-24 23:36:44,447 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-07-24 23:36:44,448 DEBUG: all custom handlers loaded
2012-07-24 23:36:44,448 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-07-24 23:36:44,449 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-24 23:36:44,461 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:36:44,563 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:44,563 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-24 23:36:44,563 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:44,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-24 23:36:44,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-24 23:36:44,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-07-24 23:36:44,721 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2012-07-24 23:36:44,721 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:44,721 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'platform:ideapad')
2012-07-24 23:36:44,722 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-24 23:36:44,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,D4,D9,E0,E1,E2,F5,F7,ram4,l0,1,2,sfw')
2012-07-24 23:36:44,730 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:36:44,730 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:44,730 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-24 23:36:44,730 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:44,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-07-24 23:36:44,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-24 23:36:44,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-24 23:36:44,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'platform:acer-wmi')
2012-07-24 23:36:44,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'wmi:431F16ED-0C2B-444C-B267-27DEB140CF9C')
2012-07-24 23:36:44,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'pci:v00001002d00006760sv000017AAsd00003976bc03sc00i00')
2012-07-24 23:36:44,903 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-07-24 23:36:44,979 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:36:44,979 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:36:44,903 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-24 23:36:44,986 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-07-24 23:36:44,997 DEBUG: fglrx.available: falling back to default
2012-07-24 23:36:45,054 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:36:45,055 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:36:45,030 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-07-24 23:36:45,055 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-07-24 23:36:45,079 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:36:45,080 DEBUG: fglrx is not the alternative in use
2012-07-24 23:36:45,055 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-24 23:36:45,086 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-07-24 23:36:45,098 DEBUG: fglrx.available: falling back to default
2012-07-24 23:36:45,155 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:36:45,155 DEBUG: fglrx is not the alternative in use
2012-07-24 23:36:45,129 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-07-24 23:36:45,155 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-07-24 23:36:45,156 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'pci:v00008086d0000008Bsv00008086sd00005315bc02sc80i00')
2012-07-24 23:36:45,165 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi'}
2012-07-24 23:36:45,165 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlwifi', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-24 23:36:45,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-24 23:36:45,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-24 23:36:45,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'pci:v00008086d00000126sv000017AAsd00003976bc03sc00i00')
2012-07-24 23:36:45,173 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2012-07-24 23:36:45,173 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,174 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-07-24 23:36:45,176 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-24 23:36:45,176 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,176 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-07-24 23:36:45,176 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,176 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-24 23:36:45,176 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-07-24 23:36:45,178 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'usb:v5986p030Cd1402dcEFdsc02dp01ic0Eisc02ip00')
2012-07-24 23:36:45,178 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-07-24 23:36:45,178 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:36:45,178 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,178 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-07-24 23:36:45,178 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:36:45,178 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,178 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'acpi:PNP0303:')
2012-07-24 23:36:45,178 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-07-24 23:36:45,180 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2012-07-24 23:36:45,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-07-24 23:36:45,180 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:36:45,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,180 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-24 23:36:45,180 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-24 23:36:45,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr57CN30WW:bd12/05/2011:svnLENOVO:pn09932TU:pvrLenovoIdeaPadU400:rvnLENOVO:rnEmeraldLake:rvrFAB1:cvnLENOVO:ct10:cvr0.1:')
2012-07-24 23:36:45,189 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-24 23:36:45,189 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-07-24 23:36:45,191 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2012-07-24 23:36:45,191 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-07-24 23:36:45,191 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:36:45,191 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,191 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-24 23:36:45,191 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-07-24 23:36:45,192 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-07-24 23:36:45,192 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2012-07-24 23:36:45,196 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-07-24 23:36:45,196 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'pci:v00008086d00001503sv000017AAsd00003975bc02sc00i00')
2012-07-24 23:36:45,198 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'e1000e'}
2012-07-24 23:36:45,198 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e1000e', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'input:b0003v5986p030Ce1402-e0,1,kD4,ramlsfw')
2012-07-24 23:36:45,198 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:36:45,198 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,198 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-24 23:36:45,198 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'acpi:CYS0001:PNP0F13:PNP0F03:PNP0F0E:PNP0F0B:PNP0F12:')
2012-07-24 23:36:45,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'wmi:D9F41781-F633-4400-9355-601770BEC510')
2012-07-24 23:36:45,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'acpi:VPC2004:')
2012-07-24 23:36:45,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'platform:pcspkr')
2012-07-24 23:36:45,199 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-07-24 23:36:45,199 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,199 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-07-24 23:36:45,199 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-07-24 23:36:45,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2012-07-24 23:36:45,199 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:36:45,199 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,199 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-24 23:36:45,199 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-24 23:36:45,199 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'usb:v5986p030Cd1402dcEFdsc02dp01ic0Eisc01ip00')
2012-07-24 23:36:45,199 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-07-24 23:36:45,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'wmi:67C3371D-95A3-4C37-BB61-DD47B491DAAB')
2012-07-24 23:36:45,200 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi'}
2012-07-24 23:36:45,200 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'acer_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'platform:regulatory')
2012-07-24 23:36:45,200 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-07-24 23:36:45,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-07-24 23:36:45,203 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-07-24 23:36:45,208 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-07-24 23:36:45,208 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,208 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-07-24 23:36:45,208 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,208 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,E3,EE,F0,ram4,lsfw')
2012-07-24 23:36:45,208 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-07-24 23:36:45,208 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,208 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-07-24 23:36:45,209 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'pci:v00001033d00000194sv000017AAsd00003975bc0Csc03i30')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'wmi:40D1BF71-A82D-4E59-A168-3985E03B2E87')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x229de60> about HardwareID('modalias', 'acpi:INT0800:')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'acpi:PNP0200:')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'pci:v00008086d00001C3Asv000017AAsd00003975bc07sc80i00')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'platform:ideapad')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,D4,D9,E0,E1,E2,F5,F7,ram4,l0,1,2,sfw')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'acpi:PNP0103:')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'platform:acer-wmi')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'wmi:431F16ED-0C2B-444C-B267-27DEB140CF9C')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'pci:v00001002d00006760sv000017AAsd00003976bc03sc00i00')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'pci:v00008086d0000008Bsv00008086sd00005315bc02sc80i00')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-07-24 23:36:45,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'pci:v00008086d00000126sv000017AAsd00003976bc03sc00i00')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'pci:v00008086d00001C20sv000017AAsd00003975bc04sc03i00')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'pci:v00008086d00001C03sv000017AAsd00003975bc01sc06i01')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'usb:v5986p030Cd1402dcEFdsc02dp01ic0Eisc02ip00')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'acpi:PNP0303:')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'pci:v00008086d00001C49sv000017AAsd00003975bc06sc01i00')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'dmi:bvnLENOVO:bvr57CN30WW:bd12/05/2011:svnLENOVO:pn09932TU:pvrLenovoIdeaPadU400:rvnLENOVO:rnEmeraldLake:rvrFAB1:cvnLENOVO:ct10:cvr0.1:')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'acpi:PNP0100:')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'pci:v00008086d00001C22sv000017AAsd00003975bc0Csc05i00')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'pci:v00008086d00001503sv000017AAsd00003975bc02sc00i00')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'input:b0003v5986p030Ce1402-e0,1,kD4,ramlsfw')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'acpi:CYS0001:PNP0F13:PNP0F03:PNP0F0E:PNP0F0B:PNP0F12:')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'wmi:D9F41781-F633-4400-9355-601770BEC510')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'acpi:VPC2004:')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'platform:pcspkr')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00')
2012-07-24 23:36:45,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'input:b0011v0002p0005e0000-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2012-07-24 23:36:45,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'acpi:PNP0000:')
2012-07-24 23:36:45,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'usb:v5986p030Cd1402dcEFdsc02dp01ic0Eisc01ip00')
2012-07-24 23:36:45,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'wmi:67C3371D-95A3-4C37-BB61-DD47B491DAAB')
2012-07-24 23:36:45,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'platform:regulatory')
2012-07-24 23:36:45,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv000017AAsd00003975bc0Csc03i20')
2012-07-24 23:36:45,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'pci:v00008086d00001C26sv000017AAsd00003975bc0Csc03i20')
2012-07-24 23:36:45,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-07-24 23:36:45,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,E3,EE,F0,ram4,lsfw')
2012-07-24 23:36:45,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'pci:v00001033d00000194sv000017AAsd00003975bc0Csc03i30')
2012-07-24 23:36:45,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'wmi:40D1BF71-A82D-4E59-A168-3985E03B2E87')
2012-07-24 23:36:45,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26124d0> about HardwareID('modalias', 'acpi:INT0800:')
2012-07-24 23:36:45,269 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:36:45,269 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:36:45,334 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:36:45,334 DEBUG: fglrx is not the alternative in use
2012-07-24 23:36:45,386 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:36:45,386 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:36:45,451 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:36:45,451 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:36:45,496 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:36:45,497 DEBUG: fglrx is not the alternative in use
2012-07-24 23:46:13,970 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf
2012-07-24 23:46:13,971 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:46:18,949 DEBUG: Installing package: fglrx-updates
2012-07-24 23:46:19,512 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-07-24 23:46:19,513 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-07-24 23:46:19,544 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-07-24 23:46:19,580 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.000000
2012-07-24 23:46:19,624 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.001486
2012-07-24 23:46:20,126 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.396877
2012-07-24 23:46:20,628 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 0.737406
2012-07-24 23:46:21,129 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.123338
2012-07-24 23:46:21,630 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.548999
2012-07-24 23:46:22,132 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 1.908446
2012-07-24 23:46:22,633 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 2.277352
2012-07-24 23:46:23,134 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 2.684095
2012-07-24 23:46:23,636 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.037866
2012-07-24 23:46:24,137 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.457852
2012-07-24 23:46:24,638 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 3.940268
2012-07-24 23:46:25,140 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.375388
2012-07-24 23:46:25,641 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 4.840777
2012-07-24 23:46:26,034 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.223435
2012-07-24 23:46:26,035 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.224419
2012-07-24 23:46:26,108 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.294087
2012-07-24 23:46:26,108 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.295979
2012-07-24 23:46:26,609 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 5.729207
2012-07-24 23:46:27,111 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.228650
2012-07-24 23:46:27,612 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 6.769712
2012-07-24 23:46:28,113 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.278613
2012-07-24 23:46:28,615 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 7.751570
2012-07-24 23:46:29,116 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 8.203716
2012-07-24 23:46:29,617 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 8.580189
2012-07-24 23:46:30,119 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 8.754237
2012-07-24 23:46:30,620 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 8.990716
2012-07-24 23:46:31,121 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 9.164764
2012-07-24 23:46:31,623 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 9.465564
2012-07-24 23:46:32,124 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 9.785283
2012-07-24 23:46:32,626 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 9.919602
2012-07-24 23:46:33,127 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.154189
2012-07-24 23:46:33,628 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.402018
2012-07-24 23:46:34,130 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.625254
2012-07-24 23:46:34,631 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 10.846597
2012-07-24 23:46:35,133 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.200369
2012-07-24 23:46:35,634 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.573058
2012-07-24 23:46:36,135 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 11.958991
2012-07-24 23:46:36,637 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.418705
2012-07-24 23:46:37,138 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 12.870851
2012-07-24 23:46:37,639 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 13.307863
2012-07-24 23:46:38,141 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 13.720281
2012-07-24 23:46:38,642 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 14.161077
2012-07-24 23:46:39,143 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 14.581062
2012-07-24 23:46:39,645 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 15.016182
2012-07-24 23:46:40,146 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 15.313199
2012-07-24 23:46:40,648 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 15.784263
2012-07-24 23:46:41,149 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 16.204249
2012-07-24 23:46:41,650 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 16.628018
2012-07-24 23:46:42,151 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 16.923143
2012-07-24 23:46:42,652 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.223943
2012-07-24 23:46:43,153 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.573931
2012-07-24 23:46:43,655 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 17.959864
2012-07-24 23:46:44,156 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 18.425253
2012-07-24 23:46:44,657 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 18.983342
2012-07-24 23:46:45,159 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 19.382517
2012-07-24 23:46:45,660 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 19.851690
2012-07-24 23:46:46,161 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.252757
2012-07-24 23:46:46,662 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 20.788144
2012-07-24 23:46:47,164 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 21.102187
2012-07-24 23:46:47,665 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 21.334881
2012-07-24 23:46:48,167 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 21.637574
2012-07-24 23:46:48,668 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 22.169177
2012-07-24 23:46:49,169 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 22.621323
2012-07-24 23:46:49,671 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 23.143467
2012-07-24 23:46:50,172 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 23.661828
2012-07-24 23:46:50,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 24.174512
2012-07-24 23:46:51,175 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 24.670171
2012-07-24 23:46:51,676 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 25.173397
2012-07-24 23:46:52,178 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 25.638786
2012-07-24 23:46:52,679 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.058771
2012-07-24 23:46:53,180 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.387949
2012-07-24 23:46:53,682 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.681182
2012-07-24 23:46:54,183 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 26.942254
2012-07-24 23:46:54,684 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 27.176841
2012-07-24 23:46:55,186 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 27.437913
2012-07-24 23:46:55,687 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 27.697093
2012-07-24 23:46:56,189 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 27.954381
2012-07-24 23:46:56,690 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.223020
2012-07-24 23:46:57,191 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.540847
2012-07-24 23:46:57,693 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.760299
2012-07-24 23:46:58,194 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 28.943806
2012-07-24 23:46:58,695 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.112179
2012-07-24 23:46:59,197 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.237039
2012-07-24 23:46:59,698 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.363792
2012-07-24 23:47:00,199 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.498111
2012-07-24 23:47:00,701 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.634323
2012-07-24 23:47:01,202 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.768642
2012-07-24 23:47:01,704 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 29.912421
2012-07-24 23:47:02,205 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 30.112955
2012-07-24 23:47:02,706 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 30.347541
2012-07-24 23:47:03,208 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 30.542399
2012-07-24 23:47:03,709 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 30.788337
2012-07-24 23:47:04,210 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.060760
2012-07-24 23:47:04,712 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.295346
2012-07-24 23:47:05,213 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.512906
2012-07-24 23:47:05,714 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.739925
2012-07-24 23:47:06,216 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 31.987755
2012-07-24 23:47:06,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.192072
2012-07-24 23:47:07,219 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.383146
2012-07-24 23:47:07,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.560978
2012-07-24 23:47:08,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 32.786105
2012-07-24 23:47:08,723 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.054745
2012-07-24 23:47:09,224 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.173930
2012-07-24 23:47:09,725 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.404732
2012-07-24 23:47:10,227 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.573105
2012-07-24 23:47:10,728 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.730126
2012-07-24 23:47:11,229 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.898499
2012-07-24 23:47:11,731 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 33.998766
2012-07-24 23:47:12,232 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.110384
2012-07-24 23:47:12,733 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.235244
2012-07-24 23:47:13,235 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.365780
2012-07-24 23:47:13,736 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.505775
2012-07-24 23:47:14,238 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.628744
2012-07-24 23:47:14,739 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.795225
2012-07-24 23:47:15,240 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 34.990083
2012-07-24 23:47:15,742 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 35.128186
2012-07-24 23:47:16,243 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 35.317369
2012-07-24 23:47:16,744 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 35.525469
2012-07-24 23:47:17,246 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 35.693842
2012-07-24 23:47:17,747 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 35.862215
2012-07-24 23:47:18,249 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.005993
2012-07-24 23:47:18,750 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.227337
2012-07-24 23:47:19,251 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.380575
2012-07-24 23:47:19,753 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.579217
2012-07-24 23:47:20,254 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.732455
2012-07-24 23:47:20,755 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 36.915962
2012-07-24 23:47:21,257 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.029471
2012-07-24 23:47:21,758 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.171358
2012-07-24 23:47:22,260 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.301894
2012-07-24 23:47:22,761 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.415404
2012-07-24 23:47:23,262 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.574317
2012-07-24 23:47:23,764 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 37.780526
2012-07-24 23:47:24,265 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.001870
2012-07-24 23:47:24,767 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.168351
2012-07-24 23:47:25,268 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.391586
2012-07-24 23:47:25,770 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.654550
2012-07-24 23:47:26,271 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 38.843733
2012-07-24 23:47:26,773 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.044266
2012-07-24 23:47:27,274 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.214531
2012-07-24 23:47:27,775 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.466143
2012-07-24 23:47:28,277 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.715864
2012-07-24 23:47:28,778 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 39.899372
2012-07-24 23:47:29,279 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.009097
2012-07-24 23:47:29,781 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.130174
2012-07-24 23:47:30,282 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.347734
2012-07-24 23:47:30,783 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.648535
2012-07-24 23:47:31,285 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 40.941768
2012-07-24 23:47:31,786 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 41.221758
2012-07-24 23:47:32,287 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 41.532018
2012-07-24 23:47:32,789 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 41.736335
2012-07-24 23:47:33,290 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 41.982272
2012-07-24 23:47:33,791 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 42.301991
2012-07-24 23:47:34,293 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 42.563063
2012-07-24 23:47:34,794 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 42.810892
2012-07-24 23:47:35,296 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.079531
2012-07-24 23:47:35,797 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.384115
2012-07-24 23:47:36,298 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.650863
2012-07-24 23:47:36,800 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 43.887341
2012-07-24 23:47:37,301 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 44.138954
2012-07-24 23:47:37,802 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 44.432187
2012-07-24 23:47:38,304 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 44.710286
2012-07-24 23:47:38,805 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 44.977033
2012-07-24 23:47:39,306 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 45.243780
2012-07-24 23:47:39,808 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 45.525663
2012-07-24 23:47:40,309 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 45.815112
2012-07-24 23:47:40,810 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 46.089427
2012-07-24 23:47:41,312 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 46.361850
2012-07-24 23:47:41,813 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 46.622922
2012-07-24 23:47:42,314 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 46.901020
2012-07-24 23:47:42,816 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.188578
2012-07-24 23:47:43,317 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.462893
2012-07-24 23:47:43,818 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.631265
2012-07-24 23:47:44,320 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 47.945308
2012-07-24 23:47:44,821 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 48.213948
2012-07-24 23:47:45,322 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 48.463669
2012-07-24 23:47:45,824 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 48.751226
2012-07-24 23:47:46,325 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 49.025541
2012-07-24 23:47:46,827 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 49.233642
2012-07-24 23:47:47,328 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 49.506065
2012-07-24 23:47:47,829 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 49.736868
2012-07-24 23:47:48,331 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 49.986589
2012-07-24 23:47:48,832 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.173879
2012-07-24 23:47:49,334 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.461437
2012-07-24 23:47:49,835 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.682781
2012-07-24 23:47:50,336 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 50.907908
2012-07-24 23:47:50,838 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 51.212492
2012-07-24 23:47:51,339 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 51.443295
2012-07-24 23:47:51,840 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 51.662747
2012-07-24 23:47:52,342 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 51.940845
2012-07-24 23:47:52,843 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.182999
2012-07-24 23:47:53,344 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.453530
2012-07-24 23:47:53,846 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 52.739196
2012-07-24 23:47:54,347 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 53.000268
2012-07-24 23:47:54,849 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 53.242422
2012-07-24 23:47:55,350 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 53.490251
2012-07-24 23:47:55,851 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 53.681325
2012-07-24 23:47:56,353 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 53.895102
2012-07-24 23:47:56,854 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 54.097527
2012-07-24 23:47:57,356 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 54.379409
2012-07-24 23:47:57,857 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 54.596969
2012-07-24 23:47:58,358 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 54.863717
2012-07-24 23:47:58,860 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 55.122897
2012-07-24 23:47:59,361 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 55.382077
2012-07-24 23:47:59,863 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 55.626122
2012-07-24 23:48:00,364 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 55.820981
2012-07-24 23:48:00,865 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.038541
2012-07-24 23:48:01,367 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.297721
2012-07-24 23:48:01,868 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.543658
2012-07-24 23:48:02,370 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 56.825540
2012-07-24 23:48:02,871 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 57.103639
2012-07-24 23:48:03,372 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 57.398764
2012-07-24 23:48:03,874 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 57.631458
2012-07-24 23:48:04,375 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 57.830100
2012-07-24 23:48:04,876 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 58.204682
2012-07-24 23:48:05,378 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 58.526292
2012-07-24 23:48:05,879 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 58.770338
2012-07-24 23:48:06,380 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.018167
2012-07-24 23:48:06,882 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.284914
2012-07-24 23:48:07,383 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.559229
2012-07-24 23:48:07,885 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 59.784356
2012-07-24 23:48:08,386 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.035969
2012-07-24 23:48:08,887 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.325419
2012-07-24 23:48:09,389 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.609193
2012-07-24 23:48:09,890 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 60.809726
2012-07-24 23:48:10,391 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.010260
2012-07-24 23:48:10,893 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.176740
2012-07-24 23:48:11,394 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.377274
2012-07-24 23:48:11,896 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.596726
2012-07-24 23:48:12,397 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.787800
2012-07-24 23:48:12,898 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 61.995901
2012-07-24 23:48:13,400 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 62.256973
2012-07-24 23:48:13,901 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 62.519937
2012-07-24 23:48:14,402 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 62.775334
2012-07-24 23:48:14,904 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.025055
2012-07-24 23:48:15,405 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.223696
2012-07-24 23:48:15,907 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.488552
2012-07-24 23:48:16,408 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.677735
2012-07-24 23:48:16,909 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 63.885836
2012-07-24 23:48:17,411 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.086369
2012-07-24 23:48:17,912 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.285011
2012-07-24 23:48:18,413 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.464734
2012-07-24 23:48:18,915 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.659592
2012-07-24 23:48:19,416 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 64.886612
2012-07-24 23:48:19,917 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 65.104172
2012-07-24 23:48:20,419 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 65.282003
2012-07-24 23:48:20,920 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 65.495780
2012-07-24 23:48:21,422 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 65.694421
2012-07-24 23:48:21,923 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 65.900630
2012-07-24 23:48:22,424 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 66.104948
2012-07-24 23:48:22,926 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 66.350885
2012-07-24 23:48:23,427 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 66.627092
2012-07-24 23:48:23,929 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 66.873029
2012-07-24 23:48:24,430 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 67.088697
2012-07-24 23:48:24,931 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 67.294906
2012-07-24 23:48:25,433 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 67.576788
2012-07-24 23:48:25,934 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 67.860562
2012-07-24 23:48:26,435 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 68.115959
2012-07-24 23:48:26,937 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 68.350545
2012-07-24 23:48:27,438 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 68.611617
2012-07-24 23:48:27,939 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 68.885932
2012-07-24 23:48:28,441 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 69.143220
2012-07-24 23:48:28,957 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 69.389158
2012-07-24 23:48:29,458 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 69.638879
2012-07-24 23:48:29,959 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 69.905626
2012-07-24 23:48:30,460 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 70.187508
2012-07-24 23:48:30,962 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 70.435338
2012-07-24 23:48:31,463 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 70.633979
2012-07-24 23:48:31,965 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 70.825054
2012-07-24 23:48:32,466 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 71.014236
2012-07-24 23:48:32,968 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 71.201527
2012-07-24 23:48:33,469 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 71.413412
2012-07-24 23:48:33,971 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 71.612054
2012-07-24 23:48:34,472 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 71.875017
2012-07-24 23:48:34,973 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 72.170142
2012-07-24 23:48:35,475 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 72.385810
2012-07-24 23:48:35,976 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 72.637423
2012-07-24 23:48:36,477 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 72.889036
2012-07-24 23:48:36,979 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 73.123623
2012-07-24 23:48:37,480 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 73.405505
2012-07-24 23:48:37,981 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 73.660901
2012-07-24 23:48:38,483 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 73.899271
2012-07-24 23:48:38,984 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 74.150884
2012-07-24 23:48:39,486 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 74.385471
2012-07-24 23:48:39,987 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 74.627624
2012-07-24 23:48:40,488 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 74.898156
2012-07-24 23:48:40,990 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.104365
2012-07-24 23:48:41,491 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.388139
2012-07-24 23:48:41,993 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.645427
2012-07-24 23:48:42,494 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 75.938660
2012-07-24 23:48:42,995 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 76.260270
2012-07-24 23:48:43,497 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 76.513775
2012-07-24 23:48:43,998 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 76.670797
2012-07-24 23:48:44,500 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 76.903491
2012-07-24 23:48:45,001 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 77.166455
2012-07-24 23:48:45,502 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 77.380232
2012-07-24 23:48:46,004 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 77.658330
2012-07-24 23:48:46,505 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 77.883457
2012-07-24 23:48:47,007 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 78.127503
2012-07-24 23:48:47,508 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 78.348847
2012-07-24 23:48:48,009 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 78.598568
2012-07-24 23:48:48,511 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 78.891801
2012-07-24 23:48:49,012 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 79.171791
2012-07-24 23:48:49,513 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 79.459348
2012-07-24 23:48:50,015 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 79.720420
2012-07-24 23:48:50,516 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 79.955007
2012-07-24 23:48:51,017 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.240673
2012-07-24 23:48:51,519 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.501745
2012-07-24 23:48:52,020 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 80.802545
2012-07-24 23:48:52,521 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 81.124156
2012-07-24 23:48:53,023 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 81.396578
2012-07-24 23:48:53,524 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 81.642516
2012-07-24 23:48:54,026 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 81.975477
2012-07-24 23:48:54,527 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 82.272494
2012-07-24 23:48:55,029 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 82.567619
2012-07-24 23:48:55,530 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 82.877878
2012-07-24 23:48:56,032 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.152193
2012-07-24 23:48:56,533 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.386780
2012-07-24 23:48:57,034 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.657311
2012-07-24 23:48:57,536 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 83.956219
2012-07-24 23:48:58,037 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.222967
2012-07-24 23:48:58,538 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.546469
2012-07-24 23:48:59,040 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 84.826459
2012-07-24 23:48:59,541 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 85.138611
2012-07-24 23:49:00,042 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 85.448870
2012-07-24 23:49:00,544 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 85.738320
2012-07-24 23:49:01,045 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.035336
2012-07-24 23:49:01,546 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.330461
2012-07-24 23:49:02,048 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.635045
2012-07-24 23:49:02,549 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 86.839362
2012-07-24 23:49:03,051 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.123136
2012-07-24 23:49:03,552 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.374749
2012-07-24 23:49:04,053 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.639605
2012-07-24 23:49:04,554 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 87.883650
2012-07-24 23:49:05,056 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 88.127696
2012-07-24 23:49:05,557 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 88.354715
2012-07-24 23:49:06,059 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 88.630922
2012-07-24 23:49:06,560 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 88.910912
2012-07-24 23:49:07,061 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 89.187119
2012-07-24 23:49:07,562 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 89.470893
2012-07-24 23:49:08,064 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 89.745207
2012-07-24 23:49:08,565 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 89.960876
2012-07-24 23:49:09,067 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.182219
2012-07-24 23:49:09,568 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.403563
2012-07-24 23:49:10,069 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.662743
2012-07-24 23:49:10,571 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 90.925707
2012-07-24 23:49:11,072 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.175428
2012-07-24 23:49:11,574 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.387312
2012-07-24 23:49:12,075 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.665411
2012-07-24 23:49:12,577 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 91.926483
2012-07-24 23:49:13,078 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.174312
2012-07-24 23:49:13,245 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.260303
2012-07-24 23:49:13,246 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.260303
2012-07-24 23:49:13,282 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.260303
2012-07-24 23:49:13,328 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.261788
2012-07-24 23:49:13,829 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.452863
2012-07-24 23:49:14,330 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.727177
2012-07-24 23:49:14,831 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 92.939062
2012-07-24 23:49:15,332 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.186891
2012-07-24 23:49:15,834 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.444180
2012-07-24 23:49:16,335 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.678766
2012-07-24 23:49:16,836 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 93.909569
2012-07-24 23:49:17,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 94.142263
2012-07-24 23:49:17,839 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 94.365499
2012-07-24 23:49:18,340 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 94.617112
2012-07-24 23:49:18,842 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 94.864941
2012-07-24 23:49:19,343 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.131688
2012-07-24 23:49:19,844 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.324655
2012-07-24 23:49:20,346 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.555458
2012-07-24 23:49:20,847 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.744640
2012-07-24 23:49:21,349 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 95.996253
2012-07-24 23:49:21,850 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.208138
2012-07-24 23:49:22,352 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.438940
2012-07-24 23:49:22,853 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.690553
2012-07-24 23:49:23,355 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 96.928923
2012-07-24 23:49:23,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.154051
2012-07-24 23:49:24,357 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.371611
2012-07-24 23:49:24,859 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.568361
2012-07-24 23:49:25,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.763219
2012-07-24 23:49:25,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 97.918348
2012-07-24 23:49:26,362 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 98.132125
2012-07-24 23:49:26,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 98.353468
2012-07-24 23:49:27,365 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 98.599406
2012-07-24 23:49:27,866 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 98.790480
2012-07-24 23:49:28,368 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 99.011824
2012-07-24 23:49:28,869 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 99.218033
2012-07-24 23:49:29,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 99.437485
2012-07-24 23:49:29,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 99.655045
2012-07-24 23:49:30,373 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 99.900982
2012-07-24 23:49:30,618 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16895L> 100.000000
2012-07-24 23:49:31,825 DEBUG: install progress dpkg-exec 0.000000
2012-07-24 23:49:34,518 DEBUG: install progress libc6-i386 0.000000
2012-07-24 23:49:34,619 DEBUG: install progress libc6-i386 5.000000
2012-07-24 23:49:35,249 DEBUG: install progress libc6-i386 10.000000
2012-07-24 23:49:35,315 DEBUG: install progress libc6-i386 15.000000
2012-07-24 23:49:35,705 DEBUG: install progress lib32gcc1 15.000000
2012-07-24 23:49:35,805 DEBUG: install progress lib32gcc1 20.000000
2012-07-24 23:49:35,922 DEBUG: install progress lib32gcc1 25.000000
2012-07-24 23:49:35,994 DEBUG: install progress lib32gcc1 30.000000
2012-07-24 23:49:36,411 DEBUG: install progress fglrx-updates 30.000000
2012-07-24 23:49:36,511 DEBUG: install progress fglrx-updates 35.000000
2012-07-24 23:49:40,756 DEBUG: install progress fglrx-updates 40.000000
2012-07-24 23:49:40,822 DEBUG: install progress fglrx-updates 45.000000
2012-07-24 23:49:41,077 DEBUG: install progress fglrx-amdcccle-updates 45.000000
2012-07-24 23:49:41,178 DEBUG: install progress fglrx-amdcccle-updates 50.000000
2012-07-24 23:49:41,623 DEBUG: install progress fglrx-amdcccle-updates 55.000000
2012-07-24 23:49:41,688 DEBUG: install progress fglrx-amdcccle-updates 60.000000
2012-07-24 23:49:41,761 DEBUG: install progress ureadahead 60.000000
2012-07-24 23:49:42,127 DEBUG: install progress dpkg-exec 60.000000
2012-07-24 23:49:42,163 DEBUG: install progress libc6-i386 60.000000
2012-07-24 23:49:42,323 DEBUG: install progress libc6-i386 65.000000
2012-07-24 23:49:42,457 DEBUG: install progress libc6-i386 70.000000
2012-07-24 23:49:42,635 DEBUG: install progress lib32gcc1 70.000000
2012-07-24 23:49:42,701 DEBUG: install progress lib32gcc1 75.000000
2012-07-24 23:49:42,813 DEBUG: install progress lib32gcc1 80.000000
2012-07-24 23:49:42,902 DEBUG: install progress fglrx-updates 80.000000
2012-07-24 23:49:43,238 DEBUG: install progress fglrx-updates 85.000000
2012-07-24 23:50:19,650 DEBUG: install progress fglrx-updates 90.000000
2012-07-24 23:50:19,995 DEBUG: install progress bamfdaemon 90.000000
2012-07-24 23:50:20,240 DEBUG: install progress fglrx-amdcccle-updates 90.000000
2012-07-24 23:50:20,329 DEBUG: install progress fglrx-amdcccle-updates 95.000000
2012-07-24 23:50:20,407 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2012-07-24 23:50:20,485 DEBUG: install progress libc-bin 100.000000
2012-07-24 23:50:20,752 DEBUG: install progress initramfs-tools 100.000000
2012-07-24 23:50:35,795 DEBUG: Selecting previously unselected package libc6-i386.
(Reading database ... 273240 files and directories currently installed.)
Unpacking libc6-i386 (from .../libc6-i386_2.15-0ubuntu10_amd64.deb) ...
Replaced by files in installed package libc6:i386 ...
Selecting previously unselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package fglrx-updates.
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.960-0ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libc6-i386 (2.15-0ubuntu10) ...
Setting up lib32gcc1 (1:4.6.3-1ubuntu5) ...
Setting up fglrx-updates (2:8.960-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.960 DKMS files...
Building only for 3.2.0-27-generic
Building for architecture x86_64
Building initial module for 3.2.0-27-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-27-generic/updates/dkms/

depmod........

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic

2012-07-24 23:50:36,015 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-07-24 23:50:54,025 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-24 23:50:54,025 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:50:54,056 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-24 23:50:54,056 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:51:12,130 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-24 23:51:12,130 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:51:12,161 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-24 23:51:12,162 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:51:12,217 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-24 23:51:12,217 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-07-24 23:51:12,277 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-24 23:51:12,278 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:51:12,309 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-24 23:51:12,309 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:51:12,389 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-24 23:51:12,390 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:51:12,420 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-24 23:51:12,421 DEBUG: fglrx_updates is not the alternative in use
2012-07-24 23:51:12,472 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-07-24 23:51:12,473 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
```Help me please!!?

---

### Post by QIII on 2012-07-25
Sometimes, inexplicably, jockey it fails.

In the ATI driver wiki in my signature, I have an example of how to do it from the command line.  Look in the table of contents for

"Using the Ubuntu repositories (alternate command line method, including hardware acceleration)"

You may also be interested in 

"Manually installing Catalyst 12.6"

which someone else prepared and tested.

---

### Post by z3nhakr on 2012-07-25
ok i'll try that. btw there were 2 drivers. the post release updates. the other one installed fine but it's got a bug so i need the newer one.

---

### Post by QIII on 2012-07-25
The fglrx-updates version sometimes does not work, so be careful. That seems to have been the one you attempted to install and that may have been part of the problem.   I have still not gotten the Catalyst Control Center to work properly -- fglrx-amdcccle-updates.

What "bug" have you encountered?

---

### Post by waynefoutz on 2012-07-25
> **z3nhakr said:**
> ok i'll try that. btw there were 2 drivers. the post release updates. the other one installed fine but it's got a bug so i need the newer one.

I've never had any luck with the post-release driver in jockey. If you want the latest ATI driver, your best bet is to install it manually from AMD's website. Just make sure you purge out the one that jockey faileed to install first.

---

### Post by z3nhakr on 2012-07-25
i followed the instructions on the link but it installed the normal drivers that i already could install via jockey. also when i was following those instructions, the output of "vainfo" was ```
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Intel i965 driver - 1.0.15
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileH264Baseline           :    VAEntrypointVLD
      VAProfileH264Baseline           :    VAEntrypointEncSlice
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointEncSlice
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointEncSlice
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD

```

the driver is intel. how can i change this from my intel card to my amd card?

---

### Post by waynefoutz on 2012-07-25
Intel drivers are built into the kernel. They are installed "out of the box." Only Nvidia and ATI have proprietary drivers. If you have an Intel GPU, there's nothing else to do after the initial install.

---

### Post by Bufeu on 2012-07-25
Why install proprietary drivers? It's only causes problems, moreover its source code is closed. I've always run the open source drivers, and I have never encountered problems.

---

### Post by QIII on 2012-07-25
> **Bufeu said:**
> Why install proprietary drivers? It's only causes problems, moreover its source code is closed. I've always run the open source drivers, and I have never encountered problems.

The drivers do not generally cause problems.

There are times when the proprietary driver is needed.  Alhough the open source drivers are very good, they can not always take advantage of all of a card's features.

Others may have different needs than you.

---

### Post by QIII on 2012-07-25
@z3nhakr:

Do you have hybrid Intel/ATI graphics?

---

### Post by z3nhakr on 2012-07-25
> **Bufeu said:**
> Why install proprietary drivers? It's only causes problems, moreover its source code is closed. I've always run the open source drivers, and I have never encountered problems.

do the open source drivers support 3d hardware acceleration? if so where can i find these?

---

### Post by z3nhakr on 2012-07-25
> **QIII said:**
> @z3nhakr:

Do you have hybrid Intel/ATI graphics?

yep *fp*

---

### Post by Bufeu on 2012-07-25
> **z3nhakr said:**
> do the open source drivers support 3d hardware acceleration? if so where can i find these?[http://linux.about.com/od/ubuntu_doc/a/ubudg19t4.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg19t4.htm)

---

### Post by QIII on 2012-07-25
> **z3nhakr said:**
> yep *fp*

Then you have a tough row to hoe.  This is a problem for both nVIDIA and ATI.

There is a thread on the forums with a subject line something like "Hybrid Intel/ATI graphics works!". It should be noted that it worked for the OP, but not for a lot of people who have left posts in the thread.

Hybrid ATI/ATI I can help you with.  Multiple discrete ATI  graphics I can help you with.

This, unfortunately not.

---

### Post by z3nhakr on 2012-07-25
ok well thanks for trying. one thing, is it actually hybrid? or are there two individual cards, one intel and one amd?

---

### Post by z3nhakr on 2012-07-25
> **Bufeu said:**
> [http://linux.about.com/od/ubuntu_doc/a/ubudg19t4.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg19t4.htm)

says it's working but vainfo says the acceleration is on my intel card. i want it on my amd card. do you know how i can switch it to the amd card?

---

### Post by QIII on 2012-07-25
You may be able to "hack" switchable graphics if your bios allows you to selectively disable your integrated graphics and enable the discrete (and vice versa), but that would have to be done through the BIOS each time.  The discrete graphics card will consume more power than the integrated, which is why switchable graphics are used in many notebooks.

If you can switch to discrete graphics only via BIOS, switch and reboot.

Check vainfo again.  If it is good on the ATI card, then you are good.

If not, try reinstalling the acceleration packages.  You may get a couple of "already the latest package" messages, but that should be OK.

---

### Post by z3nhakr on 2012-07-26
nope my bios is too locked up

---

### Post by z3nhakr on 2012-07-26
can i install the post release updates without jockey?

---

