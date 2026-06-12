---
title: "MP3 Player?"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by BruceCM on 2011-09-20
Plugged in Sansa Clip & followed the desktop help to add '.is_audio_player' document but the music folder claims to  be 'empty'! I know that's where all my music is, since I put it there; it doesn't show the 'albums' folders, at all. Any ideas?

---

### Post by BruceCM on 2011-09-21
PS, in Windows, it was a 'UDB Mass Storage Device' & it's called '8 GB File System here', if that helps?

---

### Post by mastablasta on 2011-09-21
plug the USB player in, open the terminal and type
 
lsusb
 
this should show what is actually recognised in USB port. you can copy and paste the results here.

---

### Post by aeiah on 2011-09-21
dont these things have memory card expansion ports? is there a chance you put your music on the onboard storage and ubuntu is mounting the SD card (or vice versa?)

---

### Post by BruceCM on 2011-09-25
> **mastablasta said:**
> plug the USB player in, open the terminal and type
 
lsusb
 
this should show what is actually recognised in USB port. you can copy and paste the results here.
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0781:7434 SanDisk Corp. Sansa Clip V2 (mtp)
Bus 001 Device 002: ID 090c:37bc Feiya Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
That?

---

### Post by BruceCM on 2012-03-05
It might still be nice to get the response to that, please?:o

---

### Post by mastablasta on 2012-03-05
well the USB is recognised.

are oyu sure you are checkign the music folder on your USB not in the home?

---

### Post by BruceCM on 2012-03-05
Sorry, of course it was in the player? Not the home folder! Not an easy mistake to make, it's as obvious which is which here as in Windows & I've done it enough times. I'll report back, if I can install Ubuntu, to try sorting that out, though.

---

