---
title: "NTFS $FileLog reverse engineering"
date: 2012-09-26
forum: Programming Talk
---

### Post by drakesword on 2012-09-26
So I did something stupid and as a result I lost 8 hours of work. I basically collected a couple hundred gigs of data and then promptly did a rm -rf on the directory instead of a separate folder. You live and you learn.

Anywho, as far as I know rm rf will unly unlink in the filesystem not overwrite the data. Like a good boy i dismounted by unplugging then replugged without mounting, made a dd image, made a copy of said dd. Using photorec, testdisk, ntfsundelete, get data back, nuix, ftk, etc. I have been unable to recover. In lieu of traveling 2.5 hours to retrieve the data ... again I was wondering if anyone has ever looked intop the ntfs $FileLog. It is fairly lengthy and I can see the inode data it wrote.

So first order of business would be to dump a per-file log of what the log contains. From there, hopefully it contains each segment start end etc so the files could be recreated. Anyone dealt with this sort of situation before or has anyone seen anything regarding the $FileLog in ntfs systems?

---

