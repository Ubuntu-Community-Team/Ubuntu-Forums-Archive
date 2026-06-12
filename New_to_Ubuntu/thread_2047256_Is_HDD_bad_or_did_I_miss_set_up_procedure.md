---
title: "Is HDD bad or did I miss set up procedure?"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by techcj on 2012-08-24
[FONT=Calibri][SIZE=3]:confused:We purchased intel SSD 320 series 600GB around 2 quarters ago, and recently we encountered the issue with using it:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]We are using it with Ubuntu 10.10 x64 and with ext4 filesystem on it:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Here is the log with it:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:16 crtl-l64-01 kernel: [5836148.349624] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:16 crtl-l64-01 kernel: [5836148.349629] ata6.00: failed command: CHECK POWER MODE[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:16 crtl-l64-01 kernel: [5836148.349637] ata6.00: cmd e5/00:00:00:00:00/00:00:00:00:00/00 tag 0[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:16 crtl-l64-01 kernel: [5836148.349638]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:16 crtl-l64-01 kernel: [5836148.349641] ata6.00: status: { DRDY }[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:16 crtl-l64-01 kernel: [5836148.349646] ata6: hard resetting link[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:16 crtl-l64-01 kernel: [5836148.699234] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:21 crtl-l64-01 kernel: [5836153.693436] ata6.00: qc timeout (cmd 0x27)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:21 crtl-l64-01 kernel: [5836153.693445] ata6.00: failed to read native max address (err_mask=0x4)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:21 crtl-l64-01 kernel: [5836153.693448] ata6.00: revalidation failed (errno=-5)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:21 crtl-l64-01 kernel: [5836153.693453] ata6: hard resetting link[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:21 crtl-l64-01 kernel: [5836154.043086] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:31 crtl-l64-01 kernel: [5836164.031583] ata6.00: qc timeout (cmd 0x27)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:31 crtl-l64-01 kernel: [5836164.031591] ata6.00: failed to read native max address (err_mask=0x4)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:31 crtl-l64-01 kernel: [5836164.031594] ata6.00: revalidation failed (errno=-5)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:31 crtl-l64-01 kernel: [5836164.031598] ata6: limiting SATA link speed to 1.5 Gbps[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:31 crtl-l64-01 kernel: [5836164.031602] ata6: hard resetting link[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:32 crtl-l64-01 kernel: [5836164.381195] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:42 crtl-l64-01 kernel: [5836174.369661] ata6.00: qc timeout (cmd 0x27)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:42 crtl-l64-01 kernel: [5836174.369669] ata6.00: failed to read native max address (err_mask=0x4)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:42 crtl-l64-01 kernel: [5836174.369673] ata6.00: revalidation failed (errno=-5)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:42 crtl-l64-01 kernel: [5836174.369675] ata6.00: disabled[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:42 crtl-l64-01 kernel: [5836174.369687] ata6: hard resetting link[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:42 crtl-l64-01 kernel: [5836174.719300] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 00:59:42 crtl-l64-01 kernel: [5836174.719315] ata6: EH complete[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 03:03:56 crtl-l64-01 kernel: [5843619.714879] sd 5:0:0:0: [sdc] Unhandled error code[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 03:03:56 crtl-l64-01 kernel: [5843619.714883] sd 5:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 03:03:56 crtl-l64-01 kernel: [5843619.714888] sd 5:0:0:0: [sdc] CDB: Write(10): 2a 00 22 c7 29 d7 00 00 48 00[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Aug 20 03:03:56 crtl-l64-01 kernel: [5843619.714898] end_request: I/O error, dev sdc, sector 583477719[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]After the error, we cannot find the device after rebooting. [/SIZE][/FONT]

---

### Post by pqwoerituytrueiwoq on 2012-08-24
ssds do best with ahci and use noatime and discard in /etc/fstab
if yuo can run a read only bechmark test and it complete it is probably good

---

