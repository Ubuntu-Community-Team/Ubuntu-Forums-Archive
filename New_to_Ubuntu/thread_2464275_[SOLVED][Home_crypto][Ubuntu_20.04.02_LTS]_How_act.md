---
title: "[SOLVED][Home crypto][Ubuntu 20.04.02 LTS] How activate after S.O. installation"
date: 2021-06-28
forum: New to Ubuntu
---

### Post by shadow761 on 2021-06-28
Dear users,
as per object I don't think I have activated the default home folder encryption at the time of installation and I would like to do it now.


But I don't mean a normal encryption of a generic folder, which must then be actively decrypted from the user (as in many examples that I have already found on the various forums); I mean instead the classic automatic encryption (like Bitlocker on Win, so to speak) which is then autonomously decrypted by the system when the user logs in to the operating system with his own account.


Thanks a lot to everyone!

---

### Post by TheFu on 2021-06-28
Home directory encryption was deprecated years ago due to a few performance, upgrade, and security problems.
These days, and back then, we used dm-crypt with LUKS to encrypt the entire installed storage. This tool/method solves many of the problems the other solution had while keeping overhead to a minimum.  Also, it protects data at rest much better.

I don't know anything about Win or bitlocker, except that MSFT gets a copy of the decryption access keys in most situations.

Decryption that happens automatically isn't really encrypted, is it?

To my knowledge, good encryption cannot be added easily later.  

We can possibly create a new LUKS container on an empty partition, then put LVM inside that container with the PVs, VGs, and LVs needed/desired, and we can manually setup a crypttab, but I honestly have no idea how.  Paddy writes a "manual encryption" how to guide with lots of posts in these forums for how to accomplish that. For my time and effort, it would be much easier to backup the data and settings of a system, do a fresh install with encryption selected, then restore the data and settings.  I think that would take about 30 minutes on most of my systems.

Having encryption on a system means we absolutely must have excellent backups.

---

### Post by shadow761 on 2021-06-28
Thank you very much, the post is solved and this reply works perfectly for me. Veracrypt is my choice.

---

