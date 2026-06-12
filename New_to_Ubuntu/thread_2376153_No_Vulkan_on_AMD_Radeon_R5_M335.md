---
title: "No Vulkan on AMD Radeon R5 M335"
date: 2017-10-30
forum: New to Ubuntu
---

### Post by Sam_Rosewood on 2017-10-30
Hello everyone!
I have laptop with AMD Radeon R5 M335. Windows 10 with installed official drivers shows Vulkan support for it.
I've installed Ubuntu 17.10 with package "mesa-vulkan-drivers" in addition to Windows, and command "vulkaninfo" showed me this:
```
===========
VULKAN INFO
===========


Vulkan API Version: 1.0.61


INFO: [loader] Code 0 : Found ICD manifest file /usr/share/vulkan/icd.d/intel_icd.x86_64.json, version "1.0.0"
INFO: [loader] Code 0 : Found ICD manifest file /usr/share/vulkan/icd.d/radeon_icd.x86_64.json, version "1.0.0"


Instance Extensions:
====================
Instance Extensions    count = 10
VK_KHR_external_memory_capabilities : extension revision 1
VK_KHR_get_physical_device_properties2: extension revision 1
VK_KHR_get_surface_capabilities2 : extension revision 1
VK_KHR_mir_surface : extension revision 4
VK_KHR_surface : extension revision 25
VK_KHR_wayland_surface : extension revision 6
VK_KHR_xcb_surface : extension revision 6
VK_KHR_xlib_surface : extension revision 6
VK_KHR_external_semaphore_capabilities: extension revision 1
VK_EXT_debug_report : extension revision 8
/build/vulkan-L06RNr/vulkan-1.0.61.1+dfsg1/demos/vulkaninfo.c:1722: failed with VK_ERROR_INITIALIZATION_FAILED
```
After googling, I've found this: [https://www.phoronix.com/forums/foru...vulkan-on-mesa](https://www.phoronix.com/forums/foru...vulkan-on-mesa)
I've added "modprobe.blacklist=radeon" to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub, but there was same result "VK_ERROR_INITIALIZATION_FAILED".
Here are parlty results of "lspci -v" before
```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] (rev 45) (prog-if 00 [VGA controller])
Subsystem: Dell Mullins [Radeon R4/R5 Graphics]
Flags: bus master, fast devsel, latency 0, IRQ 40
Memory at d0000000 (64-bit, prefetchable) [size=256M]
Memory at f0000000 (64-bit, prefetchable) [size=8M]
I/O ports at f000 [size=256]
Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
Expansion ROM at 000c0000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: radeon
Kernel modules: radeon, amdgpu
```
and after adding it.
```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] (rev 45) (prog-if 00 [VGA controller])
Subsystem: Dell Mullins [Radeon R4/R5 Graphics]
Flags: fast devsel, IRQ 39
Memory at d0000000 (64-bit, prefetchable) [size=256M]
Memory at f0000000 (64-bit, prefetchable) [size=8M]
I/O ports at f000 [size=256]
Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
Expansion ROM at 000c0000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel modules: radeon, amdgpu
```
Could you help me?

---

