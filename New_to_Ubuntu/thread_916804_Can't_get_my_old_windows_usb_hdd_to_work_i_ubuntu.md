---
title: "Can't get my old windows usb hdd to work i ubuntu"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Survivor Dude on 2008-09-11
Hi'

Sorry if my question are stupid, but I am quite new to all this and are desperatly trying to get my computer up running again.

The case is that, when i plug my hdd with all my doc's ect. I can find the icon and the name for the drive. But when i try to open, I am informed that the drive can't be mounted.
Is there a solution to my problem?

Thanks
Brian

---

### Post by gvartser on 2008-09-11
1) Check "/media/" to see if you can see the disk there.

2) If not then unplug your device: 

3) Then replug it again.

4) Open up a terminal/shell and enter:
   ```
dmesg
```

5) Check what device name its got from the dmesg output 

6) Mount it manually:
   ```
sudo mount /dev/<device_name> /path/to/a/folder
```

7) Done!

/g

---

### Post by Survivor Dude on 2008-09-11
Thanks so far

but i am not totally with you

i have visual on the drive, it is just not mounted.

I have now tried mounting it manually but without success.

I wrote: sudo mount dev/my book/path/to/a/folder

Where "my book" was the name of the drive

But maybe the /path/to/a/folder part also need to be replaced? and if so with what?

---

### Post by Survivor Dude on 2008-09-11
I've just worked on it - and maybe is it because I dont write the correct name - how do i find the name?

this is the section about the device:
[ 1413.632669] usb 4-3: new high speed USB device using ehci_hcd and address 4
[ 1413.766203] usb 4-3: configuration #1 chosen from 1 choice
[ 1413.818956] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1413.821215] usb-storage: device found at 4
[ 1413.821224] usb-storage: waiting for device to settle before scanning
[ 1414.621898] usb-storage: device scan complete
[ 1414.622988] scsi 4:0:0:0: Direct-Access     WD       5000AAV External 1.65 PQ: 0 ANSI: 4
[ 1414.637727] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 1414.638721] sd 4:0:0:0: [sdb] Write Protect is off
[ 1414.638732] sd 4:0:0:0: [sdb] Mode Sense: 21 00 00 00
[ 1414.638739] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1414.640341] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 1414.641342] sd 4:0:0:0: [sdb] Write Protect is off
[ 1414.641351] sd 4:0:0:0: [sdb] Mode Sense: 21 00 00 00
[ 1414.641357] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1414.641366]  sdb: sdb1
[ 1414.642617] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 1414.642710] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  530.986330] UDF-fs: No VRS found
[  531.028444] ISOFS: Unable to identify CD-ROM format.
[  875.069488] usb 4-3: USB disconnect, address 4
[  881.001823] usb 4-3: new high speed USB device using ehci_hcd and address 5
[  881.135317] usb 4-3: configuration #1 chosen from 1 choice
[  881.169969] scsi5 : SCSI emulation for USB Mass Storage devices
[  881.173625] usb-storage: device found at 5
[  881.173630] usb-storage: waiting for device to settle before scanning
[ 1061.243015] usb-storage: device scan complete
[ 1061.243582] scsi 5:0:0:0: Direct-Access     WD       5000AAV External 1.65 PQ: 0 ANSI: 4
[ 1061.256001] sd 5:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 1061.256878] sd 5:0:0:0: [sdb] Write Protect is off
[ 1061.256884] sd 5:0:0:0: [sdb] Mode Sense: 21 00 00 00
[ 1061.256888] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1061.258001] sd 5:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 1061.258752] sd 5:0:0:0: [sdb] Write Protect is off
[ 1061.258758] sd 5:0:0:0: [sdb] Mode Sense: 21 00 00 00
[ 1061.258761] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1061.258768]  sdb: sdb1

---

