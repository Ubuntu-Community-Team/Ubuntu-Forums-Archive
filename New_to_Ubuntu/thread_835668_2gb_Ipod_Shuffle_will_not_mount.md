---
title: "2gb Ipod Shuffle will not mount"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Stambo00 on 2008-06-20
I have been unable to mount my 2gb Ipod Shuffle in Hardy.

dmesg returns the following:

> [  117.527687] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  117.771046] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  118.014420] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  118.257802] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  118.390109] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  118.390120] end_request: I/O error, dev sdc, sector 0
[  118.390128] Buffer I/O error on device sdc, logical block 0
[  118.390152] Dev sdc: unable to read RDB block 0
[  118.501179] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  118.744560] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  118.987941] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  119.231327] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  119.474828] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  119.718077] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  119.850389] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  119.850399] end_request: I/O error, dev sdc, sector 0
[  119.850404] Buffer I/O error on device sdc, logical block 0
[  119.961452] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  120.204835] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  120.226318] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  120.226323] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  120.448213] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  120.691592] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  120.938973] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  121.178362] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  121.310655] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  121.310665] end_request: I/O error, dev sdc, sector 0
[  121.310673] Buffer I/O error on device sdc, logical block 0
[  121.421764] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  121.582651] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  121.582657] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  121.669105] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  121.908493] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  122.151873] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  122.395249] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  122.638628] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  122.770927] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  122.770938] end_request: I/O error, dev sdc, sector 24
[  122.770947] Buffer I/O error on device sdc, logical block 3
[  122.882018] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  123.125389] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  123.368770] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  123.612142] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  123.855531] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  124.098896] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  124.231198] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  124.231209] end_request: I/O error, dev sdc, sector 24
[  124.231218] Buffer I/O error on device sdc, logical block 3
[  124.342278] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  124.585657] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  124.829036] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  125.072413] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  125.315843] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  125.559168] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  125.691469] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  125.691480] end_request: I/O error, dev sdc, sector 0
[  125.802552] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  126.045932] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  126.293298] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  126.536682] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  126.720894] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  126.720901] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  126.780059] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  127.023436] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  127.159722] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  127.159734] end_request: I/O error, dev sdc, sector 0
[  127.159740] printk: 1 messages suppressed.
[  127.159744] Buffer I/O error on device sdc, logical block 0
[  127.159768]  unable to read partition table
[  127.160143] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[  127.160217] sd 2:0:0:0: Attached scsi generic sg3 type 0
[  127.298749] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  127.542122] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  127.785493] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  128.032863] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  128.276240] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  128.519632] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  128.655913] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  128.655926] end_request: I/O error, dev sdc, sector 0
[  128.766997] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  129.010367] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  129.253747] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  129.497123] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  129.740507] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  129.987882] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  130.120179] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  130.120190] end_request: I/O error, dev sdc, sector 0
[  130.247210] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  130.490591] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  130.733976] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  130.977353] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  131.220731] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  131.464105] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  131.596407] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  131.596416] end_request: I/O error, dev sdc, sector 0
[  131.640159] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  131.640167] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  131.707524] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  131.950861] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  132.194244] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  132.437619] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  132.681002] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  132.924379] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  133.056683] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  133.056692] end_request: I/O error, dev sdc, sector 0
[  133.056723] printk: 9 messages suppressed.
[  133.056727] Buffer I/O error on device sdc, logical block 0
[  135.358183] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  135.601577] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  135.844930] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  136.088312] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  136.335807] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  136.580067] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  136.712603] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  136.712616] end_request: I/O error, dev sdc, sector 0
[  136.712623] Buffer I/O error on device sdc, logical block 0
[  136.822431] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  137.065810] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  137.309192] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  137.552570] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  137.795949] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  138.039330] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  138.171624] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  138.171633] end_request: I/O error, dev sdc, sector 0
[  141.275939] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  141.275946] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  151.954912] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  151.954918] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  153.763044] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[  153.874923] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  154.118311] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  154.361681] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  154.605056] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  154.852454] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  155.099803] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  155.343177] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  155.590551] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  155.829935] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  156.073310] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  156.205622] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  156.205633] end_request: I/O error, dev sdc, sector 4
[  156.205675] FAT: bread failed, FSINFO block (sector = 1)
[  288.952782] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  288.952789] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  320.321064] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  320.321071] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  500.028463] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  500.028470] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  572.968700] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  572.968707] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  575.917321] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  575.917327] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  576.502468] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[  576.612307] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  576.855681] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  577.099054] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  577.342435] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  577.585813] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  577.833183] usb 5-7: reset high speed USB device using ehci_hcd and address 4
[  577.966477] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  577.966489] end_request: I/O error, dev sdc, sector 0
[  577.966555] FAT: unable to read boot sector
[  584.467874] usb 5-7: USB disconnect, address 4
[  593.828370] usb 5-8: new high speed USB device using ehci_hcd and address 5
[  593.961373] usb 5-8: configuration #1 chosen from 2 choices
[  593.961938] scsi3 : SCSI emulation for USB Mass Storage devices
[  593.962318] usb-storage: device found at 5
[  593.962323] usb-storage: waiting for device to settle before scanning
[  598.947482] usb-storage: device scan complete
[  598.948017] scsi 3:0:0:0: Direct-Access     Apple    iPod             2.70 PQ: 0 ANSI: 2
[  598.949961] sd 3:0:0:0: [sdc] 991232 2048-byte hardware sectors (2030 MB)
[  599.063036] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  599.191924] sd 3:0:0:0: [sdc] Write Protect is off
[  599.191933] sd 3:0:0:0: [sdc] Mode Sense: 64 00 00 08
[  599.191940] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  599.194031] sd 3:0:0:0: [sdc] 991232 2048-byte hardware sectors (2030 MB)
[  599.302419] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  599.435261] sd 3:0:0:0: [sdc] Write Protect is off
[  599.435270] sd 3:0:0:0: [sdc] Mode Sense: 64 00 00 08
[  599.435276] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  599.435287]  sdc:<6>usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  599.793145] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  600.036533] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  600.279913] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  600.523299] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  600.766684] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  600.900022] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  600.900037] end_request: I/O error, dev sdc, sector 0
[  600.900042] printk: 4 messages suppressed.
[  600.900046] Buffer I/O error on device sdc, logical block 0
[  601.010037] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  601.257415] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  601.504785] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  601.748160] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  601.991535] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  602.234914] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  602.367275] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  602.367289] end_request: I/O error, dev sdc, sector 0
[  602.367296] Buffer I/O error on device sdc, logical block 0
[  602.478287] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  602.722666] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  602.965045] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  603.208684] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  603.451812] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  603.695185] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  603.827549] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  603.827585] end_request: I/O error, dev sdc, sector 0
[  603.827593] Buffer I/O error on device sdc, logical block 0
[  603.939570] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  604.181947] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  604.425339] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  604.671244] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  604.912090] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  605.159457] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  605.291933] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  605.291945] end_request: I/O error, dev sdc, sector 0
[  605.291953] Buffer I/O error on device sdc, logical block 0
[  605.403829] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  605.650211] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  605.893586] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  606.136965] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  606.384330] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  606.627704] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  606.760064] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  606.760077] end_request: I/O error, dev sdc, sector 0
[  606.760086] Buffer I/O error on device sdc, logical block 0
[  606.760112] ldm_validate_partition_table(): Disk read failed.
[  606.871083] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  607.114472] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  607.359755] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  607.601242] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  607.844600] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  608.091976] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  608.224327] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  608.224339] end_request: I/O error, dev sdc, sector 0
[  608.224347] Buffer I/O error on device sdc, logical block 0
[  608.335341] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  608.578737] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  608.822113] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  609.065482] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  609.308860] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  609.552252] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  609.685599] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  609.685612] end_request: I/O error, dev sdc, sector 0
[  609.685618] Buffer I/O error on device sdc, logical block 0
[  609.795629] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  610.042997] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  610.286754] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  610.529752] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  610.773136] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  611.016515] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  611.152853] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  611.152868] end_request: I/O error, dev sdc, sector 0
[  611.152875] Buffer I/O error on device sdc, logical block 0
[  611.263877] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  611.507263] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  611.754637] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  611.998011] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  612.241374] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  612.484769] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  612.617115] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  612.617129] end_request: I/O error, dev sdc, sector 0
[  612.617136] Buffer I/O error on device sdc, logical block 0
[  612.617162] Dev sdc: unable to read RDB block 0
[  612.728145] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  612.971540] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  613.214904] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  613.458286] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  613.701656] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  613.945042] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  614.077383] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  614.077395] end_request: I/O error, dev sdc, sector 0
[  614.077403] Buffer I/O error on device sdc, logical block 0
[  614.188414] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  614.431802] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  614.675172] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  614.918556] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  615.165924] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  615.409297] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  615.541648] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  615.541660] end_request: I/O error, dev sdc, sector 0
[  615.541669] Buffer I/O error on device sdc, logical block 0
[  615.652676] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  615.896056] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  616.139446] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  616.386805] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  616.630194] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  616.873567] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  617.005910] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  617.005922] end_request: I/O error, dev sdc, sector 24
[  617.005930] Buffer I/O error on device sdc, logical block 3
[  617.117941] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  617.360320] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  617.603694] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  617.847076] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  618.092714] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  618.333833] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  618.470174] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  618.470188] end_request: I/O error, dev sdc, sector 24
[  618.470195] Buffer I/O error on device sdc, logical block 3
[  618.581203] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  618.824594] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  619.067970] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  619.311344] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  619.554724] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  619.798108] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  619.930447] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  619.930459] end_request: I/O error, dev sdc, sector 0
[  620.041492] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  620.288846] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  620.532235] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  620.779603] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  621.018999] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  621.266361] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  621.398698] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  621.398710] end_request: I/O error, dev sdc, sector 0
[  621.398717] printk: 1 messages suppressed.
[  621.398722] Buffer I/O error on device sdc, logical block 0
[  621.398747]  unable to read partition table
[  621.399122] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[  621.399196] sd 3:0:0:0: Attached scsi generic sg3 type 0
[  621.525699] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  621.770311] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  622.016437] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  622.259814] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  622.507207] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  622.750578] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  622.825230] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  622.825237] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  622.886909] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  622.886923] end_request: I/O error, dev sdc, sector 0
[  622.998975] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  623.241316] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  623.484704] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  623.728079] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  623.971464] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  624.214848] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  624.347177] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  624.347192] end_request: I/O error, dev sdc, sector 0
[  624.474162] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  624.717547] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  624.960926] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  625.204305] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  625.451682] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  625.695061] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  625.827405] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  625.827417] end_request: I/O error, dev sdc, sector 0
[  625.938437] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  626.182359] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  626.429189] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  626.672558] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  626.915936] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  627.163324] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  627.295659] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  627.295671] end_request: I/O error, dev sdc, sector 0
[  627.295678] printk: 9 messages suppressed.
[  627.295682] Buffer I/O error on device sdc, logical block 0
[  628.944469] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  628.944479] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  630.091839] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  630.335216] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  630.578592] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  630.821978] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  631.065351] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  631.312726] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  631.445115] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  631.445151] end_request: I/O error, dev sdc, sector 0
[  631.445159] Buffer I/O error on device sdc, logical block 0
[  631.556105] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  631.799515] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  632.042874] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  632.286302] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  632.529627] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  632.773000] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  632.905383] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  632.905395] end_request: I/O error, dev sdc, sector 0
[  639.908821] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  639.908828] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  641.250934] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[  641.363084] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  641.606500] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  641.849834] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  642.093222] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  642.336591] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  642.579981] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[  642.712323] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  642.712336] end_request: I/O error, dev sdc, sector 0
[  642.712411] FAT: unable to read boot sector
[  737.295472] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  737.295478] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  739.120533] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  739.120539] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  852.922125] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  852.922132] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[  853.524989] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  853.524995] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  903.500622] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  903.500631] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1080.111945] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1080.111954] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1207.845061] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1207.845069] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1236.980681] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1236.980690] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1242.044528] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[ 1242.287042] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[ 1242.535527] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[ 1242.779074] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[ 1243.021516] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[ 1243.265026] usb 5-8: reset high speed USB device using ehci_hcd and address 5
[ 1243.397443] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1243.397455] end_request: I/O error, dev sdc, sector 0
[ 1243.397567] FAT: unable to read boot sector
[ 1422.243592] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1422.243601] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1424.861690] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1424.861698] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1428.465736] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1428.465743] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1435.128079] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1435.128085] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1441.074540] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1441.074546] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 1496.571007] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[ 1496.571015] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[ 1497.243466] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 1497.243475] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.


I even rebuilt my kernel with EFI disabled but with no luck.

Trying to mount the Ipod results in the following:

> mount: /dev/sdc: can't read superblock


ANY HELP???

---

### Post by Stambo00 on 2008-06-25
bump? Really need some help here.

---

### Post by rockerphil on 2008-06-25
here's what i'd do. be sure to create a mount point for your iPod in your home folder (or wherever you want it to mount) so what i'd do is open up a terminal and type this

mkdir ~/iPod

to create the mount point. then with your iPod connected i'd run this in terminal:

sudo fdisk -l

to find the name of the iPod drive, on my machine it would typically show up as /dev/sdc seeing as i have 2 hard drives. /dev/sda and /dev/sdb respectively. so once you've got the name of the iPod id type this in terminal

sudo mount /dev/sdc ~/iPod

to mount the iPod to the file you created in your home folder. then to add files to the iPod i'd just do the drag & drop number with the file manager. hope this info helps

---

