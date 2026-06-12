---
title: "Error messages on return from sleep."
date: 2008-11-04
forum: New to Ubuntu
---

### Post by philinux on 2008-11-04
The two errors below appear on screen then pc restarts fine. Anyone else seen this?
ata3: softreset failed (device not ready)
ata1: softreset failed (device not ready)

Extract from dmesg
[ 9386.390732] parport_pc 00:07: activated
[ 9386.392572] serial 00:0b: activated
[ 9386.552028] sd 0:0:0:0: [sda] Starting disk
[ 9389.252019] ata3: softreset failed (device not ready)
[ 9389.252023] ata3: failed due to HW bug, retry pmp=0
[ 9389.416024] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 9389.416605] ata1: softreset failed (device not ready)
[ 9389.416607] ata1: failed due to HW bug, retry pmp=0
[ 9389.417206] ata3.00: configured for UDMA/133

---

