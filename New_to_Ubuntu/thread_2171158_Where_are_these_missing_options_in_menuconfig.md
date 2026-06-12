---
title: "Where are these missing options in menuconfig?"
date: 2013-08-29
forum: New to Ubuntu
---

### Post by wyPLzfk on 2013-08-29
I'm following ["How to assign devices with VT-d in KVM"]("http://www.linux-kvm.org/page/How_to_assign_devices_with_VT-d_in_KVM") and am trying to modify the Kernel config as it suggests.
 But after going to /usr/src/linux-headers-3.x.x-x and running make menuconfig I can't find the following options:
"Bus options (PCI etc.)" -> "**Support for DMA Remapping Devices**" 
"Bus options (PCI etc.)" -> "**Enable DMA Remapping Devices**"
"Bus options (PCI etc.)" -> "**PCI Stub driver**"
They're just missing in menu options. Where can I find them?

---

### Post by tgalati4 on 2013-08-29
Perhaps they don't show up if your CPU/motherboard doesn't support VT-d?

```
dmesg | grep -e DMAR -e IOMMU
dmesg | grep AMD-Vi
```

---

### Post by wyPLzfk on 2013-08-29
dmesg | grep -e DMAR -e IOMMU returns
[    0.000000] Intel-IOMMU: enabled

My CPU Q9550 support VT-d also chipset x48 also support VT-d, need to rebuil kernel with Support for DMA Remapping Devices and Enable DMA Remapping Devices options enabled, but they missed from menuconfig.

---

### Post by supmethods2 on 2014-03-17
Ran make menuconfig and found it in under:
Device drivers --> IOMMU Hardware Support

---

