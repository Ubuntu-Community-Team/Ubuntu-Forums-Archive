---
title: "DVD's Reader/Burner stopped working"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by dynamethod on 2008-06-08
Hey,


Basically as of today my DVD R/W drive has stopped working, currently trying to burn some data to a DVD right now:

```
tail /var/log/messages
```

```
Jun  8 19:14:59 darksun kernel: [ 1281.413069] sr 4:0:0:0: [sr0] Add. Sense: No additional sense information
Jun  8 19:14:59 darksun kernel: [ 1281.413073] end_request: I/O error, dev sr0, sector 0
Jun  8 19:14:59 darksun kernel: [ 1281.432430] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jun  8 19:14:59 darksun kernel: [ 1281.432434] sr 4:0:0:0: [sr0] Sense Key : Blank Check [current] 
Jun  8 19:14:59 darksun kernel: [ 1281.432437] sr 4:0:0:0: [sr0] Add. Sense: No additional sense information
Jun  8 19:14:59 darksun kernel: [ 1281.432441] end_request: I/O error, dev sr0, sector 0
Jun  8 19:14:59 darksun kernel: [ 1281.433329] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jun  8 19:14:59 darksun kernel: [ 1281.433333] sr 4:0:0:0: [sr0] Sense Key : Blank Check [current] 
Jun  8 19:14:59 darksun kernel: [ 1281.433336] sr 4:0:0:0: [sr0] Add. Sense: No additional sense information
Jun  8 19:14:59 darksun kernel: [ 1281.433340] end_request: I/O error, dev sr0, sector 0

```


I'm not totally sure this is OS specific because Windows XP is giving pretty much the same errors in Event Log (bad block)

I opened up the PC to make sure the connections are tight(this Device is connected via ATA)

Just finished the burn and tried to read the DVD

```
Jun  8 19:28:32 darksun kernel: [ 2093.922948] sr 4:0:0:0: [sr0] Add. Sense: No seek complete
Jun  8 19:28:32 darksun kernel: [ 2093.922951] end_request: I/O error, dev sr0, sector 3143004
Jun  8 19:28:41 darksun kernel: [ 2102.439210] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jun  8 19:28:41 darksun kernel: [ 2102.439216] sr 4:0:0:0: [sr0] Sense Key : Medium Error [current] 
Jun  8 19:28:41 darksun kernel: [ 2102.439220] sr 4:0:0:0: [sr0] Add. Sense: No seek complete
Jun  8 19:28:41 darksun kernel: [ 2102.439223] end_request: I/O error, dev sr0, sector 3143000
Jun  8 19:28:49 darksun kernel: [ 2110.952924] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jun  8 19:28:49 darksun kernel: [ 2110.952930] sr 4:0:0:0: [sr0] Sense Key : Medium Error [current] 
Jun  8 19:28:49 darksun kernel: [ 2110.952934] sr 4:0:0:0: [sr0] Add. Sense: No seek complete
Jun  8 19:28:49 darksun kernel: [ 2110.952937] end_request: I/O error, dev sr0, sector 5833204

```

help much appreciated

---

### Post by dynamethod on 2008-06-08
Model of DVD/CD R/W device: Asus DRW-1814BL

---

