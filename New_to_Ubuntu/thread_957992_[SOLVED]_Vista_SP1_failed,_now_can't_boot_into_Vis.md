---
title: "[SOLVED] Vista SP1 failed, now can't boot into Vista"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by dndrich on 2008-10-24
My son has a dual boot Ubuntu 8.04 and Vista.  I tried to install service pack 1 for Vista.  The installation failed for some reason, and then it rolled back to the old version.  Now, when trying to boot, I get the grub menu, but when I pick Vista, it won't boot.  It just restarts and shows the grub menu again.  What do I do to fix this?

---

### Post by melojo on 2008-10-24
look here

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by CoreyB. on 2008-10-24
It is explained in this article [http://apcmag.com/vista_sp1_wont_install_on_dualboot_systems_microsoft.htm]("http://apcmag.com/vista_sp1_wont_install_on_dualboot_systems_microsoft.htm")

---

### Post by dndrich on 2008-10-24
OK, I looked at the article regarding the Vista SP1 problem.  That is it.  I will repair the Vista MBR, and that should do it.

---

### Post by melojo on 2008-10-24
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
boot from the vista cd to recovery console

type ```
bootrec /fixmbr 
```

and  ```
bootrec /fixboot 
```

this fixes the master boot record.  start vista install the update then to restore grub use [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Harisz750 on 2008-10-24
01000010 01010010 01010101 01000011 01000101
01001100 01001111 01010110 01000101 01010011
01001010 01000101 01001110 01001110 01001001 01000101 = bruce loves jennie

---

### Post by melojo on 2008-10-24
> **Harisz750 said:**
> 01000010 01010010 01010101 01000011 01000101
01001100 01001111 01010110 01000101 01010011
01001010 01000101 01001110 01001110 01001001 01000101 = bruce loves jennie


LOL its true

23 years

---

### Post by dndrich on 2008-10-24
OK, I have booted into the recovery console for Vista, but it doesn't recognize the Vista installation.  The partition is definitely there.  rebuildbcd fails.  scanos does find vista.  It says that the volume does not contain a recognized file system.  What do I do here?

---

### Post by bumanie on 2008-10-25
My first guess would have been that the bootlaoder of vista has been corrupted - this recently happened to me and i repaired vista's bootloader with   repair disk.. But as recovery console doesn't provide any promise for you, you have two options:
1) download vista repair disk from[ neosmart]("http://neosmart.net/search.php?domains=neosmart.net&q=vista&sa=Go&sitesearch=neosmart.net&client=pub-5619864238989802&forid=1&channel=5924079665&ie=UTF-8&oe=UTF-8&flav=0000&sig=TeF8lRDSuEsYfoxO&cof=GALT%3A%23728C40%3BGL%3A1%3BDIV%3A%23999999%3BVLC%3A336633%3BAH%3Acenter%3BBGC%3AFFFFFF%3BLBGC%3AFF9900%3BALC%3A0066CC%3BLC%3A0066CC%3BT%3A000000%3BGFNT%3A666666%3BGIMP%3A666666%3BFORID%3A11&hl=en") and try that, just in case there is an irregularity with your repair disk
2) try [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to re-write the partition table of the hard drive. Are you able to see the vista files from within ubuntu? If so, copy any important data before trying testdisk. Read the documentation before trying to recover.

---

### Post by glotz on 2008-10-25
When will windoze be ready for the desktop?? #-o

---

### Post by dndrich on 2008-10-25
OK, so here is what I did and what I think happened.  I downloaded a live CD of GParted, which is part of test disc, and of course, part of our lovely Ubuntu.  From there I could see that the partition labeled boot was the ubuntu partition.  The Vista partition was labeled as disc 2, but physically was disc 4 on this drive.  So, using the flag option I changed the boot flag to the windows partition.  Then, when I booted to the Vista recovery environment it was finally able to see that there was a Vista partition.  It was able to repair the installation.  From that point I could have repaired grub, but my son just wants Vista for games (!), so within Vista I deleted the Ubuntu partition, and reformatted it NTFS.  So, now all is well.  Thanks for your help.  The key was to change the boot flag to the correct partition so that the MBR could be detected and repaired by Vista.  What a hassle.  I personally only run Ubuntu, OS X, and Windows XP (for DragonNaturallyspeaking)

---

### Post by melojo on 2008-10-25
Thanks for the update, Glad you got it fixed

---

