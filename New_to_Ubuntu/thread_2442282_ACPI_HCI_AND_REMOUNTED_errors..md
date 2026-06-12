---
title: "ACPI HCI AND REMOUNTED errors."
date: 2020-05-01
forum: New to Ubuntu
---

### Post by canahmetdursun on 2020-05-01
Hey coffee experts! :  ) 
How i solve these errors? Help me out please :  )


```
dmesg | grep error
[    8.243445] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro
[  167.067608] ACPI Error: Aborting method \_GPE.XTBT due to previous error (AE_ALREADY_EXISTS) (20190816/psparse-529)
[  167.067622] ACPI Error: Aborting method \_GPE.XTBT due to previous error (AE_ALREADY_EXISTS) (20190816/psparse-529)
[  167.067640] ACPI Error: Aborting method \_GPE._E42 due to previous error (AE_ALREADY_EXISTS) (20190816/psparse-529)
[  167.067650] ACPI: Marking method _E42 as Serialized because of AE_ALREADY_EXISTS error
[  211.421541] xhci_hcd 0000:3a:00.0: PCI post-resume error -19!

```
```

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal

```

---

### Post by canahmetdursun on 2020-05-03
Up! :)

---

