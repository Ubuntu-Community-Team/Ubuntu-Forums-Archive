---
title: "Virus Transfer from Ubuntu to Windows? Is it possible?"
date: 2010-06-24
forum: Recurring Discussions
---

### Post by ThatPerson on 2010-06-24
I know this question may have been asked before but most of the answers I found were inconclusive. So, is it possible to for a Windows virus in Ubuntu to transfer to a Windows partition. I run an antivirus suite in Windows, so I guess it wouldn't really matter to much, but I'd rather be safe than sorry. If it is possible, would the threat be lessened if the dual boot was on separate hard drives?

Thanks,
ThatPerson

---

### Post by mikewhatever on 2010-06-24
So, you want a conclusive answer? Yes, it's possible.:p
What to do about it? Read the 'Ubuntu security' sticky.

---

### Post by doas777 on 2010-06-24
it is possible, but is highly unlikely. be careful about terminology though. a virus has very little chance of taking this kind of action, as would be a worm. a trojan customized to target you and your PC specifically however can be written to download the ext drivers and mount your linux partitions.  of course, someone would have to be out to get you for that scenario to play out however. a targeted attack by a sophisticated and patient attacker will always succeed regardless of platform and security software.

---

### Post by cdenley on 2010-06-24
> **doas777 said:**
> it is possible, but is highly unlikely. be careful about terminology though. a virus has very little chance of taking this kind of action, as would be a worm. a trojan customized to target you and your PC specifically however can be written to download the ext drivers and mount your linux partitions.  of course, someone would have to be out to get you for that scenario to play out however. a targeted attack by a sophisticated and patient attacker will always succeed regardless of platform and security software.

I think you're talking about going from Windows to Ubuntu. To go from Ubuntu to Windows, wine would have to be installed, the Windows malware would have to be run with wine, the windows partition would have to be mounted, the mount point must be within a wine drive mapping, then the malware can write whatever it wants if the user it is running as has permission.

---

### Post by doas777 on 2010-06-24
> **cdenley said:**
> I think you're talking about going from Windows to Ubuntu. To go from Ubuntu to Windows, wine would have to be installed, the Windows malware would have to be run with wine, the windows partition would have to be mounted, the mount point must be within a wine drive mapping, then the malware can write whatever it wants if the user it is running as has permission.

ahh, your right. it is a little easier that direction in terms of mounting the drive, but the malware would have to have escalated it's privileges sufficiently to mount. they might use wine, or not, if it is a linux native malware.

@op, so far as I am aware, mounting a partition on one disk is the same as mounting one from another drive. I think even the dd command cannot cross partition boundaries, so it shouldn't make a difference if it;s on a different drive.

---

### Post by cdenley on 2010-06-24
> **doas777 said:**
> ahh, your right. it is a little easier that direction in terms of mounting the drive, but the malware would have to have escalated it's privileges sufficiently to mount. they might use wine, or not, if it is a linux native malware.


It would be easy for linux malware to mount a filesystem, but I don't think it is possible from within wine since we are talking about windows malware. The windows filesystem would have to be already mounted. In Lucid, I don't think a password is required to mount filesystems through nautilus by default, so I'm sure there is a way for linux malware to mount filesystems with only admin user privileges.

---

### Post by cariboo on 2010-06-24
This question has been asked and answered many times before, moved to Recurring.

---

