---
title: "[SOLVED] Ubuntu unbootable after installing dmraid"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by eilenbeb on 2008-08-04
After installing dmraid, a new initrd.img is created, and the old one is saved as a backup.  Reboot fails; init proc sys and maybe some others fail to mount, and I'm left with an initramfs prompt.

To fix this, I boot with a live CD and replace the initrd.img with the backup.

I had the same problem when I ran the system update.  Had to replace the initrd.img file.

I have both images mounted under my home directory for comparison, but I don't know enough to fix anything.  What I can tell is this:
--The newly created .img contains less files and folders, but includes dmraid stuff.
--The backup copy has lots more 'casper' entries, among other things.

Could this be caused by my doing something wrong at install time?
Could the boot devices be re-ordered somehow because the raid array is visible?

My basic config:
  (fake)SataRaid0
    primary partition:  Win2k
    logical in extended:  fat32, unused
  IDE/ATA 1
    prim:  Ubuntu hardy64 root
    locical in extended:  swap
  IDE/ATA 2
    prim:  fat32, unused

Any help would be appreciated.
laters,
b

---

### Post by sh4d0w808 on 2008-08-05
Maybe U can find [help in this topic]("http://ph.ubuntuforums.com/showthread.php?t=772107").

---

### Post by eilenbeb on 2008-08-05
Thank you.  That sounds exactly like what's going on with my system.
(my normal drives were once raided, so some leftover metadata could be screwing me up)

I'll give it a try and (hopefully) post success.

laters,
b

---

### Post by eilenbeb on 2008-08-05
Success!  Thanks again for the link, problem solved.

laters,
b

---

