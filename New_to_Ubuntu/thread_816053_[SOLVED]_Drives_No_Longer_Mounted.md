---
title: "[SOLVED] Drives No Longer Mounted"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Thee_Baron_ on 2008-06-02
Hello, turned on xubuntu today, went to access one of my drives and it wasn't there. I when into PYSDM and noticed that my two NTFS drives are not mounted. I clicked the mount button and nothing happened.

What going on? I've got important data that I need to access.

Thanks!

---

### Post by Paqman on 2008-06-02
If it's just the NTFS drives it may be because they weren't shut down cleanly. If you have Windows installed try booting into it, then reboot into Xubuntu and try again.

---

### Post by Thee_Baron_ on 2008-06-02
Currently dont have Windows installed and cant find the CD to do so. Any other method of fixing this?

Thanks!

FIXED: Its to do with my permissions as a user (don't know how it changed) but as soon as I changed PYSDM to allow any user to mount drives it worked!

---

