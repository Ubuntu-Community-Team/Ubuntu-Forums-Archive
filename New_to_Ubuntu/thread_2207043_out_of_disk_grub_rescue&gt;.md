---
title: "out of disk grub rescue&gt;"
date: 2014-02-21
forum: New to Ubuntu
---

### Post by Brendan_Tolman on 2014-02-21
Running ubuntu 12.04.03 
ive tried everything i can find,
boot-repair tool gave me this url
    [http://paste2.org/new-paste](http://paste2.org/new-paste)
I have no clue what to do 
thx in advance!

---

### Post by Impavidus on 2014-02-22
Boot repair is indeed the thing to try, but your link doesn't point to the bootinfo summary. Can you try and give us a working link?

---

### Post by Brendan_Tolman on 2014-02-22
[http://paste.ubuntu.com/6978406/](http://paste.ubuntu.com/6978406/)
here we go had to install a fresh copy and try again

---

### Post by oldfred on 2014-02-23
Your boot files all are within the first 100GB, but sometimes larger / (root) partitions can cause this when boot file is written beyond 100GB on drive.

You can try this:
 Out of disk error add to grub install disk-module=ata or use Boot-Repair ATA Disk support

What mode is hard drive set in, should be AHCI or LBA or large, not IDE nor RAID.

---

### Post by Brendan_Tolman on 2014-02-23
i have no clue what my hard drive is set to.
how can i find out/check what its set to?

---

### Post by oldfred on 2014-02-23
You have to go into BIOS and should find settings for hard drive. May be in sub-menu also. Varies a lot by vendor or BIOS vendor.
This was mine before I changed IDE to AHCI.

---

### Post by Brendan_Tolman on 2014-02-23
ok so this is what i got

---

### Post by oldfred on 2014-02-24
What are other choices than enabled under both automatic and ATA/IDE modes?
Is AHCI one of them and have you tried it?

---

### Post by Brendan_Tolman on 2014-02-24
id gave me the options legacy and enhanced. ive tried both

---

### Post by oldfred on 2014-02-25
Was that automatic setting or ATA/IDE setting?

---

### Post by Brendan_Tolman on 2014-02-25
under the automatic mode is has:
enable or disable 
when disable is selected the option 
use serial ata
pops up

---

### Post by oldfred on 2014-02-25
Try with Serial ATA unless you have old IDE/PATA drives.

---

### Post by Brendan_Tolman on 2014-02-25
ok tried it, still get a grub error

---

### Post by oldfred on 2014-02-25
Did you try shrinking the / (root) partition to less than 100GB. About 50% of those I suggest that to, find it works.

But none of your boot files were beyond the 100GB point, so I doubt if it will help.

---

### Post by Brendan_Tolman on 2014-02-26
Ill try that when I get home from school, thanks for the help.

---

