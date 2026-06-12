---
title: "[SOLVED] Anyone wanna guess what's wrong with my iPod?"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by nowhere@cox.net on 2008-05-07
I having trouble keeping my iPod connected. I'm using a thinkpad T61 with Gutsy 64 (Ubuntu) and Amarok installed. Connection is very flakey and fails totally quite a lot.  Here is dmesg:

```
[  267.226890] scsi 7:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[  267.237716] sd 7:0:0:0: [sdc] 39063023 512-byte hardware sectors (20000 MB)
[  267.239079] sd 7:0:0:0: [sdc] Write Protect is off
[  267.239087] sd 7:0:0:0: [sdc] Mode Sense: 64 00 00 08
[  267.239091] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  267.241549] sd 7:0:0:0: [sdc] 39063023 512-byte hardware sectors (20000 MB)
[  267.242574] sd 7:0:0:0: [sdc] Write Protect is off
[  267.242581] sd 7:0:0:0: [sdc] Mode Sense: 64 00 00 08
[  267.242585] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  267.242592]  sdc: sdc1 sdc2
[  267.263353] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[  267.263433] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  268.804857] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  268.804890] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  268.807264] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  268.807279] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  350.362241] sd 7:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  350.362255] sd 7:0:0:0: [sdc] Sense Key : Medium Error [current] 
[  350.362263] Info fld=0x0
[  350.362266] sd 7:0:0:0: [sdc] Add. Sense: Unrecovered read error
[  350.362276] end_request: I/O error, dev sdc, sector 99931
[  497.635876] sd 7:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[  497.635890] end_request: I/O error, dev sdc, sector 37414523
[  507.938917] sd 7:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[  507.938933] end_request: I/O error, dev sdc, sector 37414524
[  509.017801] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  509.017858] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  541.175110] sd 7:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  541.175116] sd 7:0:0:0: [sdc] Sense Key : Medium Error [current] 
[  541.175119] Info fld=0x0
[  541.175120] sd 7:0:0:0: [sdc] Add. Sense: Unrecovered read error
[  541.175124] end_request: I/O error, dev sdc, sector 12757467
[  615.859258] usb 7-1: reset high speed USB device using ehci_hcd and address 4
[  626.078038] usb 7-1: reset high speed USB device using ehci_hcd and address 4
[  636.794927] usb 7-1: reset high speed USB device using ehci_hcd and address 4
[  637.042572] usb 7-1: reset high speed USB device using ehci_hcd and address 4
[  647.261579] usb 7-1: reset high speed USB device using ehci_hcd and address 4
[  647.394966] sd 7:0:0:0: Device offlined - not ready after error recovery
[  647.394990] sd 7:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[  647.394998] end_request: I/O error, dev sdc, sector 12759995
[  647.395020] sd 7:0:0:0: rejecting I/O to offline device
[  647.395040] sd 7:0:0:0: rejecting I/O to offline device
[  647.395049] sd 7:0:0:0: rejecting I/O to offline device
[  647.395066] sd 7:0:0:0: rejecting I/O to offline device
[  647.395078] sd 7:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  647.395088] end_request: I/O error, dev sdc, sector 12760235
[  647.395118] sd 7:0:0:0: rejecting I/O to offline device
[  648.805306] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  648.805326] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  648.806692] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  648.806832] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[  693.530067] sd 7:0:0:0: rejecting I/O to offline device
[  745.031980] usb 7-1: USB disconnect, address 4
[ 4153.433521] usb 7-1: new high speed USB device using ehci_hcd and address 5
[ 4153.566917] usb 7-1: configuration #1 chosen from 1 choice
[ 4153.568620] scsi8 : SCSI emulation for USB Mass Storage devices
[ 4153.568792] usb-storage: device found at 5
[ 4153.568795] usb-storage: waiting for device to settle before scanning
[ 4154.941422] usb-storage: device scan complete
[ 4154.942116] scsi 8:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 4154.944712] sd 8:0:0:0: [sdc] 39063023 512-byte hardware sectors (20000 MB)
[ 4154.951428] sd 8:0:0:0: [sdc] Write Protect is off
[ 4154.951436] sd 8:0:0:0: [sdc] Mode Sense: 64 00 00 08
[ 4154.951441] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 4154.953784] sd 8:0:0:0: [sdc] 39063023 512-byte hardware sectors (20000 MB)
[ 4154.954907] sd 8:0:0:0: [sdc] Write Protect is off
[ 4154.954914] sd 8:0:0:0: [sdc] Mode Sense: 64 00 00 08
[ 4154.954918] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 4154.954925]  sdc:<6>sd 8:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 4160.264561] sd 8:0:0:0: [sdc] Sense Key : Medium Error [current] 
[ 4160.264573] Info fld=0x0
[ 4160.264576] sd 8:0:0:0: [sdc] Add. Sense: Unrecovered read error
[ 4160.264586] end_request: I/O error, dev sdc, sector 0
[ 4160.264593] Buffer I/O error on device sdc, logical block 0
[ 4160.264603] Buffer I/O error on device sdc, logical block 1
[ 4160.264608] Buffer I/O error on device sdc, logical block 2
[ 4160.264614] Buffer I/O error on device sdc, logical block 3
[ 4160.264620] Buffer I/O error on device sdc, logical block 4
[ 4160.264626] Buffer I/O error on device sdc, logical block 5
[ 4160.264632] Buffer I/O error on device sdc, logical block 6
[ 4160.264637] Buffer I/O error on device sdc, logical block 7
[ 4168.060174] ldm_validate_partition_table(): Disk read failed.
[ 4168.060194] Dev sdc: unable to read RDB block 0
[ 4168.061322]  unable to read partition table
[ 4168.061862] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 4168.061951] sd 8:0:0:0: Attached scsi generic sg3 type 0
[ 4181.163613] usb 7-1: USB disconnect, address 5
[ 4212.219189] usb 7-1: new high speed USB device using ehci_hcd and address 6
[ 4212.352872] usb 7-1: configuration #1 chosen from 1 choice
[ 4212.353354] scsi9 : SCSI emulation for USB Mass Storage devices
[ 4212.353872] usb-storage: device found at 6
[ 4212.353877] usb-storage: waiting for device to settle before scanning
[ 4212.792634] usb-storage: device scan complete
[ 4212.793156] scsi 9:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 4212.797111] sd 9:0:0:0: [sdc] 39063023 512-byte hardware sectors (20000 MB)
[ 4212.797976] sd 9:0:0:0: [sdc] Write Protect is off
[ 4212.797982] sd 9:0:0:0: [sdc] Mode Sense: 64 00 00 08
[ 4212.797986] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[ 4212.802213] sd 9:0:0:0: [sdc] 39063023 512-byte hardware sectors (20000 MB)
[ 4212.803096] sd 9:0:0:0: [sdc] Write Protect is off
[ 4212.803102] sd 9:0:0:0: [sdc] Mode Sense: 64 00 00 08
[ 4212.803107] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[ 4212.803114]  sdc: sdc1 sdc2
[ 4212.814904] sd 9:0:0:0: [sdc] Attached SCSI removable disk
[ 4212.814982] sd 9:0:0:0: Attached scsi generic sg3 type 0
[ 4214.506418] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4214.506442] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4214.509566] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4214.509580] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4214.986928] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4214.986975] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4214.986996] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4214.987367] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4224.426627] sd 9:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[ 4224.426641] end_request: I/O error, dev sdc, sector 99771
[ 4229.253487] sd 9:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[ 4229.253501] end_request: I/O error, dev sdc, sector 99772
[ 4329.476953] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4329.476997] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4329.480090] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4329.480489] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4332.251429] usb 7-1: USB disconnect, address 6
[ 4334.545628] usb 7-1: new high speed USB device using ehci_hcd and address 7
[ 4334.679017] usb 7-1: configuration #1 chosen from 1 choice
[ 4334.679495] scsi10 : SCSI emulation for USB Mass Storage devices
[ 4334.680017] usb-storage: device found at 7
[ 4334.680022] usb-storage: waiting for device to settle before scanning
[ 4335.966259] usb-storage: device scan complete
[ 4335.967320] scsi 10:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 4335.971134] sd 10:0:0:0: [sdc] 39063023 512-byte hardware sectors (20000 MB)
[ 4335.972504] sd 10:0:0:0: [sdc] Write Protect is off
[ 4335.972511] sd 10:0:0:0: [sdc] Mode Sense: 64 00 00 08
[ 4335.972516] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[ 4335.974994] sd 10:0:0:0: [sdc] 39063023 512-byte hardware sectors (20000 MB)
[ 4335.976117] sd 10:0:0:0: [sdc] Write Protect is off
[ 4335.976124] sd 10:0:0:0: [sdc] Mode Sense: 64 00 00 08
[ 4335.976129] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[ 4335.976136]  sdc: sdc1 sdc2
[ 4335.984670] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[ 4335.984748] sd 10:0:0:0: Attached scsi generic sg3 type 0
[ 4337.598484] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4337.598506] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4337.602086] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4337.602103] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4338.021521] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4338.021563] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4338.021583] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4338.021966] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4477.058341] usb 7-1: reset high speed USB device using ehci_hcd and address 7
[ 4487.291338] usb 7-1: reset high speed USB device using ehci_hcd and address 7
[ 4503.609624] usb 7-1: reset high speed USB device using ehci_hcd and address 7
[ 4503.857298] usb 7-1: reset high speed USB device using ehci_hcd and address 7
[ 4514.087596] usb 7-1: reset high speed USB device using ehci_hcd and address 7
[ 4514.220769] sd 10:0:0:0: Device offlined - not ready after error recovery
[ 4514.220795] sd 10:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 4514.220803] end_request: I/O error, dev sdc, sector 12730267
[ 4514.220837] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.221067] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.221079] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.221099] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.221106] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.221117] sd 10:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 4514.221124] end_request: I/O error, dev sdc, sector 12730507
[ 4514.221140] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.221176] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.221187] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.221194] Buffer I/O error on device sdc2, logical block 1
[ 4514.221199] lost page write due to I/O error on sdc2
[ 4514.221208] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.221214] Buffer I/O error on device sdc2, logical block 9142
[ 4514.221218] lost page write due to I/O error on sdc2
[ 4514.221228] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.221233] Buffer I/O error on device sdc2, logical block 18657
[ 4514.221237] lost page write due to I/O error on sdc2
[ 4514.221245] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.221249] Buffer I/O error on device sdc2, logical block 19480
[ 4514.221253] lost page write due to I/O error on sdc2
[ 4514.221389] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.221398] Buffer I/O error on device sdc2, logical block 9142
[ 4514.221404] lost page write due to I/O error on sdc2
[ 4514.221412] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.221417] Buffer I/O error on device sdc2, logical block 18657
[ 4514.221421] lost page write due to I/O error on sdc2
[ 4514.221428] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.221433] Buffer I/O error on device sdc2, logical block 19480
[ 4514.221437] lost page write due to I/O error on sdc2
[ 4514.221475] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.227945] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.227958] Buffer I/O error on device sdc2, logical block 1
[ 4514.227963] lost page write due to I/O error on sdc2
[ 4514.231358] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.231409] FAT: Directory bread(block 19480) failed
[ 4514.231612] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.231621] FAT: Directory bread(block 19480) failed
[ 4514.231763] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.231771] FAT: Directory bread(block 19480) failed
[ 4514.231856] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.231864] FAT: Directory bread(block 19480) failed
[ 4514.231986] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.231993] FAT: Directory bread(block 19480) failed
[ 4514.232075] sd 10:0:0:0: rejecting I/O to offline device
[ 4514.232082] FAT: Directory bread(block 19480) failed
[ 4515.236684] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4515.236704] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4515.237923] VMBlock warning: DentryOpRevalidate: invalid args from kernel
[ 4515.237949] VMBlock warning: DentryOpRevalidate: invalid args from kernel

```

Anyone have any ideas?

Thanks!

---

### Post by superprash2003 on 2008-05-07
well im not sure about the error.. but you could try using floola with your ipod.. [www.floola.com](www.floola.com)

---

### Post by smellydog on 2008-05-17
What kind of Ipod do you have and what firmware version is on it?  I have a classic that i had working with Amarok really well.  Safe disconnect and everything... until i upgraded the firmware on the ipod, now Amarok doesn't work for me anymore and i am lucky to get it to disconnect safely.  Needless to say, i am a bit upset.

---

### Post by nowhere@cox.net on 2008-05-17
Yeah, it's a fourth gen and it was working until about the time I let stupid i-tunes upgrade the firmware... Hmmm, guess I need to give Rockbox a try...

Eric

---

### Post by jimmy the saint on 2008-05-17
yeah, Rockbox is a good idea.  I put it on my ipod and it eliminated every problem I ever had with my ipod and ubuntu.  rockbox rocks.  Itunes.... well... doesnt.

---

### Post by bodhi.zazen on 2008-05-17
Apple has purposely configured new ipods such that they do not work with Linux. Do a google search and you will find articles and work-arounds.

My solution is to buy an alternate product. There are pleanty of alternate MP3 players which work with Linux and are as low as half the cost of an ipod.

**[SIZE=1][Slashdot | [B]Apple** Cuts Off **Linux iPod** Users]("http://apple.slashdot.org/article.pl?sid=07/09/14/1831236")[/SIZE][/B]

---

### Post by shifty_powers on 2008-05-17
+1 for rockbox.

it truly is great, though it ain't perfect.

well worth checking out. got it on my 30gb ipod video ;)

---

### Post by nowhere@cox.net on 2008-05-20
Well I installed Rockbox. Pretty nice. Needs some pretty'ing up tho. There are some hardware problems with this ipod tho. I believe the source of the problem is the sync connector in base of the unit. 

I put it under the stereo microscope at work and I could see that pin one was bent up. Trying to bend it down broke it off but the docs I found on the fourth gen says that pin 1 and 2 are tied together on the motherboard anyway. Both are grounds.  Anyway, the bent pin was not allowing the male connector to seat fully and it would lose connection intermittently and eventually corrupt the filesystem. With the pin broken, it seats much better but moving the ipod around while connect will cause it to disconnect sometimes.

The biggest problem Im pretty sure was that I had not gotten a completely good "restore" process done as it would disconnect during the process and leave the filesystem "un-repaired." I finally got itunes to finish the restore process completely and successfully and things seem to work better.

As for the Rockbox install, it was a disaster while the filesystem was not 100%. But once I got the successful restore in itunes, Rockbox installed easily and flawlessly. 

One thing I do notice is that when you connect to a PC to sync while running rockbox, the ipod reboots into the apple OS to perform the sync so I don't think there is any sync CONNECTION benefit to having rockbox on the ipod.

Thanks for replies. I hope this saga has proved entertaining to some of you. If I figure anything else out. I will post here in case anyone else is having troubles.

---

