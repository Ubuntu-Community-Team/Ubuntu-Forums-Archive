---
title: "[any_os] Update UEFI firmware"
date: 2013-09-20
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2013-09-20
I have an HP 2000 notebook with UEFI firmware, and I have no idea on how to update.

I tried booting from EFI file:

*EFI-Partition*/EFI/HP/BIOSUpdate/**ALL_FILES_IN_HERE_THAT_END_WITH_EFI**

All fail. Here is a log:

```
Failed Loading HP BIOS Image Interface Protocol (Not Found)
Failed Loading HP BIOS Image Interface Protocol
Failed Loading HP BIOS Image Interface Protocol (Not Found)
Failed Loading HP BIOS Image Interface Protocol
Failed Loading HP BIOS Image Interface Protocol (Not Found)
Failed Loading HP BIOS Image Interface Protocol
```

Any ideas???

---

### Post by oldfred on 2013-09-20
I do not know with your HP. You need to search HP for updates on your specific model. The updates should have a new file and an instruction file.

With my system I go to vendor and download a new BIOS file. My motherboard has three ways to instal new BIOS. From Windows, from a bootable (DOS) flash drive or CD, or it can read directly from BIOS a file on a FAT32 formatted flash drive which is the one I use.

---

