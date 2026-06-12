---
title: "Neither touchpad nor second monitor working on Asus Nitro 5 an515-42"
date: 2021-03-18
forum: New to Ubuntu
---

### Post by diegodarhty on 2021-03-18
I have a Asus Nitro 5 an515-42 sharing dual-boot between Ubuntu and WIndows 10.

Touchpad: just not working. Works fine in Windows

Second Monitor: Ubuntu doesn't recognize the second monitor. I tried installing the amd driver but it crashes the boot. Works fine in Windows.

---

### Post by CelticWarrior on 2021-03-18
Welcome.

The AMD Ryzen 5 2500U isn't new so therefore fully supported by the current kernel series both in Ubuntu 20.04 and 20.10. The AMD graphics driver is open-source, automatically installed and should be in use. Both the iGPU and the dGPU AMD Radeon RX560X are (should be) perfectly supported by the included amdgpu.

** No need for any user installed driver**

Regarding the touchpad (and other potential issues) make sure Fast Startup is disabled in Windows and Secure Boot is OFF in UEFI settings. Make sure Ubuntu is fully updated.
Regarding the external monitor it's use may only be possible if running the dGPU. In Windows it toggles on demand, not so much in Ubuntu.

---

