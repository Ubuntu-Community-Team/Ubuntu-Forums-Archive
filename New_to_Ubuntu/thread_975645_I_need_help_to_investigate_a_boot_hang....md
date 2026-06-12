---
title: "I need help to investigate a boot hang..."
date: 2008-11-08
forum: New to Ubuntu
---

### Post by mike.headon on 2008-11-08
Hello folks...
I have raised this problem in "Installation & Upgrades" and on Launchpad without any luck.
Could somebody please advise me on the best way to set about taking any diagnostics which might help? The extent of my knowledge at present is to start with recovery option and note the last message before the hang.
<previously posted material starts>

I have followed the automatic upgrade path from Gutsy to Hardy, but now I find that all kernels after 2.6.22-14 hang up after /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c:
A contributor to [http://ubuntuforums.org/showthread.php?t=825835](http://ubuntuforums.org/showthread.php?t=825835) suggests that it is a conflict between SATA and USB initialization. His suggested fix did not work for me.
System is Athlon XP 2000+ on Asrock K7NF2-Raid mobd ( I am not using SATA or Raid), with 512 Mb and FX5900XT graphics.
I have tried the usual tricks of removing any surplus drives and disabling SATA.
So, I will be very grateful for any hints.

<previously posted material ends>

I am a near-total novice so please phrase any reply accordingly!

Thanks - Mike

---

### Post by sdowney717 on 2008-11-08
can it boot the live cd?
if it can, then it might be a video issue.

I ran into a problem once where the bios was saying something was enabled but was not actually present in the system like a floppy drive, and it totally hung. Ubuntu kept trying to access the missing device.

the same bios setting let XP sail on past without a hick-up.

---

### Post by B34ST1Y on 2008-11-08
you can always try running ```
fsck
``` to make sure your system files are all in order..

---

### Post by mike.headon on 2008-11-09
Thanks, both of you...
The latest disc (8.10) boots fine. Sorry, I don't understand why this should indicate a video problem - can you explain please?

fsck gives:

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=5c77b1b3-e70f-4dff-a36e-de9756f44c5c'

The UUID mentioned is a disk which was on the system when I first installed Feisty last year. Why should anything still be looking for it? I remember that I had to change the Grub menu lines when I copied the system to a new HDD. I presume that the old UUID is in a file somewhere, anybody know where?

Perhaps I should try a complete new install from a bare disk up...

Thanks - Mike

---

