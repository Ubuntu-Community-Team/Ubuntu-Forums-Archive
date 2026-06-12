---
title: "XP Install Problems"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Captain666 on 2008-08-12
I know that this isn't the right place for this problem, but i dont know where else to turn since my other posts on other sites are going unanswered.

My problem is: Trying to re-install WinXP with CD. When my CD drive is connected to my computer, my HDD stops working. If i disconnect my CD drive, my HDD starts working. The computer that I am trying to fix was recently plagued with viruses, and does not even load to the desktop, though BIOs seems to work fine. If i try to manually set up my HDD in BIOs I get a message that says "primary hard disk failure" when it attempts to boot.  

I need both my CD drive and HDD working at the same time to successfully re-install XP.

Any help at all would be hugely appreciated!!!

---

### Post by sillyxone on 2008-08-12
not sure what might be wrong, but if you are connecting both drive to the same IDE cable, make sure the jumper on one drive is set to Master and the other's is set to Slave.

---

### Post by stoneybroke on 2008-08-12
You didn't say what type of hdd it is if its a IDE drive (ribbon cable) make sure the red leads are connected to pin 1 on the Hard drive and the CD drive. If they are ok and the bios still cant see it try disconnecting the CD drive and only try the hard drive make sure the bios can read the drive, if it can then re-connect the CD drive. Also if both drives are on the same ribbon cable try cable select on the jumpers on both of the drives.

If the bios can read the heads/sectors on the hard drive after that it should be ok if not the drive could be dead.

Hope thats of some help

---

### Post by lisati on 2008-08-12
As well as checking the way the cables are plugged in and master/slave settings, it won't hurt to check that the BIOS correctly recognizes the HDD, particularly when you have both plugged in. Some BIOSes have an option where you select the HDD, and press Enter to autodetect the correct settings.

---

### Post by Captain666 on 2008-08-19
thanks for all of the help guys, it is IDE and i just swapped the HDD with a different one and it worked.. im kind confused but i figure the old one must have just been trying to die or something

---

