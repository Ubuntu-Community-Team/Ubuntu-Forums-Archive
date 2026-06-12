---
title: "Ubuntu 13.10 64bit and Clonezilla"
date: 2014-03-07
forum: New to Ubuntu
---

### Post by jrs2 on 2014-03-07
I have a fresh install of Ubuntu 13.10 on my machine (used Live USB to install on a clean hard drive). I have used clonezilla to capture an image of this machine. I have tested the clonezilla image on this machine (placed test folder on desktop, went through reimaging process, rebooted machine, folder is gone).

However, when I try to do this on another (although identical) machine, the reimaging process goes through all the way, but Ubuntu will not boot. So, the way it seems, if the machine has a fresh hard drive, my clonezilla image will not work. However, if the machine has gone through the LiveUSB process, it will reimage fine.

What am I missing?

---

### Post by whitesmith on 2014-03-07
You say the machines are identical. Does this granular equality extend all the way to the disk drive? Clonezilla is so fussy about the restore process that it will only restore to a drive of identical size. Also, did you image the entire disk or simply make a partition image that could have excluded the bootable partition?  Regards.

---

### Post by jrs2 on 2014-03-07
Yes, the machines are identical. Only difference being that one has went through the LiveUSB process to install Ubuntu 13.10, and the other hasn't. I have seen the error with clonezilla regarding disk size. This is different. This will go through the entire process like it's been successfully reimaged...and then once you exit clonezilla and reboot the machine, Ubuntu fails to boot.

---

### Post by whitesmith on 2014-03-07
You are imaging the entire disk, not just a partition, correct?

---

### Post by jrs2 on 2014-03-07
Correct. Restoring entire disk.

---

### Post by whitesmith on 2014-03-07
Assuming all partitions are imaged ("diskimage," I believe they call it) and restored to a drive of identical capacity, all should go well. Obviously this is not the case here. You might get on their doc page ([http://clonezilla.org/clonezilla-live-doc.php](http://clonezilla.org/clonezilla-live-doc.php)) and see if a gotcha applies to you. Not to be disparaging, but I've found Clonezilla to be an excellent product -- at least as good as the old Symantec/Norton Ghost -- saddled with clumsy and confusing documentation, probably a reflection of the product's Taiwanese origins. I wish I could offer more help that this, but your description has managed to stump the coach. Perhaps someone with more finely honed Clonezilla skills can pick up where I've left off. Best of luck to you!

---

