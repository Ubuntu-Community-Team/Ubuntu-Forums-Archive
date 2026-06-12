---
title: "is it normal for some (but not all) folders to be locked in preview?"
date: 2024-01-03
forum: New to Ubuntu
---

### Post by ponestudios on 2024-01-03
is it normal for some (but not all) folders to be locked in the OS preview (before you install)? there were three folders on my second drive that had a lock icon on them.

---

### Post by UltimateCat on 2024-01-03
Directories (folders) that are locked are generally owned by root. So yes, it is normal for some things on the system.

The only way around that is to become root to view it and or change ownership if need be.

---

### Post by ponestudios on 2024-01-04
Ah, alright, thank you.

---

### Post by ActionParsnip on 2024-01-04
Sounds like you need to adjust mount options.

---

### Post by yancek on 2024-01-04
When using the 'live' installer, you will see the lock icon on directories used as mount point for partitions on external drives so you know they cannot be used during the install as they are mounted.  This might be what you are seeing but not enough info to know for sure.

---

### Post by Rubi1200 on 2024-01-04
> **UltimateCat said:**
> Directories (folders) that are locked are generally owned by root. So yes, it is normal for some things on the system.

The only way around that is to become root to view it and or change ownership if need be.

@ponestudios 

Yes, correct.

However, not recommended at all to become root unless you really know what you are doing or don't mind trashing your system.

---

### Post by aljames2 on 2024-01-05
Also, some newer users get “sudo” happy at the command line until they learn to not use sudo until it is required.  For example, if you sudo mkdir foldername in your /home directory, you have given that folder to root, probably not the intention.

---

