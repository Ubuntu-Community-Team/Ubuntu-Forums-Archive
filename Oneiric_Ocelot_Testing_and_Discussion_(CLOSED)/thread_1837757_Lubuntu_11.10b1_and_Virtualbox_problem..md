---
title: "Lubuntu 11.10b1 and Virtualbox problem."
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by loukingjr on 2011-09-02
bare with me... I installed Xubuntu 11.10b1 as a guest in VB and once I booted the guest I had a popup that there were addition drivers available. It downloaded "something" and when it was done I had to activate a VB module and once that was done everything worked fine; fullscreen, shared folders, shared clipboard etc.

I decided to try Lubuntu 11.10b1 and it also installed fine however, once it got to the desktop it did not offer additional drivers. I found "Additional Drivers" in the menu so selected that and it had the option to activate the same VB module as Xubuntu. Then it also downloaded "something". However, it failed to activate, said to check /var/log/jockey...something, and the log was very long and I really didn't know what I was looking for.

Does anyone know how to get Lubuntu 11.10b1 working as a guest in VB with the guest additions working?

whew... thanks ahead of time.

---

### Post by cariboo on 2011-09-02
It would help if you could tell us what was downloaded. 

If you've got the room to install in a vm, why not just create a new partition on your hard drive and install to bare metal. By testing in a vm, all you are doing is testing the virtual machine. Testing on real hardware helps finding bugs.

---

### Post by loukingjr on 2011-09-02
> **cariboo907 said:**
> It would help if you could tell us what was downloaded. 

If you've got the room to install in a vm, why not just create a new partition on your hard drive and install to bare metal. By testing in a vm, all you are doing is testing the virtual machine. Testing on real hardware helps finding bugs.

well if I could of remembered at the time I would have. I believe it downloaded the vbox dkms module or possibly the vbox z11 drivers or both. I can't swear to that however. As far as installing it on metal, I used to triple boot my iMac with OSX, windows 7 and Ubuntu 10,10. There are a number of issues running Ubuntu on an iMac not the least of which was every time I booted it without remembering to turn my speakers all the way down it would blast me out of the room. I found a patch that made Macbook's volume keys work with Ubuntu, unfortunately it didn't work with my iMac. I'm really not testing anything, I have installed over 100 Linux guests in VB just to see what they are like. The only thing I do with Linux at all is theme various DEs.

I'll reinstall Lubuntu as a guest and see if I can find more specific info on what exactly was downloaded.

---

### Post by loukingjr on 2011-09-27
okay back to this problem. when you install, Lubuntu, Xubuntu, Ubuntu 11.10 betas as a guest in virtualbox and start the guest, a popup window tells you additional drivers are available. when you open additional drivers, you see a message that VB drivers are not enabled. when you click on the enable button it downloads then installs source code for VB. It works fine in Ubuntu and Xubuntu. But for some reason it fails to install in Lubuntu and creates a very long log file. Most of which I don't understand.

maybe this will help...
[IMG]https://lh3.googleusercontent.com/-Z3wGwSakCkY/ToHUmozj2xI/AAAAAAAAJgg/FCMh9r36EMY/s640/screenshot_25.jpg[/IMG]

[IMG]https://lh6.googleusercontent.com/-gDYpLfO0GkA/ToHUmmNigVI/AAAAAAAAJgc/dvyY5--ACns/s640/screenshot_23.jpg[/IMG]

```
2011-09-27 09:37:35,700 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c>
2011-09-27 09:37:36,981 DEBUG: reading modalias file /lib/modules/3.0.0-11-generic/modules.alias
2011-09-27 09:37:37,036 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-09-27 09:37:37,036 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-09-27 09:37:37,052 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-09-27 09:37:37,061 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-09-27 09:37:37,064 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-09-27 09:37:37,064 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-09-27 09:37:37,064 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-09-27 09:37:37,064 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-09-27 09:37:37,067 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-09-27 09:37:37,070 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-09-27 09:37:37,070 DEBUG: fglrx.available: falling back to default
2011-09-27 09:37:37,103 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) not available
2011-09-27 09:37:37,105 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-09-27 09:37:37,106 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-09-27 09:37:37,107 DEBUG: fglrx.available: falling back to default
2011-09-27 09:37:37,123 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-09-27 09:37:37,123 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-09-27 09:37:37,134 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-09-27 09:37:37,134 DEBUG: Experimental 3D support for NVIDIA cards not available
2011-09-27 09:37:37,134 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-09-27 09:37:37,148 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-09-27 09:37:37,148 DEBUG: Firmware for DVB cards not available
2011-09-27 09:37:37,148 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-09-27 09:37:37,157 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-09-27 09:37:37,160 DEBUG: Software modem not available
2011-09-27 09:37:37,161 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-09-27 09:37:37,162 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-09-27 09:37:37,163 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-09-27 09:37:37,170 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-09-27 09:37:37,171 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-09-27 09:37:37,173 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-09-27 09:37:37,181 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-09-27 09:37:37,181 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-09-27 09:37:37,181 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-09-27 09:37:37,185 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-09-27 09:37:37,187 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-09-27 09:37:37,187 DEBUG: nvidia.available: falling back to default
2011-09-27 09:37:37,204 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-09-27 09:37:37,205 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-09-27 09:37:37,207 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-09-27 09:37:37,208 DEBUG: nvidia.available: falling back to default
2011-09-27 09:37:37,224 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-09-27 09:37:37,226 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-09-27 09:37:37,227 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-09-27 09:37:37,228 DEBUG: nvidia.available: falling back to default
2011-09-27 09:37:37,258 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-09-27 09:37:37,258 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-09-27 09:37:37,261 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-09-27 09:37:37,268 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-09-27 09:37:37,268 DEBUG: nvidia.available: falling back to default
2011-09-27 09:37:37,300 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-09-27 09:37:37,305 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-09-27 09:37:37,311 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-09-27 09:37:37,311 DEBUG: nvidia.available: falling back to default
2011-09-27 09:37:37,347 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-09-27 09:37:37,352 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-09-27 09:37:37,354 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-09-27 09:37:37,354 DEBUG: nvidia.available: falling back to default
2011-09-27 09:37:37,383 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-09-27 09:37:37,384 DEBUG: all custom handlers loaded
2011-09-27 09:37:37,384 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'pci:v00008086d00007111sv00000000sd00000000bc01sc01i8a')
2011-09-27 09:37:37,571 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-09-27 09:37:37,572 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'pci:v00008086d0000100Esv00008086sd0000001Ebc02sc00i00')
2011-09-27 09:37:37,573 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'e1000'}
2011-09-27 09:37:37,613 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e1000', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:37:37,613 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'pci:v00008086d00001237sv00000000sd00000000bc06sc00i00')
2011-09-27 09:37:37,615 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-09-27 09:37:37,616 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-09-27 09:37:37,627 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-09-27 09:37:37,629 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-09-27 09:37:37,630 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:37:37,630 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-09-27 09:37:37,630 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'platform:eisa')
2011-09-27 09:37:37,630 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'platform:pcspkr')
2011-09-27 09:37:37,630 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-09-27 09:37:37,630 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:37:37,630 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-09-27 09:37:37,630 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:37:37,630 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'pci:v000080EEd0000BEEFsv00000000sd00000000bc03sc00i00')
2011-09-27 09:37:37,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-09-27 09:37:37,631 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'pci:v00008086d00007000sv00000000sd00000000bc06sc01i00')
2011-09-27 09:37:37,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'acpi:PNP0400:')
2011-09-27 09:37:37,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-09-27 09:37:37,632 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'pci:v00008086d0000265Csv00000000sd00000000bc0Csc03i20')
2011-09-27 09:37:37,634 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'input:b0003v80EEp0021e0110-e0,1,2,3,4,k110,111,112,113,114,r8,a0,1,m4,lsfw')
2011-09-27 09:37:37,634 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-09-27 09:37:37,634 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:37:37,634 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-09-27 09:37:37,634 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:37:37,634 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-09-27 09:37:37,634 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-09-27 09:37:37,634 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:37:37,634 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'dmi:bvninnotekGmbH:bvrVirtualBox:bd12/01/2006:svninnotekGmbH:pnVirtualBox:pvr1.2:')
2011-09-27 09:37:37,642 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'pci:v00008086d00002415sv00008086sd00000000bc04sc01i00')
2011-09-27 09:37:37,644 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_intel8x0'}
2011-09-27 09:37:37,644 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_intel8x0', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:37:37,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'usb:v80EEp0021d0100dc00dsc00dp00ic03isc00ip00')
2011-09-27 09:37:37,644 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-09-27 09:37:37,644 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:37:37,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-09-27 09:37:37,644 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'pci:v00008086d00002829sv00000000sd00000000bc01sc06i01')
2011-09-27 09:37:37,646 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-09-27 09:37:37,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:37:37,646 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-09-27 09:37:37,646 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:37:37,646 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'pci:v00008086d00007113sv00000000sd00000000bc06sc80i00')
2011-09-27 09:37:37,648 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2011-09-27 09:37:37,648 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:37:37,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'pci:v000080EEd0000CAFEsv00000000sd00000000bc08sc80i00')
2011-09-27 09:37:37,648 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'vboxguest', 'package': 'virtualbox-guest-dkms'}
2011-09-27 09:37:37,650 WARNING: modinfo for module vboxguest failed: ERROR: modinfo: could not find module vboxguest

2011-09-27 09:37:37,660 WARNING: modinfo for module vboxguest failed: ERROR: modinfo: could not find module vboxguest

2011-09-27 09:37:37,660 DEBUG: got handler kmod:vboxguest([KernelModuleHandler, free, disabled] x86 virtualization solution - guest addition module source for dkms)
2011-09-27 09:37:37,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-09-27 09:37:37,660 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-09-27 09:37:37,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:37:37,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-09-27 09:37:37,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'platform:reg-dummy')
2011-09-27 09:37:37,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-09-27 09:37:37,666 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-09-27 09:37:37,666 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:37:37,666 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-09-27 09:37:37,666 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:37:37,666 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'input:b0011v0002p0006e0000-e0,1,2,k110,111,112,113,114,r0,1,6,8,amlsfw')
2011-09-27 09:37:37,666 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-09-27 09:37:37,666 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:37:37,666 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74e486c> about HardwareID('modalias', 'acpi:PNP0F03:')
2011-09-27 09:37:37,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'pci:v00008086d00007111sv00000000sd00000000bc01sc01i8a')
2011-09-27 09:37:37,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-09-27 09:37:37,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'pci:v00008086d0000100Esv00008086sd0000001Ebc02sc00i00')
2011-09-27 09:37:37,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'pci:v00008086d00001237sv00000000sd00000000bc06sc00i00')
2011-09-27 09:37:37,666 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'platform:eisa')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'platform:pcspkr')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'pci:v000080EEd0000BEEFsv00000000sd00000000bc03sc00i00')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'pci:v00008086d00007000sv00000000sd00000000bc06sc01i00')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'acpi:PNP0400:')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'pci:v00008086d0000265Csv00000000sd00000000bc0Csc03i20')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'input:b0003v80EEp0021e0110-e0,1,2,3,4,k110,111,112,113,114,r8,a0,1,m4,lsfw')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'dmi:bvninnotekGmbH:bvrVirtualBox:bd12/01/2006:svninnotekGmbH:pnVirtualBox:pvr1.2:')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'pci:v00008086d00002415sv00008086sd00000000bc04sc01i00')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'usb:v80EEp0021d0100dc00dsc00dp00ic03isc00ip00')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'pci:v00008086d00002829sv00000000sd00000000bc01sc06i01')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'pci:v00008086d00007113sv00000000sd00000000bc06sc80i00')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'pci:v000080EEd0000CAFEsv00000000sd00000000bc08sc80i00')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-09-27 09:37:37,667 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'platform:reg-dummy')
2011-09-27 09:37:37,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-09-27 09:37:37,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'input:b0011v0002p0006e0000-e0,1,2,k110,111,112,113,114,r0,1,6,8,amlsfw')
2011-09-27 09:37:37,668 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74e466c> about HardwareID('modalias', 'acpi:PNP0F03:')
2011-09-27 09:37:37,684 DEBUG: handler kmod:vboxguest previously unseen
2011-09-27 09:37:37,684 DEBUG: writing back check cache /var/cache/jockey/check
2011-09-27 09:38:43,488 DEBUG: Installing package: virtualbox-guest-dkms
2011-09-27 09:38:43,676 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 0.000012
2011-09-27 09:38:43,678 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 0.000012
2011-09-27 09:38:43,712 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 0.000012
2011-09-27 09:38:43,819 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 0.000012
2011-09-27 09:38:43,940 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 0.000012
2011-09-27 09:38:44,261 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 0.168612
2011-09-27 09:38:44,261 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 0.168612
2011-09-27 09:38:44,262 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 0.168612
2011-09-27 09:38:44,264 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 0.168612
2011-09-27 09:38:44,638 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 1.334142
2011-09-27 09:38:44,639 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 1.334142
2011-09-27 09:38:44,641 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 1.334142
2011-09-27 09:38:44,642 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 1.334142
2011-09-27 09:38:45,144 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 6.212906
2011-09-27 09:38:45,645 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 21.180290
2011-09-27 09:38:46,146 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 37.123620
2011-09-27 09:38:46,429 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 46.180090
2011-09-27 09:38:46,429 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 46.180090
2011-09-27 09:38:46,432 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 46.180090
2011-09-27 09:38:46,433 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 46.180090
2011-09-27 09:38:46,434 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 46.210622
2011-09-27 09:38:46,434 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 46.210622
2011-09-27 09:38:46,437 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 46.210622
2011-09-27 09:38:46,439 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 46.210622
2011-09-27 09:38:46,451 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 46.901241
2011-09-27 09:38:46,453 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 46.901241
2011-09-27 09:38:46,454 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 46.901241
2011-09-27 09:38:46,468 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 47.417158
2011-09-27 09:38:46,470 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 47.417158
2011-09-27 09:38:46,471 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 47.417158
2011-09-27 09:38:46,481 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 47.849643
2011-09-27 09:38:46,483 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 47.849643
2011-09-27 09:38:46,484 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 47.849643
2011-09-27 09:38:46,498 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 48.336155
2011-09-27 09:38:46,499 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 48.336155
2011-09-27 09:38:46,501 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 48.336155
2011-09-27 09:38:46,511 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 48.788144
2011-09-27 09:38:46,513 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 48.788144
2011-09-27 09:38:46,514 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 48.788144
2011-09-27 09:38:46,662 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 53.596710
2011-09-27 09:38:46,664 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 53.596710
2011-09-27 09:38:46,664 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 53.596710
2011-09-27 09:38:47,165 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 69.647331
2011-09-27 09:38:47,605 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 83.657742
2011-09-27 09:38:47,606 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 83.657742
2011-09-27 09:38:47,608 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 83.657742
2011-09-27 09:38:47,709 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 87.013591
2011-09-27 09:38:47,711 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 87.013591
2011-09-27 09:38:47,713 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 87.013591
2011-09-27 09:38:47,820 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 90.497750
2011-09-27 09:38:47,822 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 90.497750
2011-09-27 09:38:47,823 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 90.497750
2011-09-27 09:38:48,117 DEBUG: download progress <Package: name:'virtualbox-guest-dkms' architecture='i386' id:43772L> 100.000000
2011-09-27 09:38:48,288 DEBUG: install progress dpkg-exec 0.000000
2011-09-27 09:38:48,510 DEBUG: install progress libc-bin 1.250000
2011-09-27 09:38:48,593 DEBUG: install progress libc-bin 2.500000
2011-09-27 09:38:48,596 DEBUG: install progress libc-bin 3.750000
2011-09-27 09:38:48,599 DEBUG: install progress man-db 3.750000
2011-09-27 09:38:48,997 DEBUG: install progress dpkg-exec 3.750000
2011-09-27 09:38:49,011 DEBUG: install progress libc-bin 3.750000
2011-09-27 09:38:49,042 DEBUG: install progress libc-bin 5.000000
2011-09-27 09:38:49,044 DEBUG: install progress libc-bin 6.250000
2011-09-27 09:38:49,060 DEBUG: install progress dpkg-exec 6.250000
2011-09-27 09:38:49,147 DEBUG: install progress libc6 7.500000
2011-09-27 09:38:49,497 DEBUG: install progress libc6 8.750000
2011-09-27 09:38:49,503 DEBUG: install progress libc6 10.000000
2011-09-27 09:38:49,532 DEBUG: install progress dpkg-exec 10.000000
2011-09-27 09:38:49,547 DEBUG: install progress libc6 10.000000
2011-09-27 09:38:49,561 DEBUG: install progress libc6 11.250000
2011-09-27 09:38:49,783 DEBUG: install progress libc6 12.500000
2011-09-27 09:38:49,789 DEBUG: install progress libc-bin 12.500000
2011-09-27 09:38:49,839 DEBUG: install progress dpkg-exec 12.500000
2011-09-27 09:38:49,913 DEBUG: install progress libgomp1 12.500000
2011-09-27 09:38:49,914 DEBUG: install progress libgomp1 13.750000
2011-09-27 09:38:49,939 DEBUG: install progress libgomp1 15.000000
2011-09-27 09:38:49,941 DEBUG: install progress libgomp1 16.250000
2011-09-27 09:38:49,955 DEBUG: install progress libquadmath0 16.250000
2011-09-27 09:38:49,956 DEBUG: install progress libquadmath0 17.500000
2011-09-27 09:38:49,987 DEBUG: install progress libquadmath0 18.750000
2011-09-27 09:38:49,989 DEBUG: install progress libquadmath0 20.000000
2011-09-27 09:38:50,001 DEBUG: install progress gcc-4.6 20.000000
2011-09-27 09:38:50,004 DEBUG: install progress gcc-4.6 21.250000
2011-09-27 09:38:50,178 DEBUG: install progress gcc-4.6 22.500000
2011-09-27 09:38:50,180 DEBUG: install progress gcc-4.6 23.750000
2011-09-27 09:38:50,195 DEBUG: install progress gcc 23.750000
2011-09-27 09:38:50,197 DEBUG: install progress gcc 25.000000
2011-09-27 09:38:50,208 DEBUG: install progress gcc 26.250000
2011-09-27 09:38:50,210 DEBUG: install progress gcc 27.500000
2011-09-27 09:38:50,223 DEBUG: install progress make 27.500000
2011-09-27 09:38:50,224 DEBUG: install progress make 28.750000
2011-09-27 09:38:50,239 DEBUG: install progress make 30.000000
2011-09-27 09:38:50,242 DEBUG: install progress make 31.250000
2011-09-27 09:38:50,255 DEBUG: install progress patch 31.250000
2011-09-27 09:38:50,256 DEBUG: install progress patch 32.500000
2011-09-27 09:38:50,269 DEBUG: install progress patch 33.750000
2011-09-27 09:38:50,271 DEBUG: install progress patch 35.000000
2011-09-27 09:38:50,283 DEBUG: install progress dkms 35.000000
2011-09-27 09:38:50,287 DEBUG: install progress dkms 36.250000
2011-09-27 09:38:50,310 DEBUG: install progress dkms 37.500000
2011-09-27 09:38:50,312 DEBUG: install progress dkms 38.750000
2011-09-27 09:38:50,326 DEBUG: install progress fakeroot 38.750000
2011-09-27 09:38:50,328 DEBUG: install progress fakeroot 40.000000
2011-09-27 09:38:50,347 DEBUG: install progress fakeroot 41.250000
2011-09-27 09:38:50,349 DEBUG: install progress fakeroot 42.500000
2011-09-27 09:38:50,361 DEBUG: install progress libc-dev-bin 42.500000
2011-09-27 09:38:50,363 DEBUG: install progress libc-dev-bin 43.750000
2011-09-27 09:38:50,377 DEBUG: install progress libc-dev-bin 45.000000
2011-09-27 09:38:50,380 DEBUG: install progress libc-dev-bin 46.250000
2011-09-27 09:38:50,393 DEBUG: install progress linux-libc-dev 46.250000
2011-09-27 09:38:50,394 DEBUG: install progress linux-libc-dev 47.500000
2011-09-27 09:38:50,603 DEBUG: install progress linux-libc-dev 48.750000
2011-09-27 09:38:50,606 DEBUG: install progress linux-libc-dev 50.000000
2011-09-27 09:38:50,619 DEBUG: install progress libc6-dev 50.000000
2011-09-27 09:38:50,621 DEBUG: install progress libc6-dev 51.250000
2011-09-27 09:38:50,911 DEBUG: install progress libc6-dev 52.500000
2011-09-27 09:38:50,914 DEBUG: install progress libc6-dev 53.750000
2011-09-27 09:38:50,929 DEBUG: install progress virtualbox-guest-utils 53.750000
2011-09-27 09:38:50,930 DEBUG: install progress virtualbox-guest-utils 55.000000
2011-09-27 09:38:50,959 DEBUG: install progress virtualbox-guest-utils 56.250000
2011-09-27 09:38:50,961 DEBUG: install progress virtualbox-guest-utils 57.500000
2011-09-27 09:38:50,975 DEBUG: install progress virtualbox-guest-dkms 57.500000
2011-09-27 09:38:50,977 DEBUG: install progress virtualbox-guest-dkms 58.750000
2011-09-27 09:38:51,073 DEBUG: install progress virtualbox-guest-dkms 60.000000
2011-09-27 09:38:51,075 DEBUG: install progress virtualbox-guest-dkms 61.250000
2011-09-27 09:38:51,092 DEBUG: install progress virtualbox-guest-x11 61.250000
2011-09-27 09:38:51,094 DEBUG: install progress virtualbox-guest-x11 62.500000
2011-09-27 09:38:51,165 DEBUG: install progress virtualbox-guest-x11 63.750000
2011-09-27 09:38:51,170 DEBUG: install progress virtualbox-guest-x11 65.000000
2011-09-27 09:38:51,174 DEBUG: install progress man-db 65.000000
2011-09-27 09:38:51,568 DEBUG: install progress ureadahead 65.000000
2011-09-27 09:38:51,600 DEBUG: install progress dpkg-exec 65.000000
2011-09-27 09:38:51,617 DEBUG: install progress libgomp1 65.000000
2011-09-27 09:38:51,627 DEBUG: install progress libgomp1 66.250000
2011-09-27 09:38:51,637 DEBUG: install progress libgomp1 67.500000
2011-09-27 09:38:51,643 DEBUG: install progress libquadmath0 67.500000
2011-09-27 09:38:51,645 DEBUG: install progress libquadmath0 68.750000
2011-09-27 09:38:51,657 DEBUG: install progress libquadmath0 70.000000
2011-09-27 09:38:51,661 DEBUG: install progress gcc-4.6 70.000000
2011-09-27 09:38:51,663 DEBUG: install progress gcc-4.6 71.250000
2011-09-27 09:38:51,665 DEBUG: install progress gcc-4.6 72.500000
2011-09-27 09:38:51,667 DEBUG: install progress gcc 72.500000
2011-09-27 09:38:51,669 DEBUG: install progress gcc 73.750000
2011-09-27 09:38:51,690 DEBUG: install progress gcc 75.000000
2011-09-27 09:38:51,692 DEBUG: install progress make 75.000000
2011-09-27 09:38:51,694 DEBUG: install progress make 76.250000
2011-09-27 09:38:51,696 DEBUG: install progress make 77.500000
2011-09-27 09:38:51,698 DEBUG: install progress patch 77.500000
2011-09-27 09:38:51,700 DEBUG: install progress patch 78.750000
2011-09-27 09:38:51,701 DEBUG: install progress patch 80.000000
2011-09-27 09:38:51,703 DEBUG: install progress dkms 80.000000
2011-09-27 09:38:51,719 DEBUG: install progress dkms 81.250000
2011-09-27 09:38:51,722 DEBUG: install progress dkms 82.500000
2011-09-27 09:38:51,724 DEBUG: install progress fakeroot 82.500000
2011-09-27 09:38:51,726 DEBUG: install progress fakeroot 83.750000
2011-09-27 09:38:51,732 DEBUG: install progress fakeroot 85.000000
2011-09-27 09:38:51,741 DEBUG: install progress libc-dev-bin 85.000000
2011-09-27 09:38:51,743 DEBUG: install progress libc-dev-bin 86.250000
2011-09-27 09:38:51,745 DEBUG: install progress libc-dev-bin 87.500000
2011-09-27 09:38:51,747 DEBUG: install progress linux-libc-dev 87.500000
2011-09-27 09:38:51,748 DEBUG: install progress linux-libc-dev 88.750000
2011-09-27 09:38:51,750 DEBUG: install progress linux-libc-dev 90.000000
2011-09-27 09:38:51,752 DEBUG: install progress libc6-dev 90.000000
2011-09-27 09:38:51,753 DEBUG: install progress libc6-dev 91.250000
2011-09-27 09:38:51,755 DEBUG: install progress libc6-dev 92.500000
2011-09-27 09:38:51,757 DEBUG: install progress virtualbox-guest-utils 92.500000
2011-09-27 09:38:51,759 DEBUG: install progress virtualbox-guest-utils 93.750000
2011-09-27 09:38:51,816 DEBUG: install progress virtualbox-guest-utils 95.000000
2011-09-27 09:38:51,820 DEBUG: install progress virtualbox-guest-dkms 95.000000
2011-09-27 09:38:51,821 DEBUG: install progress virtualbox-guest-dkms 96.250000
2011-09-27 09:38:58,296 DEBUG: install progress virtualbox-guest-dkms 97.500000
2011-09-27 09:38:58,298 DEBUG: install progress virtualbox-guest-x11 97.500000
2011-09-27 09:38:58,301 DEBUG: install progress virtualbox-guest-x11 98.750000
2011-09-27 09:38:58,313 DEBUG: install progress virtualbox-guest-x11 100.000000
2011-09-27 09:38:58,318 DEBUG: install progress libc-bin 100.000000
2011-09-27 09:38:58,519 DEBUG: Preconfiguring packages ...
(Reading database ... 101881 files and directories currently installed.)
Preparing to replace libc-bin 2.13-20ubuntu2 (using .../libc-bin_2.13-20ubuntu3_i386.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
Setting up libc-bin (2.13-20ubuntu3) ...
(Reading database ... 101881 files and directories currently installed.)
Preparing to replace libc6 2.13-20ubuntu2 (using .../libc6_2.13-20ubuntu3_i386.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.13-20ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package libgomp1.
(Reading database ... 101881 files and directories currently installed.)
Unpacking libgomp1 (from .../libgomp1_4.6.1-9ubuntu3_i386.deb) ...
Selecting previously deselected package libquadmath0.
Unpacking libquadmath0 (from .../libquadmath0_4.6.1-9ubuntu3_i386.deb) ...
Selecting previously deselected package gcc-4.6.
Unpacking gcc-4.6 (from .../gcc-4.6_4.6.1-9ubuntu3_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.6.1-2ubuntu5_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../make_3.81-8.1ubuntu1_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6.1-2_i386.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.2-1ubuntu3_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.17-1_i386.deb) ...
Selecting previously deselected package libc-dev-bin.
Unpacking libc-dev-bin (from .../libc-dev-bin_2.13-20ubuntu3_i386.deb) ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_3.0.0-12.19_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.13-20ubuntu3_i386.deb) ...
Selecting previously deselected package virtualbox-guest-utils.
Unpacking virtualbox-guest-utils (from .../virtualbox-guest-utils_4.1.2-dfsg-1ubuntu1_i386.deb) ...
Selecting previously deselected package virtualbox-guest-dkms.
Unpacking virtualbox-guest-dkms (from .../virtualbox-guest-dkms_4.1.2-dfsg-1ubuntu1_all.deb) ...
Selecting previously deselected package virtualbox-guest-x11.
Unpacking virtualbox-guest-x11 (from .../virtualbox-guest-x11_4.1.2-dfsg-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libgomp1 (4.6.1-9ubuntu3) ...
Setting up libquadmath0 (4.6.1-9ubuntu3) ...
Setting up gcc-4.6 (4.6.1-9ubuntu3) ...
Setting up gcc (4:4.6.1-2ubuntu5) ...
Setting up make (3.81-8.1ubuntu1) ...
Setting up patch (2.6.1-2) ...
Setting up dkms (2.2.0.2-1ubuntu3) ...
Setting up fakeroot (1.17-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up libc-dev-bin (2.13-20ubuntu3) ...
Setting up linux-libc-dev (3.0.0-12.19) ...
Setting up libc6-dev (2.13-20ubuntu3) ...
Setting up virtualbox-guest-utils (4.1.2-dfsg-1ubuntu1) ...
Setting up virtualbox-guest-dkms (4.1.2-dfsg-1ubuntu1) ...
Loading new virtualbox-guest-4.1.2 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-11-generic
Building initial module for 3.0.0-11-generic
Error! Bad return status for module build on kernel: 3.0.0-11-generic (i686)
Consult /var/lib/dkms/virtualbox-guest/4.1.2/build/make.log for more information.
Setting up virtualbox-guest-x11 (4.1.2-dfsg-1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-09-27 09:38:58,579 WARNING: modinfo for module vboxguest failed: ERROR: modinfo: could not find module vboxguest

2011-09-27 09:38:58,579 WARNING: /sys/module/vboxguest/drivers does not exist, cannot rebind vboxguest driver
2011-09-27 09:42:50,318 DEBUG: Shutting down
2011-09-27 09:48:38,657 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c>
2011-09-27 09:48:39,598 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2011-09-27 09:48:39,651 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-09-27 09:48:39,651 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-09-27 09:48:39,669 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-09-27 09:48:39,678 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-09-27 09:48:39,686 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-09-27 09:48:39,687 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-09-27 09:48:39,687 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-09-27 09:48:39,687 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-09-27 09:48:39,691 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-09-27 09:48:39,693 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-09-27 09:48:39,693 DEBUG: fglrx.available: falling back to default
2011-09-27 09:48:39,727 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-09-27 09:48:39,729 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-09-27 09:48:39,731 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-09-27 09:48:39,731 DEBUG: fglrx.available: falling back to default
2011-09-27 09:48:39,748 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-09-27 09:48:39,748 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-09-27 09:48:39,761 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-09-27 09:48:39,761 DEBUG: Firmware for DVB cards not available
2011-09-27 09:48:39,761 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-09-27 09:48:39,770 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-09-27 09:48:39,773 DEBUG: Software modem not available
2011-09-27 09:48:39,773 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-09-27 09:48:39,775 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-09-27 09:48:39,775 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-09-27 09:48:39,783 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-09-27 09:48:39,783 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-09-27 09:48:39,786 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-09-27 09:48:39,794 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-09-27 09:48:39,794 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-09-27 09:48:39,794 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-09-27 09:48:39,797 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-09-27 09:48:39,799 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-09-27 09:48:39,799 DEBUG: nvidia.available: falling back to default
2011-09-27 09:48:39,813 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-09-27 09:48:39,815 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-09-27 09:48:39,817 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-09-27 09:48:39,817 DEBUG: nvidia.available: falling back to default
2011-09-27 09:48:39,832 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-09-27 09:48:39,833 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-09-27 09:48:39,835 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-09-27 09:48:39,835 DEBUG: nvidia.available: falling back to default
2011-09-27 09:48:39,852 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-09-27 09:48:39,853 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-09-27 09:48:39,855 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-09-27 09:48:39,857 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-09-27 09:48:39,857 DEBUG: nvidia.available: falling back to default
2011-09-27 09:48:39,871 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-09-27 09:48:39,873 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-09-27 09:48:39,875 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-09-27 09:48:39,875 DEBUG: nvidia.available: falling back to default
2011-09-27 09:48:39,890 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-09-27 09:48:39,892 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-09-27 09:48:39,893 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-09-27 09:48:39,894 DEBUG: nvidia.available: falling back to default
2011-09-27 09:48:39,909 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-09-27 09:48:39,909 DEBUG: all custom handlers loaded
2011-09-27 09:48:39,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'pci:v00008086d00007111sv00000000sd00000000bc01sc01i8a')
2011-09-27 09:48:40,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-09-27 09:48:40,067 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'pci:v00008086d0000100Esv00008086sd0000001Ebc02sc00i00')
2011-09-27 09:48:40,069 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'e1000'}
2011-09-27 09:48:40,107 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e1000', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:48:40,107 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'pci:v00008086d00001237sv00000000sd00000000bc06sc00i00')
2011-09-27 09:48:40,108 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-09-27 09:48:40,110 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-09-27 09:48:40,121 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-09-27 09:48:40,122 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-09-27 09:48:40,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:48:40,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-09-27 09:48:40,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'platform:eisa')
2011-09-27 09:48:40,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'platform:pcspkr')
2011-09-27 09:48:40,123 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-09-27 09:48:40,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:48:40,123 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-09-27 09:48:40,123 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:48:40,123 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'pci:v000080EEd0000BEEFsv00000000sd00000000bc03sc00i00')
2011-09-27 09:48:40,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-09-27 09:48:40,124 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'pci:v00008086d00007000sv00000000sd00000000bc06sc01i00')
2011-09-27 09:48:40,125 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'acpi:PNP0400:')
2011-09-27 09:48:40,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-09-27 09:48:40,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'pci:v00008086d0000265Csv00000000sd00000000bc0Csc03i20')
2011-09-27 09:48:40,127 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'input:b0003v80EEp0021e0110-e0,1,2,3,4,k110,111,112,113,114,r8,a0,1,m4,lsfw')
2011-09-27 09:48:40,128 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-09-27 09:48:40,128 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:48:40,128 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-09-27 09:48:40,128 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:48:40,128 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-09-27 09:48:40,128 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-09-27 09:48:40,128 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:48:40,128 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'dmi:bvninnotekGmbH:bvrVirtualBox:bd12/01/2006:svninnotekGmbH:pnVirtualBox:pvr1.2:')
2011-09-27 09:48:40,135 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'pci:v00008086d00002415sv00008086sd00000000bc04sc01i00')
2011-09-27 09:48:40,136 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_intel8x0'}
2011-09-27 09:48:40,137 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_intel8x0', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:48:40,137 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'usb:v80EEp0021d0100dc00dsc00dp00ic03isc00ip00')
2011-09-27 09:48:40,137 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-09-27 09:48:40,137 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:48:40,137 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-09-27 09:48:40,137 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'pci:v00008086d00002829sv00000000sd00000000bc01sc06i01')
2011-09-27 09:48:40,139 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-09-27 09:48:40,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:48:40,139 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2011-09-27 09:48:40,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:48:40,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'pci:v00008086d00007113sv00000000sd00000000bc06sc80i00')
2011-09-27 09:48:40,140 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2011-09-27 09:48:40,140 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:48:40,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'pci:v000080EEd0000CAFEsv00000000sd00000000bc08sc80i00')
2011-09-27 09:48:40,141 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'vboxguest', 'package': 'virtualbox-guest-dkms'}
2011-09-27 09:48:40,142 WARNING: modinfo for module vboxguest failed: ERROR: modinfo: could not find module vboxguest

2011-09-27 09:48:40,153 WARNING: modinfo for module vboxguest failed: ERROR: modinfo: could not find module vboxguest

2011-09-27 09:48:40,153 DEBUG: got handler kmod:vboxguest([KernelModuleHandler, free, disabled] x86 virtualization solution - guest addition module source for dkms)
2011-09-27 09:48:40,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-09-27 09:48:40,153 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-09-27 09:48:40,153 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:48:40,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-09-27 09:48:40,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'platform:reg-dummy')
2011-09-27 09:48:40,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-09-27 09:48:40,158 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-09-27 09:48:40,158 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:48:40,158 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-09-27 09:48:40,158 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:48:40,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'input:b0011v0002p0006e0000-e0,1,2,k110,111,112,113,114,r0,1,6,8,amlsfw')
2011-09-27 09:48:40,159 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-09-27 09:48:40,159 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-09-27 09:48:40,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb74c784c> about HardwareID('modalias', 'acpi:PNP0F03:')
2011-09-27 09:48:40,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'pci:v00008086d00007111sv00000000sd00000000bc01sc01i8a')
2011-09-27 09:48:40,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-09-27 09:48:40,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'pci:v00008086d0000100Esv00008086sd0000001Ebc02sc00i00')
2011-09-27 09:48:40,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'pci:v00008086d00001237sv00000000sd00000000bc06sc00i00')
2011-09-27 09:48:40,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-09-27 09:48:40,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-09-27 09:48:40,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-09-27 09:48:40,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-09-27 09:48:40,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'platform:eisa')
2011-09-27 09:48:40,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'platform:pcspkr')
2011-09-27 09:48:40,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'pci:v000080EEd0000BEEFsv00000000sd00000000bc03sc00i00')
2011-09-27 09:48:40,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-09-27 09:48:40,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'pci:v00008086d00007000sv00000000sd00000000bc06sc01i00')
2011-09-27 09:48:40,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'acpi:PNP0400:')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'pci:v00008086d0000265Csv00000000sd00000000bc0Csc03i20')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'input:b0003v80EEp0021e0110-e0,1,2,3,4,k110,111,112,113,114,r8,a0,1,m4,lsfw')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'dmi:bvninnotekGmbH:bvrVirtualBox:bd12/01/2006:svninnotekGmbH:pnVirtualBox:pvr1.2:')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'pci:v00008086d00002415sv00008086sd00000000bc04sc01i00')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'usb:v80EEp0021d0100dc00dsc00dp00ic03isc00ip00')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'pci:v00008086d00002829sv00000000sd00000000bc01sc06i01')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'pci:v00008086d00007113sv00000000sd00000000bc06sc80i00')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'pci:v000080EEd0000CAFEsv00000000sd00000000bc08sc80i00')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'platform:reg-dummy')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'input:b0011v0002p0006e0000-e0,1,2,k110,111,112,113,114,r0,1,6,8,amlsfw')
2011-09-27 09:48:40,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb74c764c> about HardwareID('modalias', 'acpi:PNP0F03:')
2011-09-27 09:48:49,010 WARNING: modinfo for module vboxguest failed: ERROR: modinfo: could not find module vboxguest

2011-09-27 09:48:49,010 WARNING: /sys/module/vboxguest/drivers does not exist, cannot rebind vboxguest driver
2011-09-27 09:49:17,585 DEBUG: Shutting down

```

---

### Post by loukingjr on 2011-09-27
I never did figure out what the problem was. I just removed the pre-installed guest additions and installed them from scratch.

---

### Post by amjjawad on 2011-09-27
Have you tried Lubuntu 11.10 Beta 2???

---

### Post by loukingjr on 2011-09-27
> **amjjawad said:**
> Have you tried Lubuntu 11.10 Beta 2???

yes, is what I installed today and re-did the guest additions as described.

---

### Post by amjjawad on 2011-09-27
> **loukingjr said:**
> yes, is what I installed today and re-did the guest additions as described.

OK, no promises here but I'll try to install that on VB if I got some time. I have lots to do before that.

---

