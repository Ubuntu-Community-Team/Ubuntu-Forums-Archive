---
title: "mp3 player doesn't show up"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by TooFreppaT on 2012-03-19
[FONT="Comic Sans MS"][[COLOR="Red"]http://www.ebay.com.au/itm/Gold-Mini-Clip-MP3-Player-Micro-SD-32GB-USB-Earphone-/190652515391#ht_3548wt_1141[/COLOR]]("http://www.ebay.com.au/itm/Gold-Mini-Clip-MP3-Player-Micro-SD-32GB-USB-Earphone-/190652515391#ht_3548wt_1141")

doesn't show up on [[FONT="Courier New"]System>Disk Utility[/FONT]], [[FONT="Courier New"]Places>Computer[/FONT]] or the [FONT="Courier New"]Desktop[/FONT]

[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]...please help! what should I do :?:[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/FONT]

---

### Post by winh8r on 2012-03-19
Open a terminal using control + alt + T

enter

```
lsusb
```

does it show up there?

---

### Post by TooFreppaT on 2012-03-19
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 1532:010b Razer USA, Ltd 
Bus 004 Device 002: ID e0ff:0002  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04a9:190a Canon, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

[FONT="Comic Sans MS"]...I have no idea what I'm supposed to be looking for¿[/FONT]

---

### Post by winh8r on 2012-03-19
> **TooFreppaT said:**
> ```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 1532:010b Razer USA, Ltd 
**[COLOR="Red"]Bus 004 Device 002: ID e0ff:0002 [/COLOR]** 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04a9:190a Canon, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

[FONT="Comic Sans MS"]...I have no idea what I'm supposed to be looking for¿[/FONT]

Try disconnecting the MP3 player and run the command again.

The entry above in red could be it but it seems to have no name.

If that entry is missing when you run the command again then , that is the MP£ player and we can work from there.

---

### Post by TooFreppaT on 2012-03-19
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 1532:010b Razer USA, Ltd 
Bus 004 Device 002: ID e0ff:0002  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04a9:190a Canon, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

[FONT="Comic Sans MS"]looks the same to me[/FONT]

---

### Post by winh8r on 2012-03-19
try this

```
cd /dev/disk/by-id
```

then 

```
ls -l
```

---

### Post by TooFreppaT on 2012-03-19
```
total 0
lrwxrwxrwx 1 root root  9 2012-03-17 21:25 ata-ST3500820AS_9QM0BM9K -> ../../sda
lrwxrwxrwx 1 root root 10 2012-03-17 21:26 ata-ST3500820AS_9QM0BM9K-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2012-03-17 21:25 ata-ST3500820AS_9QM0BM9K-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2012-03-17 21:25 ata-ST3500820AS_9QM0BM9K-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 2012-03-17 21:25 scsi-SATA_ST3500820AS_9QM0BM9K -> ../../sda
lrwxrwxrwx 1 root root 10 2012-03-17 21:26 scsi-SATA_ST3500820AS_9QM0BM9K-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2012-03-17 21:25 scsi-SATA_ST3500820AS_9QM0BM9K-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2012-03-17 21:25 scsi-SATA_ST3500820AS_9QM0BM9K-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 2012-03-17 21:25 wwn-0x5000c50009a7d9fe -> ../../sda
lrwxrwxrwx 1 root root 10 2012-03-17 21:26 wwn-0x5000c50009a7d9fe-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2012-03-17 21:25 wwn-0x5000c50009a7d9fe-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2012-03-17 21:25 wwn-0x5000c50009a7d9fe-part5 -> ../../sda5

```

---

### Post by Rodney9 on 2012-03-19
Might be a stupid question, but you do have a micro sd card inserted  ?


Rodney

---

### Post by TooFreppaT on 2012-03-19
> **Rodney9 said:**
> Might be a stupid question, but you do have a micro sd card inserted  ?


Rodney

[FONT="Comic Sans MS"]yeah I didn't notice until you said that! I thought it was, but it isn't: SanDisk 32GB Class2 microSD_HC_[/FONT]

---

### Post by Rodney9 on 2012-03-19
> **TooFreppaT said:**
> [FONT="Comic Sans MS"]yeah I didn't notice until you said that! I thought it was, but it isn't: SanDisk 32GB Class2 microSD_HC_[/FONT]

Working now ?

Rodney

---

