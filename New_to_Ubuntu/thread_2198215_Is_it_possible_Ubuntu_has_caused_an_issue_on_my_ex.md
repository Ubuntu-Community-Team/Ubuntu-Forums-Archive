---
title: "Is it possible Ubuntu has caused an issue on my external hard drive for windowss 8?"
date: 2014-01-07
forum: New to Ubuntu
---

### Post by timeyyy_da_man on 2014-01-07
I used my Girlfriends External hard drive and ever since she has been able to use it on any 3.0 ports on her computer, only the usb 2.0 ports.

Seems unlikely to me that using it on my ubuntu 12.04 and now 13.10 machine caused this.

Any thoughts would be appreciated.

Its a toshiba

---

### Post by oldos2er on 2014-01-07
NTFS? Was it "safely removed" after last use? Any error messages?

---

### Post by jdeca57 on 2014-01-07
> **timeyyy_da_man said:**
> 
Seems unlikely to me that using it on my ubuntu 12.04 and now 13.10 machine caused this.
Any thoughts would be appreciated.

My idea is that the difference between usb2/3 is hardware and that the underlying fs has little or nothing to do with it. I'm sorry to ask obvious things, but is the problem occurring on exactly the same computer and the same usb port?

---

### Post by tfrue on 2014-01-07
If you have a Window's computer, I would do a disk check against the drive, or if an ext FS, then use fsck on the drive just to make sure there aren't any errors with the drive.

---

### Post by king.of.random on 2014-01-07
Sounds more like an issue with the usb3 interface. I dual boot into win8 and Ubuntu and this has never happened to me. Has she got the usb3 drivers installed properly it's possible they are corrupted. Try uninstalling and reinstalling them.

---

