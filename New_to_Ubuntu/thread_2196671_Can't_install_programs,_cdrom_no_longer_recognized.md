---
title: "Can't install programs, cdrom no longer recognized."
date: 2013-12-30
forum: New to Ubuntu
---

### Post by rogermorin1981 on 2013-12-30
Very new to linux.  I installed Ubuntu 13.10 over Windows 8 Pro 64 (I have another copy on a separate drive), but now the the other Windows 8 is inaccessable.  I can only boot into ubuntu.  I tried using boot-repair via a disk, but at the end of burning I got an error about being unable to eject, then the computer stopped recognizing the dvd drive (after a few updates I can eject via command prompt, but nothing else).  Tried installing Unetbootin to get boot-repair on a bootable USB, and used preferences to make the file executeable, but trying to install UNetbootin gives the error from Archive Manager "An error occured while loading the archive."
I'm currently stuck in a state where I can not access my other OS, can't use my dvd burner, and can't install new programs.  Any help would be appreciated.

Asus G74SX
8gb ram

---

### Post by conversationjames on 2014-01-02
Try setting the boot order to your Win7 first, then when u want to load Ubuntu, choose on startup boot menu:
[Change boot order in Ubuntu]("http://ubuntuhandbook.org/index.php/2013/08/change-boot-order-in-ubuntu-13-10-13-04/")

---

### Post by chkneater on 2014-01-02
First, did you install Ubu OVER windows or alongside?  If you chose alongside, you may just need a grub update. 

'sudo grub-update'

If you installed OVER, windows is gone bud.  With the liveDVD do you see ubu partitions and windows partitions?

Am I right that your Ubu installation is working?

---

### Post by deadflowr on 2014-01-02
> **chkneater said:**
> First, did you install Ubu OVER windows or alongside?  If you chose alongside, you may just need a grub update. 

'sudo grub-update'

If you installed OVER, windows is gone bud.  With the liveDVD do you see ubu partitions and windows partitions?

Am I right that your Ubu installation is working?

Your command is backwards
```
sudo update-grub
```

To the OP, post the output of this, if you haven't fix the problem in these last couple of days.

---

### Post by chkneater on 2014-01-03
> **deadflowr said:**
> Your command is backwards
```
sudo update-grub
```

To the OP, post the output of this, if you haven't fix the problem in these last couple of days.

Thanx for the correction my mind is dyslexic but my eyes are fine ;)

---

