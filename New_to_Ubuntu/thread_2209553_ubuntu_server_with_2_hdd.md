---
title: "ubuntu server with 2 hdd"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by noobb2 on 2014-03-06
I have question, if i'll install ubuntu server 12.04 with raid and the hdd with the installed system will go down...the system will go down or it would continue with the second hdd?

p.s. i'm assuming that the system(and all it's data) would be mirrored on the second hdd.

---

### Post by tgalati4 on 2014-03-06
It depends on how you have it set up, but yes, the OS would continue and the RAID would be marked as "degraded" until you do something about it--like change the disk drive.

---

### Post by oldfred on 2014-03-08
Understand that RAID is not backup. May actually be better to have one drive and many backups to second drive.

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

