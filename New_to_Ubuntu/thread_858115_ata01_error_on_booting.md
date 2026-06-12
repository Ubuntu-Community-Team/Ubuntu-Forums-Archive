---
title: "ata01 error on booting"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by rohan1 on 2008-07-13
Hi

Am using Hardy 8.04 for some time...no problems until yesterday when I on booting I get a series of messages such as : Loading restricted drivers: emask ata01 DDRY Error followed by a series of similar error messages until it finally leads to the log on screen and then functions normally...would appreciate if anyone could advise on this issue..thanks in advance

rohan

---

### Post by unutbu on 2008-07-13
Log in, then open a terminal.
Type 
```
dmesg > dmesg.out
gedit dmesg.out
```

Look for (and post) anything that looks like an error message.

Then use gedit to open /var/log/messages and do the same thing.

---

### Post by rohan1 on 2008-07-13
Hi this is what appears on booting up:

  31.907309] PM: Checking swsusp image.
[   31.907575] PM: Resume from disk failed.
[   31.951688] kjournald starting.  Commit interval 5 seconds
[   31.951715] EXT3-fs: mounted filesystem with ordered data mode.
[   32.104690] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f618a405582]
[   56.103261] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   56.103370] ata1.00: BMDMA stat 0x24
[   56.103478] ata1.00: cmd c8/00:50:9f:4d:93/00:00:00:00:00/e0 tag 0 dma 40960 in
[   56.103480]          res 51/01:3a:b5:4d:93/00:00:00:00:00/e0 Emask 0x1 (device error)
[   56.103598] ata1.00: status: { DRDY ERR }
[   56.107577] ata1.00: configured for UDMA/100
[   56.107585] ata1: EH complete
[   62.939138] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   62.939245] ata1.00: BMDMA stat 0x24
[   62.939352] ata1.00: cmd c8/00:50:9f:4d:93/00:00:00:00:00/e0 tag 0 dma 40960 in
[   62.939353]          res 51/01:3a:b5:4d:93/00:00:00:00:00/e0 Emask 0x1 (device error)
[   62.939461] ata1.00: status: { DRDY ERR }
[   62.942765] ata1.00: configured for UDMA/100
[   62.942770] ata1: EH complete
[   69.766671] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   69.766778] ata1.00: BMDMA stat 0x24
[   69.766886] ata1.00: cmd c8/00:50:9f:4d:93/00:00:00:00:00/e0 tag 0 dma 40960 in
[   69.766887]          res 51/01:3a:b5:4d:93/00:00:00:00:00/e0 Emask 0x1 (device error)
[   69.766996] ata1.00: status: { DRDY ERR }
[   69.770211] ata1.00: configured for UDMA/100
[   69.770216] ata1: EH complete
[   76.587358] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   76.587465] ata1.00: BMDMA stat 0x24
[   76.587572] ata1.00: cmd c8/00:50:9f:4d:93/00:00:00:00:00/e0 tag 0 dma 40960 in
[   76.587573]          res 51/40:3a:b5:4d:93/00:00:00:00:00/e0 Emask 0x9 (media error)
[   76.587681] ata1.00: status: { DRDY ERR }
[   76.587785] ata1.00: error: { UNC }
[   76.591290] ata1.00: configured for UDMA/100
[   76.591298] ata1: EH complete
[   83.412771] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   83.412877] ata1.00: BMDMA stat 0x24
[   83.412992] ata1.00: cmd c8/00:50:9f:4d:93/00:00:00:00:00/e0 tag 0 dma 40960 in
[   83.412994]          res 51/01:3a:b5:4d:93/00:00:00:00:00/e0 Emask 0x1 (device error)
[   83.413117] ata1.00: status: { DRDY ERR }
[   83.416715] ata1.00: configured for UDMA/100
[   83.416722] ata1: EH complete
[   90.238448] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   90.238563] ata1.00: BMDMA stat 0x24
[   90.238677] ata1.00: cmd c8/00:50:9f:4d:93/00:00:00:00:00/e0 tag 0 dma 40960 in
[   90.238679]          res 51/40:3a:b5:4d:93/00:00:00:00:00/e0 Emask 0x9 (media error)
[   90.238801] ata1.00: status: { DRDY ERR }
[   90.238912] ata1.00: error: { UNC }
[   90.242481] ata1.00: configured for UDMA/100
[   90.242493] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   90.242500] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   90.242508] Descriptor sense data with sense descriptors (in hex):
[   90.242522]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   90.242531]         00 93 4d b5 
[   90.242535] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   90.242541] end_request: I/O error, dev sda, sector 9653685
[   90.242551] ata1: EH complete
[   90.242588] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   90.258195] sd 0:0:0:0: [sda] Write Protect is off
[   90.258198] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   90.258220] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   90.258240] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   90.258251] sd 0:0:0:0: [sda] Write Protect is off
[   90.258253] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   90.258271] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   97.053253] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   97.053368] ata1.00: BMDMA stat 0x24
[   97.053483] ata1.00: cmd c8/00:08:af:4d:93/00:00:00:00:00/e0 tag 0 dma 4096 in
[   97.053485]          res 51/01:02:b5:4d:93/00:00:00:00:00/e0 Emask 0x1 (device error)
[   97.053608] ata1.00: status: { DRDY ERR }
[   97.057200] ata1.00: configured for UDMA/100
[   97.057205] ata1: EH complete
[  103.880316] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  103.880430] ata1.00: BMDMA stat 0x24
[  103.880545] ata1.00: cmd c8/00:08:af:4d:93/00:00:00:00:00/e0 tag 0 dma 4096 in
[  103.880547]          res 51/01:02:b5:4d:93/00:00:00:00:00/e0 Emask 0x1 (device error)
[  103.880669] ata1.00: status: { DRDY ERR }
[  103.883523] ata1.00: configured for UDMA/100
[  103.883527] ata1: EH complete
[  110.703807] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  110.703933] ata1.00: BMDMA stat 0x24
[  110.704059] ata1.00: cmd c8/00:08:af:4d:93/00:00:00:00:00/e0 tag 0 dma 4096 in
[  110.704061]          res 51/01:02:b5:4d:93/00:00:00:00:00/e0 Emask 0x1 (device error)
[  110.704184] ata1.00: status: { DRDY ERR }
[  110.708065] ata1.00: configured for UDMA/100
[  110.708069] ata1: EH complete
[  117.528756] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  117.528871] ata1.00: BMDMA stat 0x24
[  117.528985] ata1.00: cmd c8/00:08:af:4d:93/00:00:00:00:00/e0 tag 0 dma 4096 in
[  117.528987]          res 51/01:02:b5:4d:93/00:00:00:00:00/e0 Emask 0x1 (device error)
[  117.529110] ata1.00: status: { DRDY ERR }
[  117.532068] ata1.00: configured for UDMA/100
[  117.532072] ata1: EH complete
[  124.349950] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  124.350065] ata1.00: BMDMA stat 0x24
[  124.350179] ata1.00: cmd c8/00:08:af:4d:93/00:00:00:00:00/e0 tag 0 dma 4096 in
[  124.350180]          res 51/40:02:b5:4d:93/00:00:00:00:00/e0 Emask 0x9 (media error)
[  124.350303] ata1.00: status: { DRDY ERR }
[  124.350414] ata1.00: error: { UNC }
[  124.353957] ata1.00: configured for UDMA/100
[  124.353962] ata1: EH complete
[  131.165054] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  131.165169] ata1.00: BMDMA stat 0x24
[  131.165284] ata1.00: cmd c8/00:08:af:4d:93/00:00:00:00:00/e0 tag 0 dma 4096 in
[  131.165285]          res 51/01:02:b5:4d:93/00:00:00:00:00/e0 Emask 0x1 (device error)
[  131.165408] ata1.00: status: { DRDY ERR }
[  131.168755] ata1.00: configured for UDMA/100
[  131.168761] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  131.168764] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  131.168768] Descriptor sense data with sense descriptors (in hex):
[  131.168770]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  131.168779]         00 93 4d b5 
[  131.168782] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
[  131.168788] end_request: I/O error, dev sda, sector 9653685

Eventually followed by id status link input output failed..it then boots up ok

Thanks

---

### Post by unutbu on 2008-07-13
I think this error is beyond what I know how to fix. 
Here is a bug report on a similar problem, though on different hardware:

[https://bugs.launchpad.net/linux/+bug/228540](https://bugs.launchpad.net/linux/+bug/228540)

You might have to file a bug report at bugs.launchpad.net. Or do some more searching there to see if anyone has already filed a similar bug. 

Sorry I can't help you further.

---

### Post by rohan1 on 2008-07-14
Will do..thanks anyway

---

### Post by okdok on 2008-07-28
I came across this post while searching for a solution to the same error message.

Recently, I have had to manually fsck my root partition several times and was concerned that maybe I was on the verge of a drive failure on relatively new hardware.

After changing my bios to disable native SATA, the errors went away.

Hope this help

---

### Post by okdok on 2008-07-28
um.. it looks like i was a little to eager. The error is back. :(

---

### Post by okdok on 2008-07-30
In my case the, the  hard drive was the problem. It has not failed yet but I suspect that it may soon. I swapped it for another and the error went away.

-cheers

---

