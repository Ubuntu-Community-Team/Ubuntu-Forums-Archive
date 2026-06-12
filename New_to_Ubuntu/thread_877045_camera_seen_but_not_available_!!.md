---
title: "camera seen but not available !!"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Rowanmf on 2008-08-01
guys need a quick hand , just plugged my camera in for the first time and i dont see anywhere where i can pick the pictures i just took , 
the log shows :
Aug  1 17:06:23 rowan-laptop kernel: [48352.768371] usb 3-1: new full speed USB device using uhci_hcd and address 22
Aug  1 17:06:24 rowan-laptop kernel: [48352.974106] usb 3-1: new full speed USB device using uhci_hcd and address 23
Aug  1 17:06:25 rowan-laptop kernel: [48352.982886] usb 3-1: configuration #1 chosen from 1 choice
Aug  1 17:06:25 rowan-laptop kernel: [48352.984827] scsi15 : SCSI emulation for USB Mass Storage devices
Aug  1 17:06:30 rowan-laptop kernel: [48353.799111] scsi 15:0:0:0: Direct-Access              VIVITAR          0100 PQ: 0 ANSI: 0 CCS
Aug  1 17:06:30 rowan-laptop kernel: [48353.806048] sd 15:0:0:0: [sdc] 31360 512-byte hardware sectors (16 MB)
Aug  1 17:06:30 rowan-laptop kernel: [48353.809045] sd 15:0:0:0: [sdc] Write Protect is off
Aug  1 17:06:30 rowan-laptop kernel: [48353.820046] sd 15:0:0:0: [sdc] 31360 512-byte hardware sectors (16 MB)
Aug  1 17:06:30 rowan-laptop kernel: [48353.824029] sd 15:0:0:0: [sdc] Write Protect is off
Aug  1 17:06:30 rowan-laptop kernel: [48353.824040]  sdc: sdc1
Aug  1 17:06:30 rowan-laptop kernel: [48353.841061] sd 15:0:0:0: [sdc] Attached SCSI removable disk
Aug  1 17:06:30 rowan-laptop kernel: [48353.841110] sd 15:0:0:0: Attached scsi generic sg3 type 0

what must i do to get the pictures off , i need to email them in the next 10 mins to my head office ... please .

Rowan

---

### Post by dca on 2008-08-01
When you open F-Spot and use 'source' drop-down, it doesn't reference the Vivitar camera?
 
Also post contents of 'lsusb' at command line...

---

### Post by dca on 2008-08-01
If nothing else works, you can 'try' and test with Digikam application from repos and see if that does a better job.
 
Just need to find out if your camera is showing up as an actual block device so images can be taken from it...

---

### Post by Rowanmf on 2008-08-01
ok , sorry never seen f spot , oops , i will go have a look , thanks , i did not really want anything to handle them , i just wanted to copy them myself ... will report shortly 

thanks
Rowan

---

### Post by dca on 2008-08-01
You can also try this:
 
[http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)
 
...I'm just throwing sh** out there because 10 mins isn't a lot of time unless you're waiting on results for a venereal disease test taken at a doctor's office.

---

### Post by dca on 2008-08-01
> **Rowanmf said:**
> ok , sorry never seen f spot , oops , i will go have a look , thanks , i did not really want anything to handle them , i just wanted to copy them myself ... will report shortly 

thanks
Rowan

F Spot is under your 'Applications -> Graphics' menu... (if you're running Gnome UBUNTU, not Kubuntu)

---

### Post by dca on 2008-08-01
The only cameras I've never had problems with are the Sony digis...  Their implementation of the memory sticks always (okay, most times in any distro) show up as a block device similar to a thumb-drive.  All other cameras it's a crap-shoot if it shows up because the SD card has to pass through the actual camera itself and be detected...
 
The other option is installing media card readers on desktop PCs or make sure your laptop has media readers installed because after kernel 2.6.20 (I think) a lot of the functionality was built in.

---

### Post by Rowanmf on 2008-08-01
DONE , thanks , once i ran f spot the camera came up as a block device on the desktop and i just coppied the photo's off zipped them and emailed them , wow , that was so lucky , thanks a trillion for your help ... i was panicining cos of the silly time my HQ gave me to send the photo's , typical ..sheesh , anyway thanks again 

Rowan

---

### Post by dca on 2008-08-01
No trouble...

---

### Post by dca on 2008-08-01
By the way, go into 'System -> Preferences -> Removable Drives & Media' and see what digital cameras are set for...

---

### Post by Rowanmf on 2008-08-01
there was nothing ticked , it's funny , i know my way around most of ubuntu now , but i never go anywhere near the camera / graphic stuff , cos i have never had cause to use it , but now , hmm things might change .. 

Thanks

Rowan

---

### Post by dca on 2008-08-01
> **Rowanmf said:**
> there was nothing ticked , it's funny , i know my way around most of ubuntu now , but i never go anywhere near the camera / graphic stuff , cos i have never had cause to use it , but now , hmm things might change .. 

Thanks

Rowan

Excellent, put whatever setting you want into that area, you can use F-Spot, d/l another camera dealie app & set that, or I think you can just set it to mount and open in new window right from that removable drive setting menu...

---

