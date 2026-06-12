---
title: "Issues with 18.04 LTS botting on laptop after install?"
date: 2018-11-27
forum: New to Ubuntu
---

### Post by anonuser2 on 2018-11-27
Reposted from askubuntu since I was not able to find any help:

First time installing Ubuntu. Installed 18.04 LTS on MSI GF62VR 7RF laptop as a partition (the original OS installed on the laptop being Windows 10), but came across difficulties getting past the loading screen for installation, so I used noveau.modset=0, nolapic, and noapic. This allowed for me to install Linux, but now when I boot I get the following message:
```
[0.993362] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover t
sponse buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80
[0.993363] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover t
sponse buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80
[1.118200] Couldn't get size: 0x800000000000000e
/dev/sdb4: recovering journal
/dev/sdb4: clean, 178286/12181504 files, 2837801/48719104 blocks
[9.400464] iwlwifi 0000:02:00.0: pci_enable_msi failed - -38
```
I noticed that upon booting back into Windows 10 the WiFi is disconnected. Does anybody know what might be the issue and how to fix it? Thanks.

---

