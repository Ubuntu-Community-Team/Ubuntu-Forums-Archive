---
title: "[SOLVED] possible ntfs corruption?"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by LVCNSOL on 2008-10-09
I did search but nothing helped much.
I have heard that writing to a NTFS partition can corrupt it, but reading-only is fine to do?
Is this true? if so, how can I enable read-only from my NTFS partition? or any ways i can prevent it being corrupted?

Thanks

---

### Post by Vera_ on 2008-10-09
I always write in NTFS partition, and I never have any problem. Interesting question. ;)

Sorry my bad english. :(

---

### Post by LowSky on 2008-10-09
Ubuntu can read a NTFS partition without adding any additional drivers.. As far as Writing to a NTFS partition, I've never had a problem, and most Windows users have never had a problem. Microsoft would not use NTFS for as many years as it has if it was a bad file system.

---

### Post by medic2000 on 2008-10-09
Nope! ntfs-3g driver rocks. Open your fstab and change ntfs to ntfs-3g.

---

### Post by simtaalo on 2008-10-09
you shouldnt have a problem, what you heard sounds like rubbish to me.

---

### Post by LVCNSOL on 2008-10-09
> **simtaalo said:**
> you shouldnt have a problem, what you heard sounds like rubbish to me.

OK cool, so creating new files and folders onto my windows NTFS from Ubuntu shouldn't have any implications.
I play mp3s as well from the NTFS in Ubuntu, but that's reading.

Thanks :)

---

### Post by LowSky on 2008-10-09
Yeah writing to NTFS isn't an issue, if it was I wouldn't ri music to a NTFS partition

---

### Post by az on 2008-10-09
A few years ago, writing to an NTFS filesystem was not fully implemented in Linux.  But that was long ago.

---

### Post by M-Z on 2008-11-10
> **simtaalo said:**
> you shouldnt have a problem, what you heard sounds like rubbish to me.
I wouldn't be so confident. I had NTFS truecrypt volume, which I used for emule under Windows and amule under Ubuntu 8.10. After some time the filesystem started to have more files on it than there was available space on the whole volume. This situation was triggering bluescreen in Windows Vista every time emule started to hash temp files.

---

