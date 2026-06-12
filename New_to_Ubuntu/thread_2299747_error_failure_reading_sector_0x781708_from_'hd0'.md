---
title: "error: failure reading sector 0x781708 from 'hd0'"
date: 2015-10-20
forum: New to Ubuntu
---

### Post by Nik_Lamigo on 2015-10-20
it says press any key to continue, nothing happens.

I got this error after I reboot my computer (ASUS A46CA). I just installed 14.04 LTS then **Ubuntu** Software Center won't start, i tried sudo apt-get update and then upgrade in the terminal. both didn't end well, it reported some things not installed/downloaded, I forgot this part. Tried to reboot then this, ```
error: failure reading sector 0x781708 from 'hd0' 
```

TYIA

---

### Post by doctorbighands on 2015-10-22
Looks suspiciously like a hard drive on its way out. It might just be one bad sector, or some other kind of hiccup, but it would pay to check the drive integrity before moving on to anything else.

Use some kind of HDD failure detection software (UBCD, etc), make sure the drive is healthy, and go from there.

---

### Post by shadytv on 2015-10-22
create a file called forcefsck at the root (/) of your filesystem then reboot

this will force linux to do a filesystem check on next boot (like CHKDSK in Windows)

fsck will find bad sectors on your drive and create pointers so the system doesn't use them.

But consider replacing your drive, bad sectors are usually the beginning of the end...

---

