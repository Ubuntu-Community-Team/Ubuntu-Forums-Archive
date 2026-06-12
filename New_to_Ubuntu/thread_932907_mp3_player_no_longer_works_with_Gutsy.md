---
title: "mp3 player no longer works with Gutsy"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by blairm on 2008-09-28
Hi,

Until this morning, my mp3 player worked great with Ubuntu - appeared on desktop, immediate access to files etc.
But from this morning, when I plug it in to the usb  it does nothing - no icon or anything.
Pretty sure it's not the usb plug because a 160gb usb drive still works fine.
The mp3 player is a generic brand from Dick Smith Electronics, and chain of stores in NZ and Australia.
Anyone have any suggestions?

BTW, not sure whether it's related but also since this morning I have no sound on my computer!

Cheers,

Blair

---

### Post by blairm on 2008-09-28
Additional to the above, ran dmesg and think this is the relevant part.


[ 2764.166723] scsi 6:0:0:0: Direct-Access     DSE      NEURON           1.00 PQ: 0 ANSI: 0
[ 2764.184692] sd 6:0:0:0: [sdf] 3972096 512-byte hardware sectors (2034 MB)
[ 2764.187681] sd 6:0:0:0: [sdf] Write Protect is off
[ 2764.187686] sd 6:0:0:0: [sdf] Mode Sense: 03 00 00 00
[ 2764.187689] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[ 2764.196698] sd 6:0:0:0: [sdf] 3972096 512-byte hardware sectors (2034 MB)
[ 2764.199671] sd 6:0:0:0: [sdf] Write Protect is off
[ 2764.199675] sd 6:0:0:0: [sdf] Mode Sense: 03 00 00 00
[ 2764.199677] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[ 2764.199685]  sdf: unknown partition table
[ 2764.225719] sd 6:0:0:0: [sdf] Attached SCSI removable disk
[ 2764.225780] sd 6:0:0:0: Attached scsi generic sg6 type 0

Tried using cfdisk to reformat but got a message saying fatal error - unable to open. Gparted doesn't seem to realise tje mp3 player is plugged in.
The player has been plugged into a usb at work for charging, and that computer was running XP - does that make a difference?

Any help would be much appreciated - I'm running out of ideas!

Cheers,

Blair

---

