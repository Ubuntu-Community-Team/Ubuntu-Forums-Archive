---
title: "external harddrive detected occasionally"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by zhanglini on 2012-07-06
Hi my external harddrive (Simpletech 250GB) had been working well until recently.  First I accidentally formatted it, then I tried to recover data using testdisk etc, to no avail.  So I decided to reformatted it using Gparted, it gave me an error (couldn't tell what error it was b/c I could not enlarge the error window) but the drive was reformatted anyway --- i was able to copy 80gb of stuff to the drive.
Unfortunately, the drive is only detected 5% of the time when I turn it on, most of the time it remain undetected.
Here is what I pulled from syslog that show you the message when it is and is not detected (sorry a bit long):
```
Jul  6 17:55:37 CC kernel: [  321.220098] usb 2-6: new high-speed USB device number 9 using ehci_hcd
Jul  6 17:55:37 CC kernel: [  321.441211] scsi5 : usb-storage 2-6:1.0
Jul  6 17:55:37 CC mtp-probe: checking bus 2, device 9: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-6"
Jul  6 17:55:37 CC mtp-probe: bus: 2, device: 9 was not an MTP device
Jul  6 17:55:38 CC kernel: [  322.476116] scsi 5:0:0:0: Direct-Access     ST325082 0A               3.AA PQ: 0 ANSI: 0
Jul  6 17:55:38 CC kernel: [  322.477554] sd 5:0:0:0: Attached scsi generic sg2 type 0
Jul  6 17:55:38 CC kernel: [  322.478859] sd 5:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Jul  6 17:55:38 CC kernel: [  322.483436] sd 5:0:0:0: [sdb] Write Protect is off
Jul  6 17:55:38 CC kernel: [  322.483449] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
Jul  6 17:55:38 CC kernel: [  322.484734] sd 5:0:0:0: [sdb] No Caching mode page present
Jul  6 17:55:38 CC kernel: [  322.484748] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Jul  6 17:55:38 CC kernel: [  322.488575] sd 5:0:0:0: [sdb] No Caching mode page present
Jul  6 17:55:38 CC kernel: [  322.488585] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Jul  6 17:55:38 CC kernel: [  322.503837]  sdb: sdb1
Jul  6 17:55:38 CC kernel: [  322.507600] sd 5:0:0:0: [sdb] No Caching mode page present
Jul  6 17:55:38 CC kernel: [  322.507614] sd 5:0:0:0: [sdb] Assuming drive cache: write through
Jul  6 17:55:38 CC kernel: [  322.507624] sd 5:0:0:0: [sdb] Attached SCSI disk
Jul  6 17:55:38 CC ata_id[2054]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
Jul  6 17:55:39 CC kernel: [  323.274129] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
Jul  6 17:56:04 CC ata_id[2116]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
Jul  6 17:56:06 CC ata_id[2152]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
Jul  6 17:56:06 CC ata_id[2159]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
Jul  6 17:56:08 CC ata_id[2166]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
Jul  6 17:56:31 CC kernel: [  375.736077] usb 2-6: reset high-speed USB device number 9 using ehci_hcd
Jul  6 17:56:31 CC kernel: [  375.912074] usb 2-6: device descriptor read/64, error -71
Jul  6 17:56:32 CC kernel: [  376.176067] usb 2-6: device descriptor read/64, error -71
Jul  6 17:56:32 CC kernel: [  376.392086] usb 2-6: reset high-speed USB device number 9 using ehci_hcd
Jul  6 17:56:32 CC kernel: [  376.552052] usb 2-6: device descriptor read/64, error -71
Jul  6 17:56:32 CC kernel: [  376.816073] usb 2-6: device descriptor read/64, error -71
Jul  6 17:56:33 CC kernel: [  377.032077] usb 2-6: reset high-speed USB device number 9 using ehci_hcd
Jul  6 17:56:33 CC kernel: [  377.472056] usb 2-6: device not accepting address 9, error -71
Jul  6 17:56:33 CC kernel: [  377.584054] usb 2-6: reset high-speed USB device number 9 using ehci_hcd
Jul  6 17:56:34 CC kernel: [  378.016088] usb 2-6: device not accepting address 9, error -71
Jul  6 17:56:34 CC kernel: [  378.016155] usb 2-6: USB disconnect, device number 9
Jul  6 17:56:34 CC kernel: [  378.020697] scsi 5:0:0:0: [sdb] killing request
Jul  6 17:56:34 CC kernel: [  378.020739] scsi 5:0:0:0: [sdb] Unhandled error code
Jul  6 17:56:34 CC kernel: [  378.020750] scsi 5:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jul  6 17:56:34 CC kernel: [  378.020763] scsi 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 08 00
Jul  6 17:56:34 CC kernel: [  378.020902] end_request: I/O error, dev sdb, sector 63
Jul  6 17:56:34 CC kernel: [  378.020914] quiet_error: 36 callbacks suppressed
Jul  6 17:56:34 CC kernel: [  378.020922] Buffer I/O error on device sdb1, logical block 0
Jul  6 17:56:34 CC kernel: [  378.020933] Buffer I/O error on device sdb1, logical block 1
Jul  6 17:56:34 CC kernel: [  378.020942] Buffer I/O error on device sdb1, logical block 2
Jul  6 17:56:34 CC kernel: [  378.020951] Buffer I/O error on device sdb1, logical block 3
Jul  6 17:56:34 CC kernel: [  378.020959] Buffer I/O error on device sdb1, logical block 4
Jul  6 17:56:34 CC kernel: [  378.020967] Buffer I/O error on device sdb1, logical block 5
Jul  6 17:56:34 CC kernel: [  378.020975] Buffer I/O error on device sdb1, logical block 6
Jul  6 17:56:34 CC kernel: [  378.020983] Buffer I/O error on device sdb1, logical block 7
Jul  6 17:56:34 CC kernel: [  378.023595] Buffer I/O error on device sdb1, logical block 0
Jul  6 17:56:34 CC kernel: [  378.023614] Buffer I/O error on device sdb1, logical block 1
Jul  6 17:56:34 CC kernel: [  378.148104] usb 2-6: new high-speed USB device number 10 using ehci_hcd
Jul  6 17:56:34 CC kernel: [  378.308161] usb 2-6: device descriptor read/64, error -71
Jul  6 17:56:34 CC kernel: [  378.572060] usb 2-6: device descriptor read/64, error -71
Jul  6 17:56:34 CC kernel: [  378.788065] usb 2-6: new high-speed USB device number 11 using ehci_hcd
Jul  6 17:56:34 CC kernel: [  378.948051] usb 2-6: device descriptor read/64, error -71
Jul  6 17:56:35 CC kernel: [  379.212080] usb 2-6: device descriptor read/64, error -71
Jul  6 17:56:35 CC kernel: [  379.428104] usb 2-6: new high-speed USB device number 12 using ehci_hcd
Jul  6 17:56:35 CC kernel: [  379.868082] usb 2-6: device not accepting address 12, error -71
Jul  6 17:56:35 CC kernel: [  379.980107] usb 2-6: new high-speed USB device number 13 using ehci_hcd
Jul  6 17:56:36 CC kernel: [  380.416097] usb 2-6: device not accepting address 13, error -71
Jul  6 17:56:36 CC kernel: [  380.416142] hub 2-0:1.0: unable to enumerate USB device on port 6
Jul  6 17:56:36 CC kernel: [  380.684066] usb 7-2: new full-speed USB device number 6 using uhci_hcd
Jul  6 17:56:36 CC kernel: [  380.864080] usb 7-2: device descriptor read/64, error -71
Jul  6 17:56:37 CC kernel: [  381.092062] usb 7-2: device descriptor read/64, error -71
Jul  6 17:56:37 CC kernel: [  381.308052] usb 7-2: new full-speed USB device number 7 using uhci_hcd
Jul  6 17:56:37 CC kernel: [  381.432051] usb 7-2: device descriptor read/64, error -71
Jul  6 17:56:37 CC kernel: [  381.716075] usb 7-2: device descriptor read/64, error -71
Jul  6 17:56:37 CC kernel: [  381.932065] usb 7-2: new full-speed USB device number 8 using uhci_hcd
Jul  6 17:56:38 CC kernel: [  382.344054] usb 7-2: device not accepting address 8, error -71
Jul  6 17:56:38 CC kernel: [  382.456171] usb 7-2: new full-speed USB device number 9 using uhci_hcd
Jul  6 17:56:38 CC kernel: [  382.868049] usb 7-2: device not accepting address 9, error -71
Jul  6 17:56:38 CC kernel: [  382.868075] hub 7-0:1.0: unable to enumerate USB device on port 2
Jul  6 17:57:57 CC AptDaemon: INFO: Quitting due to inactivity
Jul  6 17:57:57 CC AptDaemon: INFO: Quitting was requested
Jul  6 17:58:06 CC kernel: [  470.360049] usb 2-6: new high-speed USB device number 14 using ehci_hcd
Jul  6 17:58:06 CC kernel: [  470.581032] scsi6 : usb-storage 2-6:1.0
Jul  6 17:58:06 CC mtp-probe: checking bus 2, device 14: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-6"
Jul  6 17:58:06 CC mtp-probe: bus: 2, device: 14 was not an MTP device
Jul  6 17:58:07 CC kernel: [  471.720059] usb 2-6: reset high-speed USB device number 14 using ehci_hcd
Jul  6 17:58:07 CC kernel: [  471.900045] usb 2-6: device descriptor read/64, error -71
Jul  6 17:58:08 CC kernel: [  472.164058] usb 2-6: device descriptor read/64, error -71
Jul  6 17:58:08 CC kernel: [  472.380100] usb 2-6: reset high-speed USB device number 14 using ehci_hcd
Jul  6 17:58:08 CC kernel: [  472.540057] usb 2-6: device descriptor read/64, error -71
Jul  6 17:58:08 CC kernel: [  472.804053] usb 2-6: device descriptor read/64, error -71
Jul  6 17:58:09 CC kernel: [  473.020067] usb 2-6: reset high-speed USB device number 14 using ehci_hcd
Jul  6 17:58:09 CC kernel: [  473.460044] usb 2-6: device not accepting address 14, error -71
Jul  6 17:58:09 CC kernel: [  473.572052] usb 2-6: reset high-speed USB device number 14 using ehci_hcd
Jul  6 17:58:09 CC kernel: [  474.012057] usb 2-6: device not accepting address 14, error -71
Jul  6 17:58:09 CC kernel: [  474.012118] usb 2-6: USB disconnect, device number 14
Jul  6 17:58:10 CC kernel: [  474.132080] usb 2-6: new high-speed USB device number 15 using ehci_hcd
Jul  6 17:58:10 CC kernel: [  474.292051] usb 2-6: device descriptor read/64, error -71
Jul  6 17:58:10 CC kernel: [  474.556058] usb 2-6: device descriptor read/64, error -71
Jul  6 17:58:10 CC kernel: [  474.772039] usb 2-6: new high-speed USB device number 16 using ehci_hcd
Jul  6 17:58:10 CC kernel: [  474.932048] usb 2-6: device descriptor read/64, error -71
Jul  6 17:58:11 CC kernel: [  475.196045] usb 2-6: device descriptor read/64, error -71
Jul  6 17:58:11 CC kernel: [  475.412059] usb 2-6: new high-speed USB device number 17 using ehci_hcd
Jul  6 17:58:11 CC kernel: [  475.852052] usb 2-6: device not accepting address 17, error -71
Jul  6 17:58:11 CC kernel: [  475.964081] usb 2-6: new high-speed USB device number 18 using ehci_hcd
Jul  6 17:58:12 CC kernel: [  476.404049] usb 2-6: device not accepting address 18, error -71
Jul  6 17:58:12 CC kernel: [  476.404087] hub 2-0:1.0: unable to enumerate USB device on port 6
Jul  6 17:58:12 CC kernel: [  476.672054] usb 7-2: new full-speed USB device number 10 using uhci_hcd
Jul  6 17:58:12 CC kernel: [  476.796050] usb 7-2: device descriptor read/64, error -71
Jul  6 17:58:13 CC kernel: [  477.024067] usb 7-2: device descriptor read/64, error -71
Jul  6 17:58:13 CC kernel: [  477.240061] usb 7-2: new full-speed USB device number 11 using uhci_hcd
Jul  6 17:58:13 CC kernel: [  477.364047] usb 7-2: device descriptor read/64, error -71
Jul  6 17:58:13 CC kernel: [  477.588054] usb 7-2: device descriptor read/64, error -71
Jul  6 17:58:13 CC kernel: [  477.804062] usb 7-2: new full-speed USB device number 12 using uhci_hcd
Jul  6 17:58:14 CC kernel: [  478.220041] usb 7-2: device not accepting address 12, error -71
Jul  6 17:58:14 CC kernel: [  478.388054] usb 7-2: new full-speed USB device number 13 using uhci_hcd
Jul  6 17:58:14 CC kernel: [  478.804043] usb 7-2: device not accepting address 13, error -71
Jul  6 17:58:14 CC kernel: [  478.804070] hub 7-0:1.0: unable to enumerate USB device on port 2
Jul  6 17:58:28 CC kernel: [  492.264056] usb 2-6: new high-speed USB device number 19 using ehci_hcd
Jul  6 17:58:28 CC kernel: [  492.484202] scsi7 : usb-storage 2-6:1.0
Jul  6 17:58:28 CC mtp-probe: checking bus 2, device 19: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-6"
Jul  6 17:58:28 CC mtp-probe: bus: 2, device: 19 was not an MTP device
Jul  6 17:58:29 CC kernel: [  493.519714] scsi 7:0:0:0: Direct-Access     ST325082 0A               3.AA PQ: 0 ANSI: 0
Jul  6 17:58:29 CC kernel: [  493.521263] sd 7:0:0:0: Attached scsi generic sg2 type 0
Jul  6 17:58:29 CC kernel: [  493.524378] sd 7:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Jul  6 17:58:29 CC kernel: [  493.526092] sd 7:0:0:0: [sdb] Write Protect is off
Jul  6 17:58:29 CC kernel: [  493.526104] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
Jul  6 17:58:29 CC kernel: [  493.529123] sd 7:0:0:0: [sdb] No Caching mode page present
Jul  6 17:58:29 CC kernel: [  493.529136] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Jul  6 17:58:29 CC kernel: [  493.533551] sd 7:0:0:0: [sdb] No Caching mode page present
Jul  6 17:58:29 CC kernel: [  493.533561] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Jul  6 17:58:29 CC kernel: [  493.545145]  sdb: sdb1
Jul  6 17:58:29 CC kernel: [  493.549073] sd 7:0:0:0: [sdb] No Caching mode page present
Jul  6 17:58:29 CC kernel: [  493.549083] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Jul  6 17:58:29 CC kernel: [  493.549091] sd 7:0:0:0: [sdb] Attached SCSI disk
Jul  6 17:58:29 CC ata_id[2266]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
Jul  6 17:58:29 CC kernel: [  493.756055] usb 2-6: reset high-speed USB device number 19 using ehci_hcd
Jul  6 17:58:29 CC kernel: [  493.932057] usb 2-6: device descriptor read/64, error -71
Jul  6 17:58:30 CC kernel: [  494.196069] usb 2-6: device descriptor read/64, error -71
Jul  6 17:58:30 CC kernel: [  494.412054] usb 2-6: reset high-speed USB device number 19 using ehci_hcd
Jul  6 17:58:30 CC kernel: [  494.572060] usb 2-6: device descriptor read/64, error -71
Jul  6 17:58:30 CC kernel: [  494.836056] usb 2-6: device descriptor read/64, error -71
Jul  6 17:58:31 CC kernel: [  495.052057] usb 2-6: reset high-speed USB device number 19 using ehci_hcd
Jul  6 17:58:31 CC kernel: [  495.492042] usb 2-6: device not accepting address 19, error -71
Jul  6 17:58:31 CC kernel: [  495.604056] usb 2-6: reset high-speed USB device number 19 using ehci_hcd
Jul  6 17:58:32 CC kernel: [  496.044058] usb 2-6: device not accepting address 19, error -71
Jul  6 17:58:32 CC kernel: [  496.044121] usb 2-6: USB disconnect, device number 19
Jul  6 17:58:32 CC kernel: [  496.048437] scsi 7:0:0:0: [sdb] killing request
Jul  6 17:58:32 CC kernel: [  496.048483] scsi 7:0:0:0: [sdb] Unhandled error code
Jul  6 17:58:32 CC kernel: [  496.048491] scsi 7:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jul  6 17:58:32 CC kernel: [  496.048503] scsi 7:0:0:0: [sdb] CDB: Read(10): 28 00 1d 1c 58 68 00 00 08 00
Jul  6 17:58:32 CC kernel: [  496.048537] end_request: I/O error, dev sdb, sector 488396904
Jul  6 17:58:32 CC kernel: [  496.048549] quiet_error: 952 callbacks suppressed
Jul  6 17:58:32 CC kernel: [  496.048556] Buffer I/O error on device sdb, logical block 61049613
Jul  6 17:58:32 CC kernel: [  496.048623] Buffer I/O error on device sdb, logical block 61049613
Jul  6 17:58:32 CC kernel: [  496.048901] Buffer I/O error on device sdb, logical block 1
Jul  6 17:58:32 CC kernel: [  496.048918] Buffer I/O error on device sdb, logical block 1
Jul  6 17:58:32 CC kernel: [  496.048940] Buffer I/O error on device sdb, logical block 1
Jul  6 17:58:32 CC kernel: [  496.049036] Buffer I/O error on device sdb, logical block 61049645
Jul  6 17:58:32 CC kernel: [  496.049064] Buffer I/O error on device sdb, logical block 0
Jul  6 17:58:32 CC kernel: [  496.049084] Buffer I/O error on device sdb, logical block 0
Jul  6 17:58:32 CC kernel: [  496.049104] Buffer I/O error on device sdb, logical block 0
Jul  6 17:58:32 CC kernel: [  496.049123] Buffer I/O error on device sdb, logical block 0
Jul  6 17:58:32 CC kernel: [  496.176047] usb 2-6: new high-speed USB device number 20 using ehci_hcd
Jul  6 17:58:32 CC kernel: [  496.336053] usb 2-6: device descriptor read/64, error -71
Jul  6 17:58:32 CC kernel: [  496.600051] usb 2-6: device descriptor read/64, error -71
Jul  6 17:58:32 CC kernel: [  496.816051] usb 2-6: new high-speed USB device number 21 using ehci_hcd
Jul  6 17:58:32 CC kernel: [  496.976067] usb 2-6: device descriptor read/64, error -71
Jul  6 17:58:33 CC kernel: [  497.240061] usb 2-6: device descriptor read/64, error -71
Jul  6 17:58:33 CC kernel: [  497.456060] usb 2-6: new high-speed USB device number 22 using ehci_hcd
Jul  6 17:58:33 CC kernel: [  497.896049] usb 2-6: device not accepting address 22, error -71
Jul  6 17:58:33 CC kernel: [  498.008054] usb 2-6: new high-speed USB device number 23 using ehci_hcd
Jul  6 17:58:34 CC kernel: [  498.448053] usb 2-6: device not accepting address 23, error -71
Jul  6 17:58:34 CC kernel: [  498.448095] hub 2-0:1.0: unable to enumerate USB device on port 6
Jul  6 17:58:34 CC kernel: [  498.716062] usb 7-2: new full-speed USB device number 14 using uhci_hcd
Jul  6 17:58:34 CC kernel: [  498.840056] usb 7-2: device descriptor read/64, error -71
Jul  6 17:58:35 CC kernel: [  499.064078] usb 7-2: device descriptor read/64, error -71
Jul  6 17:58:35 CC kernel: [  499.280055] usb 7-2: new full-speed USB device number 15 using uhci_hcd
Jul  6 17:58:35 CC kernel: [  499.460064] usb 7-2: device descriptor read/64, error -71
Jul  6 17:58:35 CC kernel: [  499.684053] usb 7-2: device descriptor read/64, error -71
Jul  6 17:58:35 CC kernel: [  499.956073] usb 7-2: new full-speed USB device number 16 using uhci_hcd
Jul  6 17:58:36 CC kernel: [  500.368063] usb 7-2: device not accepting address 16, error -71
Jul  6 17:58:36 CC kernel: [  500.480054] usb 7-2: new full-speed USB device number 17 using uhci_hcd
Jul  6 17:58:36 CC kernel: [  500.892074] usb 7-2: device not accepting address 17, error -71
Jul  6 17:58:36 CC kernel: [  500.892110] hub 7-0:1.0: unable to enumerate USB device on port 2
Jul  6 17:59:04 CC kernel: [  528.540099] usb 2-6: new high-speed USB device number 24 using ehci_hcd
Jul  6 17:59:04 CC kernel: [  528.762124] scsi8 : usb-storage 2-6:1.0
Jul  6 17:59:04 CC mtp-probe: checking bus 2, device 24: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-6"
Jul  6 17:59:04 CC mtp-probe: bus: 2, device: 24 was not an MTP device
Jul  6 17:59:05 CC kernel: [  529.904059] usb 2-6: reset high-speed USB device number 24 using ehci_hcd
Jul  6 17:59:06 CC kernel: [  530.076072] usb 2-6: device descriptor read/64, error -71
Jul  6 17:59:06 CC kernel: [  530.340062] usb 2-6: device descriptor read/64, error -71
Jul  6 17:59:06 CC kernel: [  530.556060] usb 2-6: reset high-speed USB device number 24 using ehci_hcd
Jul  6 17:59:06 CC kernel: [  530.716059] usb 2-6: device descriptor read/64, error -71
Jul  6 17:59:06 CC kernel: [  530.980057] usb 2-6: device descriptor read/64, error -71
Jul  6 17:59:07 CC kernel: [  531.196068] usb 2-6: reset high-speed USB device number 24 using ehci_hcd
Jul  6 17:59:07 CC kernel: [  531.636056] usb 2-6: device not accepting address 24, error -71
Jul  6 17:59:07 CC kernel: [  531.748059] usb 2-6: reset high-speed USB device number 24 using ehci_hcd
Jul  6 17:59:08 CC kernel: [  532.188058] usb 2-6: device not accepting address 24, error -71
Jul  6 17:59:08 CC kernel: [  532.188120] usb 2-6: USB disconnect, device number 24
Jul  6 17:59:08 CC kernel: [  532.308053] usb 2-6: new high-speed USB device number 25 using ehci_hcd
Jul  6 17:59:08 CC kernel: [  532.468061] usb 2-6: device descriptor read/64, error -71
Jul  6 17:59:08 CC kernel: [  532.732042] usb 2-6: device descriptor read/64, error -71
Jul  6 17:59:08 CC kernel: [  532.948051] usb 2-6: new high-speed USB device number 26 using ehci_hcd
Jul  6 17:59:09 CC kernel: [  533.108059] usb 2-6: device descriptor read/64, error -71
Jul  6 17:59:09 CC kernel: [  533.372047] usb 2-6: device descriptor read/64, error -71
Jul  6 17:59:09 CC kernel: [  533.588034] usb 2-6: new high-speed USB device number 27 using ehci_hcd
Jul  6 17:59:10 CC kernel: [  534.028078] usb 2-6: device not accepting address 27, error -71
Jul  6 17:59:10 CC kernel: [  534.140057] usb 2-6: new high-speed USB device number 28 using ehci_hcd
Jul  6 17:59:10 CC kernel: [  534.580048] usb 2-6: device not accepting address 28, error -71
Jul  6 17:59:10 CC kernel: [  534.580080] hub 2-0:1.0: unable to enumerate USB device on port 6
Jul  6 17:59:10 CC kernel: [  534.848052] usb 7-2: new full-speed USB device number 18 using uhci_hcd
Jul  6 17:59:10 CC kernel: [  534.968051] usb 7-2: device descriptor read/64, error -71
Jul  6 17:59:11 CC kernel: [  535.192050] usb 7-2: device descriptor read/64, error -71
Jul  6 17:59:11 CC kernel: [  535.408056] usb 7-2: new full-speed USB device number 19 using uhci_hcd
Jul  6 17:59:11 CC kernel: [  535.528056] usb 7-2: device descriptor read/64, error -71
Jul  6 17:59:11 CC kernel: [  535.808053] usb 7-2: device descriptor read/64, error -71
Jul  6 17:59:12 CC kernel: [  536.024076] usb 7-2: new full-speed USB device number 20 using uhci_hcd
Jul  6 17:59:12 CC kernel: [  536.436050] usb 7-2: device not accepting address 20, error -71
Jul  6 17:59:12 CC kernel: [  536.604052] usb 7-2: new full-speed USB device number 21 using uhci_hcd
Jul  6 17:59:12 CC kernel: [  537.012045] usb 7-2: device not accepting address 21, error -71
Jul  6 17:59:12 CC kernel: [  537.012072] hub 7-0:1.0: unable to enumerate USB device on port 2
Jul  6 17:59:34 CC kernel: [  558.560048] usb 2-6: new high-speed USB device number 29 using ehci_hcd
Jul  6 17:59:34 CC kernel: [  558.782590] scsi9 : usb-storage 2-6:1.0
Jul  6 17:59:34 CC mtp-probe: checking bus 2, device 29: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-6"
Jul  6 17:59:34 CC mtp-probe: bus: 2, device: 29 was not an MTP device
Jul  6 17:59:35 CC kernel: [  559.924057] usb 2-6: reset high-speed USB device number 29 using ehci_hcd
Jul  6 17:59:36 CC kernel: [  560.096061] usb 2-6: device descriptor read/64, error -71
Jul  6 17:59:36 CC kernel: [  560.360061] usb 2-6: device descriptor read/64, error -71
Jul  6 17:59:36 CC kernel: [  560.576062] usb 2-6: reset high-speed USB device number 29 using ehci_hcd
Jul  6 17:59:36 CC kernel: [  560.736053] usb 2-6: device descriptor read/64, error -71
Jul  6 17:59:36 CC kernel: [  561.000055] usb 2-6: device descriptor read/64, error -71
Jul  6 17:59:37 CC kernel: [  561.216058] usb 2-6: reset high-speed USB device number 29 using ehci_hcd
Jul  6 17:59:37 CC kernel: [  561.652045] usb 2-6: device not accepting address 29, error -71
Jul  6 17:59:37 CC kernel: [  561.764065] usb 2-6: reset high-speed USB device number 29 using ehci_hcd
Jul  6 17:59:38 CC kernel: [  562.200082] usb 2-6: device not accepting address 29, error -71
Jul  6 17:59:38 CC kernel: [  562.200147] usb 2-6: USB disconnect, device number 29
Jul  6 17:59:38 CC kernel: [  562.320060] usb 2-6: new high-speed USB device number 30 using ehci_hcd
Jul  6 17:59:38 CC kernel: [  562.480058] usb 2-6: device descriptor read/64, error -71
Jul  6 17:59:38 CC kernel: [  562.744060] usb 2-6: device descriptor read/64, error -71
Jul  6 17:59:38 CC kernel: [  562.960058] usb 2-6: new high-speed USB device number 31 using ehci_hcd
Jul  6 17:59:39 CC kernel: [  563.120056] usb 2-6: device descriptor read/64, error -71
Jul  6 17:59:39 CC kernel: [  563.384053] usb 2-6: device descriptor read/64, error -71
Jul  6 17:59:39 CC kernel: [  563.600059] usb 2-6: new high-speed USB device number 32 using ehci_hcd
Jul  6 17:59:40 CC kernel: [  564.032043] usb 2-6: device not accepting address 32, error -71
Jul  6 17:59:40 CC kernel: [  564.144198] usb 2-6: new high-speed USB device number 33 using ehci_hcd
Jul  6 17:59:40 CC kernel: [  564.580045] usb 2-6: device not accepting address 33, error -71
Jul  6 17:59:40 CC kernel: [  564.580078] hub 2-0:1.0: unable to enumerate USB device on port 6
Jul  6 17:59:40 CC kernel: [  564.848059] usb 7-2: new full-speed USB device number 22 using uhci_hcd
Jul  6 17:59:40 CC kernel: [  564.972047] usb 7-2: device descriptor read/64, error -71
Jul  6 17:59:41 CC kernel: [  565.200050] usb 7-2: device descriptor read/64, error -71
Jul  6 17:59:41 CC kernel: [  565.416060] usb 7-2: new full-speed USB device number 23 using uhci_hcd
Jul  6 17:59:41 CC kernel: [  565.540058] usb 7-2: device descriptor read/64, error -71
Jul  6 17:59:41 CC kernel: [  565.764056] usb 7-2: device descriptor read/64, error -71
Jul  6 17:59:41 CC kernel: [  565.980046] usb 7-2: new full-speed USB device number 24 using uhci_hcd
Jul  6 17:59:42 CC kernel: [  566.392059] usb 7-2: device not accepting address 24, error -71
Jul  6 17:59:42 CC kernel: [  566.560054] usb 7-2: new full-speed USB device number 25 using uhci_hcd
Jul  6 17:59:42 CC kernel: [  566.976058] usb 7-2: device not accepting address 25, error -71
Jul  6 17:59:42 CC kernel: [  566.976092] hub 7-0:1.0: unable to enumerate USB device on port 2
Jul  6 18:00:02 CC kernel: [  586.092048] usb 2-6: new high-speed USB device number 34 using ehci_hcd
Jul  6 18:00:02 CC kernel: [  586.314354] scsi10 : usb-storage 2-6:1.0
Jul  6 18:00:02 CC mtp-probe: checking bus 2, device 34: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-6"
Jul  6 18:00:02 CC mtp-probe: bus: 2, device: 34 was not an MTP device
Jul  6 18:00:03 CC kernel: [  587.456077] usb 2-6: reset high-speed USB device number 34 using ehci_hcd
Jul  6 18:00:03 CC kernel: [  587.628103] usb 2-6: device descriptor read/64, error -71
Jul  6 18:00:03 CC kernel: [  587.892061] usb 2-6: device descriptor read/64, error -71
Jul  6 18:00:04 CC kernel: [  588.108058] usb 2-6: reset high-speed USB device number 34 using ehci_hcd
Jul  6 18:00:04 CC kernel: [  588.268064] usb 2-6: device descriptor read/64, error -71
Jul  6 18:00:04 CC kernel: [  588.532063] usb 2-6: device descriptor read/64, error -71
Jul  6 18:00:04 CC kernel: [  588.748062] usb 2-6: reset high-speed USB device number 34 using ehci_hcd
Jul  6 18:00:05 CC kernel: [  589.188043] usb 2-6: device not accepting address 34, error -71
Jul  6 18:00:05 CC kernel: [  589.300055] usb 2-6: reset high-speed USB device number 34 using ehci_hcd
Jul  6 18:00:05 CC kernel: [  589.740055] usb 2-6: device not accepting address 34, error -71
Jul  6 18:00:05 CC kernel: [  589.740123] usb 2-6: USB disconnect, device number 34
Jul  6 18:00:05 CC kernel: [  589.860049] usb 2-6: new high-speed USB device number 35 using ehci_hcd
Jul  6 18:00:06 CC kernel: [  590.020067] usb 2-6: device descriptor read/64, error -71
Jul  6 18:00:06 CC kernel: [  590.284040] usb 2-6: device descriptor read/64, error -71
Jul  6 18:00:06 CC kernel: [  590.500061] usb 2-6: new high-speed USB device number 36 using ehci_hcd
Jul  6 18:00:06 CC kernel: [  590.660045] usb 2-6: device descriptor read/64, error -71
Jul  6 18:00:06 CC kernel: [  590.924074] usb 2-6: device descriptor read/64, error -71
Jul  6 18:00:07 CC kernel: [  591.140049] usb 2-6: new high-speed USB device number 37 using ehci_hcd
Jul  6 18:00:07 CC kernel: [  591.580047] usb 2-6: device not accepting address 37, error -71
Jul  6 18:00:07 CC kernel: [  591.692098] usb 2-6: new high-speed USB device number 38 using ehci_hcd
Jul  6 18:00:08 CC kernel: [  592.132041] usb 2-6: device not accepting address 38, error -71
Jul  6 18:00:08 CC kernel: [  592.132074] hub 2-0:1.0: unable to enumerate USB device on port 6
Jul  6 18:00:08 CC kernel: [  592.400056] usb 7-2: new full-speed USB device number 26 using uhci_hcd
Jul  6 18:00:08 CC kernel: [  592.524074] usb 7-2: device descriptor read/64, error -71
Jul  6 18:00:08 CC kernel: [  592.752050] usb 7-2: device descriptor read/64, error -71
Jul  6 18:00:08 CC kernel: [  592.968095] usb 7-2: new full-speed USB device number 27 using uhci_hcd
Jul  6 18:00:09 CC kernel: [  593.092068] usb 7-2: device descriptor read/64, error -71
Jul  6 18:00:09 CC kernel: [  593.320088] usb 7-2: device descriptor read/64, error -71
Jul  6 18:00:09 CC kernel: [  593.536054] usb 7-2: new full-speed USB device number 28 using uhci_hcd
Jul  6 18:00:09 CC kernel: [  593.952044] usb 7-2: device not accepting address 28, error -71
Jul  6 18:00:10 CC kernel: [  594.064049] usb 7-2: new full-speed USB device number 29 using uhci_hcd
Jul  6 18:00:10 CC kernel: [  594.480078] usb 7-2: device not accepting address 29, error -71
Jul  6 18:00:10 CC kernel: [  594.480118] hub 7-0:1.0: unable to enumerate USB device on port 2
```

---

### Post by ronnysingh on 2012-07-06
I had a Transcend HDD which ceased to mount for no reason. I installed storage device manager from the software center and it detected the disk all the time. The problem was that the disk did not mount by itself and I had to mount it by using storage device manager.

---

### Post by NikTh on 2012-07-06
> **zhanglini said:**
> ```

Jul  6 17:56:34 CC kernel: [  378.016155] usb 2-6: USB disconnect, device number 9
Jul  6 17:56:34 CC kernel: [  378.020697] scsi 5:0:0:0: [sdb] killing request
Jul  6 17:56:34 CC kernel: [  378.020739] scsi 5:0:0:0: [sdb] Unhandled error code
Jul  6 17:56:34 CC kernel: [  378.020750] scsi 5:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jul  6 17:56:34 CC kernel: [  378.020763] scsi 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 08 00
Jul  6 17:56:34 CC kernel: [  378.020902] end_request: I/O error, dev sdb, sector 63
Jul  6 17:56:34 CC kernel: [  378.020914] quiet_error: 36 callbacks suppressed
Jul  6 17:56:34 CC kernel: [  378.020922] Buffer I/O error on device sdb1, logical block 0
Jul  6 17:56:34 CC kernel: [  378.020933] Buffer I/O error on device sdb1, logical block 1
Jul  6 17:56:34 CC kernel: [  378.020942] Buffer I/O error on device sdb1, logical block 2
Jul  6 17:56:34 CC kernel: [  378.020951] Buffer I/O error on device sdb1, logical block 3
Jul  6 17:56:34 CC kernel: [  378.020959] Buffer I/O error on device sdb1, logical block 4
Jul  6 17:56:34 CC kernel: [  378.020967] Buffer I/O error on device sdb1, logical block 5
Jul  6 17:56:34 CC kernel: [  378.020975] Buffer I/O error on device sdb1, logical block 6
Jul  6 17:56:34 CC kernel: [  378.020983] Buffer I/O error on device sdb1, logical block 7
Jul  6 17:56:34 CC kernel: [  378.023595] Buffer I/O error on device sdb1, logical block 0
Jul  6 17:56:34 CC kernel: [  378.023614] Buffer I/O error on device sdb1, logical block 1
Jul  6 17:56:34 CC kernel: [  378.148104] usb 2-6: new high-speed USB device number 10 using ehci_hcd
``` 

I think you can see by yourself all those I/O errors ... 

I suggest re-formating with another way.. 
1)Connect the disk and [COLOR=Red]backup your data [/COLOR]
2) Open **Disk Utility** and click on this disk 
3) Unmount it 
4) [COLOR=Red]Delete[/COLOR] it . Delete ALL and filesystem. 
5)[COLOR=DarkGreen]Create[/COLOR] a new filesystem (NTFS if you want access from windows too) 
Done.

---

### Post by zhanglini on 2012-07-07
Mmmm thanks.
I had partial success with Nik's suggestions: After I deleted everything, the HD always shows up as /dev/sdb when I turned it on.  But when I tried to format it, it would disappear.  So I created a 1MB partition, then increased its size gradually to 250GB.  I got the following errors along the way, ```
resize2fs: Attempt to write block to filesystem resulted in short write
``` and ran ```
e2fsck -fy /dev/sdb1
``` as suggested.  I was sort of successful in formatting the whole HD this way, only had 10~ GB available.  
So I decide to try it again --- this time with much worse luck, every time I turned it on, it showed up as /dev/sdb, but whenever I tried to do something (delete/format etc) it disappeared.  I tried the "badblock" command, as leat the first 6% of the drive is error free (did not finish as it would take 20 hours).
Is my drive toasted?

---

### Post by NikTh on 2012-07-08
When i said [COLOR=Red]Delete it [COLOR=Black]i meant the disk stated as "Unallocated space" . Did you do that correctly ? 
I suggest something else now.... Create a NTFS file-system with Disk Utility and IF you have windows , boot in windows and use ```
chkdsk /r
``` command from a cmd prompt . Windows will search for bad sectors and attempt to correct them. 
Google for more about chkdsk and /r parameter. 
[/COLOR][/COLOR]

---

### Post by zhanglini on 2012-07-08
My disk did not have unallocated space, I deleted everything --- I guess a bit too much.
I don't have Windows, and even when the drive WAS working, I tried it on school and work computers (XP/Win7) and windows could never recognize it (used to have NTFS/ext2).
Now the drive is detected and added as /dev/sdb, but anytime I wanted to do anything (format/add partition/add partition table) it disappeared....

---

### Post by zhanglini on 2012-07-16
I was able to use fdisk commands to add a partition table and add a primary partition, but everytime I try to add an extended partition, I was only able to get 1GB (out of 250), when I tried to resize above that I got this magic number wrong error.
Is there a way you can wipe out everything, including superblock etc and start from scatch?  or is this drive physically toasted?

---

### Post by zhanglini on 2012-07-20
ok, using fdisk I was able to add a partition table, add a primary partition (that covers the whole drive).  Then I used Gparted to give he partition a label.  And it mounts fine too.
But I just can't save anything to the drive --- I/O error every time!  How do I fix this I/O error?

---

### Post by Bashing-om on 2012-07-20
If it helps, I had a similar problem. My disk was disappearing in Gpatred.
my solution was the dd command from CLI off-course.
be aware and careful. My disk was sda and  I applied the following:
```

dd if=/dev/zero of=/dev/sda bs=1M

```
This zero's out the entire disk.
Then after a reboot, Gparted picked it up; I was able to select device sda, write a partition table to format it, and write all my partitions to the disk.

Hope this helps.

---

### Post by zhanglini on 2012-07-23
Thank you!
I used this dd command to 0 out the whole drive (tried this a week ago, but error-ed out after 1GB; something changed since then).  Then I formatted it to NTFS (could not do ext2, /dev/sdb disappears every time I tried that), and I actually managed to copy 5GB of stuff to the drive.
But when I tried to use the drive to back up my computer, it would work for a while and then  gave me this error all the time:
```
Jul 23 17:59:52 CC kernel: [ 1031.532101] usb 2-5: reset high-speed USB device number 14 using ehci_hcd
Jul 23 17:59:52 CC kernel: [ 1031.708071] usb 2-5: device descriptor read/64, error -71
Jul 23 17:59:52 CC kernel: [ 1031.972228] usb 2-5: device descriptor read/64, error -71
Jul 23 17:59:53 CC kernel: [ 1032.188083] usb 2-5: reset high-speed USB device number 14 using ehci_hcd
Jul 23 17:59:53 CC kernel: [ 1032.356075] usb 2-5: device descriptor read/64, error -71
Jul 23 17:59:53 CC kernel: [ 1032.620088] usb 2-5: device descriptor read/64, error -71
Jul 23 17:59:53 CC kernel: [ 1032.840108] usb 2-5: reset high-speed USB device number 14 using ehci_hcd
Jul 23 17:59:54 CC kernel: [ 1033.280078] usb 2-5: device not accepting address 14, error -71
Jul 23 17:59:54 CC kernel: [ 1033.392062] usb 2-5: reset high-speed USB device number 14 using ehci_hcd
Jul 23 17:59:54 CC kernel: [ 1033.832067] usb 2-5: device not accepting address 14, error -71
Jul 23 17:59:54 CC kernel: [ 1033.832139] usb 2-5: USB disconnect, device number 14
Jul 23 17:59:54 CC kernel: [ 1033.836076] sd 6:0:0:0: [sdb] Unhandled error code
Jul 23 17:59:54 CC kernel: [ 1033.836086] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jul 23 17:59:54 CC kernel: [ 1033.836098] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 a2 b0 00 00 f0 00
Jul 23 17:59:54 CC kernel: [ 1033.836124] end_request: I/O error, dev sdb, sector 41648
Jul 23 17:59:54 CC kernel: [ 1033.836133] quiet_error: 411 callbacks suppressed
Jul 23 17:59:54 CC kernel: [ 1033.836140] Buffer I/O error on device sdb, logical block 5206
Jul 23 17:59:54 CC kernel: [ 1033.836156] Buffer I/O error on device sdb, logical block 5207
Jul 23 17:59:54 CC kernel: [ 1033.836164] Buffer I/O error on device sdb, logical block 5208
Jul 23 17:59:54 CC kernel: [ 1033.836172] Buffer I/O error on device sdb, logical block 5209
Jul 23 17:59:54 CC kernel: [ 1033.836180] Buffer I/O error on device sdb, logical block 5210
Jul 23 17:59:54 CC kernel: [ 1033.836187] Buffer I/O error on device sdb, logical block 5211
Jul 23 17:59:54 CC kernel: [ 1033.836195] Buffer I/O error on device sdb, logical block 5212
Jul 23 17:59:54 CC kernel: [ 1033.836203] Buffer I/O error on device sdb, logical block 5213
Jul 23 17:59:54 CC kernel: [ 1033.836211] Buffer I/O error on device sdb, logical block 5214
Jul 23 17:59:54 CC kernel: [ 1033.836218] Buffer I/O error on device sdb, logical block 5215
Jul 23 17:59:54 CC kernel: [ 1033.836324] sd 6:0:0:0: [sdb] Unhandled error code
Jul 23 17:59:54 CC kernel: [ 1033.836332] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jul 23 17:59:54 CC kernel: [ 1033.836342] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 a3 a0 00 00 10 00
Jul 23 17:59:54 CC kernel: [ 1033.836368] end_request: I/O error, dev sdb, sector 41888
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Reading $BITMAP failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to allocate clusters: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Cluster allocation failed (1): Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to enlarge attribute: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_mst_pwrite: written=-1: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to write index block 3, inode 16854: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to add filename to the index: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Reading $BITMAP failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to allocate clusters: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Cluster allocation failed (1): Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to enlarge attribute: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_mst_pwrite: written=-1: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to write index block 3, inode 16854: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to add filename to the index: Input/output error
Jul 23 17:59:55 CC kernel: [ 1034.168058] usb 2-5: new high-speed USB device number 15 using ehci_hcd
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Reading $BITMAP failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to allocate clusters: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Cluster allocation failed (1): Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to enlarge attribute: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_mst_pwrite: written=-1: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to write index block 3, inode 16854: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to add filename to the index: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Reading $BITMAP failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to allocate clusters: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Cluster allocation failed (1): Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to enlarge attribute: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_mst_pwrite: written=-1: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to write index block 3, inode 16854: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to add filename to the index: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Reading $BITMAP failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to allocate clusters: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Cluster allocation failed (1): Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to enlarge attribute: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_mst_pwrite: written=-1: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to write index block 3, inode 16854: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to add filename to the index: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Reading $BITMAP failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to allocate clusters: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Cluster allocation failed (1): Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to enlarge attribute: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_mst_pwrite: written=-1: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to write index block 3, inode 16854: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to add filename to the index: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Reading $BITMAP failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to allocate clusters: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Cluster allocation failed (1): Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to enlarge attribute: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_mst_pwrite: written=-1: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to write index block 3, inode 16854: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to add filename to the index: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Reading $BITMAP failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to allocate clusters: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Cluster allocation failed (1): Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to enlarge attribute: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_mst_pwrite: written=-1: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to write index block 3, inode 16854: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to add filename to the index: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Reading $BITMAP failed: Input/output error
Jul 23 17:59:55 CC ntfs-3g[2338]: Failed to allocate clusters: Input/output error
Jul 23 17:59:55 CC kernel: [ 1034.328086] usb 2-5: device descriptor read/64, error -71
Jul 23 17:59:55 CC kernel: [ 1034.592055] usb 2-5: device descriptor read/64, error -71
Jul 23 17:59:55 CC ntfs-3g[2338]: Unmounting /dev/sdb (Shared)
Jul 23 17:59:55 CC kernel: [ 1034.808049] usb 2-5: new high-speed USB device number 16 using ehci_hcd
Jul 23 17:59:55 CC kernel: [ 1034.968071] usb 2-5: device descriptor read/64, error -71
Jul 23 17:59:56 CC kernel: [ 1035.232047] usb 2-5: device descriptor read/64, error -71
Jul 23 17:59:56 CC kernel: [ 1035.448059] usb 2-5: new high-speed USB device number 17 using ehci_hcd
Jul 23 17:59:56 CC kernel: [ 1035.888351] usb 2-5: device not accepting address 17, error -71
Jul 23 17:59:56 CC kernel: [ 1036.000062] usb 2-5: new high-speed USB device number 18 using ehci_hcd
Jul 23 17:59:57 CC kernel: [ 1036.444055] usb 2-5: device not accepting address 18, error -71
Jul 23 17:59:57 CC kernel: [ 1036.444090] hub 2-0:1.0: unable to enumerate USB device on port 5
Jul 23 17:59:57 CC kernel: [ 1036.712063] usb 7-1: new full-speed USB device number 10 using uhci_hcd
Jul 23 17:59:57 CC kernel: [ 1036.892048] usb 7-1: device descriptor read/64, error -71
Jul 23 17:59:58 CC kernel: [ 1037.121142] usb 7-1: device descriptor read/64, error -71
Jul 23 17:59:58 CC kernel: [ 1037.336063] usb 7-1: new full-speed USB device number 11 using uhci_hcd
Jul 23 17:59:58 CC kernel: [ 1037.460080] usb 7-1: device descriptor read/64, error -71
Jul 23 17:59:58 CC kernel: [ 1037.688063] usb 7-1: device descriptor read/64, error -71
Jul 23 17:59:58 CC kernel: [ 1037.960089] usb 7-1: new full-speed USB device number 12 using uhci_hcd
Jul 23 17:59:59 CC kernel: [ 1038.376062] usb 7-1: device not accepting address 12, error -71
Jul 23 17:59:59 CC kernel: [ 1038.488097] usb 7-1: new full-speed USB device number 13 using uhci_hcd
Jul 23 17:59:59 CC kernel: [ 1038.900049] usb 7-1: device not accepting address 13, error -71
Jul 23 17:59:59 CC kernel: [ 1038.900076] hub 7-0:1.0: unable to enumerate USB device on port 1
```

---

### Post by westie457 on 2012-07-23
Hi, open Disk Utility - palimpsest in a terminal - and check the health and SMART status of the drive. That will probably give a better idea of the hard drive becoming a paperweight. Post the results here if you are not sure what they mean.

Thank you.

Edit... Just realised you are using a USB drive. The SMART check might not be supported

---

### Post by zhanglini on 2012-07-23
Thanks, you are right, SMART is not supported.

---

### Post by Bashing-om on 2012-07-31
looks to me like the drive was mounted when you ran the test. To zero out that drive it must not be mounted ... ie use a live cd....
is this what you have tried ????
   one step at a time ... till resolution!

---

### Post by Bashing-om on 2012-07-31
Hey ; Have ya thought it might be a cable problem ... Have you tried a different usb cable and see what haps ? /// I have seen similar issues on internal sata drives ... changing the port sometimes helped....
      kind regards

---

