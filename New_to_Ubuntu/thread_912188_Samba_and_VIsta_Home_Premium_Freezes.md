---
title: "Samba and VIsta Home Premium Freezes"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by laserbeak43 on 2008-09-06
Hi,
I'm using Kubuntu, the latest(?) I installed it last night. And i have Vista Home premium. Vista can detect my samba drive and displays its contents but if i try to copy any of its contents to the vista drive, it freezes and i have to restart vista.
i've found a page that tells me i have to modify a registry key. LSA\ lmsomethingsomething = 1. it's all over google but that doesn't work.

do you guys have any idea what else i can do? here's my smb.conf:
```
[global]
   workgroup = WORKGROUP
   server string = DIVA-LICIOUS
   security = share
[Shared]
path = /home/laserbeak43/Desktop/
available = yes
browsable = yes
public = yes
writable = yes
guest ok = yes
create mask = 0777
directory mask = 0777
```

-edit-
i've also fetched all updates and installed them.

---

