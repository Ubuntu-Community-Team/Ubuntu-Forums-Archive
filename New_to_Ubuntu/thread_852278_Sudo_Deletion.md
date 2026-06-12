---
title: "Sudo Deletion"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by petdog on 2008-07-07
Oh no,
I had this huge error where i could not update, thinking i was a cleaver new guy i would try redo all accounts, i deleted myself off the ROOT group, and well now i can not do anything cause i ain't root/SUDO empowered, please may someone with a heart inform me of how to fix this critical error, i know sudo password i need to find out how to log on as ROOT!!!! 

Please Help!
PetDog!

---

### Post by bapoumba on 2008-07-07
Assuming petdog is your login name, boot in recovery mode from grub menu, you'll be root with a # prompt:
```
# adduser petdog admin
# reboot
```
Adjust to your actual login if not petdog.

---

### Post by petdog on 2008-07-07
Thanks man!!

---

