---
title: "FGLRX problem"
date: 2011-07-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Vrroom on 2011-07-05
I am getting this error whenever I try to install fglrx drivers from jockey : SystemError: installArchives() failed

Running sudo dpkg --configure -a gives this output:


```

Setting up fglrx (2:8.861-0ubuntu2) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: error: unable to make /usr/lib/dri/fglrx_dri.so.dpkg-tmp a symlink to /etc/alternatives/i386-linux-gnu_fglrx_dri: No such file or directory
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
```Haven't tried anything else but any idea what's the issue?

---

### Post by Harry33 on 2011-07-05
> **Vrroom said:**
> I am getting this error whenever I try to install fglrx drivers from jockey : SystemError: installArchives() failed
Running sudo dpkg --configure -a gives this output:
...
Haven't tried anything else but any idea what's the issue?

This is the issue:
 unable to make /usr/lib/dri/fglrx_dri.so.dpkg-tmp a symlink to /etc/alternatives/i386-linux-gnu_fglrx_dri: No such file or directory

It may be because of the mesa packages you are using.
You should use mesa packages from the Oneiric repos, not from any PPA.
If this is the case, correct it.
Then try to install fglrx with Synaptic.
Print here any error messages you may get.

---

### Post by rbrick49 on 2011-07-06
I have the same problem Harry and I am using oneiric repos maybe its an 86x64 problemo as kubuntu oneiric is giving me the same problem I will go back in later and check the errors
regards Ron

---

### Post by P-I H on 2011-07-06
Installation of fglrx hasn't worked for me for some time.
Last time Jockey crashed and I made a bug report, bug 805553.
This was however marked as a duplicate of the private bug 804709.

---

### Post by Vrroom on 2011-07-06
> **Harry33 said:**
> This is the issue:
 unable to make /usr/lib/dri/fglrx_dri.so.dpkg-tmp a symlink to /etc/alternatives/i386-linux-gnu_fglrx_dri: No such file or directory

It may be because of the mesa packages you are using.
You should use mesa packages from the Oneiric repos, not from any PPA.
If this is the case, correct it.
Then try to install fglrx with Synaptic.
Print here any error messages you may get.

Not using any PPA. I have mesa installed from OO repos. I thought this could be a multi arch problem as according to recent jockey changelog some multi arch problem with fglrx has been fixed. But this seems not to be the case as I am getting this error even after the update.

---

### Post by rbrick49 on 2011-07-06
kubuntu oneiric is giving me the same grief

---

### Post by jfernyhough on 2011-07-06
You could try adding the xorg-edgers PPA and updating - there are a number of updates to mesa that might fix the problem (I'm running with it and it's working fine at the minute).

---

### Post by rbrick49 on 2011-07-06
```
2011-07-07 02:16:02,525 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8>
2011-07-07 02:16:04,180 DEBUG: reading modalias file /lib/modules/3.0-2-generic/modules.alias
2011-07-07 02:16:04,312 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-07-07 02:16:04,313 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-07-07 02:16:04,383 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-07-07 02:16:04,404 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-07-07 02:16:04,424 DEBUG: Software modem not available
2011-07-07 02:16:04,425 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-07-07 02:16:04,472 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-07-07 02:16:04,478 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-07-07 02:16:04,478 DEBUG: nvidia.available: falling back to default
2011-07-07 02:16:04,557 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-07-07 02:16:04,558 DEBUG: NVIDIA accelerated graphics driver not available
2011-07-07 02:16:04,564 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-07-07 02:16:04,571 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-07-07 02:16:04,571 DEBUG: nvidia.available: falling back to default
2011-07-07 02:16:04,622 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-07 02:16:04,622 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 947, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-07-07 02:16:04,645 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-07-07 02:16:04,653 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-07-07 02:16:04,653 DEBUG: nvidia.available: falling back to default
2011-07-07 02:16:04,704 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-07 02:16:04,705 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-07-07 02:16:04,712 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-07 02:16:04,738 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-07-07 02:16:04,738 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-07-07 02:16:04,738 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-07-07 02:16:04,747 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-07 02:16:04,755 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-07-07 02:16:04,755 DEBUG: fglrx.available: falling back to default
2011-07-07 02:16:04,806 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-07-07 02:16:04,806 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-07-07 02:16:04,869 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-07-07 02:16:04,870 DEBUG: Firmware for DVB cards not available
2011-07-07 02:16:04,871 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-07-07 02:16:04,883 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-07-07 02:16:04,885 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-07-07 02:16:04,885 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-07-07 02:16:04,885 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-07-07 02:16:04,974 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-07-07 02:16:04,975 DEBUG: Experimental 3D support for NVIDIA cards not available
2011-07-07 02:16:04,976 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-07-07 02:16:04,987 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-07-07 02:16:04,988 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-07-07 02:16:05,036 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-07-07 02:16:05,037 DEBUG: all custom handlers loaded
2011-07-07 02:16:05,037 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-07 02:16:05,037 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'input:b0003v046DpC526e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-07-07 02:16:05,202 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:05,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'acpi:PNP0501:')
2011-07-07 02:16:05,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-07 02:16:05,203 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000082C6bc02sc00i00')
2011-07-07 02:16:05,216 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:05,217 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-07 02:16:05,217 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-07-07 02:16:05,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-07 02:16:05,243 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:05,243 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2011-07-07 02:16:05,274 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:05,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2011-07-07 02:16:05,276 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:05,276 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:05,276 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-07 02:16:05,276 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'platform:pcspkr')
2011-07-07 02:16:05,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:05,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:05,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-07-07 02:16:05,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'pci:v00001022d00009600sv00001043sd000082EEbc06sc00i00')
2011-07-07 02:16:05,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2011-07-07 02:16:05,295 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:05,295 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:05,295 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-07-07 02:16:05,295 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-07 02:16:05,295 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'pci:v00001002d00006719sv00001043sd000003BAbc03sc00i00')
2011-07-07 02:16:05,648 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-07 02:16:05,654 DEBUG: fglrx.available: falling back to default
2011-07-07 02:16:06,138 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-07-07 02:16:06,139 DEBUG: fglrx is not the alternative in use
2011-07-07 02:16:05,674 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-07-07 02:16:06,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd000082EFbc01sc01i8a')
2011-07-07 02:16:06,152 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-07 02:16:06,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2011-07-07 02:16:06,154 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2011-07-07 02:16:06,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic01isc01ip00')
2011-07-07 02:16:06,158 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'usb:v04E8p343Dd0100dc00dsc00dp00ic07isc01ip02')
2011-07-07 02:16:06,196 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,197 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-07-07 02:16:06,221 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,221 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-07-07 02:16:06,222 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'acpi:PNP0400:')
2011-07-07 02:16:06,222 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-07-07 02:16:06,233 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'input:b0003v046Dp0809e0010-e0,1,kD4,ramlsfw')
2011-07-07 02:16:06,234 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,234 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr2601:bd06/28/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM3A78-CM:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-07-07 02:16:06,276 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'acpi:PNP0700:')
2011-07-07 02:16:06,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'usb:v046DpC526d0500dc00dsc00dp00ic03isc00ip00')
2011-07-07 02:16:06,279 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2011-07-07 02:16:06,280 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-07-07 02:16:06,280 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,281 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'usb:v04E8p343Dd0100dc00dsc00dp00icFFiscFFipFF')
2011-07-07 02:16:06,281 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-07-07 02:16:06,282 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic0Eisc01ip00')
2011-07-07 02:16:06,283 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,283 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd000082EFbc0Csc03i20')
2011-07-07 02:16:06,287 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'input:b0003v046DpC526e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-07-07 02:16:06,288 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,288 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-07 02:16:06,288 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd000082EFbc01sc06i01')
2011-07-07 02:16:06,293 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,293 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'usb:v046DpC526d0500dc00dsc00dp00ic03isc01ip02')
2011-07-07 02:16:06,294 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,294 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'acpi:PNP0800:')
2011-07-07 02:16:06,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic01isc02ip00')
2011-07-07 02:16:06,295 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'pci:v00001002d0000AA80sv00001043sd0000AA80bc04sc03i00')
2011-07-07 02:16:06,300 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-07 02:16:06,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic0Eisc02ip00')
2011-07-07 02:16:06,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-07 02:16:06,302 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2011-07-07 02:16:06,302 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,302 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'pci:v00001002d00004385sv00001043sd000082EFbc0Csc05i00')
2011-07-07 02:16:06,307 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,307 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,307 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd000082EFbc06sc01i00')
2011-07-07 02:16:06,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-07 02:16:06,312 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,312 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,312 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-07-07 02:16:06,313 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,313 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd000082EAbc04sc03i00')
2011-07-07 02:16:06,317 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,318 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 02:16:06,318 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x11312d8> about HardwareID('modalias', 'acpi:PNP0103:')
2011-07-07 02:16:06,318 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-07 02:16:06,318 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'input:b0003v046DpC526e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-07-07 02:16:06,318 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'acpi:PNP0501:')
2011-07-07 02:16:06,318 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-07 02:16:06,318 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000082C6bc02sc00i00')
2011-07-07 02:16:06,318 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-07 02:16:06,318 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-07-07 02:16:06,319 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-07 02:16:06,319 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2011-07-07 02:16:06,319 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2011-07-07 02:16:06,319 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-07 02:16:06,319 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'platform:pcspkr')
2011-07-07 02:16:06,319 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-07-07 02:16:06,319 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'pci:v00001022d00009600sv00001043sd000082EEbc06sc00i00')
2011-07-07 02:16:06,319 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2011-07-07 02:16:06,319 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-07-07 02:16:06,320 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-07 02:16:06,320 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'pci:v00001002d00006719sv00001043sd000003BAbc03sc00i00')
2011-07-07 02:16:06,320 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd000082EFbc01sc01i8a')
2011-07-07 02:16:06,320 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-07 02:16:06,320 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2011-07-07 02:16:06,320 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2011-07-07 02:16:06,320 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic01isc01ip00')
2011-07-07 02:16:06,320 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'usb:v04E8p343Dd0100dc00dsc00dp00ic07isc01ip02')
2011-07-07 02:16:06,320 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-07-07 02:16:06,321 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-07-07 02:16:06,321 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'acpi:PNP0400:')
2011-07-07 02:16:06,321 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-07-07 02:16:06,321 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'input:b0003v046Dp0809e0010-e0,1,kD4,ramlsfw')
2011-07-07 02:16:06,321 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr2601:bd06/28/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM3A78-CM:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-07-07 02:16:06,321 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'acpi:PNP0700:')
2011-07-07 02:16:06,321 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'usb:v046DpC526d0500dc00dsc00dp00ic03isc00ip00')
2011-07-07 02:16:06,321 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2011-07-07 02:16:06,321 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-07-07 02:16:06,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'usb:v04E8p343Dd0100dc00dsc00dp00icFFiscFFipFF')
2011-07-07 02:16:06,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-07-07 02:16:06,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic0Eisc01ip00')
2011-07-07 02:16:06,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd000082EFbc0Csc03i20')
2011-07-07 02:16:06,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'input:b0003v046DpC526e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-07-07 02:16:06,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-07 02:16:06,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd000082EFbc01sc06i01')
2011-07-07 02:16:06,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'usb:v046DpC526d0500dc00dsc00dp00ic03isc01ip02')
2011-07-07 02:16:06,322 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'acpi:PNP0800:')
2011-07-07 02:16:06,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic01isc02ip00')
2011-07-07 02:16:06,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'pci:v00001002d0000AA80sv00001043sd0000AA80bc04sc03i00')
2011-07-07 02:16:06,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-07 02:16:06,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic0Eisc02ip00')
2011-07-07 02:16:06,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-07 02:16:06,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2011-07-07 02:16:06,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'pci:v00001002d00004385sv00001043sd000082EFbc0Csc05i00')
2011-07-07 02:16:06,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd000082EFbc06sc01i00')
2011-07-07 02:16:06,323 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-07 02:16:06,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-07-07 02:16:06,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd000082EAbc04sc03i00')
2011-07-07 02:16:06,324 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x16f8b00> about HardwareID('modalias', 'acpi:PNP0103:')
2011-07-07 02:16:06,383 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-07-07 02:16:06,384 DEBUG: fglrx is not the alternative in use
2011-07-07 02:16:06,489 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-07-07 02:16:06,489 DEBUG: fglrx is not the alternative in use
2011-07-07 02:16:06,559 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-07-07 02:16:06,560 DEBUG: fglrx is not the alternative in use
2011-07-07 02:16:09,696 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-07-07 02:16:09,696 DEBUG: fglrx is not the alternative in use
2011-07-07 02:16:18,576 DEBUG: Installing package: fglrx
2011-07-07 02:16:18,949 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.000000
2011-07-07 02:16:18,951 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.000000
2011-07-07 02:16:19,452 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.000000
2011-07-07 02:16:19,953 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.000000
2011-07-07 02:16:20,455 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.000000
2011-07-07 02:16:20,956 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.000000
2011-07-07 02:16:21,254 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.000000
2011-07-07 02:16:21,276 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.000000
2011-07-07 02:16:21,778 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.000000
2011-07-07 02:16:22,279 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.000000
2011-07-07 02:16:22,780 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.000000
2011-07-07 02:16:23,282 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.000000
2011-07-07 02:16:23,605 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.000000
2011-07-07 02:16:24,106 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.059386
2011-07-07 02:16:24,607 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.178157
2011-07-07 02:16:24,642 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.190634
2011-07-07 02:16:24,652 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.190634
2011-07-07 02:16:24,653 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.190634
2011-07-07 02:16:25,155 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.251420
2011-07-07 02:16:25,476 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.360375
2011-07-07 02:16:25,477 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.360375
2011-07-07 02:16:25,479 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.360375
2011-07-07 02:16:25,980 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.514146
2011-07-07 02:16:26,419 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.618416
2011-07-07 02:16:26,419 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.620352
2011-07-07 02:16:26,921 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.754834
2011-07-07 02:16:27,422 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.854833
2011-07-07 02:16:27,923 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 0.944488
2011-07-07 02:16:28,425 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 1.113452
2011-07-07 02:16:28,926 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 1.147935
2011-07-07 02:16:29,428 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 1.282417
2011-07-07 02:16:29,930 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 1.372071
2011-07-07 02:16:30,431 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 1.513449
2011-07-07 02:16:30,932 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 1.616897
2011-07-07 02:16:31,434 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 1.758275
2011-07-07 02:16:31,935 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 1.892757
2011-07-07 02:16:32,437 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 2.044480
2011-07-07 02:16:32,938 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 2.141031
2011-07-07 02:16:33,439 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 2.265168
2011-07-07 02:16:33,940 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 2.392754
2011-07-07 02:16:34,442 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 2.437581
2011-07-07 02:16:34,943 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 2.527235
2011-07-07 02:16:35,445 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 2.627235
2011-07-07 02:16:35,946 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 2.723786
2011-07-07 02:16:36,447 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 2.803095
2011-07-07 02:16:36,949 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 2.861716
2011-07-07 02:16:37,450 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 2.941026
2011-07-07 02:16:37,952 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 3.006542
2011-07-07 02:16:38,453 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 3.075507
2011-07-07 02:16:38,955 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 3.134128
2011-07-07 02:16:39,456 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 3.199644
2011-07-07 02:16:39,957 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 3.265161
2011-07-07 02:16:40,459 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 3.334126
2011-07-07 02:16:40,960 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 3.389298
2011-07-07 02:16:41,462 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 3.451367
2011-07-07 02:16:41,963 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 3.523780
2011-07-07 02:16:42,464 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 3.589297
2011-07-07 02:16:42,966 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 3.654814
2011-07-07 02:16:43,467 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 3.730675
2011-07-07 02:16:43,969 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 3.803088
2011-07-07 02:16:44,470 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 3.861709
2011-07-07 02:16:44,971 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 3.937570
2011-07-07 02:16:45,473 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 4.013432
2011-07-07 02:16:45,974 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 4.054811
2011-07-07 02:16:46,476 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 4.141017
2011-07-07 02:16:46,977 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 4.206534
2011-07-07 02:16:47,478 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 4.268602
2011-07-07 02:16:47,980 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 4.375498
2011-07-07 02:16:48,482 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 4.434118
2011-07-07 02:16:48,983 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 4.541014
2011-07-07 02:16:49,484 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 4.565152
2011-07-07 02:16:49,986 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 4.661703
2011-07-07 02:16:50,487 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 4.734116
2011-07-07 02:16:50,989 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 4.865150
2011-07-07 02:16:51,490 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 4.951356
2011-07-07 02:16:51,992 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 5.078941
2011-07-07 02:16:52,493 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 5.241009
2011-07-07 02:16:52,995 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 5.385836
2011-07-07 02:16:53,496 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 5.516869
2011-07-07 02:16:53,998 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 5.651351
2011-07-07 02:16:54,499 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 5.761695
2011-07-07 02:16:55,001 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 5.927211
2011-07-07 02:16:55,502 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 6.054797
2011-07-07 02:16:56,004 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 6.209968
2011-07-07 02:16:56,505 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 6.306519
2011-07-07 02:16:57,006 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 6.441001
2011-07-07 02:16:57,508 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 6.530655
2011-07-07 02:16:58,009 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 6.613413
2011-07-07 02:16:58,511 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 6.716861
2011-07-07 02:16:59,012 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 6.792722
2011-07-07 02:16:59,513 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 6.885825
2011-07-07 02:17:00,015 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 6.937549
2011-07-07 02:17:00,517 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 7.013411
2011-07-07 02:17:01,020 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 7.072031
2011-07-07 02:17:01,521 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 7.130651
2011-07-07 02:17:02,023 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 7.223754
2011-07-07 02:17:02,524 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 7.265133
2011-07-07 02:17:03,026 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 7.327201
2011-07-07 02:17:03,527 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 7.406511
2011-07-07 02:17:04,029 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 7.475476
2011-07-07 02:17:04,531 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 7.540993
2011-07-07 02:17:05,032 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 7.616855
2011-07-07 02:17:05,533 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 7.678923
2011-07-07 02:17:06,035 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 7.782371
2011-07-07 02:17:06,537 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 7.830646
2011-07-07 02:17:07,038 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 7.916852
2011-07-07 02:17:07,539 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 7.940990
2011-07-07 02:17:08,041 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 8.013403
2011-07-07 02:17:08,542 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 8.099610
2011-07-07 02:17:09,044 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 8.158230
2011-07-07 02:17:09,545 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 8.303057
2011-07-07 02:17:10,047 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 8.447883
2011-07-07 02:17:10,548 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 8.596158
2011-07-07 02:17:11,049 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 8.744433
2011-07-07 02:17:11,551 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 8.903052
2011-07-07 02:17:12,053 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 9.037534
2011-07-07 02:17:12,554 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 9.151326
2011-07-07 02:17:13,055 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 9.268567
2011-07-07 02:17:13,557 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 9.361670
2011-07-07 02:17:14,058 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 9.544427
2011-07-07 02:17:14,560 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 9.620289
2011-07-07 02:17:15,061 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 9.754771
2011-07-07 02:17:15,563 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 9.837529
2011-07-07 02:17:16,064 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 9.985803
2011-07-07 02:17:16,565 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 10.058217
2011-07-07 02:17:17,067 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 10.175457
2011-07-07 02:17:17,568 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 10.334077
2011-07-07 02:17:18,070 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 10.458214
2011-07-07 02:17:18,571 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 10.540972
2011-07-07 02:17:19,073 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 10.661661
2011-07-07 02:17:19,575 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 10.778901
2011-07-07 02:17:20,077 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 10.830625
2011-07-07 02:17:20,578 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 10.958210
2011-07-07 02:17:21,080 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 11.054761
2011-07-07 02:17:21,581 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 11.130623
2011-07-07 02:17:22,082 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 11.196140
2011-07-07 02:17:22,584 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 11.258208
2011-07-07 02:17:23,085 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 11.347863
2011-07-07 02:17:23,587 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 11.406483
2011-07-07 02:17:24,088 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 11.465103
2011-07-07 02:17:24,589 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 11.530620
2011-07-07 02:17:25,091 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 11.589240
2011-07-07 02:17:25,592 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 11.689240
2011-07-07 02:17:26,094 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 11.747860
2011-07-07 02:17:26,595 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 11.803032
2011-07-07 02:17:27,096 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 11.882342
2011-07-07 02:17:27,597 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 11.958203
2011-07-07 02:17:28,099 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 12.006479
2011-07-07 02:17:28,600 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 12.106478
2011-07-07 02:17:29,101 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 12.168547
2011-07-07 02:17:29,603 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 12.203029
2011-07-07 02:17:30,105 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 12.278891
2011-07-07 02:17:30,620 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 12.368545
2011-07-07 02:17:31,122 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 12.423717
2011-07-07 02:17:31,624 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 12.489234
2011-07-07 02:17:32,125 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 12.592682
2011-07-07 02:17:32,626 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 12.623716
2011-07-07 02:17:33,128 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 12.809921
2011-07-07 02:17:33,629 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 12.930610
2011-07-07 02:17:34,131 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 13.040954
2011-07-07 02:17:34,632 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 13.223712
2011-07-07 02:17:35,133 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 13.330607
2011-07-07 02:17:35,635 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 13.468537
2011-07-07 02:17:36,136 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 13.640950
2011-07-07 02:17:36,638 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 13.727156
2011-07-07 02:17:37,139 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 13.868535
2011-07-07 02:17:37,641 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 13.992672
2011-07-07 02:17:38,142 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 14.092671
2011-07-07 02:17:38,643 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 14.192670
2011-07-07 02:17:39,145 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 14.292669
2011-07-07 02:17:39,646 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 14.385772
2011-07-07 02:17:40,148 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 14.447841
2011-07-07 02:17:40,649 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 14.558185
2011-07-07 02:17:41,151 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 14.620253
2011-07-07 02:17:41,652 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 14.658184
2011-07-07 02:17:42,154 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 14.744390
2011-07-07 02:17:42,655 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 14.827148
2011-07-07 02:17:43,156 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 14.871976
2011-07-07 02:17:43,657 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 14.958182
2011-07-07 02:17:44,159 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 15.037492
2011-07-07 02:17:44,660 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 15.106457
2011-07-07 02:17:45,162 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 15.161629
2011-07-07 02:17:45,663 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 15.206456
2011-07-07 02:17:46,164 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 15.292662
2011-07-07 02:17:46,666 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 15.334041
2011-07-07 02:17:47,167 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 15.444386
2011-07-07 02:17:47,668 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 15.458179
2011-07-07 02:17:48,169 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 15.523695
2011-07-07 02:17:48,671 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 15.634039
2011-07-07 02:17:49,172 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 15.706453
2011-07-07 02:17:49,673 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 15.751280
2011-07-07 02:17:50,175 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 15.871969
2011-07-07 02:17:50,677 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 15.892658
2011-07-07 02:17:51,178 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 16.003002
2011-07-07 02:17:51,680 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 16.071967
2011-07-07 02:17:52,181 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 16.147829
2011-07-07 02:17:52,683 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 16.251276
2011-07-07 02:17:53,184 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 16.313345
2011-07-07 02:17:53,685 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 16.482309
2011-07-07 02:17:54,187 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 16.644377
2011-07-07 02:17:54,688 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 16.740928
2011-07-07 02:17:55,190 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 16.902996
2011-07-07 02:17:55,691 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 17.047822
2011-07-07 02:17:56,193 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 17.158167
2011-07-07 02:17:56,694 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 17.213339
2011-07-07 02:17:57,196 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 17.371958
2011-07-07 02:17:57,697 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 17.509888
2011-07-07 02:17:58,198 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 17.592646
2011-07-07 02:17:58,700 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 17.744369
2011-07-07 02:17:59,201 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 17.875403
2011-07-07 02:17:59,702 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 17.940920
2011-07-07 02:18:00,204 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 18.065057
2011-07-07 02:18:00,705 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 18.182297
2011-07-07 02:18:01,207 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 18.292641
2011-07-07 02:18:01,708 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 18.340917
2011-07-07 02:18:02,209 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 18.544364
2011-07-07 02:18:02,710 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 18.613329
2011-07-07 02:18:03,212 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 18.747810
2011-07-07 02:18:03,713 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 18.871948
2011-07-07 02:18:04,214 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 18.968499
2011-07-07 02:18:04,716 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 19.082291
2011-07-07 02:18:05,217 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 19.175394
2011-07-07 02:18:05,719 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 19.268496
2011-07-07 02:18:06,220 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 19.371944
2011-07-07 02:18:06,722 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 19.416771
2011-07-07 02:18:07,223 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 19.544357
2011-07-07 02:18:07,725 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 19.616770
2011-07-07 02:18:08,226 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 19.699528
2011-07-07 02:18:08,728 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 19.802975
2011-07-07 02:18:09,229 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 19.882285
2011-07-07 02:18:09,730 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 19.954698
2011-07-07 02:18:10,232 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 20.071939
2011-07-07 02:18:10,733 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 20.168490
2011-07-07 02:18:11,235 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 20.309868
2011-07-07 02:18:11,736 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 20.434005
2011-07-07 02:18:12,238 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 20.606418
2011-07-07 02:18:12,739 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 20.713314
2011-07-07 02:18:13,241 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 20.878830
2011-07-07 02:18:13,742 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 21.040898
2011-07-07 02:18:14,244 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 21.120207
2011-07-07 02:18:14,745 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 21.275379
2011-07-07 02:18:15,246 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 21.427102
2011-07-07 02:18:15,748 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 21.565032
2011-07-07 02:18:16,249 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 21.702962
2011-07-07 02:18:16,751 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 21.792617
2011-07-07 02:18:17,252 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 21.954684
2011-07-07 02:18:17,754 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 22.027098
2011-07-07 02:18:18,255 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 22.154683
2011-07-07 02:18:18,756 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 22.271923
2011-07-07 02:18:19,258 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 22.368475
2011-07-07 02:18:19,759 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 22.451233
2011-07-07 02:18:20,261 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 22.558128
2011-07-07 02:18:20,762 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 22.633990
2011-07-07 02:18:21,263 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 22.740886
2011-07-07 02:18:21,765 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 22.754679
2011-07-07 02:18:22,266 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 22.882264
2011-07-07 02:18:22,768 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 22.999505
2011-07-07 02:18:23,269 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 23.061573
2011-07-07 02:18:23,771 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 23.147779
2011-07-07 02:18:24,272 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 23.258123
2011-07-07 02:18:24,773 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 23.316744
2011-07-07 02:18:25,275 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 23.423639
2011-07-07 02:18:25,776 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 23.458122
2011-07-07 02:18:26,278 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 23.551225
2011-07-07 02:18:26,779 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 23.596052
2011-07-07 02:18:27,281 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 23.702948
2011-07-07 02:18:27,782 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 23.816740
2011-07-07 02:18:28,284 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 23.889153
2011-07-07 02:18:28,785 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 23.999498
2011-07-07 02:18:29,286 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 24.116738
2011-07-07 02:18:29,788 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 24.271909
2011-07-07 02:18:30,289 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 24.399495
2011-07-07 02:18:30,791 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 24.544321
2011-07-07 02:18:31,292 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 24.627079
2011-07-07 02:18:31,793 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 24.771906
2011-07-07 02:18:32,295 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 24.965008
2011-07-07 02:18:32,796 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 25.058111
2011-07-07 02:18:33,298 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 25.199489
2011-07-07 02:18:33,799 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 25.265006
2011-07-07 02:18:34,301 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 25.385695
2011-07-07 02:18:34,802 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 25.544314
2011-07-07 02:18:35,303 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 25.616727
2011-07-07 02:18:35,805 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 25.685692
2011-07-07 02:18:36,306 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 25.758106
2011-07-07 02:18:36,808 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 25.816726
2011-07-07 02:18:37,309 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 25.899484
2011-07-07 02:18:37,811 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 25.982242
2011-07-07 02:18:38,312 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 26.030518
2011-07-07 02:18:38,813 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 26.096034
2011-07-07 02:18:39,314 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 26.182241
2011-07-07 02:18:39,816 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 26.264999
2011-07-07 02:18:40,317 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 26.320171
2011-07-07 02:18:40,819 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 26.399481
2011-07-07 02:18:41,320 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 26.475342
2011-07-07 02:18:41,822 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 26.533962
2011-07-07 02:18:42,323 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 26.606376
2011-07-07 02:18:42,824 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 26.668444
2011-07-07 02:18:43,325 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 26.761547
2011-07-07 02:18:43,827 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 26.833960
2011-07-07 02:18:44,328 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 26.906374
2011-07-07 02:18:44,830 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 26.996028
2011-07-07 02:18:45,331 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 27.071890
2011-07-07 02:18:45,832 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 27.137406
2011-07-07 02:18:46,334 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 27.223613
2011-07-07 02:18:46,835 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 27.340853
2011-07-07 02:18:47,337 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 27.451197
2011-07-07 02:18:47,838 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 27.585679
2011-07-07 02:18:48,339 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 27.723609
2011-07-07 02:18:48,841 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 27.899470
2011-07-07 02:18:49,342 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 28.009814
2011-07-07 02:18:49,844 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 28.147744
2011-07-07 02:18:50,345 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 28.306364
2011-07-07 02:18:50,846 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 28.447742
2011-07-07 02:18:51,348 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 28.609810
2011-07-07 02:18:51,849 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 28.713257
2011-07-07 02:18:52,351 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 28.889118
2011-07-07 02:18:52,852 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 28.985669
2011-07-07 02:18:53,354 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 29.154634
2011-07-07 02:18:53,855 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 29.309805
2011-07-07 02:18:54,356 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 29.423597
2011-07-07 02:18:54,858 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 29.589113
2011-07-07 02:18:55,359 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 29.751181
2011-07-07 02:18:55,861 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 29.858077
2011-07-07 02:18:56,362 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 30.013248
2011-07-07 02:18:56,864 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 30.137385
2011-07-07 02:18:57,365 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 30.230488
2011-07-07 02:18:57,866 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 30.333936
2011-07-07 02:18:58,368 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 30.475314
2011-07-07 02:18:58,869 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 30.561520
2011-07-07 02:18:59,371 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 30.696002
2011-07-07 02:18:59,872 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 30.758070
2011-07-07 02:19:00,374 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 30.885656
2011-07-07 02:19:00,875 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 30.933931
2011-07-07 02:19:01,377 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 31.047724
2011-07-07 02:19:01,878 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 31.061517
2011-07-07 02:19:02,379 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 31.168412
2011-07-07 02:19:02,880 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 31.258067
2011-07-07 02:19:03,382 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 31.327032
2011-07-07 02:19:03,883 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 31.413238
2011-07-07 02:19:04,384 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 31.461514
2011-07-07 02:19:04,885 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 31.516686
2011-07-07 02:19:05,387 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 31.602892
2011-07-07 02:19:05,888 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 31.633926
2011-07-07 02:19:06,389 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 31.713236
2011-07-07 02:19:06,890 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 31.823580
2011-07-07 02:19:07,392 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 31.975303
2011-07-07 02:19:07,893 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 32.071854
2011-07-07 02:19:08,395 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 32.240819
2011-07-07 02:19:08,896 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 32.347714
2011-07-07 02:19:09,398 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 32.527023
2011-07-07 02:19:09,899 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 32.630471
2011-07-07 02:19:10,401 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 32.764953
2011-07-07 02:19:10,902 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 32.882193
2011-07-07 02:19:11,403 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 33.030468
2011-07-07 02:19:11,904 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 33.092537
2011-07-07 02:19:12,406 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 33.216674
2011-07-07 02:19:12,907 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 33.285639
2011-07-07 02:19:13,408 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 33.451155
2011-07-07 02:19:13,910 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 33.520120
2011-07-07 02:19:14,411 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 33.654602
2011-07-07 02:19:14,913 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 33.727015
2011-07-07 02:19:15,414 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 33.920117
2011-07-07 02:19:15,916 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 34.027013
2011-07-07 02:19:16,417 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 34.127012
2011-07-07 02:19:16,918 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 34.282184
2011-07-07 02:19:17,420 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 34.464941
2011-07-07 02:19:17,921 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 34.533906
2011-07-07 02:19:18,423 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 34.699422
2011-07-07 02:19:18,924 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 34.823559
2011-07-07 02:19:19,426 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 34.958041
2011-07-07 02:19:19,928 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 35.092523
2011-07-07 02:19:20,429 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 35.213211
2011-07-07 02:19:20,930 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 35.382176
2011-07-07 02:19:21,432 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 35.492520
2011-07-07 02:19:21,933 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 35.582174
2011-07-07 02:19:22,435 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 35.723553
2011-07-07 02:19:22,936 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 35.789069
2011-07-07 02:19:23,437 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 35.920103
2011-07-07 02:19:23,939 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 36.020102
2011-07-07 02:19:24,440 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 36.099412
2011-07-07 02:19:24,941 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 36.161481
2011-07-07 02:19:25,443 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 36.258032
2011-07-07 02:19:25,945 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 36.364927
2011-07-07 02:19:26,446 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 36.430444
2011-07-07 02:19:26,948 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 36.502857
2011-07-07 02:19:27,449 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 36.602857
2011-07-07 02:19:27,951 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 36.671822
2011-07-07 02:19:28,452 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 36.747683
2011-07-07 02:19:28,954 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 36.799407
2011-07-07 02:19:29,455 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 36.882165
2011-07-07 02:19:29,957 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 36.989061
2011-07-07 02:19:30,458 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 37.078715
2011-07-07 02:19:30,959 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 37.192508
2011-07-07 02:19:31,461 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 37.313197
2011-07-07 02:19:31,962 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 37.389058
2011-07-07 02:19:32,463 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 37.571815
2011-07-07 02:19:32,965 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 37.720090
2011-07-07 02:19:33,466 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 37.847676
2011-07-07 02:19:33,968 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 37.964916
2011-07-07 02:19:34,469 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 38.085605
2011-07-07 02:19:34,970 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 38.213190
2011-07-07 02:19:35,472 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 38.385603
2011-07-07 02:19:35,973 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 38.509740
2011-07-07 02:19:36,475 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 38.626980
2011-07-07 02:19:36,976 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 38.740773
2011-07-07 02:19:37,477 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 38.889048
2011-07-07 02:19:37,979 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 38.940771
2011-07-07 02:19:38,481 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 39.099391
2011-07-07 02:19:38,982 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 39.213183
2011-07-07 02:19:39,483 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 39.351113
2011-07-07 02:19:39,985 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 39.437320
2011-07-07 02:19:40,486 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 39.513181
2011-07-07 02:19:40,988 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 39.637318
2011-07-07 02:19:41,489 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 39.685594
2011-07-07 02:19:41,991 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 39.799386
2011-07-07 02:19:42,492 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 39.875247
2011-07-07 02:19:42,994 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 39.923523
2011-07-07 02:19:43,495 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 40.044212
2011-07-07 02:19:43,996 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 40.120073
2011-07-07 02:19:44,497 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 40.199383
2011-07-07 02:19:44,999 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 40.320072
2011-07-07 02:19:45,500 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 40.461450
2011-07-07 02:19:46,002 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 40.595932
2011-07-07 02:19:46,503 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 40.730414
2011-07-07 02:19:47,005 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 40.899378
2011-07-07 02:19:47,506 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 40.989033
2011-07-07 02:19:48,007 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 41.126963
2011-07-07 02:19:48,509 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 41.313168
2011-07-07 02:19:49,010 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 41.399375
2011-07-07 02:19:49,512 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 41.568339
2011-07-07 02:19:50,013 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 41.737303
2011-07-07 02:19:50,515 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 41.864889
2011-07-07 02:19:51,016 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 41.995922
2011-07-07 02:19:51,518 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 42.130404
2011-07-07 02:19:52,019 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 42.251093
2011-07-07 02:19:52,520 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 42.406264
2011-07-07 02:19:53,022 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 42.554539
2011-07-07 02:19:53,523 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 42.702814
2011-07-07 02:19:54,025 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 42.844192
2011-07-07 02:19:54,526 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 42.961433
2011-07-07 02:19:55,028 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 43.071777
2011-07-07 02:19:55,529 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 43.178672
2011-07-07 02:19:56,030 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 43.271775
2011-07-07 02:19:56,532 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 43.409705
2011-07-07 02:19:57,033 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 43.485567
2011-07-07 02:19:57,535 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 43.571773
2011-07-07 02:19:58,036 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 43.616600
2011-07-07 02:19:58,537 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 43.740737
2011-07-07 02:19:59,039 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 43.816599
2011-07-07 02:19:59,540 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 43.913150
2011-07-07 02:20:00,042 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 43.992460
2011-07-07 02:20:00,543 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 44.082114
2011-07-07 02:20:01,044 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 44.171769
2011-07-07 02:20:01,545 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 44.261423
2011-07-07 02:20:02,047 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 44.295906
2011-07-07 02:20:02,548 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 44.382112
2011-07-07 02:20:03,050 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 44.471767
2011-07-07 02:20:03,551 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 44.554525
2011-07-07 02:20:04,052 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 44.623490
2011-07-07 02:20:04,554 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 44.716593
2011-07-07 02:20:05,055 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 44.778661
2011-07-07 02:20:05,556 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 44.854523
2011-07-07 02:20:06,058 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 44.926936
2011-07-07 02:20:06,559 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 44.989004
2011-07-07 02:20:07,060 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 45.061418
2011-07-07 02:20:07,562 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 45.133831
2011-07-07 02:20:08,063 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 45.189003
2011-07-07 02:20:08,565 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 45.299347
2011-07-07 02:20:09,066 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 45.382105
2011-07-07 02:20:09,568 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 45.444174
2011-07-07 02:20:10,069 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 45.516587
2011-07-07 02:20:10,570 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 45.582104
2011-07-07 02:20:11,072 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 45.626931
2011-07-07 02:20:11,573 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 45.726930
2011-07-07 02:20:12,075 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 45.816585
2011-07-07 02:20:12,576 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 45.892446
2011-07-07 02:20:13,077 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 45.964860
2011-07-07 02:20:13,579 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 46.020032
2011-07-07 02:20:14,080 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 46.126927
2011-07-07 02:20:14,582 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 46.171755
2011-07-07 02:20:15,083 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 46.292444
2011-07-07 02:20:15,585 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 46.464856
2011-07-07 02:20:16,086 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 46.588993
2011-07-07 02:20:16,588 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 46.720027
2011-07-07 02:20:17,089 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 46.823474
2011-07-07 02:20:17,591 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 46.985542
2011-07-07 02:20:18,092 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 47.061404
2011-07-07 02:20:18,593 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 47.185541
2011-07-07 02:20:19,095 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 47.264850
2011-07-07 02:20:19,596 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 47.368298
2011-07-07 02:20:20,098 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 47.451056
2011-07-07 02:20:20,599 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 47.520021
2011-07-07 02:20:21,100 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 47.592434
2011-07-07 02:20:21,602 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 47.688985
2011-07-07 02:20:22,103 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 47.751054
2011-07-07 02:20:22,605 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 47.854501
2011-07-07 02:20:23,107 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 47.923466
2011-07-07 02:20:23,608 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 47.982087
2011-07-07 02:20:24,109 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 48.061397
2011-07-07 02:20:24,611 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 48.130362
2011-07-07 02:20:25,113 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 48.233809
2011-07-07 02:20:25,614 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 48.299326
2011-07-07 02:20:26,116 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 48.402773
2011-07-07 02:20:26,617 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 48.471738
2011-07-07 02:20:27,119 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 48.585531
2011-07-07 02:20:27,620 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 48.616565
2011-07-07 02:20:28,121 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 48.726909
2011-07-07 02:20:28,623 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 48.823460
2011-07-07 02:20:29,124 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 48.920011
2011-07-07 02:20:29,626 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 48.999321
2011-07-07 02:20:30,127 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 49.109665
2011-07-07 02:20:30,629 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 49.206216
2011-07-07 02:20:31,130 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 49.306215
2011-07-07 02:20:31,631 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 49.416559
2011-07-07 02:20:32,133 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 49.588972
2011-07-07 02:20:32,634 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 49.716557
2011-07-07 02:20:33,136 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 49.809660
2011-07-07 02:20:33,637 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 49.992417
2011-07-07 02:20:34,139 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 50.102761
2011-07-07 02:20:34,640 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 50.216554
2011-07-07 02:20:35,141 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 50.354484
2011-07-07 02:20:35,643 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 50.485517
2011-07-07 02:20:36,144 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 50.585517
2011-07-07 02:20:36,646 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 50.682068
2011-07-07 02:20:37,147 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 50.744136
2011-07-07 02:20:37,649 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 50.888963
2011-07-07 02:20:38,150 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 51.006203
2011-07-07 02:20:38,651 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 51.123444
2011-07-07 02:20:39,153 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 51.219995
2011-07-07 02:20:39,654 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 51.278615
2011-07-07 02:20:40,155 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 51.419994
2011-07-07 02:20:40,657 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 51.488959
2011-07-07 02:20:41,158 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 51.619992
2011-07-07 02:20:41,660 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 51.754474
2011-07-07 02:20:42,161 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 51.785508
2011-07-07 02:20:42,662 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 51.916542
2011-07-07 02:20:43,164 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 52.019989
2011-07-07 02:20:43,665 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 52.137230
2011-07-07 02:20:44,167 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 52.226884
2011-07-07 02:20:44,668 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 52.302746
2011-07-07 02:20:45,170 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 52.378607
2011-07-07 02:20:45,671 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 52.440676
2011-07-07 02:20:46,173 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 52.523434
2011-07-07 02:20:46,674 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 52.588951
2011-07-07 02:20:47,175 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 52.640675
2011-07-07 02:20:47,676 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 52.692398
2011-07-07 02:20:48,178 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 52.771708
2011-07-07 02:20:48,679 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 52.819984
2011-07-07 02:20:49,181 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 52.913086
2011-07-07 02:20:49,682 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 52.978603
2011-07-07 02:20:50,183 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 53.030327
2011-07-07 02:20:50,685 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 53.099292
2011-07-07 02:20:51,186 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 53.171705
2011-07-07 02:20:51,688 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 53.233774
2011-07-07 02:20:52,189 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 53.302739
2011-07-07 02:20:52,691 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 53.385497
2011-07-07 02:20:53,192 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 53.447565
2011-07-07 02:20:53,693 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 53.513082
2011-07-07 02:20:54,195 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 53.571702
2011-07-07 02:20:54,696 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 53.668254
2011-07-07 02:20:55,198 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 53.723426
2011-07-07 02:20:55,699 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 53.795839
2011-07-07 02:20:56,201 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 53.871700
2011-07-07 02:20:56,702 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 53.919976
2011-07-07 02:20:57,204 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 54.037216
2011-07-07 02:20:57,705 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 54.188939
2011-07-07 02:20:58,206 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 54.326870
2011-07-07 02:20:58,708 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 54.471696
2011-07-07 02:20:59,209 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 54.578592
2011-07-07 02:20:59,710 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 54.754453
2011-07-07 02:21:00,212 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 54.885486
2011-07-07 02:21:00,713 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 54.999279
2011-07-07 02:21:01,215 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 55.151002
2011-07-07 02:21:01,716 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 55.295828
2011-07-07 02:21:02,218 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 55.340655
2011-07-07 02:21:02,719 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 55.475137
2011-07-07 02:21:03,221 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 55.592378
2011-07-07 02:21:03,722 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 55.685481
2011-07-07 02:21:04,223 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 55.802721
2011-07-07 02:21:04,725 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 55.882031
2011-07-07 02:21:05,226 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 55.961341
2011-07-07 02:21:05,728 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 56.026858
2011-07-07 02:21:06,229 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 56.130305
2011-07-07 02:21:06,731 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 56.202718
2011-07-07 02:21:07,233 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 56.309614
2011-07-07 02:21:07,734 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 56.413062
2011-07-07 02:21:08,236 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 56.475130
2011-07-07 02:21:08,738 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 56.571681
2011-07-07 02:21:09,240 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 56.661336
2011-07-07 02:21:09,741 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 56.778576
2011-07-07 02:21:10,242 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 56.847541
2011-07-07 02:21:10,744 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 56.913058
2011-07-07 02:21:11,245 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 57.019954
2011-07-07 02:21:11,747 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 57.099264
2011-07-07 02:21:12,248 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 57.206160
2011-07-07 02:21:12,749 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 57.302711
2011-07-07 02:21:13,251 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 57.392365
2011-07-07 02:21:13,752 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 57.523399
2011-07-07 02:21:14,253 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 57.709604
2011-07-07 02:21:14,755 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 57.809604
2011-07-07 02:21:15,256 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 57.933741
2011-07-07 02:21:15,758 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 58.040636
2011-07-07 02:21:16,260 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 58.095808
2011-07-07 02:21:16,761 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 58.206152
2011-07-07 02:21:17,262 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 58.295807
2011-07-07 02:21:17,764 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 58.437185
2011-07-07 02:21:18,265 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 58.499254
2011-07-07 02:21:18,767 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 58.571667
2011-07-07 02:21:19,268 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 58.668218
2011-07-07 02:21:19,770 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 58.726838
2011-07-07 02:21:20,271 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 58.795803
2011-07-07 02:21:20,772 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 58.864769
2011-07-07 02:21:21,274 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 58.895803
2011-07-07 02:21:21,776 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 58.988906
2011-07-07 02:21:22,277 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 59.061319
2011-07-07 02:21:22,778 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 59.099250
2011-07-07 02:21:23,280 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 59.199249
2011-07-07 02:21:23,781 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 59.230283
2011-07-07 02:21:24,283 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 59.319938
2011-07-07 02:21:24,784 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 59.395799
2011-07-07 02:21:25,285 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 59.461316
2011-07-07 02:21:25,787 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 59.482006
2011-07-07 02:21:26,288 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 59.609591
2011-07-07 02:21:26,790 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 59.685452
2011-07-07 02:21:27,291 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 59.761314
2011-07-07 02:21:27,793 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 59.861313
2011-07-07 02:21:28,294 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 59.937175
2011-07-07 02:21:28,795 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 59.954416
2011-07-07 02:21:29,297 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 60.057864
2011-07-07 02:21:29,798 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 60.154415
2011-07-07 02:21:30,300 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 60.199242
2011-07-07 02:21:30,801 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 60.275103
2011-07-07 02:21:31,303 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 60.375103
2011-07-07 02:21:31,804 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 60.557860
2011-07-07 02:21:32,305 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 60.709583
2011-07-07 02:21:32,807 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 60.844065
2011-07-07 02:21:33,308 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 60.961305
2011-07-07 02:21:33,810 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 61.116477
2011-07-07 02:21:34,311 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 61.268200
2011-07-07 02:21:34,813 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 61.419923
2011-07-07 02:21:35,314 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 61.557853
2011-07-07 02:21:35,816 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 61.688887
2011-07-07 02:21:36,317 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 61.792334
2011-07-07 02:21:36,819 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 61.923368
2011-07-07 02:21:37,320 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 62.006126
2011-07-07 02:21:37,821 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 62.147504
2011-07-07 02:21:38,323 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 62.295779
2011-07-07 02:21:38,824 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 62.447502
2011-07-07 02:21:39,325 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 62.585432
2011-07-07 02:21:39,827 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 62.702672
2011-07-07 02:21:40,328 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 62.813017
2011-07-07 02:21:40,829 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 62.950947
2011-07-07 02:21:41,331 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 63.081980
2011-07-07 02:21:41,833 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 63.199221
2011-07-07 02:21:42,334 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 63.292323
2011-07-07 02:21:42,836 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 63.426805
2011-07-07 02:21:43,336 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 63.564735
2011-07-07 02:21:43,838 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 63.709562
2011-07-07 02:21:44,339 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 63.864733
2011-07-07 02:21:44,841 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 63.940595
2011-07-07 02:21:45,342 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 64.092318
2011-07-07 02:21:45,843 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 64.209558
2011-07-07 02:21:46,345 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 64.319902
2011-07-07 02:21:46,846 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 64.468177
2011-07-07 02:21:47,348 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 64.544039
2011-07-07 02:21:47,849 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 64.678521
2011-07-07 02:21:48,351 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 64.833692
2011-07-07 02:21:48,852 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 64.964725
2011-07-07 02:21:49,353 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 65.123345
2011-07-07 02:21:49,855 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 65.264723
2011-07-07 02:21:50,356 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 65.395757
2011-07-07 02:21:50,858 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 65.550928
2011-07-07 02:21:51,359 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 65.675065
2011-07-07 02:21:51,861 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 65.833685
2011-07-07 02:21:52,362 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 65.975063
2011-07-07 02:21:52,864 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 66.112993
2011-07-07 02:21:53,365 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 66.281958
2011-07-07 02:21:53,866 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 66.399198
2011-07-07 02:21:54,368 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 66.523335
2011-07-07 02:21:54,869 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 66.671610
2011-07-07 02:21:55,370 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 66.809540
2011-07-07 02:21:55,871 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 66.940574
2011-07-07 02:21:56,373 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 66.964711
2011-07-07 02:21:56,875 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 66.999194
2011-07-07 02:21:57,376 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 66.999194
2011-07-07 02:21:57,877 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.054366
2011-07-07 02:21:58,379 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.068159
2011-07-07 02:21:58,880 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.102641
2011-07-07 02:21:59,382 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.147469
2011-07-07 02:21:59,883 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.147469
2011-07-07 02:22:00,385 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.206089
2011-07-07 02:22:00,886 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.223330
2011-07-07 02:22:01,388 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.230227
2011-07-07 02:22:01,889 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.264709
2011-07-07 02:22:02,391 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.278502
2011-07-07 02:22:02,892 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.295743
2011-07-07 02:22:03,393 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.306088
2011-07-07 02:22:03,895 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.330226
2011-07-07 02:22:04,396 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.354364
2011-07-07 02:22:04,898 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.378502
2011-07-07 02:22:05,399 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.392295
2011-07-07 02:22:05,901 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.412984
2011-07-07 02:22:06,402 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.426777
2011-07-07 02:22:06,903 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.450915
2011-07-07 02:22:07,405 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.464708
2011-07-07 02:22:07,906 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.488846
2011-07-07 02:22:08,408 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.516432
2011-07-07 02:22:08,909 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.526776
2011-07-07 02:22:09,411 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.550914
2011-07-07 02:22:09,912 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.564707
2011-07-07 02:22:10,413 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.581948
2011-07-07 02:22:10,915 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.599190
2011-07-07 02:22:11,416 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.619879
2011-07-07 02:22:11,917 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.633672
2011-07-07 02:22:12,419 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.657810
2011-07-07 02:22:12,920 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.671603
2011-07-07 02:22:13,422 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.699189
2011-07-07 02:22:13,923 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.719878
2011-07-07 02:22:14,424 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.740568
2011-07-07 02:22:14,926 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.757809
2011-07-07 02:22:15,427 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.764706
2011-07-07 02:22:15,929 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.792292
2011-07-07 02:22:16,430 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.812981
2011-07-07 02:22:16,932 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.830222
2011-07-07 02:22:17,433 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.857808
2011-07-07 02:22:17,934 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.871601
2011-07-07 02:22:18,436 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.888843
2011-07-07 02:22:18,937 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.909532
2011-07-07 02:22:19,438 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.919877
2011-07-07 02:22:19,939 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.944015
2011-07-07 02:22:20,440 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.968153
2011-07-07 02:22:20,941 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 67.978497
2011-07-07 02:22:21,443 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.006083
2011-07-07 02:22:21,944 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.023325
2011-07-07 02:22:22,446 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.078497
2011-07-07 02:22:22,947 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.106083
2011-07-07 02:22:23,449 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.140565
2011-07-07 02:22:23,950 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.178496
2011-07-07 02:22:24,451 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.195737
2011-07-07 02:22:24,953 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.247461
2011-07-07 02:22:25,454 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.275047
2011-07-07 02:22:25,956 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.302633
2011-07-07 02:22:26,457 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.344012
2011-07-07 02:22:26,959 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.378494
2011-07-07 02:22:27,460 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.419873
2011-07-07 02:22:27,961 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.454356
2011-07-07 02:22:28,463 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.488838
2011-07-07 02:22:28,964 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.516425
2011-07-07 02:22:29,465 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.557804
2011-07-07 02:22:29,967 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.557804
2011-07-07 02:22:30,468 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.616424
2011-07-07 02:22:30,970 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.619872
2011-07-07 02:22:31,471 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.650906
2011-07-07 02:22:31,973 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.668148
2011-07-07 02:22:32,474 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.678492
2011-07-07 02:22:32,976 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.702630
2011-07-07 02:22:33,477 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.719871
2011-07-07 02:22:33,979 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.744009
2011-07-07 02:22:34,480 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.771595
2011-07-07 02:22:34,982 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.785388
2011-07-07 02:22:35,483 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.802629
2011-07-07 02:22:35,984 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.840560
2011-07-07 02:22:36,486 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.861250
2011-07-07 02:22:36,987 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.888836
2011-07-07 02:22:37,488 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.899180
2011-07-07 02:22:37,989 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.926766
2011-07-07 02:22:38,491 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.954352
2011-07-07 02:22:38,992 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.964697
2011-07-07 02:22:39,493 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 68.988835
2011-07-07 02:22:39,994 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.002628
2011-07-07 02:22:40,496 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.026766
2011-07-07 02:22:40,997 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.044007
2011-07-07 02:22:41,499 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.054352
2011-07-07 02:22:42,000 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.078490
2011-07-07 02:22:42,502 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.092283
2011-07-07 02:22:43,003 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.116420
2011-07-07 02:22:43,504 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.140558
2011-07-07 02:22:44,005 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.157799
2011-07-07 02:22:44,507 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.185385
2011-07-07 02:22:45,008 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.195730
2011-07-07 02:22:45,510 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.219868
2011-07-07 02:22:46,011 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.237109
2011-07-07 02:22:46,513 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.247454
2011-07-07 02:22:47,014 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.275040
2011-07-07 02:22:47,515 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.292281
2011-07-07 02:22:48,017 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.302626
2011-07-07 02:22:48,518 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.337108
2011-07-07 02:22:49,019 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.354350
2011-07-07 02:22:49,521 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.375039
2011-07-07 02:22:50,022 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.399177
2011-07-07 02:22:50,524 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.409522
2011-07-07 02:22:51,025 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.426763
2011-07-07 02:22:51,526 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.454349
2011-07-07 02:22:52,028 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.468142
2011-07-07 02:22:52,529 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.478487
2011-07-07 02:22:53,031 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.506073
2011-07-07 02:22:53,532 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.530210
2011-07-07 02:22:54,033 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.547452
2011-07-07 02:22:54,535 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.564693
2011-07-07 02:22:55,036 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.588831
2011-07-07 02:22:55,538 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.606072
2011-07-07 02:22:56,039 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.616417
2011-07-07 02:22:56,541 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.644003
2011-07-07 02:22:57,042 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.657796
2011-07-07 02:22:57,543 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.685382
2011-07-07 02:22:58,044 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.695727
2011-07-07 02:22:58,545 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.719864
2011-07-07 02:22:59,047 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.747450
2011-07-07 02:22:59,548 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.757795
2011-07-07 02:23:00,049 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.775036
2011-07-07 02:23:00,550 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.799174
2011-07-07 02:23:01,052 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.802622
2011-07-07 02:23:01,553 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.837105
2011-07-07 02:23:02,054 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.861243
2011-07-07 02:23:02,556 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.878484
2011-07-07 02:23:03,057 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.895725
2011-07-07 02:23:03,558 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.909518
2011-07-07 02:23:04,060 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.937104
2011-07-07 02:23:04,561 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.944001
2011-07-07 02:23:05,062 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.968138
2011-07-07 02:23:05,563 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 69.995724
2011-07-07 02:23:06,064 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.009517
2011-07-07 02:23:06,566 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.023310
2011-07-07 02:23:07,067 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.047448
2011-07-07 02:23:07,569 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.071586
2011-07-07 02:23:08,070 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.085379
2011-07-07 02:23:08,572 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.099172
2011-07-07 02:23:09,073 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.123310
2011-07-07 02:23:09,575 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.147447
2011-07-07 02:23:10,076 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.161240
2011-07-07 02:23:10,578 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.185378
2011-07-07 02:23:11,079 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.199171
2011-07-07 02:23:11,580 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.223309
2011-07-07 02:23:12,082 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.233654
2011-07-07 02:23:12,583 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.257792
2011-07-07 02:23:13,085 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.271585
2011-07-07 02:23:13,586 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.299171
2011-07-07 02:23:14,088 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.316412
2011-07-07 02:23:14,590 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.323308
2011-07-07 02:23:15,091 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.350894
2011-07-07 02:23:15,592 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.375032
2011-07-07 02:23:16,093 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.402618
2011-07-07 02:23:16,595 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.416411
2011-07-07 02:23:17,096 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.426756
2011-07-07 02:23:17,598 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.454342
2011-07-07 02:23:18,099 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.464687
2011-07-07 02:23:18,600 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.502617
2011-07-07 02:23:19,101 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.502617
2011-07-07 02:23:19,602 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.530203
2011-07-07 02:23:20,104 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.554341
2011-07-07 02:23:20,605 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.568134
2011-07-07 02:23:21,107 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.595720
2011-07-07 02:23:21,608 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.609513
2011-07-07 02:23:22,110 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.623306
2011-07-07 02:23:22,611 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.650892
2011-07-07 02:23:23,112 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.661237
2011-07-07 02:23:23,614 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.685375
2011-07-07 02:23:24,115 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.699168
2011-07-07 02:23:24,617 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.719857
2011-07-07 02:23:25,118 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.747443
2011-07-07 02:23:25,620 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.761236
2011-07-07 02:23:26,121 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.781926
2011-07-07 02:23:26,623 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.802615
2011-07-07 02:23:27,124 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.819857
2011-07-07 02:23:27,625 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.843994
2011-07-07 02:23:28,127 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.854339
2011-07-07 02:23:28,628 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.878477
2011-07-07 02:23:29,129 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.892270
2011-07-07 02:23:29,631 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.916408
2011-07-07 02:23:30,132 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.926752
2011-07-07 02:23:30,633 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.950890
2011-07-07 02:23:31,135 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.961235
2011-07-07 02:23:31,637 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 70.995717
2011-07-07 02:23:32,138 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.009510
2011-07-07 02:23:32,640 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.026752
2011-07-07 02:23:33,142 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.037096
2011-07-07 02:23:33,643 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.061234
2011-07-07 02:23:34,145 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.088820
2011-07-07 02:23:34,647 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.112958
2011-07-07 02:23:35,148 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.126751
2011-07-07 02:23:35,649 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.150889
2011-07-07 02:23:36,151 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.164682
2011-07-07 02:23:36,652 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.188819
2011-07-07 02:23:37,154 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.206061
2011-07-07 02:23:37,656 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.216405
2011-07-07 02:23:38,157 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.240543
2011-07-07 02:23:38,659 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.254336
2011-07-07 02:23:39,160 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.278474
2011-07-07 02:23:39,662 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.306060
2011-07-07 02:23:40,164 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.319853
2011-07-07 02:23:40,665 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.343991
2011-07-07 02:23:41,167 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.357784
2011-07-07 02:23:41,668 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.371577
2011-07-07 02:23:42,170 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.395715
2011-07-07 02:23:42,671 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.409508
2011-07-07 02:23:43,173 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.433645
2011-07-07 02:23:43,675 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.447438
2011-07-07 02:23:44,176 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.471576
2011-07-07 02:23:44,677 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.481921
2011-07-07 02:23:45,179 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.506059
2011-07-07 02:23:45,680 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.519852
2011-07-07 02:23:46,181 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.557782
2011-07-07 02:23:46,683 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.571575
2011-07-07 02:23:47,184 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.581920
2011-07-07 02:23:47,685 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.609506
2011-07-07 02:23:48,186 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.619851
2011-07-07 02:23:48,688 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.654333
2011-07-07 02:23:49,189 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.671575
2011-07-07 02:23:49,691 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.681919
2011-07-07 02:23:50,192 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.706057
2011-07-07 02:23:50,694 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.719850
2011-07-07 02:23:51,195 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.747436
2011-07-07 02:23:51,697 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.761229
2011-07-07 02:23:52,198 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.788815
2011-07-07 02:23:52,699 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.802608
2011-07-07 02:23:53,200 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.812953
2011-07-07 02:23:53,702 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.843987
2011-07-07 02:23:54,203 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.861228
2011-07-07 02:23:54,704 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.878470
2011-07-07 02:23:55,206 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.888814
2011-07-07 02:23:55,708 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.912952
2011-07-07 02:23:56,209 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.940538
2011-07-07 02:23:56,711 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.957780
2011-07-07 02:23:57,212 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.981917
2011-07-07 02:23:57,714 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 71.995710
2011-07-07 02:23:58,215 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.006055
2011-07-07 02:23:58,717 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.033641
2011-07-07 02:23:59,219 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.057779
2011-07-07 02:23:59,720 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.071572
2011-07-07 02:24:00,221 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.099158
2011-07-07 02:24:00,723 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.109503
2011-07-07 02:24:01,225 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.133640
2011-07-07 02:24:01,726 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.150882
2011-07-07 02:24:02,228 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.171571
2011-07-07 02:24:02,729 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.188812
2011-07-07 02:24:03,231 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.202605
2011-07-07 02:24:03,732 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.216398
2011-07-07 02:24:04,233 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.250881
2011-07-07 02:24:04,735 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.264674
2011-07-07 02:24:05,236 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.292260
2011-07-07 02:24:05,738 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.306053
2011-07-07 02:24:06,239 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.316398
2011-07-07 02:24:06,740 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.343984
2011-07-07 02:24:07,242 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.368121
2011-07-07 02:24:07,743 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.381914
2011-07-07 02:24:08,245 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.406052
2011-07-07 02:24:08,746 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.406052
2011-07-07 02:24:09,248 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.443983
2011-07-07 02:24:09,750 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.454328
2011-07-07 02:24:10,251 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.481914
2011-07-07 02:24:10,752 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.506052
2011-07-07 02:24:11,253 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.519845
2011-07-07 02:24:11,755 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.543982
2011-07-07 02:24:12,256 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.554327
2011-07-07 02:24:12,757 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.578465
2011-07-07 02:24:13,259 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.595706
2011-07-07 02:24:13,761 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.616396
2011-07-07 02:24:14,262 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.630189
2011-07-07 02:24:14,764 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.654326
2011-07-07 02:24:15,266 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.668119
2011-07-07 02:24:15,767 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.695705
2011-07-07 02:24:16,268 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.709498
2011-07-07 02:24:16,770 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.737084
2011-07-07 02:24:17,271 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.747429
2011-07-07 02:24:17,773 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.771567
2011-07-07 02:24:18,274 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.785360
2011-07-07 02:24:18,775 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.809498
2011-07-07 02:24:19,277 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.823291
2011-07-07 02:24:19,779 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.847428
2011-07-07 02:24:20,280 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.857773
2011-07-07 02:24:20,781 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.881911
2011-07-07 02:24:21,283 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.909497
2011-07-07 02:24:21,785 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.923290
2011-07-07 02:24:22,286 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.950876
2011-07-07 02:24:22,788 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.964669
2011-07-07 02:24:23,289 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 72.978462
2011-07-07 02:24:23,790 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.002600
2011-07-07 02:24:24,292 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.023289
2011-07-07 02:24:24,793 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.040530
2011-07-07 02:24:25,295 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.068117
2011-07-07 02:24:25,796 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.078461
2011-07-07 02:24:26,297 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.102599
2011-07-07 02:24:26,799 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.116392
2011-07-07 02:24:27,301 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.130185
2011-07-07 02:24:27,802 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.157771
2011-07-07 02:24:28,304 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.171564
2011-07-07 02:24:28,805 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.192254
2011-07-07 02:24:29,306 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.219840
2011-07-07 02:24:29,807 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.223288
2011-07-07 02:24:30,309 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.257770
2011-07-07 02:24:30,810 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.271563
2011-07-07 02:24:31,312 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.299149
2011-07-07 02:24:31,814 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.309494
2011-07-07 02:24:32,315 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.333632
2011-07-07 02:24:32,816 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.347425
2011-07-07 02:24:33,318 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.375011
2011-07-07 02:24:33,820 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.402597
2011-07-07 02:24:34,321 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.426735
2011-07-07 02:24:34,822 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.478458
2011-07-07 02:24:35,323 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.512941
2011-07-07 02:24:35,825 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.550872
2011-07-07 02:24:36,326 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.585354
2011-07-07 02:24:36,828 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.616388
2011-07-07 02:24:37,330 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.643975
2011-07-07 02:24:37,831 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.692250
2011-07-07 02:24:38,332 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.699147
2011-07-07 02:24:38,834 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.743974
2011-07-07 02:24:39,336 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.781905
2011-07-07 02:24:39,837 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.802594
2011-07-07 02:24:40,339 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.830180
2011-07-07 02:24:40,840 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.847421
2011-07-07 02:24:41,341 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.864663
2011-07-07 02:24:41,843 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.881904
2011-07-07 02:24:42,344 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.899145
2011-07-07 02:24:42,846 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.923283
2011-07-07 02:24:43,347 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.933628
2011-07-07 02:24:43,848 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.957765
2011-07-07 02:24:44,349 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 73.981903
2011-07-07 02:24:44,850 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.009489
2011-07-07 02:24:45,352 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.019834
2011-07-07 02:24:45,853 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.043972
2011-07-07 02:24:46,355 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.054316
2011-07-07 02:24:46,857 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.078454
2011-07-07 02:24:47,358 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.106040
2011-07-07 02:24:47,859 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.140523
2011-07-07 02:24:48,361 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.168109
2011-07-07 02:24:48,862 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.188798
2011-07-07 02:24:49,364 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.212936
2011-07-07 02:24:49,866 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.233626
2011-07-07 02:24:50,367 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.247419
2011-07-07 02:24:50,869 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.268108
2011-07-07 02:24:51,370 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.278453
2011-07-07 02:24:51,871 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.299142
2011-07-07 02:24:52,373 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.312935
2011-07-07 02:24:52,874 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.333625
2011-07-07 02:24:53,375 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.357763
2011-07-07 02:24:53,876 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.409486
2011-07-07 02:24:54,378 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.409486
2011-07-07 02:24:54,879 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.461210
2011-07-07 02:24:55,381 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.481900
2011-07-07 02:24:55,882 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.537072
2011-07-07 02:24:56,384 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.564658
2011-07-07 02:24:56,885 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.585347
2011-07-07 02:24:57,387 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.626726
2011-07-07 02:24:57,889 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.650864
2011-07-07 02:24:58,390 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.681898
2011-07-07 02:24:58,891 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.723277
2011-07-07 02:24:59,393 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.737070
2011-07-07 02:24:59,894 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.747415
2011-07-07 02:25:00,396 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.785346
2011-07-07 02:25:00,897 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.788794
2011-07-07 02:25:01,399 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.823277
2011-07-07 02:25:01,900 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.823277
2011-07-07 02:25:02,402 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.861207
2011-07-07 02:25:02,904 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.871552
2011-07-07 02:25:03,405 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.892242
2011-07-07 02:25:03,907 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.902586
2011-07-07 02:25:04,408 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.930172
2011-07-07 02:25:04,909 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.940517
2011-07-07 02:25:05,411 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.971551
2011-07-07 02:25:05,912 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 74.975000
2011-07-07 02:25:06,413 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.006034
2011-07-07 02:25:06,914 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.019827
2011-07-07 02:25:07,416 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.040516
2011-07-07 02:25:07,918 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.061206
2011-07-07 02:25:08,419 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.074999
2011-07-07 02:25:08,920 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.099137
2011-07-07 02:25:09,421 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.123274
2011-07-07 02:25:09,923 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.147412
2011-07-07 02:25:10,424 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.171550
2011-07-07 02:25:10,925 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.216377
2011-07-07 02:25:11,426 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.233618
2011-07-07 02:25:11,928 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.281894
2011-07-07 02:25:12,430 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.306032
2011-07-07 02:25:12,931 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.354307
2011-07-07 02:25:13,433 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.364652
2011-07-07 02:25:13,934 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.412928
2011-07-07 02:25:14,436 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.440514
2011-07-07 02:25:14,937 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.471548
2011-07-07 02:25:15,439 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.502582
2011-07-07 02:25:15,940 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.543961
2011-07-07 02:25:16,442 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.564651
2011-07-07 02:25:16,943 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.578444
2011-07-07 02:25:17,445 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.602581
2011-07-07 02:25:17,946 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.612926
2011-07-07 02:25:18,448 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.637064
2011-07-07 02:25:18,949 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.664650
2011-07-07 02:25:19,450 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.674995
2011-07-07 02:25:19,952 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.699132
2011-07-07 02:25:20,453 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.709477
2011-07-07 02:25:20,955 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.737063
2011-07-07 02:25:21,456 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.757753
2011-07-07 02:25:21,958 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.774994
2011-07-07 02:25:22,459 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.785339
2011-07-07 02:25:22,961 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.809476
2011-07-07 02:25:23,462 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.823269
2011-07-07 02:25:23,963 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.861200
2011-07-07 02:25:24,465 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.874993
2011-07-07 02:25:24,966 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.899131
2011-07-07 02:25:25,468 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.923269
2011-07-07 02:25:25,969 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.971544
2011-07-07 02:25:26,471 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 75.995682
2011-07-07 02:25:26,972 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.016372
2011-07-07 02:25:27,474 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.050854
2011-07-07 02:25:27,975 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.102578
2011-07-07 02:25:28,477 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.130164
2011-07-07 02:25:28,979 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.168095
2011-07-07 02:25:29,481 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.199129
2011-07-07 02:25:29,982 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.230163
2011-07-07 02:25:30,483 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.250853
2011-07-07 02:25:30,984 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.288783
2011-07-07 02:25:31,486 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.302576
2011-07-07 02:25:31,988 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.330162
2011-07-07 02:25:32,489 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.340507
2011-07-07 02:25:32,991 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.368093
2011-07-07 02:25:33,492 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.374990
2011-07-07 02:25:33,994 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.409472
2011-07-07 02:25:34,495 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.409472
2011-07-07 02:25:34,996 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.440506
2011-07-07 02:25:35,498 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.450851
2011-07-07 02:25:35,999 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.474989
2011-07-07 02:25:36,500 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.495679
2011-07-07 02:25:37,002 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.509472
2011-07-07 02:25:37,503 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.530161
2011-07-07 02:25:38,005 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.540506
2011-07-07 02:25:38,506 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.564644
2011-07-07 02:25:39,008 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.574988
2011-07-07 02:25:39,510 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.599126
2011-07-07 02:25:40,011 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.606023
2011-07-07 02:25:40,512 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.640505
2011-07-07 02:25:41,014 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.640505
2011-07-07 02:25:41,516 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.674988
2011-07-07 02:25:42,017 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.695677
2011-07-07 02:25:42,519 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.709470
2011-07-07 02:25:43,021 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.719815
2011-07-07 02:25:43,523 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.740504
2011-07-07 02:25:44,025 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.750849
2011-07-07 02:25:44,526 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.778435
2011-07-07 02:25:45,028 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.785332
2011-07-07 02:25:45,529 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.819814
2011-07-07 02:25:46,030 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.830159
2011-07-07 02:25:46,532 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.854297
2011-07-07 02:25:47,033 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.874986
2011-07-07 02:25:47,535 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.888779
2011-07-07 02:25:48,036 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.909469
2011-07-07 02:25:48,538 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.919813
2011-07-07 02:25:49,040 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.940503
2011-07-07 02:25:49,541 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.950848
2011-07-07 02:25:50,042 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.978434
2011-07-07 02:25:50,544 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 76.985330
2011-07-07 02:25:51,045 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.016364
2011-07-07 02:25:51,546 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.019813
2011-07-07 02:25:52,048 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.050847
2011-07-07 02:25:52,549 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.068088
2011-07-07 02:25:53,051 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.088778
2011-07-07 02:25:53,552 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.099123
2011-07-07 02:25:54,053 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.119812
2011-07-07 02:25:54,554 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.143950
2011-07-07 02:25:55,056 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.150846
2011-07-07 02:25:55,557 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.178432
2011-07-07 02:25:56,059 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.199122
2011-07-07 02:25:56,560 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.209467
2011-07-07 02:25:57,062 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.233604
2011-07-07 02:25:57,564 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.243949
2011-07-07 02:25:58,065 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.264639
2011-07-07 02:25:58,567 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.274983
2011-07-07 02:25:59,068 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.302569
2011-07-07 02:25:59,570 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.309466
2011-07-07 02:26:00,072 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.340500
2011-07-07 02:26:00,573 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.340500
2011-07-07 02:26:01,074 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.374983
2011-07-07 02:26:01,576 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.385327
2011-07-07 02:26:02,077 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.409465
2011-07-07 02:26:02,579 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.430155
2011-07-07 02:26:03,080 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.440499
2011-07-07 02:26:03,582 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.457741
2011-07-07 02:26:04,084 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.468085
2011-07-07 02:26:04,585 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.481878
2011-07-07 02:26:05,087 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.492223
2011-07-07 02:26:05,588 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.502568
2011-07-07 02:26:06,090 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.502568
2011-07-07 02:26:06,591 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.526706
2011-07-07 02:26:07,093 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.530154
2011-07-07 02:26:07,594 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.537050
2011-07-07 02:26:08,096 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.537050
2011-07-07 02:26:08,597 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.561188
2011-07-07 02:26:09,099 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.564636
2011-07-07 02:26:09,601 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.581878
2011-07-07 02:26:10,103 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.595671
2011-07-07 02:26:10,604 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.599119
2011-07-07 02:26:11,106 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.612912
2011-07-07 02:26:11,608 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.616360
2011-07-07 02:26:12,110 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.637050
2011-07-07 02:26:12,611 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.637050
2011-07-07 02:26:13,113 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.647395
2011-07-07 02:26:13,615 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.647395
2011-07-07 02:26:14,116 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.674981
2011-07-07 02:26:14,618 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.681877
2011-07-07 02:26:15,119 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.695670
2011-07-07 02:26:15,621 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.709463
2011-07-07 02:26:16,123 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.719808
2011-07-07 02:26:16,624 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.737049
2011-07-07 02:26:17,126 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.743946
2011-07-07 02:26:17,628 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.761187
2011-07-07 02:26:18,129 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.768083
2011-07-07 02:26:18,631 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.785325
2011-07-07 02:26:19,133 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.802566
2011-07-07 02:26:19,635 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.816359
2011-07-07 02:26:20,137 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.833600
2011-07-07 02:26:20,638 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.843945
2011-07-07 02:26:21,140 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.861186
2011-07-07 02:26:21,641 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.868083
2011-07-07 02:26:22,143 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.878427
2011-07-07 02:26:22,645 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.878427
2011-07-07 02:26:23,146 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.902565
2011-07-07 02:26:23,647 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.909462
2011-07-07 02:26:24,149 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.919806
2011-07-07 02:26:24,651 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.919806
2011-07-07 02:26:25,152 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.940496
2011-07-07 02:26:25,654 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.947392
2011-07-07 02:26:26,156 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.954289
2011-07-07 02:26:26,658 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.954289
2011-07-07 02:26:27,160 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.971530
2011-07-07 02:26:27,662 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.981875
2011-07-07 02:26:28,164 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.992220
2011-07-07 02:26:28,665 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.999116
2011-07-07 02:26:29,167 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 77.999116
2011-07-07 02:26:29,668 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.019806
2011-07-07 02:26:30,170 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.023254
2011-07-07 02:26:30,671 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.033599
2011-07-07 02:26:31,173 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.033599
2011-07-07 02:26:31,674 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.050840
2011-07-07 02:26:32,175 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.054288
2011-07-07 02:26:32,677 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.071529
2011-07-07 02:26:33,178 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.074978
2011-07-07 02:26:33,680 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.081874
2011-07-07 02:26:34,181 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.099115
2011-07-07 02:26:34,683 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.106012
2011-07-07 02:26:35,185 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.119805
2011-07-07 02:26:35,686 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.130150
2011-07-07 02:26:36,188 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.143943
2011-07-07 02:26:36,689 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.157736
2011-07-07 02:26:37,191 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.174977
2011-07-07 02:26:37,692 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.185322
2011-07-07 02:26:38,193 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.209460
2011-07-07 02:26:38,695 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.233597
2011-07-07 02:26:39,197 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.243942
2011-07-07 02:26:39,698 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.264632
2011-07-07 02:26:40,200 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.274976
2011-07-07 02:26:40,701 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.292218
2011-07-07 02:26:41,203 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.302562
2011-07-07 02:26:41,705 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.333597
2011-07-07 02:26:42,207 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.333597
2011-07-07 02:26:42,708 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.361183
2011-07-07 02:26:43,209 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.361183
2011-07-07 02:26:43,711 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.395665
2011-07-07 02:26:44,212 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.419803
2011-07-07 02:26:44,714 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.437044
2011-07-07 02:26:45,215 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.447389
2011-07-07 02:26:45,716 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.471527
2011-07-07 02:26:46,218 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.481871
2011-07-07 02:26:46,719 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.506009
2011-07-07 02:26:47,220 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.526699
2011-07-07 02:26:47,722 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.547388
2011-07-07 02:26:48,224 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.561181
2011-07-07 02:26:48,725 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.571526
2011-07-07 02:26:49,227 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.595664
2011-07-07 02:26:49,728 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.606008
2011-07-07 02:26:50,229 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.637043
2011-07-07 02:26:50,731 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.643939
2011-07-07 02:26:51,232 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.668077
2011-07-07 02:26:51,734 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.685318
2011-07-07 02:26:52,236 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.699111
2011-07-07 02:26:52,737 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.723249
2011-07-07 02:26:53,238 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.733594
2011-07-07 02:26:53,739 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.754283
2011-07-07 02:26:54,241 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.768076
2011-07-07 02:26:54,742 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.795662
2011-07-07 02:26:55,243 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.806007
2011-07-07 02:26:55,745 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.840490
2011-07-07 02:26:56,246 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.843938
2011-07-07 02:26:56,748 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.878420
2011-07-07 02:26:57,249 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.885317
2011-07-07 02:26:57,751 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.916351
2011-07-07 02:26:58,252 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.926696
2011-07-07 02:26:58,754 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.950834
2011-07-07 02:26:59,255 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.968075
2011-07-07 02:26:59,757 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 78.992213
2011-07-07 02:27:00,258 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.006006
2011-07-07 02:27:00,759 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.033592
2011-07-07 02:27:01,261 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.043936
2011-07-07 02:27:01,762 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.068074
2011-07-07 02:27:02,263 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.078419
2011-07-07 02:27:02,765 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.102557
2011-07-07 02:27:03,267 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.112901
2011-07-07 02:27:03,768 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.140487
2011-07-07 02:27:04,269 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.150832
2011-07-07 02:27:04,770 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.185315
2011-07-07 02:27:05,272 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.188763
2011-07-07 02:27:05,773 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.216349
2011-07-07 02:27:06,274 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.226694
2011-07-07 02:27:06,776 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.250831
2011-07-07 02:27:07,277 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.271521
2011-07-07 02:27:07,779 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.316348
2011-07-07 02:27:08,280 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.343934
2011-07-07 02:27:08,781 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.371520
2011-07-07 02:27:09,283 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.395658
2011-07-07 02:27:09,784 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.412899
2011-07-07 02:27:10,285 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.437037
2011-07-07 02:27:10,787 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.450830
2011-07-07 02:27:11,288 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.495657
2011-07-07 02:27:11,790 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.509450
2011-07-07 02:27:12,291 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.533588
2011-07-07 02:27:12,793 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.543933
2011-07-07 02:27:13,294 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.571519
2011-07-07 02:27:13,796 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.581864
2011-07-07 02:27:14,297 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.606001
2011-07-07 02:27:14,798 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.619794
2011-07-07 02:27:15,300 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.643932
2011-07-07 02:27:15,801 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.657725
2011-07-07 02:27:16,303 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.681863
2011-07-07 02:27:16,805 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.692208
2011-07-07 02:27:17,307 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.716345
2011-07-07 02:27:17,809 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.730138
2011-07-07 02:27:18,310 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.754276
2011-07-07 02:27:18,812 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.768069
2011-07-07 02:27:19,313 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.792207
2011-07-07 02:27:19,814 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.819793
2011-07-07 02:27:20,316 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.830138
2011-07-07 02:27:20,817 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.857724
2011-07-07 02:27:21,319 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.868068
2011-07-07 02:27:21,820 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.892206
2011-07-07 02:27:22,321 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.919792
2011-07-07 02:27:22,823 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.930137
2011-07-07 02:27:23,324 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.954275
2011-07-07 02:27:23,825 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.968068
2011-07-07 02:27:24,326 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 79.992206
2011-07-07 02:27:24,828 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.005999
2011-07-07 02:27:25,329 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.033585
2011-07-07 02:27:25,831 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.054274
2011-07-07 02:27:26,332 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.057722
2011-07-07 02:27:26,833 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.095653
2011-07-07 02:27:27,335 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.109446
2011-07-07 02:27:27,836 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.126687
2011-07-07 02:27:28,338 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.133584
2011-07-07 02:27:28,839 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.157722
2011-07-07 02:27:29,341 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.181859
2011-07-07 02:27:29,843 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.199101
2011-07-07 02:27:30,344 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.223238
2011-07-07 02:27:30,845 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.250824
2011-07-07 02:27:31,347 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.264617
2011-07-07 02:27:31,848 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.281859
2011-07-07 02:27:32,349 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.305996
2011-07-07 02:27:32,851 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.316341
2011-07-07 02:27:33,352 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.340479
2011-07-07 02:27:33,854 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.354272
2011-07-07 02:27:34,355 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.381858
2011-07-07 02:27:34,856 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.395651
2011-07-07 02:27:35,358 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.423237
2011-07-07 02:27:35,859 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.433582
2011-07-07 02:27:36,361 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.457719
2011-07-07 02:27:36,862 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.471512
2011-07-07 02:27:37,363 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.495650
2011-07-07 02:27:37,865 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.499099
2011-07-07 02:27:38,366 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.526685
2011-07-07 02:27:38,867 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.543926
2011-07-07 02:27:39,369 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.554271
2011-07-07 02:27:39,870 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.568064
2011-07-07 02:27:40,372 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.578408
2011-07-07 02:27:40,874 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.592201
2011-07-07 02:27:41,375 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.602546
2011-07-07 02:27:41,877 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.619787
2011-07-07 02:27:42,378 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.626684
2011-07-07 02:27:42,879 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.647373
2011-07-07 02:27:43,380 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.647373
2011-07-07 02:27:43,882 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.671511
2011-07-07 02:27:44,383 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.678408
2011-07-07 02:27:44,885 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.695649
2011-07-07 02:27:45,386 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.709442
2011-07-07 02:27:45,888 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.719787
2011-07-07 02:27:46,389 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.733580
2011-07-07 02:27:46,891 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.740476
2011-07-07 02:27:47,392 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.764614
2011-07-07 02:27:47,894 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.768062
2011-07-07 02:27:48,395 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.788752
2011-07-07 02:27:48,897 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.802545
2011-07-07 02:27:49,398 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.809441
2011-07-07 02:27:49,899 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.826682
2011-07-07 02:27:50,400 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.833579
2011-07-07 02:27:50,901 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.847372
2011-07-07 02:27:51,403 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.857717
2011-07-07 02:27:51,904 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.881854
2011-07-07 02:27:52,406 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.881854
2011-07-07 02:27:52,907 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.902544
2011-07-07 02:27:53,409 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.919785
2011-07-07 02:27:53,910 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.926682
2011-07-07 02:27:54,411 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.940475
2011-07-07 02:27:54,913 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.950819
2011-07-07 02:27:55,414 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.964612
2011-07-07 02:27:55,916 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.988750
2011-07-07 02:27:56,417 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 80.992198
2011-07-07 02:27:56,919 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.026681
2011-07-07 02:27:57,421 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.040474
2011-07-07 02:27:57,922 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.064612
2011-07-07 02:27:58,424 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.085301
2011-07-07 02:27:58,925 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.102543
2011-07-07 02:27:59,426 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.126680
2011-07-07 02:27:59,928 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.140473
2011-07-07 02:28:00,429 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.157715
2011-07-07 02:28:00,930 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.164611
2011-07-07 02:28:01,432 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.199094
2011-07-07 02:28:01,934 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.216335
2011-07-07 02:28:02,436 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.233576
2011-07-07 02:28:02,937 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.257714
2011-07-07 02:28:03,439 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.274955
2011-07-07 02:28:03,940 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.295645
2011-07-07 02:28:04,441 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.319782
2011-07-07 02:28:04,943 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.333575
2011-07-07 02:28:05,444 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.354265
2011-07-07 02:28:05,945 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.371506
2011-07-07 02:28:06,447 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.395644
2011-07-07 02:28:06,948 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.399092
2011-07-07 02:28:07,449 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.433575
2011-07-07 02:28:07,951 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.433575
2011-07-07 02:28:08,452 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.471505
2011-07-07 02:28:08,954 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.481850
2011-07-07 02:28:09,455 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.499091
2011-07-07 02:28:09,956 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.540470
2011-07-07 02:28:10,458 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.578401
2011-07-07 02:28:10,959 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.616332
2011-07-07 02:28:11,461 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.654263
2011-07-07 02:28:11,962 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.685297
2011-07-07 02:28:12,463 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.716331
2011-07-07 02:28:12,964 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.743917
2011-07-07 02:28:13,466 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.795641
2011-07-07 02:28:13,967 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.826675
2011-07-07 02:28:14,468 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.847365
2011-07-07 02:28:14,970 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.878399
2011-07-07 02:28:15,471 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.888744
2011-07-07 02:28:15,972 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.912882
2011-07-07 02:28:16,474 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.926675
2011-07-07 02:28:16,975 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.950812
2011-07-07 02:28:17,477 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.964605
2011-07-07 02:28:17,978 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.988743
2011-07-07 02:28:18,479 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 81.999088
2011-07-07 02:28:18,981 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.023226
2011-07-07 02:28:19,483 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.037019
2011-07-07 02:28:19,984 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.064605
2011-07-07 02:28:20,485 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.088742
2011-07-07 02:28:20,987 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.088742
2011-07-07 02:28:21,488 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.123225
2011-07-07 02:28:21,990 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.123225
2011-07-07 02:28:22,491 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.161156
2011-07-07 02:28:22,993 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.174949
2011-07-07 02:28:23,494 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.192190
2011-07-07 02:28:23,996 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.212880
2011-07-07 02:28:24,497 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.237017
2011-07-07 02:28:24,999 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.250810
2011-07-07 02:28:25,500 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.278396
2011-07-07 02:28:26,002 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.292189
2011-07-07 02:28:26,504 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.316327
2011-07-07 02:28:27,005 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.333568
2011-07-07 02:28:27,506 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.347361
2011-07-07 02:28:28,008 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.357706
2011-07-07 02:28:28,509 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.392189
2011-07-07 02:28:29,010 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.395637
2011-07-07 02:28:29,512 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.426671
2011-07-07 02:28:30,013 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.430119
2011-07-07 02:28:30,515 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.464602
2011-07-07 02:28:31,016 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.474947
2011-07-07 02:28:31,517 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.502533
2011-07-07 02:28:32,019 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.526670
2011-07-07 02:28:32,520 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.543912
2011-07-07 02:28:33,022 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.554256
2011-07-07 02:28:33,523 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.578394
2011-07-07 02:28:34,025 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.605980
2011-07-07 02:28:34,526 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.654256
2011-07-07 02:28:35,028 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.678393
2011-07-07 02:28:35,529 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.705979
2011-07-07 02:28:36,031 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.726669
2011-07-07 02:28:36,532 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.778393
2011-07-07 02:28:37,033 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.812875
2011-07-07 02:28:37,535 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.843910
2011-07-07 02:28:38,036 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.881840
2011-07-07 02:28:38,538 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.899082
2011-07-07 02:28:39,039 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.909426
2011-07-07 02:28:39,540 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.943909
2011-07-07 02:28:40,042 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.964598
2011-07-07 02:28:40,543 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 82.988736
2011-07-07 02:28:41,044 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.002529
2011-07-07 02:28:41,546 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.030115
2011-07-07 02:28:42,047 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.047356
2011-07-07 02:28:42,548 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.081839
2011-07-07 02:28:43,049 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.092184
2011-07-07 02:28:43,551 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.126666
2011-07-07 02:28:44,052 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.137011
2011-07-07 02:28:44,553 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.181838
2011-07-07 02:28:45,055 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.185286
2011-07-07 02:28:45,556 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.219769
2011-07-07 02:28:46,058 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.233562
2011-07-07 02:28:46,559 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.254251
2011-07-07 02:28:47,060 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.264596
2011-07-07 02:28:47,562 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.295630
2011-07-07 02:28:48,063 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.299079
2011-07-07 02:28:48,564 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.330113
2011-07-07 02:28:49,066 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.343906
2011-07-07 02:28:49,567 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.361147
2011-07-07 02:28:50,068 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.381837
2011-07-07 02:28:50,569 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.395630
2011-07-07 02:28:51,071 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.419768
2011-07-07 02:28:51,572 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.426664
2011-07-07 02:28:52,073 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.454250
2011-07-07 02:28:52,575 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.505974
2011-07-07 02:28:53,077 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.519767
2011-07-07 02:28:53,578 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.533560
2011-07-07 02:28:54,079 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.561146
2011-07-07 02:28:54,581 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.571491
2011-07-07 02:28:55,082 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.592180
2011-07-07 02:28:55,584 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.602525
2011-07-07 02:28:56,085 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.626663
2011-07-07 02:28:56,587 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.640456
2011-07-07 02:28:57,088 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.668042
2011-07-07 02:28:57,590 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.688731
2011-07-07 02:28:58,091 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.702524
2011-07-07 02:28:58,592 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.723214
2011-07-07 02:28:59,094 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.733558
2011-07-07 02:28:59,595 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.757696
2011-07-07 02:29:00,096 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.785282
2011-07-07 02:29:00,598 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.802523
2011-07-07 02:29:01,100 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.850799
2011-07-07 02:29:01,601 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.895626
2011-07-07 02:29:02,102 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.899074
2011-07-07 02:29:02,603 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.943902
2011-07-07 02:29:03,105 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.981833
2011-07-07 02:29:03,606 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 83.988729
2011-07-07 02:29:04,107 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.023212
2011-07-07 02:29:04,609 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.043901
2011-07-07 02:29:05,110 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.057694
2011-07-07 02:29:05,611 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.085280
2011-07-07 02:29:06,112 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.105970
2011-07-07 02:29:06,614 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.123211
2011-07-07 02:29:07,115 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.133556
2011-07-07 02:29:07,616 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.157693
2011-07-07 02:29:08,117 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.181831
2011-07-07 02:29:08,618 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.195624
2011-07-07 02:29:09,119 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.212865
2011-07-07 02:29:09,621 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.233555
2011-07-07 02:29:10,123 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.268037
2011-07-07 02:29:10,625 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.295623
2011-07-07 02:29:11,126 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.361140
2011-07-07 02:29:11,628 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.364588
2011-07-07 02:29:12,130 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.419760
2011-07-07 02:29:12,631 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.437002
2011-07-07 02:29:13,132 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.485277
2011-07-07 02:29:13,634 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.499070
2011-07-07 02:29:14,135 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.523208
2011-07-07 02:29:14,636 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.537001
2011-07-07 02:29:15,138 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.568035
2011-07-07 02:29:15,639 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.571484
2011-07-07 02:29:16,141 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.602518
2011-07-07 02:29:16,642 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.612863
2011-07-07 02:29:17,143 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.633552
2011-07-07 02:29:17,644 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.654242
2011-07-07 02:29:18,145 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.668035
2011-07-07 02:29:18,647 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.688724
2011-07-07 02:29:19,148 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.699069
2011-07-07 02:29:19,649 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.730103
2011-07-07 02:29:20,150 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.743896
2011-07-07 02:29:20,651 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.764586
2011-07-07 02:29:21,152 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.774930
2011-07-07 02:29:21,654 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.795620
2011-07-07 02:29:22,155 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.819758
2011-07-07 02:29:22,656 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.830102
2011-07-07 02:29:23,158 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.854240
2011-07-07 02:29:23,659 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.874930
2011-07-07 02:29:24,160 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.885274
2011-07-07 02:29:24,661 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.909412
2011-07-07 02:29:25,162 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.919757
2011-07-07 02:29:25,663 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.940446
2011-07-07 02:29:26,164 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.954239
2011-07-07 02:29:26,666 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.978377
2011-07-07 02:29:27,167 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 84.985274
2011-07-07 02:29:27,669 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.019756
2011-07-07 02:29:28,170 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.030101
2011-07-07 02:29:28,671 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.050791
2011-07-07 02:29:29,172 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.064584
2011-07-07 02:29:29,674 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.074928
2011-07-07 02:29:30,175 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.109411
2011-07-07 02:29:30,676 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.119756
2011-07-07 02:29:31,178 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.140445
2011-07-07 02:29:31,679 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.150790
2011-07-07 02:29:32,181 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.174928
2011-07-07 02:29:32,682 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.185272
2011-07-07 02:29:33,184 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.205962
2011-07-07 02:29:33,686 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.257686
2011-07-07 02:29:34,188 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.264582
2011-07-07 02:29:34,689 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.305961
2011-07-07 02:29:35,190 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.323202
2011-07-07 02:29:35,692 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.357685
2011-07-07 02:29:36,194 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.368030
2011-07-07 02:29:36,695 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.392167
2011-07-07 02:29:37,196 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.405960
2011-07-07 02:29:37,698 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.430098
2011-07-07 02:29:38,199 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.440443
2011-07-07 02:29:38,701 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.464581
2011-07-07 02:29:39,203 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.474925
2011-07-07 02:29:39,704 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.509408
2011-07-07 02:29:40,206 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.519753
2011-07-07 02:29:40,707 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.540442
2011-07-07 02:29:41,208 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.554235
2011-07-07 02:29:41,710 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.574925
2011-07-07 02:29:42,212 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.585269
2011-07-07 02:29:42,713 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.605959
2011-07-07 02:29:43,214 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.619752
2011-07-07 02:29:43,716 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.643890
2011-07-07 02:29:44,217 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.650786
2011-07-07 02:29:44,719 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.685269
2011-07-07 02:29:45,220 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.685269
2011-07-07 02:29:45,722 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.716303
2011-07-07 02:29:46,224 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.719751
2011-07-07 02:29:46,725 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.750786
2011-07-07 02:29:47,226 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.774923
2011-07-07 02:29:47,728 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.785268
2011-07-07 02:29:48,229 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.809406
2011-07-07 02:29:48,730 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.819751
2011-07-07 02:29:49,232 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.840440
2011-07-07 02:29:49,733 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.854233
2011-07-07 02:29:50,235 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.874923
2011-07-07 02:29:50,736 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.885267
2011-07-07 02:29:51,238 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.919750
2011-07-07 02:29:51,739 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.919750
2011-07-07 02:29:52,241 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.954232
2011-07-07 02:29:52,742 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.968025
2011-07-07 02:29:53,243 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.978370
2011-07-07 02:29:53,745 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 85.999060
2011-07-07 02:29:54,246 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.009404
2011-07-07 02:29:54,748 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.030094
2011-07-07 02:29:55,249 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.064576
2011-07-07 02:29:55,751 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.078369
2011-07-07 02:29:56,252 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.099059
2011-07-07 02:29:56,754 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.109404
2011-07-07 02:29:57,255 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.130093
2011-07-07 02:29:57,757 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.143886
2011-07-07 02:29:58,258 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.164576
2011-07-07 02:29:58,760 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.174920
2011-07-07 02:29:59,261 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.209403
2011-07-07 02:29:59,763 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.219748
2011-07-07 02:30:00,265 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.243886
2011-07-07 02:30:00,766 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.254230
2011-07-07 02:30:01,267 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.274920
2011-07-07 02:30:01,769 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.285265
2011-07-07 02:30:02,270 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.309402
2011-07-07 02:30:02,772 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.319747
2011-07-07 02:30:03,273 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.347333
2011-07-07 02:30:03,774 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.350781
2011-07-07 02:30:04,276 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.385264
2011-07-07 02:30:04,777 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.385264
2011-07-07 02:30:05,278 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.419746
2011-07-07 02:30:05,780 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.433539
2011-07-07 02:30:06,281 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.457677
2011-07-07 02:30:06,782 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.468022
2011-07-07 02:30:07,283 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.488711
2011-07-07 02:30:07,785 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.499056
2011-07-07 02:30:08,286 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.526642
2011-07-07 02:30:08,788 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.533539
2011-07-07 02:30:09,289 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.564573
2011-07-07 02:30:09,791 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.578366
2011-07-07 02:30:10,292 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.599055
2011-07-07 02:30:10,793 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.619745
2011-07-07 02:30:11,295 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.633538
2011-07-07 02:30:11,797 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.654227
2011-07-07 02:30:12,298 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.664572
2011-07-07 02:30:12,800 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.685262
2011-07-07 02:30:12,920 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.697021
2011-07-07 02:30:12,921 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.698370
2011-07-07 02:30:13,423 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.708715
2011-07-07 02:30:13,924 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.729404
2011-07-07 02:30:14,426 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.743197
2011-07-07 02:30:14,927 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.753542
2011-07-07 02:30:15,429 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.788024
2011-07-07 02:30:15,930 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.798369
2011-07-07 02:30:16,432 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.819059
2011-07-07 02:30:16,933 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.832852
2011-07-07 02:30:17,434 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.853541
2011-07-07 02:30:17,936 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.870782
2011-07-07 02:30:18,439 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.877679
2011-07-07 02:30:18,941 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.908713
2011-07-07 02:30:19,442 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.919058
2011-07-07 02:30:19,943 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.943196
2011-07-07 02:30:20,445 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.960437
2011-07-07 02:30:20,946 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.974230
2011-07-07 02:30:21,448 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 86.998368
2011-07-07 02:30:21,949 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.012161
2011-07-07 02:30:22,450 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.032850
2011-07-07 02:30:22,952 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.056988
2011-07-07 02:30:23,453 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.056988
2011-07-07 02:30:23,955 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.088022
2011-07-07 02:30:24,457 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.108712
2011-07-07 02:30:24,959 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.122505
2011-07-07 02:30:25,460 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.143194
2011-07-07 02:30:25,962 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.153539
2011-07-07 02:30:26,463 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.177677
2011-07-07 02:30:26,965 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.188022
2011-07-07 02:30:27,466 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.208711
2011-07-07 02:30:27,967 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.222504
2011-07-07 02:30:28,469 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.253538
2011-07-07 02:30:28,971 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.253538
2011-07-07 02:30:29,472 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.288021
2011-07-07 02:30:29,974 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.288021
2011-07-07 02:30:30,475 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.322503
2011-07-07 02:30:30,977 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.332848
2011-07-07 02:30:31,478 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.353538
2011-07-07 02:30:31,979 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.367331
2011-07-07 02:30:32,481 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.388020
2011-07-07 02:30:32,982 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.401813
2011-07-07 02:30:33,484 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.432847
2011-07-07 02:30:33,985 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.432847
2011-07-07 02:30:34,486 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.467330
2011-07-07 02:30:34,988 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.467330
2011-07-07 02:30:35,490 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.498364
2011-07-07 02:30:35,991 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.519054
2011-07-07 02:30:36,492 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.529398
2011-07-07 02:30:36,993 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.553536
2011-07-07 02:30:37,495 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.563881
2011-07-07 02:30:37,997 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.588019
2011-07-07 02:30:38,499 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.598363
2011-07-07 02:30:39,000 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.619053
2011-07-07 02:30:39,502 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.643191
2011-07-07 02:30:40,003 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.663880
2011-07-07 02:30:40,505 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.674225
2011-07-07 02:30:41,006 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.698363
2011-07-07 02:30:41,508 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.708707
2011-07-07 02:30:42,009 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.729397
2011-07-07 02:30:42,510 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.739742
2011-07-07 02:30:43,012 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.763880
2011-07-07 02:30:43,513 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.788017
2011-07-07 02:30:44,015 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.832845
2011-07-07 02:30:44,516 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.853534
2011-07-07 02:30:45,018 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.898361
2011-07-07 02:30:45,519 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.922499
2011-07-07 02:30:46,021 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 87.981119
2011-07-07 02:30:46,523 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.008705
2011-07-07 02:30:47,024 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.036291
2011-07-07 02:30:47,526 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.077670
2011-07-07 02:30:48,027 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.094912
2011-07-07 02:30:48,529 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.115601
2011-07-07 02:30:49,030 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.167325
2011-07-07 02:30:49,532 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.201807
2011-07-07 02:30:50,033 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.229393
2011-07-07 02:30:50,535 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.253531
2011-07-07 02:30:51,036 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.274221
2011-07-07 02:30:51,537 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.322496
2011-07-07 02:30:52,039 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.367324
2011-07-07 02:30:52,540 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.398358
2011-07-07 02:30:53,042 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.432840
2011-07-07 02:30:53,544 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.463875
2011-07-07 02:30:54,045 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.505254
2011-07-07 02:30:54,547 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.529391
2011-07-07 02:30:55,048 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.553529
2011-07-07 02:30:55,549 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.598356
2011-07-07 02:30:56,050 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.625942
2011-07-07 02:30:56,552 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.670770
2011-07-07 02:30:57,053 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.701804
2011-07-07 02:30:57,554 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.725942
2011-07-07 02:30:58,056 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.746631
2011-07-07 02:30:58,557 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.767321
2011-07-07 02:30:59,059 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.815596
2011-07-07 02:30:59,560 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.846630
2011-07-07 02:31:00,061 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.863872
2011-07-07 02:31:00,562 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.912147
2011-07-07 02:31:01,064 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.939733
2011-07-07 02:31:01,565 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.974216
2011-07-07 02:31:02,067 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 88.988009
2011-07-07 02:31:02,568 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.036284
2011-07-07 02:31:03,069 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.077663
2011-07-07 02:31:03,570 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.098353
2011-07-07 02:31:04,072 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.129387
2011-07-07 02:31:04,573 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.156973
2011-07-07 02:31:05,074 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.184559
2011-07-07 02:31:05,576 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.215593
2011-07-07 02:31:06,078 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.270765
2011-07-07 02:31:06,579 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.270765
2011-07-07 02:31:07,081 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.339730
2011-07-07 02:31:07,582 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.343179
2011-07-07 02:31:08,083 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.384558
2011-07-07 02:31:08,585 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.432833
2011-07-07 02:31:09,086 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.456971
2011-07-07 02:31:09,588 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.481109
2011-07-07 02:31:10,089 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.491454
2011-07-07 02:31:10,591 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.515591
2011-07-07 02:31:11,092 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.529384
2011-07-07 02:31:11,593 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.553522
2011-07-07 02:31:12,095 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.567315
2011-07-07 02:31:12,596 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.591453
2011-07-07 02:31:13,098 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.605246
2011-07-07 02:31:13,599 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.629384
2011-07-07 02:31:14,100 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.632832
2011-07-07 02:31:14,601 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.667314
2011-07-07 02:31:15,103 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.688004
2011-07-07 02:31:15,604 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.701797
2011-07-07 02:31:16,105 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.725935
2011-07-07 02:31:16,606 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.739728
2011-07-07 02:31:17,108 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.760417
2011-07-07 02:31:17,609 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.774210
2011-07-07 02:31:18,111 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.788003
2011-07-07 02:31:18,612 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.808693
2011-07-07 02:31:19,113 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.825934
2011-07-07 02:31:19,615 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.850072
2011-07-07 02:31:20,117 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.877658
2011-07-07 02:31:20,618 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.891451
2011-07-07 02:31:21,120 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.915588
2011-07-07 02:31:21,621 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.929381
2011-07-07 02:31:22,123 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.950071
2011-07-07 02:31:22,624 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.963864
2011-07-07 02:31:23,125 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.984553
2011-07-07 02:31:23,627 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 89.998346
2011-07-07 02:31:24,128 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.022484
2011-07-07 02:31:24,629 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.036277
2011-07-07 02:31:25,131 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.060415
2011-07-07 02:31:25,632 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.074208
2011-07-07 02:31:26,133 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.094898
2011-07-07 02:31:26,635 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.119035
2011-07-07 02:31:27,136 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.119035
2011-07-07 02:31:27,638 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.153518
2011-07-07 02:31:28,139 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.156966
2011-07-07 02:31:28,641 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.191449
2011-07-07 02:31:29,142 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.208690
2011-07-07 02:31:29,643 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.222483
2011-07-07 02:31:30,145 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.246621
2011-07-07 02:31:30,646 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.274207
2011-07-07 02:31:31,148 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.284551
2011-07-07 02:31:31,649 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.308689
2011-07-07 02:31:32,151 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.322482
2011-07-07 02:31:32,652 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.346620
2011-07-07 02:31:33,153 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.363861
2011-07-07 02:31:33,655 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.381102
2011-07-07 02:31:34,156 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.401792
2011-07-07 02:31:34,657 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.422481
2011-07-07 02:31:35,159 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.432826
2011-07-07 02:31:35,660 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.456964
2011-07-07 02:31:36,162 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.470757
2011-07-07 02:31:36,663 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.494895
2011-07-07 02:31:37,164 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.508688
2011-07-07 02:31:37,666 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.536274
2011-07-07 02:31:38,167 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.553515
2011-07-07 02:31:38,668 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.567308
2011-07-07 02:31:39,169 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.587998
2011-07-07 02:31:39,671 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.612135
2011-07-07 02:31:40,172 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.625928
2011-07-07 02:31:40,674 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.653514
2011-07-07 02:31:41,175 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.667307
2011-07-07 02:31:41,676 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.694893
2011-07-07 02:31:42,177 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.705238
2011-07-07 02:31:42,679 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.729376
2011-07-07 02:31:43,180 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.746617
2011-07-07 02:31:43,681 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.770755
2011-07-07 02:31:44,182 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.784548
2011-07-07 02:31:44,684 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.794893
2011-07-07 02:31:45,185 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.819030
2011-07-07 02:31:45,687 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.832823
2011-07-07 02:31:46,188 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.867306
2011-07-07 02:31:46,689 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.870754
2011-07-07 02:31:47,191 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.908685
2011-07-07 02:31:47,692 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.912133
2011-07-07 02:31:48,193 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.946616
2011-07-07 02:31:48,695 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.956960
2011-07-07 02:31:49,196 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.981098
2011-07-07 02:31:49,698 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 90.994891
2011-07-07 02:31:50,200 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.012132
2011-07-07 02:31:50,701 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.029374
2011-07-07 02:31:51,202 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.053511
2011-07-07 02:31:51,704 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.063856
2011-07-07 02:31:52,205 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.087994
2011-07-07 02:31:52,707 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.112132
2011-07-07 02:31:53,208 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.125925
2011-07-07 02:31:53,709 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.150062
2011-07-07 02:31:54,210 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.163856
2011-07-07 02:31:54,711 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.187993
2011-07-07 02:31:55,213 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.215579
2011-07-07 02:31:55,714 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.225924
2011-07-07 02:31:56,216 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.250062
2011-07-07 02:31:56,717 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.263855
2011-07-07 02:31:57,218 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.287993
2011-07-07 02:31:57,719 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.301786
2011-07-07 02:31:58,221 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.325923
2011-07-07 02:31:58,722 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.339716
2011-07-07 02:31:59,224 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.367302
2011-07-07 02:31:59,725 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.381095
2011-07-07 02:32:00,226 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.408681
2011-07-07 02:32:00,728 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.419026
2011-07-07 02:32:01,229 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.443164
2011-07-07 02:32:01,731 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.456957
2011-07-07 02:32:02,232 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.474198
2011-07-07 02:32:02,733 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.498336
2011-07-07 02:32:03,235 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.508681
2011-07-07 02:32:03,736 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.532818
2011-07-07 02:32:04,237 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.560404
2011-07-07 02:32:04,739 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.570749
2011-07-07 02:32:05,240 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.594887
2011-07-07 02:32:05,741 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.608680
2011-07-07 02:32:06,243 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.632818
2011-07-07 02:32:06,744 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.653507
2011-07-07 02:32:07,246 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.667300
2011-07-07 02:32:07,747 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.684541
2011-07-07 02:32:08,249 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.712127
2011-07-07 02:32:08,750 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.725920
2011-07-07 02:32:09,252 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.736265
2011-07-07 02:32:09,753 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.760403
2011-07-07 02:32:10,254 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.787989
2011-07-07 02:32:10,756 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.805230
2011-07-07 02:32:11,257 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.812127
2011-07-07 02:32:11,759 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.846609
2011-07-07 02:32:12,260 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.850058
2011-07-07 02:32:12,762 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.877644
2011-07-07 02:32:13,263 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.901781
2011-07-07 02:32:13,764 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.912126
2011-07-07 02:32:14,266 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.936264
2011-07-07 02:32:14,767 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.950057
2011-07-07 02:32:15,269 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.974195
2011-07-07 02:32:15,770 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 91.984539
2011-07-07 02:32:16,271 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.008677
2011-07-07 02:32:16,772 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.032815
2011-07-07 02:32:17,274 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.046608
2011-07-07 02:32:17,774 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.067297
2011-07-07 02:32:18,276 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.084539
2011-07-07 02:32:18,777 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.105228
2011-07-07 02:32:19,279 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.122469
2011-07-07 02:32:19,780 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.146607
2011-07-07 02:32:20,281 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.160400
2011-07-07 02:32:20,783 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.184538
2011-07-07 02:32:21,284 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.198331
2011-07-07 02:32:21,786 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.219020
2011-07-07 02:32:22,287 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.232813
2011-07-07 02:32:22,788 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.256951
2011-07-07 02:32:23,290 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.284537
2011-07-07 02:32:23,791 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.298330
2011-07-07 02:32:24,292 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.315572
2011-07-07 02:32:24,793 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.336261
2011-07-07 02:32:25,295 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.346606
2011-07-07 02:32:25,796 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.374192
2011-07-07 02:32:26,297 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.401778
2011-07-07 02:32:26,799 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.415571
2011-07-07 02:32:27,300 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.425916
2011-07-07 02:32:27,801 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.453502
2011-07-07 02:32:28,303 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.477639
2011-07-07 02:32:28,804 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.491432
2011-07-07 02:32:29,305 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.505225
2011-07-07 02:32:29,807 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.525915
2011-07-07 02:32:30,308 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.543156
2011-07-07 02:32:30,810 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.567294
2011-07-07 02:32:31,311 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.594880
2011-07-07 02:32:31,813 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.608673
2011-07-07 02:32:32,314 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.619018
2011-07-07 02:32:32,816 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.650052
2011-07-07 02:32:33,317 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.667293
2011-07-07 02:32:33,819 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.684534
2011-07-07 02:32:34,320 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.712120
2011-07-07 02:32:34,821 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.722465
2011-07-07 02:32:35,323 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.722465
2011-07-07 02:32:35,824 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.760396
2011-07-07 02:32:36,325 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.784534
2011-07-07 02:32:36,826 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.805223
2011-07-07 02:32:37,328 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.822464
2011-07-07 02:32:37,829 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.846602
2011-07-07 02:32:38,331 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.860395
2011-07-07 02:32:38,832 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.884533
2011-07-07 02:32:39,333 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.898326
2011-07-07 02:32:39,835 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.915567
2011-07-07 02:32:40,336 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.922464
2011-07-07 02:32:40,838 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.950050
2011-07-07 02:32:41,339 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 92.974188
2011-07-07 02:32:41,840 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.001774
2011-07-07 02:32:42,342 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.015567
2011-07-07 02:32:42,843 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.039704
2011-07-07 02:32:43,345 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.053497
2011-07-07 02:32:43,846 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.074187
2011-07-07 02:32:44,348 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.091428
2011-07-07 02:32:44,849 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.115566
2011-07-07 02:32:45,350 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.129359
2011-07-07 02:32:45,852 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.153497
2011-07-07 02:32:46,353 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.163841
2011-07-07 02:32:46,854 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.187979
2011-07-07 02:32:47,356 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.208669
2011-07-07 02:32:47,857 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.229358
2011-07-07 02:32:48,359 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.250048
2011-07-07 02:32:48,860 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.267289
2011-07-07 02:32:49,362 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.284530
2011-07-07 02:32:49,863 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.294875
2011-07-07 02:32:50,365 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.319013
2011-07-07 02:32:50,866 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.346599
2011-07-07 02:32:51,367 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.360392
2011-07-07 02:32:51,869 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.384529
2011-07-07 02:32:52,370 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.398322
2011-07-07 02:32:52,872 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.422460
2011-07-07 02:32:53,373 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.446598
2011-07-07 02:32:53,875 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.460391
2011-07-07 02:32:54,376 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.474184
2011-07-07 02:32:54,877 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.498322
2011-07-07 02:32:55,378 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.508667
2011-07-07 02:32:55,880 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.536253
2011-07-07 02:32:56,381 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.563839
2011-07-07 02:32:56,883 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.577632
2011-07-07 02:32:57,384 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.587976
2011-07-07 02:32:57,886 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.612114
2011-07-07 02:32:58,387 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.639700
2011-07-07 02:32:58,889 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.653493
2011-07-07 02:32:59,390 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.667286
2011-07-07 02:32:59,892 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.691424
2011-07-07 02:33:00,393 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.694872
2011-07-07 02:33:00,894 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.729355
2011-07-07 02:33:01,396 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.743148
2011-07-07 02:33:01,897 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.770734
2011-07-07 02:33:02,398 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.794871
2011-07-07 02:33:02,899 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.798320
2011-07-07 02:33:03,401 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.829354
2011-07-07 02:33:03,902 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.846595
2011-07-07 02:33:04,403 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.860388
2011-07-07 02:33:04,905 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.874181
2011-07-07 02:33:05,406 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.894871
2011-07-07 02:33:05,907 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.922457
2011-07-07 02:33:06,409 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.946594
2011-07-07 02:33:06,910 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.963836
2011-07-07 02:33:07,412 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 93.974180
2011-07-07 02:33:07,913 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.001766
2011-07-07 02:33:08,415 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.012111
2011-07-07 02:33:08,916 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.046594
2011-07-07 02:33:09,417 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.060387
2011-07-07 02:33:09,919 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.081076
2011-07-07 02:33:10,420 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.087973
2011-07-07 02:33:10,922 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.112111
2011-07-07 02:33:11,423 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.125904
2011-07-07 02:33:11,924 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.160386
2011-07-07 02:33:12,426 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.160386
2011-07-07 02:33:12,927 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.198317
2011-07-07 02:33:13,428 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.205213
2011-07-07 02:33:13,930 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.236248
2011-07-07 02:33:14,432 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.253489
2011-07-07 02:33:14,933 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.260385
2011-07-07 02:33:15,434 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.287971
2011-07-07 02:33:15,935 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.312109
2011-07-07 02:33:16,437 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.325902
2011-07-07 02:33:16,938 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.353488
2011-07-07 02:33:17,439 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.367281
2011-07-07 02:33:17,941 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.391419
2011-07-07 02:33:18,442 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.391419
2011-07-07 02:33:18,943 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.429350
2011-07-07 02:33:19,445 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.446591
2011-07-07 02:33:19,946 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.467280
2011-07-07 02:33:20,448 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.477625
2011-07-07 02:33:20,949 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.505211
2011-07-07 02:33:21,450 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.519004
2011-07-07 02:33:21,951 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.546590
2011-07-07 02:33:22,453 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.560383
2011-07-07 02:33:22,954 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.570728
2011-07-07 02:33:23,455 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.594866
2011-07-07 02:33:23,957 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.608659
2011-07-07 02:33:24,458 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.643141
2011-07-07 02:33:24,959 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.653486
2011-07-07 02:33:25,461 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.681072
2011-07-07 02:33:25,962 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.694865
2011-07-07 02:33:26,463 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.719003
2011-07-07 02:33:26,965 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.732796
2011-07-07 02:33:27,466 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.746589
2011-07-07 02:33:27,968 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.774175
2011-07-07 02:33:28,469 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.798313
2011-07-07 02:33:28,971 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.805209
2011-07-07 02:33:29,472 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.832795
2011-07-07 02:33:29,973 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.856933
2011-07-07 02:33:30,475 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.870726
2011-07-07 02:33:30,976 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.894864
2011-07-07 02:33:31,478 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.908657
2011-07-07 02:33:31,980 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.932794
2011-07-07 02:33:32,481 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.950036
2011-07-07 02:33:32,982 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.960380
2011-07-07 02:33:33,483 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.984518
2011-07-07 02:33:33,985 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 94.998311
2011-07-07 02:33:34,486 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.022449
2011-07-07 02:33:34,987 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.036242
2011-07-07 02:33:35,489 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.060380
2011-07-07 02:33:35,990 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.074173
2011-07-07 02:33:36,491 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.108655
2011-07-07 02:33:36,993 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.108655
2011-07-07 02:33:37,494 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.146586
2011-07-07 02:33:37,996 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.160379
2011-07-07 02:33:38,497 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.177620
2011-07-07 02:33:38,999 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.201758
2011-07-07 02:33:39,500 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.215551
2011-07-07 02:33:40,001 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.243137
2011-07-07 02:33:40,503 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.256930
2011-07-07 02:33:41,004 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.267275
2011-07-07 02:33:41,505 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.294861
2011-07-07 02:33:42,006 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.305206
2011-07-07 02:33:42,508 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.339688
2011-07-07 02:33:43,009 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.356929
2011-07-07 02:33:43,510 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.367274
2011-07-07 02:33:44,012 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.391412
2011-07-07 02:33:44,513 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.405205
2011-07-07 02:33:45,015 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.432791
2011-07-07 02:33:45,516 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.446584
2011-07-07 02:33:46,018 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.474170
2011-07-07 02:33:46,519 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.484515
2011-07-07 02:33:47,021 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.508652
2011-07-07 02:33:47,522 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.525894
2011-07-07 02:33:48,023 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.550031
2011-07-07 02:33:48,525 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.563824
2011-07-07 02:33:49,026 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.587962
2011-07-07 02:33:49,528 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.608652
2011-07-07 02:33:50,029 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.625893
2011-07-07 02:33:50,531 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.650031
2011-07-07 02:33:51,032 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.667272
2011-07-07 02:33:51,533 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.677617
2011-07-07 02:33:52,035 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.701754
2011-07-07 02:33:52,536 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.718996
2011-07-07 02:33:53,038 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.743134
2011-07-07 02:33:53,539 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.756927
2011-07-07 02:33:54,041 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.784513
2011-07-07 02:33:54,542 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.794857
2011-07-07 02:33:55,043 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.818995
2011-07-07 02:33:55,545 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.832788
2011-07-07 02:33:56,046 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.856926
2011-07-07 02:33:56,548 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.874167
2011-07-07 02:33:57,049 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.894857
2011-07-07 02:33:57,551 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.905201
2011-07-07 02:33:58,052 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.932787
2011-07-07 02:33:58,554 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.956925
2011-07-07 02:33:59,055 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.970718
2011-07-07 02:33:59,556 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 95.998304
2011-07-07 02:34:00,058 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.008649
2011-07-07 02:34:00,559 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.032787
2011-07-07 02:34:01,060 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.056924
2011-07-07 02:34:01,562 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.074166
2011-07-07 02:34:02,063 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.084510
2011-07-07 02:34:02,564 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.108648
2011-07-07 02:34:03,066 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.122441
2011-07-07 02:34:03,567 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.150027
2011-07-07 02:34:04,069 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.163820
2011-07-07 02:34:04,571 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.191406
2011-07-07 02:34:05,072 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.205199
2011-07-07 02:34:05,573 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.215544
2011-07-07 02:34:06,075 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.246578
2011-07-07 02:34:06,576 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.256923
2011-07-07 02:34:07,078 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.281061
2011-07-07 02:34:07,579 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.305199
2011-07-07 02:34:08,081 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.318992
2011-07-07 02:34:08,582 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.343129
2011-07-07 02:34:09,083 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.356922
2011-07-07 02:34:09,585 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.381060
2011-07-07 02:34:10,086 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.394853
2011-07-07 02:34:10,588 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.418991
2011-07-07 02:34:11,089 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.429336
2011-07-07 02:34:11,591 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.456922
2011-07-07 02:34:12,092 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.477611
2011-07-07 02:34:12,594 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.494852
2011-07-07 02:34:13,095 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.508645
2011-07-07 02:34:13,596 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.525887
2011-07-07 02:34:14,097 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.546576
2011-07-07 02:34:14,599 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.560369
2011-07-07 02:34:15,100 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.594852
2011-07-07 02:34:15,601 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.608645
2011-07-07 02:34:16,102 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.632782
2011-07-07 02:34:16,603 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.650024
2011-07-07 02:34:17,104 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.663817
2011-07-07 02:34:17,605 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.691403
2011-07-07 02:34:18,107 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.705196
2011-07-07 02:34:18,608 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.729333
2011-07-07 02:34:19,110 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.746575
2011-07-07 02:34:19,611 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.760368
2011-07-07 02:34:20,112 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.774161
2011-07-07 02:34:20,614 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.794850
2011-07-07 02:34:21,115 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.822436
2011-07-07 02:34:21,616 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.850022
2011-07-07 02:34:22,118 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.863815
2011-07-07 02:34:22,619 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.874160
2011-07-07 02:34:23,120 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.901746
2011-07-07 02:34:23,621 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.922436
2011-07-07 02:34:24,123 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.939677
2011-07-07 02:34:24,624 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.953470
2011-07-07 02:34:25,126 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 96.981056
2011-07-07 02:34:25,627 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.001745
2011-07-07 02:34:26,129 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.005194
2011-07-07 02:34:26,630 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.043124
2011-07-07 02:34:27,132 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.056917
2011-07-07 02:34:27,633 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.070710
2011-07-07 02:34:28,134 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.091400
2011-07-07 02:34:28,636 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.098296
2011-07-07 02:34:29,137 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.132779
2011-07-07 02:34:29,639 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.160365
2011-07-07 02:34:30,140 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.174158
2011-07-07 02:34:30,642 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.184503
2011-07-07 02:34:31,143 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.208640
2011-07-07 02:34:31,644 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.218985
2011-07-07 02:34:32,146 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.253468
2011-07-07 02:34:32,647 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.253468
2011-07-07 02:34:33,149 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.291398
2011-07-07 02:34:33,650 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.305191
2011-07-07 02:34:34,152 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.318984
2011-07-07 02:34:34,653 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.346570
2011-07-07 02:34:35,155 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.360363
2011-07-07 02:34:35,656 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.384501
2011-07-07 02:34:36,157 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.391398
2011-07-07 02:34:36,659 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.422432
2011-07-07 02:34:37,160 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.439673
2011-07-07 02:34:37,661 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.456915
2011-07-07 02:34:38,163 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.474156
2011-07-07 02:34:38,664 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.498294
2011-07-07 02:34:39,165 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.512087
2011-07-07 02:34:39,667 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.522431
2011-07-07 02:34:40,168 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.546569
2011-07-07 02:34:40,670 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.556914
2011-07-07 02:34:41,171 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.594845
2011-07-07 02:34:41,672 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.608638
2011-07-07 02:34:42,173 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.632775
2011-07-07 02:34:42,675 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.636224
2011-07-07 02:34:43,176 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.670706
2011-07-07 02:34:43,678 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.687947
2011-07-07 02:34:44,179 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.701740
2011-07-07 02:34:44,680 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.722430
2011-07-07 02:34:45,181 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.746568
2011-07-07 02:34:45,683 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.760361
2011-07-07 02:34:46,184 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.787947
2011-07-07 02:34:46,686 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.805188
2011-07-07 02:34:47,187 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.825877
2011-07-07 02:34:47,689 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.839670
2011-07-07 02:34:48,190 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.863808
2011-07-07 02:34:48,692 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.877601
2011-07-07 02:34:49,193 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.898291
2011-07-07 02:34:49,694 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.918980
2011-07-07 02:34:50,196 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.946566
2011-07-07 02:34:50,697 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.956911
2011-07-07 02:34:51,199 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.981049
2011-07-07 02:34:51,700 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 97.994842
2011-07-07 02:34:52,202 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.012083
2011-07-07 02:34:52,703 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.036221
2011-07-07 02:34:53,204 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.046566
2011-07-07 02:34:53,706 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.070703
2011-07-07 02:34:54,207 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.084496
2011-07-07 02:34:54,708 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.101738
2011-07-07 02:34:55,210 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.115531
2011-07-07 02:34:55,711 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.150013
2011-07-07 02:34:56,212 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.150013
2011-07-07 02:34:56,714 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.187944
2011-07-07 02:34:57,215 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.201737
2011-07-07 02:34:57,716 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.215530
2011-07-07 02:34:58,217 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.236219
2011-07-07 02:34:58,719 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.256909
2011-07-07 02:34:59,220 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.284495
2011-07-07 02:34:59,722 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.294840
2011-07-07 02:35:00,223 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.318977
2011-07-07 02:35:00,725 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.332770
2011-07-07 02:35:01,226 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.360356
2011-07-07 02:35:01,727 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.377598
2011-07-07 02:35:02,229 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.384494
2011-07-07 02:35:02,730 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.412080
2011-07-07 02:35:03,232 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.436218
2011-07-07 02:35:03,734 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.450011
2011-07-07 02:35:04,235 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.477597
2011-07-07 02:35:04,736 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.494838
2011-07-07 02:35:05,238 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.515528
2011-07-07 02:35:05,739 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.532769
2011-07-07 02:35:06,241 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.550010
2011-07-07 02:35:06,742 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.560355
2011-07-07 02:35:07,244 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.594838
2011-07-07 02:35:07,745 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.608631
2011-07-07 02:35:08,247 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.636217
2011-07-07 02:35:08,748 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.646561
2011-07-07 02:35:09,249 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.670699
2011-07-07 02:35:09,751 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.684492
2011-07-07 02:35:10,252 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.705182
2011-07-07 02:35:10,753 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.722423
2011-07-07 02:35:11,255 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.746561
2011-07-07 02:35:11,756 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.756905
2011-07-07 02:35:12,258 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.781043
2011-07-07 02:35:12,759 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.798284
2011-07-07 02:35:13,261 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.822422
2011-07-07 02:35:13,762 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.836215
2011-07-07 02:35:14,264 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.860353
2011-07-07 02:35:14,765 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.884491
2011-07-07 02:35:15,267 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.898284
2011-07-07 02:35:15,768 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.915525
2011-07-07 02:35:16,269 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.939663
2011-07-07 02:35:16,770 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.950007
2011-07-07 02:35:17,271 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 98.974145
2011-07-07 02:35:17,773 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.001731
2011-07-07 02:35:18,274 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.015524
2011-07-07 02:35:18,775 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.043110
2011-07-07 02:35:19,277 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.053455
2011-07-07 02:35:19,778 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.077593
2011-07-07 02:35:20,279 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.091386
2011-07-07 02:35:20,781 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.108627
2011-07-07 02:35:21,282 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.132765
2011-07-07 02:35:21,784 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.146558
2011-07-07 02:35:22,285 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.170696
2011-07-07 02:35:22,786 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.194833
2011-07-07 02:35:23,288 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.208626
2011-07-07 02:35:23,789 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.232764
2011-07-07 02:35:24,291 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.246557
2011-07-07 02:35:24,793 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.270695
2011-07-07 02:35:25,294 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.284488
2011-07-07 02:35:25,795 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.298281
2011-07-07 02:35:26,297 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.325867
2011-07-07 02:35:26,798 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.346556
2011-07-07 02:35:27,299 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.367246
2011-07-07 02:35:27,800 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.377591
2011-07-07 02:35:28,302 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.401728
2011-07-07 02:35:28,803 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.415521
2011-07-07 02:35:29,305 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.439659
2011-07-07 02:35:29,806 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.453452
2011-07-07 02:35:30,308 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.477590
2011-07-07 02:35:30,809 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.481038
2011-07-07 02:35:31,311 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.515521
2011-07-07 02:35:31,812 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.543107
2011-07-07 02:35:32,314 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.556900
2011-07-07 02:35:32,815 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.567244
2011-07-07 02:35:33,316 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.601727
2011-07-07 02:35:33,817 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.629313
2011-07-07 02:35:34,319 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.674140
2011-07-07 02:35:34,820 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.698278
2011-07-07 02:35:35,322 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.743105
2011-07-07 02:35:35,823 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.787933
2011-07-07 02:35:36,324 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.818967
2011-07-07 02:35:36,825 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.843105
2011-07-07 02:35:37,327 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.863794
2011-07-07 02:35:37,828 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.922414
2011-07-07 02:35:38,330 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.946552
2011-07-07 02:35:38,831 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 99.974138
2011-07-07 02:35:38,939 DEBUG: download progress <Package: name:'fglrx' architecture='amd64' id:4674L> 100.000000
2011-07-07 02:35:39,667 DEBUG: install progress dpkg-exec 0.000000
2011-07-07 02:35:40,273 DEBUG: install progress patch 0.000000
2011-07-07 02:35:40,373 DEBUG: install progress patch 4.000000
2011-07-07 02:35:40,798 DEBUG: install progress patch 8.000000
2011-07-07 02:35:40,882 DEBUG: install progress patch 12.000000
2011-07-07 02:35:41,343 DEBUG: install progress dkms 12.000000
2011-07-07 02:35:41,344 DEBUG: install progress dkms 16.000000
2011-07-07 02:35:41,921 DEBUG: install progress dkms 20.000000
2011-07-07 02:35:42,006 DEBUG: install progress dkms 24.000000
2011-07-07 02:35:42,444 DEBUG: install progress fakeroot 24.000000
2011-07-07 02:35:42,545 DEBUG: install progress fakeroot 28.000000
2011-07-07 02:35:42,955 DEBUG: install progress fakeroot 32.000000
2011-07-07 02:35:43,051 DEBUG: install progress fakeroot 36.000000
2011-07-07 02:35:43,635 DEBUG: install progress fglrx 36.000000
2011-07-07 02:35:43,636 DEBUG: install progress fglrx 40.000000
2011-07-07 02:35:47,762 DEBUG: install progress fglrx 44.000000
2011-07-07 02:35:47,847 DEBUG: install progress fglrx 48.000000
2011-07-07 02:35:48,140 DEBUG: install progress fglrx-amdcccle 48.000000
2011-07-07 02:35:48,241 DEBUG: install progress fglrx-amdcccle 52.000000
2011-07-07 02:35:48,781 DEBUG: install progress fglrx-amdcccle 56.000000
2011-07-07 02:35:48,865 DEBUG: install progress fglrx-amdcccle 60.000000
2011-07-07 02:35:48,965 DEBUG: install progress man-db 60.000000
2011-07-07 02:35:52,391 DEBUG: install progress ureadahead 60.000000
2011-07-07 02:35:52,856 DEBUG: install progress dpkg-exec 60.000000
2011-07-07 02:35:52,964 DEBUG: install progress patch 60.000000
2011-07-07 02:35:53,084 DEBUG: install progress patch 64.000000
2011-07-07 02:35:53,206 DEBUG: install progress patch 68.000000
2011-07-07 02:35:53,329 DEBUG: install progress dkms 68.000000
2011-07-07 02:35:54,957 DEBUG: install progress dkms 72.000000
2011-07-07 02:35:55,100 DEBUG: install progress dkms 76.000000
2011-07-07 02:35:55,236 DEBUG: install progress fakeroot 76.000000
2011-07-07 02:35:55,370 DEBUG: install progress fakeroot 80.000000
2011-07-07 02:35:55,532 DEBUG: install progress fakeroot 84.000000
2011-07-07 02:35:55,662 DEBUG: install progress fglrx 84.000000
2011-07-07 02:35:56,055 DEBUG: install progress fglrx 88.000000
2011-07-07 02:36:59,423 DEBUG: install progress fglrx 92.000000
2011-07-07 02:37:00,195 DEBUG: install progress bamfdaemon 92.000000
2011-07-07 02:37:00,453 DEBUG: install progress gnome-menus 92.000000
2011-07-07 02:37:00,787 DEBUG: install progress fglrx-amdcccle 92.000000
2011-07-07 02:37:00,933 DEBUG: install progress fglrx-amdcccle 96.000000
2011-07-07 02:37:01,056 DEBUG: install progress fglrx-amdcccle 100.000000
2011-07-07 02:37:01,168 DEBUG: install progress initramfs-tools 100.000000
2011-07-07 02:37:28,912 DEBUG: install progress libc-bin 100.000000
2011-07-07 02:37:30,318 DEBUG: Selecting previously deselected package patch.
(Reading database ... 165488 files and directories currently installed.)
Unpacking patch (from .../patch_2.6.1-2_amd64.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.1.1.2-5ubuntu1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.16-1_amd64.deb) ...
Selecting previously deselected package fglrx.
Unpacking fglrx (from .../fglrx_2%3a8.861-0ubuntu2_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.861-0ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up patch (2.6.1-2) ...
Setting up dkms (2.1.1.2-5ubuntu1) ...
Setting up fakeroot (1.16-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up fglrx (2:8.861-0ubuntu2) ...
update-alternatives: renaming x86_64-linux-gnu_xorg_extra_modules slave link from /usr/lib/x86_64-linux-gnu/xorg/extra-modules to /usr/lib/xorg/extra-modules.
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.0-2-generic
Loading new fglrx-8.861 DKMS files...
First Installation: checking all kernels...
Building for 3.0-2-generic and 3.0-3-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 3.0-3-generic
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0-3-generic/updates/dkms/

depmod........

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle (2:8.861-0ubuntu2) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0-3-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-07-07 02:37:30,707 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-07 02:37:30,707 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-07-07 02:37:30,707 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-07-07 02:38:13,663 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 02:38:13,663 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 02:38:13,745 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 02:38:13,745 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 02:38:19,243 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 02:38:19,244 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 02:38:19,326 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 02:38:19,326 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 02:38:19,441 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 02:38:19,441 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 02:38:19,523 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 02:38:19,524 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 02:38:19,655 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 02:38:19,656 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 02:38:19,738 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 02:38:19,739 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 02:38:21,960 DEBUG: Shutting down
2011-07-07 03:46:05,705 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8>
2011-07-07 03:46:07,993 DEBUG: reading modalias file /lib/modules/3.0-2-generic/modules.alias
2011-07-07 03:46:08,144 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-07-07 03:46:08,153 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-07-07 03:46:08,267 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-07-07 03:46:08,291 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-07-07 03:46:08,322 DEBUG: Software modem not available
2011-07-07 03:46:08,322 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-07-07 03:46:08,428 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-07-07 03:46:08,441 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-07-07 03:46:08,441 DEBUG: nvidia.available: falling back to default
2011-07-07 03:46:08,608 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-07-07 03:46:08,608 DEBUG: NVIDIA accelerated graphics driver not available
2011-07-07 03:46:08,618 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-07-07 03:46:08,631 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-07-07 03:46:08,631 DEBUG: nvidia.available: falling back to default
2011-07-07 03:46:08,720 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-07 03:46:08,721 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 947, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-07-07 03:46:08,744 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-07-07 03:46:08,756 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-07-07 03:46:08,757 DEBUG: nvidia.available: falling back to default
2011-07-07 03:46:08,844 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-07 03:46:08,845 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-07-07 03:46:08,857 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-07 03:46:08,900 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-07-07 03:46:08,901 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-07-07 03:46:08,901 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-07-07 03:46:08,915 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-07 03:46:08,928 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-07-07 03:46:08,929 DEBUG: fglrx.available: falling back to default
2011-07-07 03:46:09,016 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-07-07 03:46:09,017 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-07-07 03:46:09,095 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-07-07 03:46:09,096 DEBUG: Firmware for DVB cards not available
2011-07-07 03:46:09,096 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-07-07 03:46:09,108 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-07-07 03:46:09,110 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-07-07 03:46:09,110 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-07-07 03:46:09,110 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-07-07 03:46:09,201 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-07-07 03:46:09,202 DEBUG: Experimental 3D support for NVIDIA cards not available
2011-07-07 03:46:09,203 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-07-07 03:46:09,213 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-07-07 03:46:09,214 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-07-07 03:46:09,257 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-07-07 03:46:09,258 DEBUG: all custom handlers loaded
2011-07-07 03:46:09,258 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-07 03:46:09,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'input:b0003v046DpC526e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-07-07 03:46:09,466 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:09,467 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'acpi:PNP0501:')
2011-07-07 03:46:09,467 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-07 03:46:09,467 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000082C6bc02sc00i00')
2011-07-07 03:46:09,502 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:09,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-07 03:46:09,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-07-07 03:46:09,532 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-07 03:46:09,532 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:09,532 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2011-07-07 03:46:09,563 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:09,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2011-07-07 03:46:09,564 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:09,564 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:09,564 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-07 03:46:09,564 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'platform:pcspkr')
2011-07-07 03:46:09,565 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:09,565 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:09,565 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-07-07 03:46:09,566 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'pci:v00001022d00009600sv00001043sd000082EEbc06sc00i00')
2011-07-07 03:46:09,582 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2011-07-07 03:46:09,583 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:09,583 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:09,583 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-07-07 03:46:09,583 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-07 03:46:09,583 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'pci:v00001002d00006719sv00001043sd000003BAbc03sc00i00')
2011-07-07 03:46:09,929 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-07 03:46:09,935 DEBUG: fglrx.available: falling back to default
2011-07-07 03:46:10,638 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 03:46:10,639 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 03:46:09,954 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-07-07 03:46:10,640 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,640 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd000082EFbc01sc01i8a')
2011-07-07 03:46:10,652 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-07 03:46:10,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2011-07-07 03:46:10,654 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,654 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2011-07-07 03:46:10,655 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic01isc01ip00')
2011-07-07 03:46:10,658 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,658 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'usb:v04E8p343Dd0100dc00dsc00dp00ic07isc01ip02')
2011-07-07 03:46:10,692 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,692 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-07-07 03:46:10,716 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,716 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-07-07 03:46:10,717 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,717 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'acpi:PNP0400:')
2011-07-07 03:46:10,718 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-07-07 03:46:10,729 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'input:b0003v046Dp0809e0010-e0,1,kD4,ramlsfw')
2011-07-07 03:46:10,729 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,730 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr2601:bd06/28/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM3A78-CM:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-07-07 03:46:10,771 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'acpi:PNP0700:')
2011-07-07 03:46:10,771 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'usb:v046DpC526d0500dc00dsc00dp00ic03isc00ip00')
2011-07-07 03:46:10,774 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,774 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2011-07-07 03:46:10,775 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-07-07 03:46:10,776 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,776 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,776 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'usb:v04E8p343Dd0100dc00dsc00dp00icFFiscFFipFF')
2011-07-07 03:46:10,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-07-07 03:46:10,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic0Eisc01ip00')
2011-07-07 03:46:10,781 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,782 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd000082EFbc0Csc03i20')
2011-07-07 03:46:10,793 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'input:b0003v046DpC526e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-07-07 03:46:10,794 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,794 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,794 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-07 03:46:10,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd000082EFbc01sc06i01')
2011-07-07 03:46:10,806 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,806 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,807 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'usb:v046DpC526d0500dc00dsc00dp00ic03isc01ip02')
2011-07-07 03:46:10,809 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,809 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,810 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'acpi:PNP0800:')
2011-07-07 03:46:10,810 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic01isc02ip00')
2011-07-07 03:46:10,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'pci:v00001002d0000AA80sv00001043sd0000AA80bc04sc03i00')
2011-07-07 03:46:10,823 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,823 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-07 03:46:10,824 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic0Eisc02ip00')
2011-07-07 03:46:10,826 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-07 03:46:10,827 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2011-07-07 03:46:10,829 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,829 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'pci:v00001002d00004385sv00001043sd000082EFbc0Csc05i00')
2011-07-07 03:46:10,840 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,840 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd000082EFbc06sc01i00')
2011-07-07 03:46:10,852 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-07 03:46:10,853 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,853 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,853 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-07-07 03:46:10,854 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,854 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd000082EAbc04sc03i00')
2011-07-07 03:46:10,865 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,866 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 03:46:10,866 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x136e2d8> about HardwareID('modalias', 'acpi:PNP0103:')
2011-07-07 03:46:10,866 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-07 03:46:10,866 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'input:b0003v046DpC526e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-07-07 03:46:10,867 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'acpi:PNP0501:')
2011-07-07 03:46:10,867 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-07 03:46:10,867 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000082C6bc02sc00i00')
2011-07-07 03:46:10,867 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-07 03:46:10,868 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-07-07 03:46:10,868 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-07 03:46:10,868 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2011-07-07 03:46:10,868 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2011-07-07 03:46:10,869 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-07 03:46:10,869 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'platform:pcspkr')
2011-07-07 03:46:10,869 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-07-07 03:46:10,869 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'pci:v00001022d00009600sv00001043sd000082EEbc06sc00i00')
2011-07-07 03:46:10,870 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2011-07-07 03:46:10,870 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-07-07 03:46:10,870 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-07 03:46:10,870 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'pci:v00001002d00006719sv00001043sd000003BAbc03sc00i00')
2011-07-07 03:46:10,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd000082EFbc01sc01i8a')
2011-07-07 03:46:10,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-07 03:46:10,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2011-07-07 03:46:10,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2011-07-07 03:46:10,871 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic01isc01ip00')
2011-07-07 03:46:10,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'usb:v04E8p343Dd0100dc00dsc00dp00ic07isc01ip02')
2011-07-07 03:46:10,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-07-07 03:46:10,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-07-07 03:46:10,872 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'acpi:PNP0400:')
2011-07-07 03:46:10,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-07-07 03:46:10,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'input:b0003v046Dp0809e0010-e0,1,kD4,ramlsfw')
2011-07-07 03:46:10,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr2601:bd06/28/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM3A78-CM:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-07-07 03:46:10,873 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'acpi:PNP0700:')
2011-07-07 03:46:10,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'usb:v046DpC526d0500dc00dsc00dp00ic03isc00ip00')
2011-07-07 03:46:10,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2011-07-07 03:46:10,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-07-07 03:46:10,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'usb:v04E8p343Dd0100dc00dsc00dp00icFFiscFFipFF')
2011-07-07 03:46:10,874 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-07-07 03:46:10,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic0Eisc01ip00')
2011-07-07 03:46:10,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd000082EFbc0Csc03i20')
2011-07-07 03:46:10,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'input:b0003v046DpC526e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-07-07 03:46:10,875 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-07 03:46:10,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd000082EFbc01sc06i01')
2011-07-07 03:46:10,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'usb:v046DpC526d0500dc00dsc00dp00ic03isc01ip02')
2011-07-07 03:46:10,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'acpi:PNP0800:')
2011-07-07 03:46:10,876 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic01isc02ip00')
2011-07-07 03:46:10,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'pci:v00001002d0000AA80sv00001043sd0000AA80bc04sc03i00')
2011-07-07 03:46:10,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-07 03:46:10,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic0Eisc02ip00')
2011-07-07 03:46:10,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-07 03:46:10,877 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2011-07-07 03:46:10,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'pci:v00001002d00004385sv00001043sd000082EFbc0Csc05i00')
2011-07-07 03:46:10,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd000082EFbc06sc01i00')
2011-07-07 03:46:10,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-07 03:46:10,878 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-07-07 03:46:10,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd000082EAbc04sc03i00')
2011-07-07 03:46:10,879 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1935b00> about HardwareID('modalias', 'acpi:PNP0103:')
2011-07-07 03:46:10,978 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 03:46:10,978 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 03:46:11,111 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 03:46:11,111 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 03:46:11,180 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 03:46:11,181 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 03:46:19,773 DEBUG: Shutting down
2011-07-07 08:27:55,910 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8>
2011-07-07 08:27:57,700 DEBUG: reading modalias file /lib/modules/3.0-2-generic/modules.alias
2011-07-07 08:27:57,861 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-07-07 08:27:57,862 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-07-07 08:27:57,973 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-07-07 08:27:57,998 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-07-07 08:27:58,028 DEBUG: Software modem not available
2011-07-07 08:27:58,028 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-07-07 08:27:58,145 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-07-07 08:27:58,158 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-07-07 08:27:58,159 DEBUG: nvidia.available: falling back to default
2011-07-07 08:27:58,376 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-07-07 08:27:58,376 DEBUG: NVIDIA accelerated graphics driver not available
2011-07-07 08:27:58,387 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-07-07 08:27:58,400 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-07-07 08:27:58,400 DEBUG: nvidia.available: falling back to default
2011-07-07 08:27:58,486 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-07 08:27:58,487 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 947, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-07-07 08:27:58,517 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-07-07 08:27:58,530 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-07-07 08:27:58,531 DEBUG: nvidia.available: falling back to default
2011-07-07 08:27:58,617 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-07-07 08:27:58,617 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-07-07 08:27:58,630 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-07-07 08:27:58,673 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-07-07 08:27:58,674 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-07-07 08:27:58,674 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-07-07 08:27:58,689 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-07 08:27:58,702 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-07-07 08:27:58,703 DEBUG: fglrx.available: falling back to default
2011-07-07 08:27:58,790 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-07-07 08:27:58,791 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-07-07 08:27:58,870 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-07-07 08:27:58,871 DEBUG: Firmware for DVB cards not available
2011-07-07 08:27:58,872 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-07-07 08:27:58,884 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-07-07 08:27:58,886 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-07-07 08:27:58,886 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-07-07 08:27:58,886 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-07-07 08:27:58,975 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-07-07 08:27:58,976 DEBUG: Experimental 3D support for NVIDIA cards not available
2011-07-07 08:27:58,976 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-07-07 08:27:58,987 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-07-07 08:27:58,988 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-07-07 08:27:59,035 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-07-07 08:27:59,035 DEBUG: all custom handlers loaded
2011-07-07 08:27:59,036 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-07 08:27:59,036 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'input:b0003v046DpC526e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-07-07 08:27:59,299 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:27:59,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'acpi:PNP0501:')
2011-07-07 08:27:59,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-07 08:27:59,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000082C6bc02sc00i00')
2011-07-07 08:27:59,336 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:27:59,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-07 08:27:59,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-07-07 08:27:59,402 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-07 08:27:59,403 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:27:59,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2011-07-07 08:27:59,483 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:27:59,484 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2011-07-07 08:27:59,486 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:27:59,486 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:27:59,487 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-07 08:27:59,487 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'platform:pcspkr')
2011-07-07 08:27:59,488 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:27:59,489 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:27:59,489 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-07-07 08:27:59,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'pci:v00001022d00009600sv00001043sd000082EEbc06sc00i00')
2011-07-07 08:27:59,532 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2011-07-07 08:27:59,534 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:27:59,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:27:59,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-07-07 08:27:59,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-07 08:27:59,536 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'pci:v00001002d00006719sv00001043sd000003BAbc03sc00i00')
2011-07-07 08:27:59,946 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-07 08:27:59,952 DEBUG: fglrx.available: falling back to default
2011-07-07 08:28:00,734 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 08:28:00,734 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 08:27:59,972 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-07-07 08:28:00,735 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,735 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd000082EFbc01sc01i8a')
2011-07-07 08:28:00,747 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,748 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-07 08:28:00,748 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2011-07-07 08:28:00,749 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2011-07-07 08:28:00,750 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic01isc01ip00')
2011-07-07 08:28:00,753 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,753 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'usb:v04E8p343Dd0100dc00dsc00dp00ic07isc01ip02')
2011-07-07 08:28:00,787 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,788 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-07-07 08:28:00,812 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,812 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-07-07 08:28:00,813 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,813 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'acpi:PNP0400:')
2011-07-07 08:28:00,813 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-07-07 08:28:00,824 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'input:b0003v046Dp0809e0010-e0,1,kD4,ramlsfw')
2011-07-07 08:28:00,825 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,825 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr2601:bd06/28/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM3A78-CM:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-07-07 08:28:00,856 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'acpi:PNP0700:')
2011-07-07 08:28:00,856 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'usb:v046DpC526d0500dc00dsc00dp00ic03isc00ip00')
2011-07-07 08:28:00,857 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,857 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2011-07-07 08:28:00,858 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-07-07 08:28:00,858 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,858 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,858 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'usb:v04E8p343Dd0100dc00dsc00dp00icFFiscFFipFF')
2011-07-07 08:28:00,859 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-07-07 08:28:00,859 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic0Eisc01ip00')
2011-07-07 08:28:00,860 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,860 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd000082EFbc0Csc03i20')
2011-07-07 08:28:00,865 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'input:b0003v046DpC526e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-07-07 08:28:00,865 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,865 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,865 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-07 08:28:00,865 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd000082EFbc01sc06i01')
2011-07-07 08:28:00,870 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,870 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,870 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'usb:v046DpC526d0500dc00dsc00dp00ic03isc01ip02')
2011-07-07 08:28:00,871 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,871 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'acpi:PNP0800:')
2011-07-07 08:28:00,871 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic01isc02ip00')
2011-07-07 08:28:00,872 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'pci:v00001002d0000AA80sv00001043sd0000AA80bc04sc03i00')
2011-07-07 08:28:00,877 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,877 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-07 08:28:00,877 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic0Eisc02ip00')
2011-07-07 08:28:00,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-07 08:28:00,878 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2011-07-07 08:28:00,879 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'pci:v00001002d00004385sv00001043sd000082EFbc0Csc05i00')
2011-07-07 08:28:00,883 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,883 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,884 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd000082EFbc06sc01i00')
2011-07-07 08:28:00,888 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-07 08:28:00,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,888 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-07-07 08:28:00,889 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,889 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd000082EAbc04sc03i00')
2011-07-07 08:28:00,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,893 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-07-07 08:28:00,894 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x17322d8> about HardwareID('modalias', 'acpi:PNP0103:')
2011-07-07 08:28:00,894 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-07-07 08:28:00,894 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'input:b0003v046DpC526e0111-e0,1,2,4,k110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,r0,1,6,8,am4,lsfw')
2011-07-07 08:28:00,894 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'acpi:PNP0501:')
2011-07-07 08:28:00,894 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'acpi:PNP0000:')
2011-07-07 08:28:00,894 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd000082C6bc02sc00i00')
2011-07-07 08:28:00,894 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-07-07 08:28:00,894 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-07-07 08:28:00,894 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-07-07 08:28:00,895 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc00ip00')
2011-07-07 08:28:00,895 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip01')
2011-07-07 08:28:00,895 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-07-07 08:28:00,895 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'platform:pcspkr')
2011-07-07 08:28:00,895 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-07-07 08:28:00,895 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'pci:v00001022d00009600sv00001043sd000082EEbc06sc00i00')
2011-07-07 08:28:00,895 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'usb:v046DpC52Bd1201dc00dsc00dp00ic03isc01ip02')
2011-07-07 08:28:00,895 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-07-07 08:28:00,895 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'acpi:PNP0100:')
2011-07-07 08:28:00,896 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'pci:v00001002d00006719sv00001043sd000003BAbc03sc00i00')
2011-07-07 08:28:00,896 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd000082EFbc01sc01i8a')
2011-07-07 08:28:00,896 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-07-07 08:28:00,896 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2011-07-07 08:28:00,896 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2011-07-07 08:28:00,896 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic01isc01ip00')
2011-07-07 08:28:00,896 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'usb:v04E8p343Dd0100dc00dsc00dp00ic07isc01ip02')
2011-07-07 08:28:00,896 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-07-07 08:28:00,896 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2011-07-07 08:28:00,897 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'acpi:PNP0400:')
2011-07-07 08:28:00,897 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-07-07 08:28:00,897 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'input:b0003v046Dp0809e0010-e0,1,kD4,ramlsfw')
2011-07-07 08:28:00,897 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr2601:bd06/28/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnM3A78-CM:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-07-07 08:28:00,897 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'acpi:PNP0700:')
2011-07-07 08:28:00,897 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'usb:v046DpC526d0500dc00dsc00dp00ic03isc00ip00')
2011-07-07 08:28:00,897 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2011-07-07 08:28:00,897 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'input:b0003v046DpC52Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E2,E4,E7,E8,E9,EA,EB,F1,100,110,111,112,113,114,115,116,117,118,119,11A,11B,11C,11D,11E,11F,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r0,1,6,7,8,a20,m4,lsfw')
2011-07-07 08:28:00,897 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'usb:v04E8p343Dd0100dc00dsc00dp00icFFiscFFipFF')
2011-07-07 08:28:00,898 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-07-07 08:28:00,898 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic0Eisc01ip00')
2011-07-07 08:28:00,898 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd000082EFbc0Csc03i20')
2011-07-07 08:28:00,898 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'input:b0003v046DpC526e0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-07-07 08:28:00,898 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-07-07 08:28:00,898 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd000082EFbc01sc06i01')
2011-07-07 08:28:00,898 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'usb:v046DpC526d0500dc00dsc00dp00ic03isc01ip02')
2011-07-07 08:28:00,898 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'acpi:PNP0800:')
2011-07-07 08:28:00,898 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic01isc02ip00')
2011-07-07 08:28:00,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'pci:v00001002d0000AA80sv00001043sd0000AA80bc04sc03i00')
2011-07-07 08:28:00,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'acpi:PNP0200:')
2011-07-07 08:28:00,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'usb:v046Dp0809d0010dcEFdsc02dp01ic0Eisc02ip00')
2011-07-07 08:28:00,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'platform:reg-dummy')
2011-07-07 08:28:00,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2011-07-07 08:28:00,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'pci:v00001002d00004385sv00001043sd000082EFbc0Csc05i00')
2011-07-07 08:28:00,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd000082EFbc06sc01i00')
2011-07-07 08:28:00,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-07-07 08:28:00,899 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-07-07 08:28:00,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd000082EAbc04sc03i00')
2011-07-07 08:28:00,900 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1cf9b00> about HardwareID('modalias', 'acpi:PNP0103:')
2011-07-07 08:28:01,013 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 08:28:01,013 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 08:28:01,118 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 08:28:01,118 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 08:28:01,187 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 08:28:01,188 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 08:28:04,052 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 08:28:04,053 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 08:28:11,298 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-07-07 08:28:11,298 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-07-07 08:28:11,299 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-07-07 08:29:14,922 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 08:29:14,923 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-07-07 08:29:14,995 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-07-07 08:29:14,995 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
```heres a copy of my jockey.log if anyone can decipher this I would be grateful

---

