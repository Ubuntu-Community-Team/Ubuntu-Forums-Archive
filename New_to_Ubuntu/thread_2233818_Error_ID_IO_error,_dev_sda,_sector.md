---
title: "Error ID I/O error, dev sda, sector"
date: 2014-07-10
forum: New to Ubuntu
---

### Post by teodyseguin on 2014-07-10
I am experiencing the same problem as this person posted over here [http://ubuntuforums.org/showthread.php?t=2048100](http://ubuntuforums.org/showthread.php?t=2048100)

I had my machine bought just 1 week now, and I expect everything will just go smooth. I installed Ubuntu 13.04. At some time, when I'm working my screen will just freeze for a few seconds and some of my open apps will just close instantly. I also have to press hold the cpu button just to kill it, and sometimes when I start over I always get this message error attempt read and write outside 'hd0', something like that. I have to kill the machine again, wait for a few minutes before it can totally open up ubuntu.

Please check my dmesg and my smart test. I can't really continue my work with these. Should I follow the suggested solution by **hadaka** from the link above? 

```

**dmesg**

[  681.472852] ata1.00: failed command: READ DMA EXT
[  681.472856] ata1.00: cmd 25/00:00:f8:eb:bd/00:01:1d:00:00/e0 tag 0 dma 131072 in
[  681.472856]          res 51/84:b0:48:ec:bd/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
 [  681.472858] ata1.00: status: { DRDY ERR }
[  681.472859] ata1.00: error: { ICRC ABRT }
[  681.472866] ata1.00: hard resetting link
[  681.791147] ata1.01: hard resetting link
 [  682.818130] ata1.01: failed to resume link (SControl 0)
[  682.974052] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  682.974067] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  682.998511] ata1.00: configured for UDMA/33
[  682.998861] ata1: EH complete
[  683.215898] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  683.215901] ata1.00: BMDMA stat 0x26
 [  683.215904] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  683.215906] ata1.00: failed command: READ DMA EXT
[  683.215909] ata1.00: cmd 25/00:88:a0:16:cb/00:00:1d:00:00/e0 tag 0 dma 69632 in
 [  683.215909]          res 51/84:38:f0:16:cb/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  683.215911] ata1.00: status: { DRDY ERR }
[  683.215912] ata1.00: error: { ICRC ABRT }
[  683.215918] ata1.00: hard resetting link
 [  683.533423] ata1.01: hard resetting link
[  684.560454] ata1.01: failed to resume link (SControl 0)
[  684.716356] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  684.716370] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  684.740813] ata1.00: configured for UDMA/33
[  684.741165] ata1: EH complete
[  685.034719] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  685.034725] ata1.00: BMDMA stat 0x26
 [  685.034729] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  685.034732] ata1.00: failed command: READ DMA EXT
[  685.034739] ata1.00: cmd 25/00:80:50:ab:c7/00:00:1d:00:00/e0 tag 0 dma 65536 in
 [  685.034739]          res 51/84:30:a0:ab:c7/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  685.034742] ata1.00: status: { DRDY ERR }
[  685.034744] ata1.00: error: { ICRC ABRT }
[  685.034753] ata1.00: hard resetting link
 [  685.351687] ata1.01: hard resetting link
[  686.378690] ata1.01: failed to resume link (SControl 0)
[  686.534516] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  686.534528] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  686.559018] ata1.00: configured for UDMA/33
[  686.559366] ata1: EH complete
[  686.624986] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  686.624989] ata1.00: BMDMA stat 0x26
 [  686.624992] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  686.624994] ata1.00: failed command: READ DMA EXT
[  686.624997] ata1.00: cmd 25/00:00:f0:6a:c1/00:01:1d:00:00/e0 tag 0 dma 131072 in
 [  686.624997]          res 51/84:40:b0:6b:c1/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  686.624999] ata1.00: status: { DRDY ERR }
[  686.625000] ata1.00: error: { ICRC ABRT }
[  686.625006] ata1.00: hard resetting link
 [  686.942134] ata1.01: hard resetting link
[  687.969136] ata1.01: failed to resume link (SControl 0)
[  688.125029] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  688.125040] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  688.149517] ata1.00: configured for UDMA/33
[  688.149860] ata1: EH complete
[  688.243204] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  688.243208] ata1.00: BMDMA stat 0x26
 [  688.243211] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  688.243213] ata1.00: failed command: READ DMA EXT
[  688.243217] ata1.00: cmd 25/00:00:60:11:c0/00:01:1d:00:00/e0 tag 0 dma 131072 in
 [  688.243217]          res 51/84:30:30:12:c0/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  688.243220] ata1.00: status: { DRDY ERR }
[  688.243221] ata1.00: error: { ICRC ABRT }
[  688.243228] ata1.00: hard resetting link
 [  688.560572] ata1.01: hard resetting link
[  689.587564] ata1.01: failed to resume link (SControl 0)
[  689.743467] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  689.743478] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  689.767933] ata1.00: configured for UDMA/33
[  689.768277] ata1: EH complete
[  689.833382] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  689.833387] ata1.00: BMDMA stat 0x26
 [  689.833391] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  689.833394] ata1.00: failed command: READ DMA EXT
[  689.833400] ata1.00: cmd 25/00:00:d0:ff:c7/00:01:1d:00:00/e0 tag 0 dma 131072 in
 [  689.833400]          res 51/84:80:50:00:c8/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  689.833404] ata1.00: status: { DRDY ERR }
[  689.833406] ata1.00: error: { ICRC ABRT }
[  689.833415] ata1.00: hard resetting link
 [  690.151010] ata1.01: hard resetting link
[  691.178027] ata1.01: failed to resume link (SControl 0)
[  691.333915] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  691.333929] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  691.368811] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[  691.368815] ata1.00: revalidation failed (errno=-5)
[  696.329020] ata1.00: hard resetting link
[  696.648694] ata1.01: hard resetting link
 [  697.675713] ata1.01: failed to resume link (SControl 0)
[  697.831615] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  697.831627] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  697.856091] ata1.00: configured for UDMA/33
[  697.856435] ata1: EH complete
[  697.876932] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  697.876935] ata1.00: BMDMA stat 0x26
 [  697.876937] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  697.876939] ata1.00: failed command: READ DMA EXT
[  697.876943] ata1.00: cmd 25/00:00:d0:ff:c7/00:01:1d:00:00/e0 tag 0 dma 131072 in
 [  697.876943]          res 51/84:20:b0:00:c8/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  697.876945] ata1.00: status: { DRDY ERR }
[  697.876947] ata1.00: error: { ICRC ABRT }
[  697.876954] ata1.00: hard resetting link
 [  698.195208] ata1.01: hard resetting link
[  699.222204] ata1.01: failed to resume link (SControl 0)
[  699.378120] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  699.378134] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  699.402614] ata1.00: configured for UDMA/33
[  699.402957] ata1: EH complete
[  699.421821] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  699.421824] ata1.00: BMDMA stat 0x26
 [  699.421827] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  699.421829] ata1.00: failed command: READ DMA EXT
[  699.421833] ata1.00: cmd 25/00:00:d0:ff:c7/00:01:1d:00:00/e0 tag 0 dma 131072 in
 [  699.421833]          res 51/84:d0:00:00:c8/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  699.421835] ata1.00: status: { DRDY ERR }
[  699.421836] ata1.00: error: { ICRC ABRT }
[  699.421843] ata1.00: hard resetting link
 [  699.737720] ata1.01: hard resetting link
[  700.764706] ata1.01: failed to resume link (SControl 0)
[  700.920632] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  700.920645] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  700.945095] ata1.00: configured for UDMA/33
[  700.945441] ata1: EH complete
[  701.195805] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  701.195808] ata1.00: BMDMA stat 0x26
 [  701.195811] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  701.195813] ata1.00: failed command: READ DMA EXT
[  701.195816] ata1.00: cmd 25/00:00:a0:73:c1/00:01:1d:00:00/e0 tag 0 dma 131072 in
 [  701.195816]          res 51/84:80:20:74:c1/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  701.195818] ata1.00: status: { DRDY ERR }
[  701.195819] ata1.00: error: { ICRC ABRT }
[  701.195825] ata1.00: hard resetting link
 [  701.511981] ata1.01: hard resetting link
[  702.538964] ata1.01: failed to resume link (SControl 0)
[  702.694903] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  702.694919] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  702.719364] ata1.00: configured for UDMA/33
[  702.719710] ata1: EH complete
[  702.837017] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  702.837020] ata1.00: BMDMA stat 0x26
 [  702.837023] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  702.837026] ata1.00: failed command: READ DMA EXT
[  702.837030] ata1.00: cmd 25/00:d8:28:a7:c1/00:00:1d:00:00/e0 tag 0 dma 110592 in
 [  702.837030]          res 51/84:88:78:a7:c1/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  702.837033] ata1.00: status: { DRDY ERR }
[  702.837034] ata1.00: error: { ICRC ABRT }
[  702.837042] ata1.00: hard resetting link
 [  703.154387] ata1.01: hard resetting link
[  704.181410] ata1.01: failed to resume link (SControl 0)
[  704.337303] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  704.337317] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  704.361777] ata1.00: configured for UDMA/33
[  704.362119] ata1: EH complete
[  704.873571] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  704.873576] ata1.00: BMDMA stat 0x26
 [  704.873578] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  704.873580] ata1.00: failed command: READ DMA EXT
[  704.873583] ata1.00: cmd 25/00:a0:40:88:c3/00:00:1d:00:00/e0 tag 0 dma 81920 in
 [  704.873583]          res 51/84:20:c0:88:c3/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  704.873585] ata1.00: status: { DRDY ERR }
[  704.873586] ata1.00: error: { ICRC ABRT }
[  704.873593] ata1.00: hard resetting link
 [  705.192408] ata1.01: hard resetting link
[  706.219430] ata1.01: failed to resume link (SControl 0)
[  706.375283] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  706.375298] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  706.394223] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[  706.394228] ata1.00: revalidation failed (errno=-5)
[  711.370345] ata1.00: hard resetting link
[  711.690108] ata1.01: hard resetting link
 [  712.717119] ata1.01: failed to resume link (SControl 0)
[  712.873000] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  712.873012] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  712.897484] ata1.00: configured for UDMA/33
[  712.897770] ata1: EH complete
[  713.158852] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  713.158856] ata1.00: BMDMA stat 0x26
 [  713.158858] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  713.158860] ata1.00: failed command: READ DMA EXT
[  713.158864] ata1.00: cmd 25/00:f8:50:95:c7/00:00:1d:00:00/e0 tag 0 dma 126976 in
 [  713.158864]          res 51/84:08:40:96:c7/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  713.158865] ata1.00: status: { DRDY ERR }
[  713.158866] ata1.00: error: { ICRC ABRT }
[  713.158873] ata1.00: hard resetting link
 [  713.476365] ata1.01: hard resetting link
[  714.503384] ata1.01: failed to resume link (SControl 0)
[  714.659288] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  714.659300] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  714.694185] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[  714.694190] ata1.00: revalidation failed (errno=-5)
[  719.654379] ata1.00: hard resetting link
[  719.974076] ata1.01: hard resetting link
 [  721.001060] ata1.01: failed to resume link (SControl 0)
[  721.156952] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  721.156966] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  721.181442] ata1.00: configured for UDMA/33
[  721.181795] ata1: EH complete
[  721.204168] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  721.204171] ata1.00: BMDMA stat 0x26
 [  721.204174] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  721.204176] ata1.00: failed command: READ DMA EXT
[  721.204180] ata1.00: cmd 25/00:00:a8:a1:c7/00:01:1d:00:00/e0 tag 0 dma 131072 in
 [  721.204180]          res 51/84:d0:d8:a1:c7/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  721.204182] ata1.00: status: { DRDY ERR }
[  721.204184] ata1.00: error: { ICRC ABRT }
[  721.204191] ata1.00: hard resetting link
 [  721.520570] ata1.01: hard resetting link
[  722.547497] ata1.01: failed to resume link (SControl 0)
[  722.703466] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  722.703478] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  722.722287] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[  722.722290] ata1.00: revalidation failed (errno=-5)
[  727.698562] ata1.00: hard resetting link
[  728.018253] ata1.01: hard resetting link
 [  729.045263] ata1.01: failed to resume link (SControl 0)
[  729.201164] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  729.201177] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  729.225649] ata1.00: configured for UDMA/33
[  729.225982] ata1: EH complete
[  729.993399] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  729.993403] ata1.00: BMDMA stat 0x26
 [  729.993405] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  729.993407] ata1.00: failed command: READ DMA EXT
[  729.993410] ata1.00: cmd 25/00:00:d8:3f:c7/00:01:1d:00:00/e0 tag 0 dma 131072 in
 [  729.993410]          res 51/84:80:58:40:c7/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  729.993412] ata1.00: status: { DRDY ERR }
[  729.993413] ata1.00: error: { ICRC ABRT }
[  729.993420] ata1.00: hard resetting link
 [  730.312030] ata1.01: hard resetting link
[  731.339022] ata1.01: failed to resume link (SControl 0)
[  731.494932] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  731.494943] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  731.519410] ata1.00: configured for UDMA/33
[  731.519754] ata1: EH complete
[  731.832438] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  731.832441] ata1.00: BMDMA stat 0x26
 [  731.832444] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  731.832446] ata1.00: failed command: READ DMA EXT
[  731.832449] ata1.00: cmd 25/00:00:e8:6f:ca/00:01:1d:00:00/e0 tag 0 dma 131072 in
 [  731.832449]          res 51/84:b0:38:70:ca/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  731.832451] ata1.00: status: { DRDY ERR }
[  731.832452] ata1.00: error: { ICRC ABRT }
[  731.832458] ata1.00: hard resetting link
 [  732.150204] ata1.01: hard resetting link
[  733.177237] ata1.01: failed to resume link (SControl 0)
[  733.333157] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  733.333171] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  733.352026] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[  733.352032] ata1.00: revalidation failed (errno=-5)
[  738.328246] ata1.00: hard resetting link
[  738.647905] ata1.01: hard resetting link
 [  739.674945] ata1.01: failed to resume link (SControl 0)
[  739.830838] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  739.830850] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  739.855299] ata1.00: configured for UDMA/33
[  739.855588] ata1: EH complete
[  740.665659] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  740.665663] ata1.00: BMDMA stat 0x26
 [  740.665665] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  740.665667] ata1.00: failed command: READ DMA EXT
[  740.665670] ata1.00: cmd 25/00:00:c0:be:c9/00:01:1d:00:00/e0 tag 0 dma 131072 in
 [  740.665670]          res 51/84:b0:10:bf:c9/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  740.665672] ata1.00: status: { DRDY ERR }
[  740.665673] ata1.00: error: { ICRC ABRT }
[  740.665680] ata1.00: hard resetting link
 [  740.981672] ata1.01: hard resetting link
[  742.008672] ata1.01: failed to resume link (SControl 0)
[  742.164596] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  742.164609] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  742.183310] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[  742.183313] ata1.00: revalidation failed (errno=-5)
[  747.159648] ata1.00: hard resetting link
[  747.479366] ata1.01: hard resetting link
 [  748.506360] ata1.01: failed to resume link (SControl 0)
[  748.662264] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  748.662276] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  748.686717] ata1.00: configured for UDMA/33
[  748.687006] ata1: EH complete
[  750.250379] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  750.250382] ata1.00: BMDMA stat 0x26
 [  750.250385] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  750.250387] ata1.00: failed command: READ DMA EXT
[  750.250390] ata1.00: cmd 25/00:d0:68:3d:f1/00:00:1d:00:00/e0 tag 0 dma 106496 in
 [  750.250390]          res 51/84:b0:88:3d:f1/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  750.250392] ata1.00: status: { DRDY ERR }
[  750.250393] ata1.00: error: { ICRC ABRT }
[  750.250400] ata1.00: hard resetting link
 [  750.568327] ata1.01: hard resetting link
[  751.595361] ata1.01: failed to resume link (SControl 0)
[  751.751268] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  751.751279] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  751.775716] ata1.00: configured for UDMA/33
[  751.776005] ata1: EH complete
[  751.902468] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  751.902471] ata1.00: BMDMA stat 0x26
 [  751.902474] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  751.902476] ata1.00: failed command: READ DMA EXT
[  751.902479] ata1.00: cmd 25/00:88:f0:a5:c1/00:00:1d:00:00/e0 tag 0 dma 69632 in
 [  751.902479]          res 51/84:08:70:a6:c1/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  751.902481] ata1.00: status: { DRDY ERR }
[  751.902482] ata1.00: error: { ICRC ABRT }
[  751.902489] ata1.00: hard resetting link
 [  752.218765] ata1.01: hard resetting link
[  753.245760] ata1.01: failed to resume link (SControl 0)
[  753.401674] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  753.401687] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  753.426116] ata1.00: configured for UDMA/33
[  753.426460] ata1: EH complete
[  753.986512] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  753.986515] ata1.00: BMDMA stat 0x26
 [  753.986518] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  753.986520] ata1.00: failed command: READ DMA EXT
[  753.986523] ata1.00: cmd 25/00:70:60:75:e1/00:00:1d:00:00/e0 tag 0 dma 57344 in
 [  753.986523]          res 51/84:00:cf:75:e1/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  753.986525] ata1.00: status: { DRDY ERR }
[  753.986526] ata1.00: error: { ICRC ABRT }
[  753.986533] ata1.00: hard resetting link
 [  754.304663] ata1.01: hard resetting link
[  755.331729] ata1.01: failed to resume link (SControl 0)
[  755.487644] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  755.487656] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  755.512053] ata1.00: configured for UDMA/33
[  755.512332] ata1: EH complete
[  757.163859] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  757.163862] ata1.00: BMDMA stat 0x26
 [  757.163865] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  757.163867] ata1.00: failed command: READ DMA EXT
[  757.163870] ata1.00: cmd 25/00:00:a8:e2:c3/00:01:1d:00:00/e0 tag 0 dma 131072 in
 [  757.163870]          res 51/84:50:58:e3:c3/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  757.163872] ata1.00: status: { DRDY ERR }
[  757.163873] ata1.00: error: { ICRC ABRT }
[  757.163879] ata1.00: hard resetting link
 [  757.481665] ata1.01: hard resetting link
[  758.508650] ata1.01: failed to resume link (SControl 0)
[  758.664486] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  758.664499] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  758.688951] ata1.00: configured for UDMA/33
[  758.689228] ata1: EH complete
[  759.391993] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  759.391997] ata1.00: BMDMA stat 0x26
 [  759.391999] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  759.392001] ata1.00: failed command: READ DMA EXT
[  759.392004] ata1.00: cmd 25/00:80:20:f1:c6/00:00:1d:00:00/e0 tag 0 dma 65536 in
 [  759.392004]          res 51/84:20:80:f1:c6/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  759.392006] ata1.00: status: { DRDY ERR }
[  759.392007] ata1.00: error: { ICRC ABRT }
[  759.392014] ata1.00: hard resetting link
 [  759.711497] ata1.01: hard resetting link
[  760.738482] ata1.01: failed to resume link (SControl 0)
[  760.894348] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  760.894359] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  760.918871] ata1.00: configured for UDMA/33
[  760.919148] ata1: EH complete
[  763.621744] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  763.621748] ata1.00: BMDMA stat 0x26
 [  763.621751] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  763.621753] ata1.00: failed command: READ DMA EXT
[  763.621756] ata1.00: cmd 25/00:08:a8:3f:52/00:00:23:00:00/e0 tag 0 dma 4096 in
 [  763.621756]          res 51/84:00:af:3f:52/84:00:23:00:00/e0 Emask 0x70 (host bus error)
[  763.621759] ata1.00: status: { DRDY ERR }
[  763.621760] ata1.00: error: { ICRC ABRT }
[  763.621767] ata1.00: hard resetting link
 [  763.939391] ata1.01: hard resetting link
[  764.966380] ata1.01: failed to resume link (SControl 0)
[  765.122261] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  765.122272] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  765.146748] ata1.00: configured for UDMA/33
[  765.147108] ata1: EH complete
[  766.145654] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  766.145659] ata1.00: BMDMA stat 0x26
 [  766.145661] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  766.145663] ata1.00: failed command: READ DMA EXT
[  766.145667] ata1.00: cmd 25/00:00:80:48:e1/00:02:1d:00:00/e0 tag 0 dma 262144 in
 [  766.145667]          res 51/84:80:00:4a:e1/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  766.145670] ata1.00: status: { DRDY ERR }
[  766.145671] ata1.00: error: { ICRC ABRT }
[  766.145678] ata1.00: hard resetting link
 [  766.464927] ata1.01: hard resetting link
[  767.491950] ata1.01: failed to resume link (SControl 0)
[  767.647832] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  767.647845] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  767.672268] ata1.00: configured for UDMA/33
[  767.672612] ata1: EH complete
[  767.769304] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  767.769309] ata1.00: BMDMA stat 0x26
 [  767.769311] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  767.769313] ata1.00: failed command: READ DMA EXT
[  767.769317] ata1.00: cmd 25/00:00:80:4e:e1/00:01:1d:00:00/e0 tag 0 dma 131072 in
 [  767.769317]          res 51/84:80:00:4f:e1/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  767.769318] ata1.00: status: { DRDY ERR }
[  767.769320] ata1.00: error: { ICRC ABRT }
[  767.769326] ata1.00: hard resetting link
 [  768.087366] ata1.01: hard resetting link
[  769.114309] ata1.01: failed to resume link (SControl 0)
[  769.270214] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  769.270226] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  769.289062] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[  769.289065] ata1.00: revalidation failed (errno=-5)
[  774.265346] ata1.00: hard resetting link
[  774.585041] ata1.01: hard resetting link
 [  775.612045] ata1.01: failed to resume link (SControl 0)
[  775.767948] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  775.767960] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  775.802713] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[  775.802716] ata1.00: revalidation failed (errno=-5)
[  775.802729] ata1.00: limiting speed to UDMA/33:PIO3
[  780.763044] ata1.00: hard resetting link
 [  781.082750] ata1.01: hard resetting link
[  782.109685] ata1.01: failed to resume link (SControl 0)
[  782.265613] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  782.265624] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  782.290123] ata1.00: configured for UDMA/33
[  782.290468] ata1: EH complete
[  782.550435] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  782.550439] ata1.00: BMDMA stat 0x26
 [  782.550441] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  782.550443] ata1.00: failed command: READ DMA EXT
[  782.550447] ata1.00: cmd 25/00:00:80:59:e1/00:02:1d:00:00/e0 tag 0 dma 262144 in
 [  782.550447]          res 51/84:30:50:5a:e1/84:01:1d:00:00/e0 Emask 0x70 (host bus error)
[  782.550449] ata1.00: status: { DRDY ERR }
[  782.550450] ata1.00: error: { ICRC ABRT }
[  782.550456] ata1.00: hard resetting link
 [  782.869011] ata1.01: hard resetting link
[  783.896003] ata1.01: failed to resume link (SControl 0)
[  784.051917] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  784.051929] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  784.076377] ata1.00: configured for UDMA/33
[  784.076705] ata1: EH complete
[  784.184072] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  784.184075] ata1.00: BMDMA stat 0x26
 [  784.184077] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  784.184080] ata1.00: failed command: READ DMA EXT
[  784.184083] ata1.00: cmd 25/00:00:80:5e:e1/00:02:1d:00:00/e0 tag 0 dma 262144 in
 [  784.184083]          res 51/84:20:60:5f:e1/84:01:1d:00:00/e0 Emask 0x70 (host bus error)
[  784.184085] ata1.00: status: { DRDY ERR }
[  784.184086] ata1.00: error: { ICRC ABRT }
[  784.184092] ata1.00: hard resetting link
 [  784.503447] ata1.01: hard resetting link
[  785.530352] ata1.01: failed to resume link (SControl 0)
[  785.686315] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  785.686327] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  785.710784] ata1.00: configured for UDMA/33
[  785.711070] ata1: EH complete
[  786.211775] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x480900 action 0x6
[  786.211780] ata1.00: BMDMA stat 0x26
 [  786.211782] ata1.00: SError: { UnrecovData HostInt 10B8B Handshk }
[  786.211785] ata1.00: failed command: WRITE DMA EXT
[  786.211789] ata1.00: cmd 35/00:08:50:6d:55/00:00:27:00:00/e0 tag 0 dma 4096 out
 [  786.211789]          res 51/84:01:57:6d:55/84:00:27:00:00/e0 Emask 0x70 (host bus error)
[  786.211790] ata1.00: status: { DRDY ERR }
[  786.211791] ata1.00: error: { ICRC ABRT }
[  786.211798] ata1.00: hard resetting link
 [  786.529406] ata1.01: hard resetting link
[  787.556448] ata1.01: failed to resume link (SControl 0)
[  787.712362] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  787.712376] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  787.736824] ata1.00: configured for UDMA/33
[  787.737110] ata1: EH complete
[  789.459200] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  789.459204] ata1.00: BMDMA stat 0x26
 [  789.459207] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  789.459209] ata1.00: failed command: READ DMA EXT
[  789.459213] ata1.00: cmd 25/00:e8:28:df:bb/00:00:1d:00:00/e0 tag 0 dma 118784 in
 [  789.459213]          res 51/84:68:a8:df:bb/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  789.459214] ata1.00: status: { DRDY ERR }
[  789.459216] ata1.00: error: { ICRC ABRT }
[  789.459222] ata1.00: hard resetting link
 [  789.778311] ata1.01: hard resetting link
[  790.805290] ata1.01: failed to resume link (SControl 0)
[  790.961205] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  790.961218] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  791.045617] ata1.00: configured for UDMA/33
[  791.045960] ata1: EH complete
[  791.313535] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x280900 action 0x6
[  791.313539] ata1.00: BMDMA stat 0x26
 [  791.313541] ata1.00: SError: { UnrecovData HostInt 10B8B BadCRC }
[  791.313544] ata1.00: failed command: READ DMA EXT
[  791.313547] ata1.00: cmd 25/00:00:e0:d1:bb/00:01:1d:00:00/e0 tag 0 dma 131072 in
 [  791.313547]          res 51/84:60:80:d2:bb/84:00:1d:00:00/e0 Emask 0x70 (host bus error)
[  791.313549] ata1.00: status: { DRDY ERR }
[  791.313550] ata1.00: error: { ICRC ABRT }
[  791.313557] ata1.00: hard resetting link
 [  791.632505] ata1.01: hard resetting link
[  792.659494] ata1.01: failed to resume link (SControl 0)
[  792.815411] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  792.815424] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  792.939751] ata1.00: configured for UDMA/33
[  792.940044] ata1: EH complete
[  851.472244] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x480900 action 0x6
[  851.472250] ata1.00: BMDMA stat 0x26
 [  851.472254] ata1.00: SError: { UnrecovData HostInt 10B8B Handshk }
[  851.472257] ata1.00: failed command: WRITE DMA EXT
[  851.472264] ata1.00: cmd 35/00:08:68:dc:57/00:00:22:00:00/e0 tag 0 dma 4096 out
 [  851.472264]          res 51/84:01:6f:dc:57/84:00:22:00:00/e0 Emask 0x70 (host bus error)
[  851.472267] ata1.00: status: { DRDY ERR }
[  851.472270] ata1.00: error: { ICRC ABRT }
[  851.472279] ata1.00: hard resetting link
 [  851.790087] ata1.01: hard resetting link
[  852.817087] ata1.01: failed to resume link (SControl 0)
[  852.973007] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  852.973021] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  852.991734] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[  852.991736] ata1.00: revalidation failed (errno=-5)
[  857.968039] ata1.00: hard resetting link
[  858.287739] ata1.01: hard resetting link
 [  859.314778] ata1.01: failed to resume link (SControl 0)
[  859.470687] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  859.470699] ata1.01: SATA link down (SStatus 0 SControl 0)
 [  859.495143] ata1.00: configured for UDMA/33
[  859.495473] ata1: EH complete

```

```

**smart test**


smartctl 5.43 2012-06-30 r3573 [i686-linux-3.8.0-35-generic] (local build)
 Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)


=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda (SATA 3Gb/s, 4K Sectors)
 Device Model:     ST500DM002-1BD142
Serial Number:    Z6E56314
LU WWN Device Id: 5 000c50 066fce7f0
Firmware Version: KC45
User Capacity:    500,107,862,016 bytes [500 GB]
 Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
 Local Time is:    Fri Jul 11 10:50:09 2014 PHT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
 SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                     was completed without error.
                    Auto Offline Data Collection: Enabled.
 Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                     been run.
Total time to complete Offline 
data collection:         (  609) seconds.
 Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                     Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                     Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
 SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                     Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                     General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
 Extended self-test routine
recommended polling time:      (  84) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
 SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                     SCT Feature Control supported.
                    SCT Data Table supported.


 SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
   1 Raw_Read_Error_Rate     0x000f   110   099   006    Pre-fail  Always       -       26679192
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       69
   5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   060   060   030    Pre-fail  Always       -       1192938
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       105
  10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       69
183 Runtime_Bad_Block       0x0032   020   020   000    Old_age   Always       -       80
 184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   096   000    Old_age   Always       -       468158644334
 189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   063   061   045    Old_age   Always       -       37 (Min/Max 37/37)
194 Temperature_Celsius     0x0022   037   040   000    Old_age   Always       -       37 (0 25 0 0 0)
 195 Hardware_ECC_Recovered  0x001a   049   037   000    Old_age   Always       -       26679192
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
 199 UDMA_CRC_Error_Count    0x003e   200   194   000    Old_age   Always       -       9105
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       259480449187943
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       1072978654
 242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2265266160


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
 No self-tests have been logged.  [To run self-tests, use: smartctl -t]




SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
     1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
 Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

---

### Post by Vladlenin5000 on 2014-07-11
Hi, welcome.

Your HDD is giving you warnings and you should consider backing up any important data - probably not important because you just installed it -, replace it and start with a fresh installation of a supported version like the current 14.04. 13.04 is end of life, it has no repositories to update from, and it ISN'T supported here.

---

### Post by teodyseguin on 2014-07-11
Hi Vladlenin5000

Thanks for you reply. I'll try your suggestion.

---

### Post by teodyseguin on 2014-07-11
Okay, I made a clean install again. This time, it's 14.04, although I'm still experiencing the same situation. I actually went back to the shop where I bought my unit. They diagnose the drive and the memory as well, both went good. 

Btw, I have done the installation using a live USB, and it took me 3x to perfect the installation. The first 2 attempts went problematic due to I/O error as well :(

---

### Post by tgalati4 on 2014-07-11
It's possible that a bad cable or poor solder connection on the motherboard or the hard disk is causing the problem.  Since the laptop is new, it could simply be a break-in issue.  The laptop passes the simple diagnostics, but when you really start to use it, problems show up.  

Is this a dual-boot machine?  Does it work with Windows for long periods of time?

---

### Post by teodyseguin on 2014-07-11
Hi tgalati4

It's not actually a laptop but a desktop. Come to  think of it, I have an extra SATA cable given to me upon my purchase of  the unit. I will give it a try. 

It's not a dual-boot. It's a one OS linux now. Never tried on Windows cause I really don't have plan on going to Windows :)

---

### Post by teodyseguin on 2014-07-12
Okay, I tried to replace the current SATA cable with the spare I had, thinking that it may be faulty and was the one causing the problem. In the end, it turns out to be the same. Still experiencing randomly getting Read Only File system.

I was watching the /var/log/kern.log, until I found out that whenever this message appear from the log

ata1.00: revalidation failed (errno=-5)

each of my applications, automatically close, commands from terminal starts to become unsuable because the system becomes read only.

Really hoping to get more light on this :(

---

### Post by bensocket on 2014-07-12
i would guess your hard drive is faulty

---

### Post by tgalati4 on 2014-07-12
Try different SATA sockets.  It could be a bad SATA controller.  Also try checking SATA settings in BIOS.  Turn off any legacy, IDE modes.

---

### Post by teodyseguin on 2014-07-12
@bensucket .. even if it's brand new? I got it bought since July 5.

@tgalati4 .. I'm not exactly sure how to do that but I will try and let you know. But surprisingly, as I left my unit open since last night, no trace of the same experience I had from the last 2 days. Very weird.

---

### Post by Vladlenin5000 on 2014-07-12
> **teodyseguin said:**
> @bensucket .. even if it's brand new? I got it bought since July 5.

A ST500DM002-1BD142 - Seagate Barracuda 500GB - can't be considered 'brand new' under any criteria. It was released circa July 2011 and the SMART tests systematically showed "old age"/"pre failure" in any given parameters therefore it isn't even a case of an old drive sitting on a shelf for 2-3 years but otherwise 'new'... No, the drive you tested has been used and used a LOT.
It's an accident waiting to happen.
That said, what you've been experiencing may not be directly related with the drive but rather, as previously suggested, due to incorrect BIOS settings. The optimal setting for this drives is AHCI (or RAID if in an array, not applicable here), never 'legacy', 'IDE' or similar... Please check this before anything else.

---

### Post by teodyseguin on 2014-07-13
That did it! Changing the SATA mode from IDE to AHCI did the fix for me. I found the option under Integrated Peripherals from the BIOS. Thank you so much for the help :)

---

