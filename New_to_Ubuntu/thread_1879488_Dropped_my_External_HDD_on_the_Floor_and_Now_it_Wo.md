---
title: "Dropped my External HDD on the Floor and Now it Won't Mount"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by Sandbagger3 on 2011-11-11
My external hard drive was mounted and spinning when I knocked it of the shelf.  Now when I plug in the USB drive I see the proper name in the file manager, but attempting to mount it gives the error:

"Unable to mount [drivename]
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending"

Any idea how I can get the drive communicating again?


dmesg output is
```

[96763.441331] sd 6:0:0:0: timing out command, waited 180s
[96763.441358] sd 6:0:0:0: [sde] Unhandled sense code
[96763.441364] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[96763.441373] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[96763.441384] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[96763.441398] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e4 f5 66 00 00 01 00
[96763.441416] end_request: I/O error, dev sde, sector 120040240
[96763.441427] Buffer I/O error on device sde, logical block 15005030
[96763.441432] lost page write due to I/O error on sde
[96763.442438] sd 6:0:0:0: timing out command, waited 180s
[96763.442448] sd 6:0:0:0: [sde] Unhandled sense code
[96763.442453] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[96763.442460] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[96763.442468] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[96763.442477] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e4 f9 67 00 00 01 00
[96763.442492] end_request: I/O error, dev sde, sector 120048440
[96763.442498] Buffer I/O error on device sde, logical block 15006055
[96763.442503] lost page write due to I/O error on sde
[96943.454375] sd 6:0:0:0: timing out command, waited 180s
[96943.454402] sd 6:0:0:0: [sde] Unhandled sense code
[96943.454407] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[96943.454417] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[96943.454427] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[96943.454442] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 97 14 00 00 01 00
[96943.454459] end_request: I/O error, dev sde, sector 118274208
[96943.454470] Buffer I/O error on device sde, logical block 14784276
[96943.454475] lost page write due to I/O error on sde
[96943.654371] sd 6:0:0:0: timing out command, waited 180s
[96943.654398] sd 6:0:0:0: [sde] Unhandled sense code
[96943.654404] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[96943.654413] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[96943.654423] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[96943.654438] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 9b 15 00 00 01 00
[96943.654456] end_request: I/O error, dev sde, sector 118282408
[96943.654466] Buffer I/O error on device sde, logical block 14785301
[96943.654471] lost page write due to I/O error on sde
[97123.457048] sd 6:0:0:0: timing out command, waited 180s
[97123.457074] sd 6:0:0:0: [sde] Unhandled sense code
[97123.457080] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[97123.457090] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[97123.457100] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[97123.457115] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 9f 16 00 00 01 00
[97123.457133] end_request: I/O error, dev sde, sector 118290608
[97123.457144] Buffer I/O error on device sde, logical block 14786326
[97123.457149] lost page write due to I/O error on sde
[97303.461106] sd 6:0:0:0: timing out command, waited 180s
[97303.461125] sd 6:0:0:0: [sde] Unhandled sense code
[97303.461131] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[97303.461140] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[97303.461150] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[97303.461165] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e4 fd 68 00 00 01 00
[97303.461182] end_request: I/O error, dev sde, sector 120056640
[97303.461191] Buffer I/O error on device sde, logical block 15007080
[97303.461196] lost page write due to I/O error on sde
[97303.462597] sd 6:0:0:0: timing out command, waited 180s
[97303.462607] sd 6:0:0:0: [sde] Unhandled sense code
[97303.462612] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[97303.462619] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[97303.462627] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[97303.462636] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 47 7c 00 00 01 00
[97303.462650] end_request: I/O error, dev sde, sector 120208352
[97303.462657] Buffer I/O error on device sde, logical block 15026044
[97303.462662] lost page write due to I/O error on sde
[97483.471426] sd 6:0:0:0: timing out command, waited 180s
[97483.471453] sd 6:0:0:0: [sde] Unhandled sense code
[97483.471459] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[97483.471468] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[97483.471479] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[97483.471494] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 4b 7d 00 00 01 00
[97483.471512] end_request: I/O error, dev sde, sector 120216552
[97483.471522] Buffer I/O error on device sde, logical block 15027069
[97483.471526] lost page write due to I/O error on sde
[97483.473290] sd 6:0:0:0: timing out command, waited 180s
[97483.473302] sd 6:0:0:0: [sde] Unhandled sense code
[97483.473307] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[97483.473314] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[97483.473322] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[97483.473331] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 4f 7e 00 00 01 00
[97483.473346] end_request: I/O error, dev sde, sector 120224752
[97483.473353] Buffer I/O error on device sde, logical block 15028094
[97483.473358] lost page write due to I/O error on sde
[97663.484505] sd 6:0:0:0: timing out command, waited 180s
[97663.484533] sd 6:0:0:0: [sde] Unhandled sense code
[97663.484539] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[97663.484548] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[97663.484559] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[97663.484574] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 a3 17 00 00 01 00
[97663.484592] end_request: I/O error, dev sde, sector 118298808
[97663.484603] Buffer I/O error on device sde, logical block 14787351
[97663.484607] lost page write due to I/O error on sde
[97663.684491] sd 6:0:0:0: timing out command, waited 180s
[97663.684519] sd 6:0:0:0: [sde] Unhandled sense code
[97663.684525] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[97663.684534] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[97663.684544] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[97663.684559] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 a7 18 00 00 01 00
[97663.684577] end_request: I/O error, dev sde, sector 118307008
[97663.684588] Buffer I/O error on device sde, logical block 14788376
[97663.684593] lost page write due to I/O error on sde
[97843.497680] sd 6:0:0:0: timing out command, waited 180s
[97843.497706] sd 6:0:0:0: [sde] Unhandled sense code
[97843.497712] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[97843.497722] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[97843.497732] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[97843.497746] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 ab 19 00 00 01 00
[97843.497764] end_request: I/O error, dev sde, sector 118315208
[97843.497775] Buffer I/O error on device sde, logical block 14789401
[97843.497780] lost page write due to I/O error on sde
[98023.510620] sd 6:0:0:0: timing out command, waited 180s
[98023.510649] sd 6:0:0:0: [sde] Unhandled sense code
[98023.510655] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98023.510664] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98023.510675] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98023.510689] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 53 7f 00 00 01 00
[98023.510706] end_request: I/O error, dev sde, sector 120232952
[98023.510716] Buffer I/O error on device sde, logical block 15029119
[98023.510721] lost page write due to I/O error on sde
[98023.511732] sd 6:0:0:0: timing out command, waited 180s
[98023.511742] sd 6:0:0:0: [sde] Unhandled sense code
[98023.511747] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98023.511754] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98023.511762] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98023.511770] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 57 80 00 00 01 00
[98023.511786] end_request: I/O error, dev sde, sector 120241152
[98023.511792] Buffer I/O error on device sde, logical block 15030144
[98023.511797] lost page write due to I/O error on sde
[98203.512823] sd 6:0:0:0: timing out command, waited 180s
[98203.512850] sd 6:0:0:0: [sde] Unhandled sense code
[98203.512855] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98203.512864] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98203.512875] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98203.512890] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 5b 81 00 00 01 00
[98203.512917] end_request: I/O error, dev sde, sector 120249352
[98203.512927] Buffer I/O error on device sde, logical block 15031169
[98203.512932] lost page write due to I/O error on sde
[98203.513929] sd 6:0:0:0: timing out command, waited 180s
[98203.513939] sd 6:0:0:0: [sde] Unhandled sense code
[98203.513944] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98203.513951] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98203.513959] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98203.513968] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 5f 82 00 00 01 00
[98203.513983] end_request: I/O error, dev sde, sector 120257552
[98203.513990] Buffer I/O error on device sde, logical block 15032194
[98203.513994] lost page write due to I/O error on sde
[98383.526021] sd 6:0:0:0: timing out command, waited 180s
[98383.526047] sd 6:0:0:0: [sde] Unhandled sense code
[98383.526053] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98383.526062] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98383.526073] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98383.526088] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 af 1a 00 00 01 00
[98383.526106] end_request: I/O error, dev sde, sector 118323408
[98383.526116] Buffer I/O error on device sde, logical block 14790426
[98383.526121] lost page write due to I/O error on sde
[98383.726013] sd 6:0:0:0: timing out command, waited 180s
[98383.726039] sd 6:0:0:0: [sde] Unhandled sense code
[98383.726044] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98383.726054] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98383.726064] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98383.726079] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 b3 1b 00 00 01 00
[98383.726096] end_request: I/O error, dev sde, sector 118331608
[98383.726106] Buffer I/O error on device sde, logical block 14791451
[98383.726111] lost page write due to I/O error on sde
[98563.529121] sd 6:0:0:0: timing out command, waited 180s
[98563.529148] sd 6:0:0:0: [sde] Unhandled sense code
[98563.529154] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98563.529164] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98563.529174] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98563.529189] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 b7 1c 00 00 01 00
[98563.529207] end_request: I/O error, dev sde, sector 118339808
[98563.529217] Buffer I/O error on device sde, logical block 14792476
[98563.529222] lost page write due to I/O error on sde
[98743.537178] sd 6:0:0:0: timing out command, waited 180s
[98743.537204] sd 6:0:0:0: [sde] Unhandled sense code
[98743.537210] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98743.537220] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98743.537230] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98743.537245] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 63 83 00 00 01 00
[98743.537263] end_request: I/O error, dev sde, sector 120265752
[98743.537273] Buffer I/O error on device sde, logical block 15033219
[98743.537278] lost page write due to I/O error on sde
[98743.538293] sd 6:0:0:0: timing out command, waited 180s
[98743.538304] sd 6:0:0:0: [sde] Unhandled sense code
[98743.538309] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98743.538316] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98743.538324] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98743.538332] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 67 84 00 00 01 00
[98743.538348] end_request: I/O error, dev sde, sector 120273952
[98743.538354] Buffer I/O error on device sde, logical block 15034244
[98743.538359] lost page write due to I/O error on sde
[98923.543141] sd 6:0:0:0: timing out command, waited 180s
[98923.543168] sd 6:0:0:0: [sde] Unhandled sense code
[98923.543174] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98923.543183] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98923.543194] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98923.543209] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 6b 85 00 00 01 00
[98923.543226] end_request: I/O error, dev sde, sector 120282152
[98923.543237] Buffer I/O error on device sde, logical block 15035269
[98923.543241] lost page write due to I/O error on sde
[98923.544307] sd 6:0:0:0: timing out command, waited 180s
[98923.544318] sd 6:0:0:0: [sde] Unhandled sense code
[98923.544322] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98923.544329] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98923.544337] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98923.544346] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 6f 86 00 00 01 00
[98923.544361] end_request: I/O error, dev sde, sector 120290352
[98923.544367] Buffer I/O error on device sde, logical block 15036294
[98923.544372] lost page write due to I/O error on sde
[99103.556087] sd 6:0:0:0: timing out command, waited 180s
[99103.556113] sd 6:0:0:0: [sde] Unhandled sense code
[99103.556119] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99103.556129] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99103.556139] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99103.556154] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 bb 1d 00 00 01 00
[99103.556172] end_request: I/O error, dev sde, sector 118348008
[99103.556182] Buffer I/O error on device sde, logical block 14793501
[99103.556186] lost page write due to I/O error on sde
[99103.756618] sd 6:0:0:0: timing out command, waited 180s
[99103.756646] sd 6:0:0:0: [sde] Unhandled sense code
[99103.756651] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99103.756661] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99103.756671] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99103.756686] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 bf 1e 00 00 01 00
[99103.756704] end_request: I/O error, dev sde, sector 118356208
[99103.756714] Buffer I/O error on device sde, logical block 14794526
[99103.756719] lost page write due to I/O error on sde
[99283.569296] sd 6:0:0:0: timing out command, waited 180s
[99283.569324] sd 6:0:0:0: [sde] Unhandled sense code
[99283.569329] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99283.569338] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99283.569349] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99283.569364] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 c3 1f 00 00 01 00
[99283.569382] end_request: I/O error, dev sde, sector 118364408
[99283.569392] Buffer I/O error on device sde, logical block 14795551
[99283.569397] lost page write due to I/O error on sde
[99463.582385] sd 6:0:0:0: timing out command, waited 180s
[99463.582413] sd 6:0:0:0: [sde] Unhandled sense code
[99463.582419] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99463.582428] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99463.582439] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99463.582453] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 73 87 00 00 01 00
[99463.582471] end_request: I/O error, dev sde, sector 120298552
[99463.582481] Buffer I/O error on device sde, logical block 15037319
[99463.582486] lost page write due to I/O error on sde
[99463.583567] sd 6:0:0:0: timing out command, waited 180s
[99463.583578] sd 6:0:0:0: [sde] Unhandled sense code
[99463.583583] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99463.583590] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99463.583598] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99463.583607] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 77 88 00 00 01 00
[99463.583622] end_request: I/O error, dev sde, sector 120306752
[99463.583629] Buffer I/O error on device sde, logical block 15038344
[99463.583633] lost page write due to I/O error on sde
[99643.584559] sd 6:0:0:0: timing out command, waited 180s
[99643.584579] sd 6:0:0:0: [sde] Unhandled sense code
[99643.584585] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99643.584595] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99643.584605] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99643.584620] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 7b 89 00 00 01 00
[99643.584638] end_request: I/O error, dev sde, sector 120314952
[99643.584648] Buffer I/O error on device sde, logical block 15039369
[99643.584653] lost page write due to I/O error on sde
[99643.585667] sd 6:0:0:0: timing out command, waited 180s
[99643.585677] sd 6:0:0:0: [sde] Unhandled sense code
[99643.585682] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99643.585690] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99643.585699] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99643.585707] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 7f 8a 00 00 01 00
[99643.585723] end_request: I/O error, dev sde, sector 120323152
[99643.585729] Buffer I/O error on device sde, logical block 15040394
[99643.585733] lost page write due to I/O error on sde
[99823.597646] sd 6:0:0:0: timing out command, waited 180s
[99823.597675] sd 6:0:0:0: [sde] Unhandled sense code
[99823.597681] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99823.597690] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99823.597701] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99823.597716] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 c7 20 00 00 01 00
[99823.597734] end_request: I/O error, dev sde, sector 118372608
[99823.597745] Buffer I/O error on device sde, logical block 14796576
[99823.597749] lost page write due to I/O error on sde
[99823.797769] sd 6:0:0:0: timing out command, waited 180s
[99823.797797] sd 6:0:0:0: [sde] Unhandled sense code
[99823.797803] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99823.797813] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99823.797823] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99823.797838] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 cb 21 00 00 01 00
[99823.797857] end_request: I/O error, dev sde, sector 118380808
[99823.797867] Buffer I/O error on device sde, logical block 14797601
[99823.797872] lost page write due to I/O error on sde
[100003.610698] sd 6:0:0:0: timing out command, waited 180s
[100003.610726] sd 6:0:0:0: [sde] Unhandled sense code
[100003.610731] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100003.610741] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100003.610751] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100003.610766] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 cf 22 00 00 01 00
[100003.610784] end_request: I/O error, dev sde, sector 118389008
[100003.610795] Buffer I/O error on device sde, logical block 14798626
[100003.610800] lost page write due to I/O error on sde
[100183.613082] sd 6:0:0:0: timing out command, waited 180s
[100183.613109] sd 6:0:0:0: [sde] Unhandled sense code
[100183.613115] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100183.613125] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100183.613136] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100183.613151] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 83 cb 00 00 01 00
[100183.613168] end_request: I/O error, dev sde, sector 120331864
[100183.613179] Buffer I/O error on device sde, logical block 15041483
[100183.613184] lost page write due to I/O error on sde
[100183.614272] sd 6:0:0:0: timing out command, waited 180s
[100183.614282] sd 6:0:0:0: [sde] Unhandled sense code
[100183.614287] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100183.614293] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100183.614301] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100183.614310] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 85 8d 00 00 01 00
[100183.614325] end_request: I/O error, dev sde, sector 120335464
[100183.614332] Buffer I/O error on device sde, logical block 15041933
[100183.614337] lost page write due to I/O error on sde
[100363.618366] sd 6:0:0:0: timing out command, waited 180s
[100363.618392] sd 6:0:0:0: [sde] Unhandled sense code
[100363.618398] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100363.618408] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100363.618418] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100363.618433] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 89 8e 00 00 01 00
[100363.618451] end_request: I/O error, dev sde, sector 120343664
[100363.618461] Buffer I/O error on device sde, logical block 15042958
[100363.618466] lost page write due to I/O error on sde
[100363.624614] sd 6:0:0:0: timing out command, waited 180s
[100363.624634] sd 6:0:0:0: [sde] Unhandled sense code
[100363.624639] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100363.624647] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100363.624655] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100363.624666] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 8d 8f 00 00 01 00
[100363.624682] end_request: I/O error, dev sde, sector 120351864
[100363.624690] Buffer I/O error on device sde, logical block 15043983
[100363.624695] lost page write due to I/O error on sde
[100543.635821] sd 6:0:0:0: timing out command, waited 180s
[100543.635847] sd 6:0:0:0: [sde] Unhandled sense code
[100543.635853] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100543.635862] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100543.635873] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100543.635888] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 d3 23 00 00 01 00
[100543.635906] end_request: I/O error, dev sde, sector 118397208
[100543.635917] Buffer I/O error on device sde, logical block 14799651
[100543.635922] lost page write due to I/O error on sde
[100543.832934] sd 6:0:0:0: timing out command, waited 180s
[100543.832961] sd 6:0:0:0: [sde] Unhandled sense code
[100543.832967] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100543.832977] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100543.832988] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100543.833003] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 d7 24 00 00 01 00
[100543.833026] end_request: I/O error, dev sde, sector 118405408
[100543.833036] Buffer I/O error on device sde, logical block 14800676
[100543.833041] lost page write due to I/O error on sde
[100723.642156] sd 6:0:0:0: timing out command, waited 180s
[100723.642183] sd 6:0:0:0: [sde] Unhandled sense code
[100723.642189] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100723.642199] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100723.642210] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100723.642224] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 db 25 00 00 01 00
[100723.642243] end_request: I/O error, dev sde, sector 118413608
[100723.642253] Buffer I/O error on device sde, logical block 14801701
[100723.642258] lost page write due to I/O error on sde
[100903.648467] sd 6:0:0:0: timing out command, waited 180s
[100903.648493] sd 6:0:0:0: [sde] Unhandled sense code
[100903.648499] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100903.648509] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100903.648519] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100903.648534] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 91 90 00 00 01 00
[100903.648553] end_request: I/O error, dev sde, sector 120360064
[100903.648564] Buffer I/O error on device sde, logical block 15045008
[100903.648568] lost page write due to I/O error on sde
[100903.649581] sd 6:0:0:0: timing out command, waited 180s
[100903.649592] sd 6:0:0:0: [sde] Unhandled sense code
[100903.649596] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100903.649603] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100903.649611] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100903.649620] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 95 91 00 00 01 00
[100903.649635] end_request: I/O error, dev sde, sector 120368264
[100903.649641] Buffer I/O error on device sde, logical block 15046033
[100903.649646] lost page write due to I/O error on sde
[101083.654793] sd 6:0:0:0: timing out command, waited 180s
[101083.654812] sd 6:0:0:0: [sde] Unhandled sense code
[101083.654818] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101083.654828] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101083.654838] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101083.654853] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 99 92 00 00 01 00
[101083.654871] end_request: I/O error, dev sde, sector 120376464
[101083.654881] Buffer I/O error on device sde, logical block 15047058
[101083.654886] lost page write due to I/O error on sde
[101083.655900] sd 6:0:0:0: timing out command, waited 180s
[101083.655910] sd 6:0:0:0: [sde] Unhandled sense code
[101083.655915] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101083.655922] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101083.655930] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101083.655942] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 9d 93 00 00 01 00
[101083.655957] end_request: I/O error, dev sde, sector 120384664
[101083.655963] Buffer I/O error on device sde, logical block 15048083
[101083.655968] lost page write due to I/O error on sde
[101263.661361] sd 6:0:0:0: timing out command, waited 180s
[101263.661387] sd 6:0:0:0: [sde] Unhandled sense code
[101263.661392] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101263.661402] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101263.661413] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101263.661427] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 df 26 00 00 01 00
[101263.661445] end_request: I/O error, dev sde, sector 118421808
[101263.661455] Buffer I/O error on device sde, logical block 14802726
[101263.661460] lost page write due to I/O error on sde
[101263.872184] sd 6:0:0:0: timing out command, waited 180s
[101263.872215] sd 6:0:0:0: [sde] Unhandled sense code
[101263.872221] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101263.872230] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101263.872241] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101263.872257] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 e3 27 00 00 01 00
[101263.872276] end_request: I/O error, dev sde, sector 118430008
[101263.872286] Buffer I/O error on device sde, logical block 14803751
[101263.872291] lost page write due to I/O error on sde
[101443.667688] sd 6:0:0:0: timing out command, waited 180s
[101443.667713] sd 6:0:0:0: [sde] Unhandled sense code
[101443.667719] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101443.667728] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101443.667739] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101443.667753] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 e7 28 00 00 01 00
[101443.667772] end_request: I/O error, dev sde, sector 118438208
[101443.667782] Buffer I/O error on device sde, logical block 14804776
[101443.667787] lost page write due to I/O error on sde
[101623.673887] sd 6:0:0:0: timing out command, waited 180s
[101623.673913] sd 6:0:0:0: [sde] Unhandled sense code
[101623.673919] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101623.673929] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101623.673939] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101623.673954] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 a1 94 00 00 01 00
[101623.673972] end_request: I/O error, dev sde, sector 120392864
[101623.673982] Buffer I/O error on device sde, logical block 15049108
[101623.673987] lost page write due to I/O error on sde
[101623.675124] sd 6:0:0:0: timing out command, waited 180s
[101623.675134] sd 6:0:0:0: [sde] Unhandled sense code
[101623.675139] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101623.675146] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101623.675154] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101623.675163] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 a5 95 00 00 01 00
[101623.675178] end_request: I/O error, dev sde, sector 120401064
[101623.675185] Buffer I/O error on device sde, logical block 15050133
[101623.675190] lost page write due to I/O error on sde
[101803.681090] sd 6:0:0:0: timing out command, waited 180s
[101803.681117] sd 6:0:0:0: [sde] Unhandled sense code
[101803.681123] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101803.681132] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101803.681142] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101803.681157] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 a9 96 00 00 01 00
[101803.681175] end_request: I/O error, dev sde, sector 120409264
[101803.681185] Buffer I/O error on device sde, logical block 15051158
[101803.681190] lost page write due to I/O error on sde
[101803.682203] sd 6:0:0:0: timing out command, waited 180s
[101803.682213] sd 6:0:0:0: [sde] Unhandled sense code
[101803.682219] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101803.682226] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101803.682233] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101803.682242] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 ad 97 00 00 01 00
[101803.682258] end_request: I/O error, dev sde, sector 120417464
[101803.682264] Buffer I/O error on device sde, logical block 15052183
[101803.682269] lost page write due to I/O error on sde

```

---

### Post by westie457 on 2011-11-11
Hello, welcome to the Forum.

First step open Disk Utility and check the SMART status of the drive if possible. Sometimes with USB drives SMART reporting is not supported, sometimes it is. That should tell you more about the condition of the drive.

If no luck that way then download the manufacturers Diagnostic Software to check your drive thoroughly.

USB drives are probably more robust than normal drives for taking knocks, however if the drive is running when the knock happens they are fragile like all drives.

---

### Post by Sandbagger3 on 2011-11-11
No luck on the SMART status, and attempts to mount, remove, or 'check filesystem' all throw the same 'device is busy' error.

---

### Post by jtarin on 2011-11-11
[Try this.]("http://www.innovationsts.com/blog/?p=658")

---

### Post by JayKay3OOO on 2011-11-11
> **jtarin said:**
> [Try this.]("http://www.innovationsts.com/blog/?p=658")

Sounds like that should work.

Drive should be OK if it was not doing too much as then the head will be in park away from the spinning disks.

The drive normally gets damaged when dropped due the head smashing into the disk and damaging the surface (think record player) often causing the drive to get stuck at certain points and throwing I/O errors before needing hard re-set.

Drives can take a lot of shock abuse these days and to be honest the external hard drives mostly fail due to some component in the case dying like USB interface or something.

---

### Post by texaswriter on 2011-11-11
Dropping a hdd while running amounts to crashing the reading arm onto the plates that contain the data. The plates are essentially spinning extremely fast.  (almost 100% guaranteed). This is probably the worst type of "hard drive" crash there is... 

Forgive the lack of technical lingo, but pretty sure your only option is to send the drive to a professional recovery company, given that data contained on it is valuable. 

> **Sandbagger3 said:**
> My external hard drive was mounted and spinning when I knocked it of the shelf.  Now when I plug in the USB drive I see the proper name in the file manager, but attempting to mount it gives the error:

"Unable to mount [drivename]
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending"

Any idea how I can get the drive communicating again?


dmesg output is
```

[96763.441331] sd 6:0:0:0: timing out command, waited 180s
[96763.441358] sd 6:0:0:0: [sde] Unhandled sense code
[96763.441364] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[96763.441373] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[96763.441384] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[96763.441398] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e4 f5 66 00 00 01 00
[96763.441416] end_request: I/O error, dev sde, sector 120040240
[96763.441427] Buffer I/O error on device sde, logical block 15005030
[96763.441432] lost page write due to I/O error on sde
[96763.442438] sd 6:0:0:0: timing out command, waited 180s
[96763.442448] sd 6:0:0:0: [sde] Unhandled sense code
[96763.442453] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[96763.442460] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[96763.442468] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[96763.442477] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e4 f9 67 00 00 01 00
[96763.442492] end_request: I/O error, dev sde, sector 120048440
[96763.442498] Buffer I/O error on device sde, logical block 15006055
[96763.442503] lost page write due to I/O error on sde
[96943.454375] sd 6:0:0:0: timing out command, waited 180s
[96943.454402] sd 6:0:0:0: [sde] Unhandled sense code
[96943.454407] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[96943.454417] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[96943.454427] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[96943.454442] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 97 14 00 00 01 00
[96943.454459] end_request: I/O error, dev sde, sector 118274208
[96943.454470] Buffer I/O error on device sde, logical block 14784276
[96943.454475] lost page write due to I/O error on sde
[96943.654371] sd 6:0:0:0: timing out command, waited 180s
[96943.654398] sd 6:0:0:0: [sde] Unhandled sense code
[96943.654404] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[96943.654413] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[96943.654423] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[96943.654438] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 9b 15 00 00 01 00
[96943.654456] end_request: I/O error, dev sde, sector 118282408
[96943.654466] Buffer I/O error on device sde, logical block 14785301
[96943.654471] lost page write due to I/O error on sde
[97123.457048] sd 6:0:0:0: timing out command, waited 180s
[97123.457074] sd 6:0:0:0: [sde] Unhandled sense code
[97123.457080] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[97123.457090] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[97123.457100] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[97123.457115] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 9f 16 00 00 01 00
[97123.457133] end_request: I/O error, dev sde, sector 118290608
[97123.457144] Buffer I/O error on device sde, logical block 14786326
[97123.457149] lost page write due to I/O error on sde
[97303.461106] sd 6:0:0:0: timing out command, waited 180s
[97303.461125] sd 6:0:0:0: [sde] Unhandled sense code
[97303.461131] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[97303.461140] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[97303.461150] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[97303.461165] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e4 fd 68 00 00 01 00
[97303.461182] end_request: I/O error, dev sde, sector 120056640
[97303.461191] Buffer I/O error on device sde, logical block 15007080
[97303.461196] lost page write due to I/O error on sde
[97303.462597] sd 6:0:0:0: timing out command, waited 180s
[97303.462607] sd 6:0:0:0: [sde] Unhandled sense code
[97303.462612] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[97303.462619] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[97303.462627] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[97303.462636] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 47 7c 00 00 01 00
[97303.462650] end_request: I/O error, dev sde, sector 120208352
[97303.462657] Buffer I/O error on device sde, logical block 15026044
[97303.462662] lost page write due to I/O error on sde
[97483.471426] sd 6:0:0:0: timing out command, waited 180s
[97483.471453] sd 6:0:0:0: [sde] Unhandled sense code
[97483.471459] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[97483.471468] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[97483.471479] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[97483.471494] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 4b 7d 00 00 01 00
[97483.471512] end_request: I/O error, dev sde, sector 120216552
[97483.471522] Buffer I/O error on device sde, logical block 15027069
[97483.471526] lost page write due to I/O error on sde
[97483.473290] sd 6:0:0:0: timing out command, waited 180s
[97483.473302] sd 6:0:0:0: [sde] Unhandled sense code
[97483.473307] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[97483.473314] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[97483.473322] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[97483.473331] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 4f 7e 00 00 01 00
[97483.473346] end_request: I/O error, dev sde, sector 120224752
[97483.473353] Buffer I/O error on device sde, logical block 15028094
[97483.473358] lost page write due to I/O error on sde
[97663.484505] sd 6:0:0:0: timing out command, waited 180s
[97663.484533] sd 6:0:0:0: [sde] Unhandled sense code
[97663.484539] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[97663.484548] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[97663.484559] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[97663.484574] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 a3 17 00 00 01 00
[97663.484592] end_request: I/O error, dev sde, sector 118298808
[97663.484603] Buffer I/O error on device sde, logical block 14787351
[97663.484607] lost page write due to I/O error on sde
[97663.684491] sd 6:0:0:0: timing out command, waited 180s
[97663.684519] sd 6:0:0:0: [sde] Unhandled sense code
[97663.684525] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[97663.684534] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[97663.684544] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[97663.684559] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 a7 18 00 00 01 00
[97663.684577] end_request: I/O error, dev sde, sector 118307008
[97663.684588] Buffer I/O error on device sde, logical block 14788376
[97663.684593] lost page write due to I/O error on sde
[97843.497680] sd 6:0:0:0: timing out command, waited 180s
[97843.497706] sd 6:0:0:0: [sde] Unhandled sense code
[97843.497712] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[97843.497722] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[97843.497732] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[97843.497746] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 ab 19 00 00 01 00
[97843.497764] end_request: I/O error, dev sde, sector 118315208
[97843.497775] Buffer I/O error on device sde, logical block 14789401
[97843.497780] lost page write due to I/O error on sde
[98023.510620] sd 6:0:0:0: timing out command, waited 180s
[98023.510649] sd 6:0:0:0: [sde] Unhandled sense code
[98023.510655] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98023.510664] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98023.510675] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98023.510689] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 53 7f 00 00 01 00
[98023.510706] end_request: I/O error, dev sde, sector 120232952
[98023.510716] Buffer I/O error on device sde, logical block 15029119
[98023.510721] lost page write due to I/O error on sde
[98023.511732] sd 6:0:0:0: timing out command, waited 180s
[98023.511742] sd 6:0:0:0: [sde] Unhandled sense code
[98023.511747] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98023.511754] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98023.511762] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98023.511770] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 57 80 00 00 01 00
[98023.511786] end_request: I/O error, dev sde, sector 120241152
[98023.511792] Buffer I/O error on device sde, logical block 15030144
[98023.511797] lost page write due to I/O error on sde
[98203.512823] sd 6:0:0:0: timing out command, waited 180s
[98203.512850] sd 6:0:0:0: [sde] Unhandled sense code
[98203.512855] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98203.512864] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98203.512875] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98203.512890] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 5b 81 00 00 01 00
[98203.512917] end_request: I/O error, dev sde, sector 120249352
[98203.512927] Buffer I/O error on device sde, logical block 15031169
[98203.512932] lost page write due to I/O error on sde
[98203.513929] sd 6:0:0:0: timing out command, waited 180s
[98203.513939] sd 6:0:0:0: [sde] Unhandled sense code
[98203.513944] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98203.513951] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98203.513959] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98203.513968] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 5f 82 00 00 01 00
[98203.513983] end_request: I/O error, dev sde, sector 120257552
[98203.513990] Buffer I/O error on device sde, logical block 15032194
[98203.513994] lost page write due to I/O error on sde
[98383.526021] sd 6:0:0:0: timing out command, waited 180s
[98383.526047] sd 6:0:0:0: [sde] Unhandled sense code
[98383.526053] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98383.526062] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98383.526073] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98383.526088] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 af 1a 00 00 01 00
[98383.526106] end_request: I/O error, dev sde, sector 118323408
[98383.526116] Buffer I/O error on device sde, logical block 14790426
[98383.526121] lost page write due to I/O error on sde
[98383.726013] sd 6:0:0:0: timing out command, waited 180s
[98383.726039] sd 6:0:0:0: [sde] Unhandled sense code
[98383.726044] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98383.726054] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98383.726064] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98383.726079] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 b3 1b 00 00 01 00
[98383.726096] end_request: I/O error, dev sde, sector 118331608
[98383.726106] Buffer I/O error on device sde, logical block 14791451
[98383.726111] lost page write due to I/O error on sde
[98563.529121] sd 6:0:0:0: timing out command, waited 180s
[98563.529148] sd 6:0:0:0: [sde] Unhandled sense code
[98563.529154] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98563.529164] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98563.529174] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98563.529189] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 b7 1c 00 00 01 00
[98563.529207] end_request: I/O error, dev sde, sector 118339808
[98563.529217] Buffer I/O error on device sde, logical block 14792476
[98563.529222] lost page write due to I/O error on sde
[98743.537178] sd 6:0:0:0: timing out command, waited 180s
[98743.537204] sd 6:0:0:0: [sde] Unhandled sense code
[98743.537210] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98743.537220] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98743.537230] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98743.537245] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 63 83 00 00 01 00
[98743.537263] end_request: I/O error, dev sde, sector 120265752
[98743.537273] Buffer I/O error on device sde, logical block 15033219
[98743.537278] lost page write due to I/O error on sde
[98743.538293] sd 6:0:0:0: timing out command, waited 180s
[98743.538304] sd 6:0:0:0: [sde] Unhandled sense code
[98743.538309] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98743.538316] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98743.538324] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98743.538332] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 67 84 00 00 01 00
[98743.538348] end_request: I/O error, dev sde, sector 120273952
[98743.538354] Buffer I/O error on device sde, logical block 15034244
[98743.538359] lost page write due to I/O error on sde
[98923.543141] sd 6:0:0:0: timing out command, waited 180s
[98923.543168] sd 6:0:0:0: [sde] Unhandled sense code
[98923.543174] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98923.543183] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98923.543194] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98923.543209] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 6b 85 00 00 01 00
[98923.543226] end_request: I/O error, dev sde, sector 120282152
[98923.543237] Buffer I/O error on device sde, logical block 15035269
[98923.543241] lost page write due to I/O error on sde
[98923.544307] sd 6:0:0:0: timing out command, waited 180s
[98923.544318] sd 6:0:0:0: [sde] Unhandled sense code
[98923.544322] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[98923.544329] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[98923.544337] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[98923.544346] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 6f 86 00 00 01 00
[98923.544361] end_request: I/O error, dev sde, sector 120290352
[98923.544367] Buffer I/O error on device sde, logical block 15036294
[98923.544372] lost page write due to I/O error on sde
[99103.556087] sd 6:0:0:0: timing out command, waited 180s
[99103.556113] sd 6:0:0:0: [sde] Unhandled sense code
[99103.556119] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99103.556129] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99103.556139] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99103.556154] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 bb 1d 00 00 01 00
[99103.556172] end_request: I/O error, dev sde, sector 118348008
[99103.556182] Buffer I/O error on device sde, logical block 14793501
[99103.556186] lost page write due to I/O error on sde
[99103.756618] sd 6:0:0:0: timing out command, waited 180s
[99103.756646] sd 6:0:0:0: [sde] Unhandled sense code
[99103.756651] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99103.756661] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99103.756671] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99103.756686] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 bf 1e 00 00 01 00
[99103.756704] end_request: I/O error, dev sde, sector 118356208
[99103.756714] Buffer I/O error on device sde, logical block 14794526
[99103.756719] lost page write due to I/O error on sde
[99283.569296] sd 6:0:0:0: timing out command, waited 180s
[99283.569324] sd 6:0:0:0: [sde] Unhandled sense code
[99283.569329] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99283.569338] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99283.569349] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99283.569364] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 c3 1f 00 00 01 00
[99283.569382] end_request: I/O error, dev sde, sector 118364408
[99283.569392] Buffer I/O error on device sde, logical block 14795551
[99283.569397] lost page write due to I/O error on sde
[99463.582385] sd 6:0:0:0: timing out command, waited 180s
[99463.582413] sd 6:0:0:0: [sde] Unhandled sense code
[99463.582419] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99463.582428] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99463.582439] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99463.582453] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 73 87 00 00 01 00
[99463.582471] end_request: I/O error, dev sde, sector 120298552
[99463.582481] Buffer I/O error on device sde, logical block 15037319
[99463.582486] lost page write due to I/O error on sde
[99463.583567] sd 6:0:0:0: timing out command, waited 180s
[99463.583578] sd 6:0:0:0: [sde] Unhandled sense code
[99463.583583] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99463.583590] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99463.583598] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99463.583607] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 77 88 00 00 01 00
[99463.583622] end_request: I/O error, dev sde, sector 120306752
[99463.583629] Buffer I/O error on device sde, logical block 15038344
[99463.583633] lost page write due to I/O error on sde
[99643.584559] sd 6:0:0:0: timing out command, waited 180s
[99643.584579] sd 6:0:0:0: [sde] Unhandled sense code
[99643.584585] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99643.584595] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99643.584605] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99643.584620] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 7b 89 00 00 01 00
[99643.584638] end_request: I/O error, dev sde, sector 120314952
[99643.584648] Buffer I/O error on device sde, logical block 15039369
[99643.584653] lost page write due to I/O error on sde
[99643.585667] sd 6:0:0:0: timing out command, waited 180s
[99643.585677] sd 6:0:0:0: [sde] Unhandled sense code
[99643.585682] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99643.585690] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99643.585699] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99643.585707] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 7f 8a 00 00 01 00
[99643.585723] end_request: I/O error, dev sde, sector 120323152
[99643.585729] Buffer I/O error on device sde, logical block 15040394
[99643.585733] lost page write due to I/O error on sde
[99823.597646] sd 6:0:0:0: timing out command, waited 180s
[99823.597675] sd 6:0:0:0: [sde] Unhandled sense code
[99823.597681] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99823.597690] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99823.597701] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99823.597716] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 c7 20 00 00 01 00
[99823.597734] end_request: I/O error, dev sde, sector 118372608
[99823.597745] Buffer I/O error on device sde, logical block 14796576
[99823.597749] lost page write due to I/O error on sde
[99823.797769] sd 6:0:0:0: timing out command, waited 180s
[99823.797797] sd 6:0:0:0: [sde] Unhandled sense code
[99823.797803] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[99823.797813] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[99823.797823] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[99823.797838] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 cb 21 00 00 01 00
[99823.797857] end_request: I/O error, dev sde, sector 118380808
[99823.797867] Buffer I/O error on device sde, logical block 14797601
[99823.797872] lost page write due to I/O error on sde
[100003.610698] sd 6:0:0:0: timing out command, waited 180s
[100003.610726] sd 6:0:0:0: [sde] Unhandled sense code
[100003.610731] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100003.610741] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100003.610751] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100003.610766] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 cf 22 00 00 01 00
[100003.610784] end_request: I/O error, dev sde, sector 118389008
[100003.610795] Buffer I/O error on device sde, logical block 14798626
[100003.610800] lost page write due to I/O error on sde
[100183.613082] sd 6:0:0:0: timing out command, waited 180s
[100183.613109] sd 6:0:0:0: [sde] Unhandled sense code
[100183.613115] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100183.613125] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100183.613136] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100183.613151] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 83 cb 00 00 01 00
[100183.613168] end_request: I/O error, dev sde, sector 120331864
[100183.613179] Buffer I/O error on device sde, logical block 15041483
[100183.613184] lost page write due to I/O error on sde
[100183.614272] sd 6:0:0:0: timing out command, waited 180s
[100183.614282] sd 6:0:0:0: [sde] Unhandled sense code
[100183.614287] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100183.614293] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100183.614301] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100183.614310] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 85 8d 00 00 01 00
[100183.614325] end_request: I/O error, dev sde, sector 120335464
[100183.614332] Buffer I/O error on device sde, logical block 15041933
[100183.614337] lost page write due to I/O error on sde
[100363.618366] sd 6:0:0:0: timing out command, waited 180s
[100363.618392] sd 6:0:0:0: [sde] Unhandled sense code
[100363.618398] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100363.618408] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100363.618418] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100363.618433] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 89 8e 00 00 01 00
[100363.618451] end_request: I/O error, dev sde, sector 120343664
[100363.618461] Buffer I/O error on device sde, logical block 15042958
[100363.618466] lost page write due to I/O error on sde
[100363.624614] sd 6:0:0:0: timing out command, waited 180s
[100363.624634] sd 6:0:0:0: [sde] Unhandled sense code
[100363.624639] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100363.624647] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100363.624655] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100363.624666] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 8d 8f 00 00 01 00
[100363.624682] end_request: I/O error, dev sde, sector 120351864
[100363.624690] Buffer I/O error on device sde, logical block 15043983
[100363.624695] lost page write due to I/O error on sde
[100543.635821] sd 6:0:0:0: timing out command, waited 180s
[100543.635847] sd 6:0:0:0: [sde] Unhandled sense code
[100543.635853] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100543.635862] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100543.635873] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100543.635888] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 d3 23 00 00 01 00
[100543.635906] end_request: I/O error, dev sde, sector 118397208
[100543.635917] Buffer I/O error on device sde, logical block 14799651
[100543.635922] lost page write due to I/O error on sde
[100543.832934] sd 6:0:0:0: timing out command, waited 180s
[100543.832961] sd 6:0:0:0: [sde] Unhandled sense code
[100543.832967] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100543.832977] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100543.832988] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100543.833003] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 d7 24 00 00 01 00
[100543.833026] end_request: I/O error, dev sde, sector 118405408
[100543.833036] Buffer I/O error on device sde, logical block 14800676
[100543.833041] lost page write due to I/O error on sde
[100723.642156] sd 6:0:0:0: timing out command, waited 180s
[100723.642183] sd 6:0:0:0: [sde] Unhandled sense code
[100723.642189] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100723.642199] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100723.642210] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100723.642224] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 db 25 00 00 01 00
[100723.642243] end_request: I/O error, dev sde, sector 118413608
[100723.642253] Buffer I/O error on device sde, logical block 14801701
[100723.642258] lost page write due to I/O error on sde
[100903.648467] sd 6:0:0:0: timing out command, waited 180s
[100903.648493] sd 6:0:0:0: [sde] Unhandled sense code
[100903.648499] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100903.648509] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100903.648519] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100903.648534] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 91 90 00 00 01 00
[100903.648553] end_request: I/O error, dev sde, sector 120360064
[100903.648564] Buffer I/O error on device sde, logical block 15045008
[100903.648568] lost page write due to I/O error on sde
[100903.649581] sd 6:0:0:0: timing out command, waited 180s
[100903.649592] sd 6:0:0:0: [sde] Unhandled sense code
[100903.649596] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[100903.649603] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[100903.649611] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[100903.649620] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 95 91 00 00 01 00
[100903.649635] end_request: I/O error, dev sde, sector 120368264
[100903.649641] Buffer I/O error on device sde, logical block 15046033
[100903.649646] lost page write due to I/O error on sde
[101083.654793] sd 6:0:0:0: timing out command, waited 180s
[101083.654812] sd 6:0:0:0: [sde] Unhandled sense code
[101083.654818] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101083.654828] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101083.654838] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101083.654853] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 99 92 00 00 01 00
[101083.654871] end_request: I/O error, dev sde, sector 120376464
[101083.654881] Buffer I/O error on device sde, logical block 15047058
[101083.654886] lost page write due to I/O error on sde
[101083.655900] sd 6:0:0:0: timing out command, waited 180s
[101083.655910] sd 6:0:0:0: [sde] Unhandled sense code
[101083.655915] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101083.655922] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101083.655930] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101083.655942] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 9d 93 00 00 01 00
[101083.655957] end_request: I/O error, dev sde, sector 120384664
[101083.655963] Buffer I/O error on device sde, logical block 15048083
[101083.655968] lost page write due to I/O error on sde
[101263.661361] sd 6:0:0:0: timing out command, waited 180s
[101263.661387] sd 6:0:0:0: [sde] Unhandled sense code
[101263.661392] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101263.661402] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101263.661413] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101263.661427] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 df 26 00 00 01 00
[101263.661445] end_request: I/O error, dev sde, sector 118421808
[101263.661455] Buffer I/O error on device sde, logical block 14802726
[101263.661460] lost page write due to I/O error on sde
[101263.872184] sd 6:0:0:0: timing out command, waited 180s
[101263.872215] sd 6:0:0:0: [sde] Unhandled sense code
[101263.872221] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101263.872230] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101263.872241] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101263.872257] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 e3 27 00 00 01 00
[101263.872276] end_request: I/O error, dev sde, sector 118430008
[101263.872286] Buffer I/O error on device sde, logical block 14803751
[101263.872291] lost page write due to I/O error on sde
[101443.667688] sd 6:0:0:0: timing out command, waited 180s
[101443.667713] sd 6:0:0:0: [sde] Unhandled sense code
[101443.667719] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101443.667728] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101443.667739] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101443.667753] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e1 e7 28 00 00 01 00
[101443.667772] end_request: I/O error, dev sde, sector 118438208
[101443.667782] Buffer I/O error on device sde, logical block 14804776
[101443.667787] lost page write due to I/O error on sde
[101623.673887] sd 6:0:0:0: timing out command, waited 180s
[101623.673913] sd 6:0:0:0: [sde] Unhandled sense code
[101623.673919] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101623.673929] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101623.673939] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101623.673954] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 a1 94 00 00 01 00
[101623.673972] end_request: I/O error, dev sde, sector 120392864
[101623.673982] Buffer I/O error on device sde, logical block 15049108
[101623.673987] lost page write due to I/O error on sde
[101623.675124] sd 6:0:0:0: timing out command, waited 180s
[101623.675134] sd 6:0:0:0: [sde] Unhandled sense code
[101623.675139] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101623.675146] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101623.675154] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101623.675163] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 a5 95 00 00 01 00
[101623.675178] end_request: I/O error, dev sde, sector 120401064
[101623.675185] Buffer I/O error on device sde, logical block 15050133
[101623.675190] lost page write due to I/O error on sde
[101803.681090] sd 6:0:0:0: timing out command, waited 180s
[101803.681117] sd 6:0:0:0: [sde] Unhandled sense code
[101803.681123] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101803.681132] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101803.681142] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101803.681157] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 a9 96 00 00 01 00
[101803.681175] end_request: I/O error, dev sde, sector 120409264
[101803.681185] Buffer I/O error on device sde, logical block 15051158
[101803.681190] lost page write due to I/O error on sde
[101803.682203] sd 6:0:0:0: timing out command, waited 180s
[101803.682213] sd 6:0:0:0: [sde] Unhandled sense code
[101803.682219] sd 6:0:0:0: [sde]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[101803.682226] sd 6:0:0:0: [sde]  Sense Key : Hardware Error [current] 
[101803.682233] sd 6:0:0:0: [sde]  Add. Sense: Internal target failure
[101803.682242] sd 6:0:0:0: [sde] CDB: Write(10): 2a 00 00 e5 ad 97 00 00 01 00
[101803.682258] end_request: I/O error, dev sde, sector 120417464
[101803.682264] Buffer I/O error on device sde, logical block 15052183
[101803.682269] lost page write due to I/O error on sde

```

---

### Post by anewguy on 2011-11-11
To me, given the log messages, you have a hard failure on the drive - like in not usable any more.  If the data on in is extremely important so it is worth the high cost you could try sending it to an external data recovery specialist to see if they can recover anything.  These services are normally extremely high priced due to the service they are providing.

My advise?  If you can't mount the drive, due to the hardware errors showing in the log, on your own you won't get anywhere.  It looks like it had a very solid head crash.  Besides messing up the disk surface, head crashing can really ruin a head also (like I've seen them all the way off the arms). Trash the drive.  Hope you had a back up.

Dave ;)

---

### Post by cavh on 2011-11-12
I have read advice to the effect of you may get it working again if you stick it in a waterproof bag (like a sealable freezerbag) and stick in the freezer for a couple of hours. Never tried it myself, but may be worth Googling it.

If you do get it working again, get the data off it super quick, because it sure won't last long.

---

### Post by sadaruwan12 on 2011-11-12
The new HDD's are pretty hard but when you drop it while spinning then that's what we say as "sorry .com bro".

Wish your data bye.... bye, if you've the money and your data is extremely valuable then go to a professional data recovery guy or a company.

Thats why I use clod base system to backup or to sync my files they never breaks unless you delete them and pretty much safe.

I normally use three services ubuntu one, dropbox and spideroak very good one is casual other two is safe consider living in the cloud.

If you want more space the you certainly go with ubuntu one.

---

### Post by rng on 2011-11-12
Why don't you try ddrescue or dd_rescue or myrescue. They reads data directly from hard disks even if it is not mounting. These may work. No harm in trying before you give up.

ddrescue and myrescue are installable from synaptic package manager.

---

### Post by Paqman on 2011-11-12
A head crash is pretty much game over. You could try the [System Rescue CD]("http://www.sysresccd.org/Main_Page"), it's a handy thing to have, but all the tools on it are in the repos if you prefer to do it that way. If you can't get recovery tools to read the disk then it's toast. 

The big question: did you have backups? If you did, pat yourself on the back.

---

### Post by texaswriter on 2011-11-12
> **cavh said:**
> I have read advice to the effect of you may get it working again if you stick it in a waterproof bag (like a sealable freezerbag) and stick in the freezer for a couple of hours. Never tried it myself, but may be worth Googling it.

If you do get it working again, get the data off it super quick, because it sure won't last long.

I've heard that for dropping cellphones in water (I don't think it works for that either :confused::confused::o )

---

### Post by rosencrantz on 2011-11-12
I'm not quite sure whether you have already established a head crash from the error messages, but you could try removing the drive from its case and plug it into a computer (and try stuff like ddrescue afterwards).
Two remarks: 3.5'' and 2.5'' disks have the same SATA connectors, so you can plug a modern laptop drive into a desktop mainboard.
If you only have a laptop, you can always exchange its hard drive for the damaged one and boot a live CD/USB.

Good luck
rosencrantz

---

### Post by rng on 2011-11-13
You can boot laptop (or any available computer) with ubuntu livecd, then download and run ddrescue (or gddrescue or dd_rescue or myrescue or dd_rhelp). Many of these can be installed from synaptic package manager.

---

