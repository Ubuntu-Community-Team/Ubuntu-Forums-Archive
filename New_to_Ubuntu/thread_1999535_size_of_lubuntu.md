---
title: "size of lubuntu"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by rapk on 2012-06-08
hi everyone,
i switched to lubuntu 12.04 - it is a nice one!
my HD has a storage of 320 GiB and pcmanfm tells me that i've just
288 GiB free space. But i only installed lubuntu and personal data
with a size of ~2 GiB.
When i open the properties of all personal data, it tells me  

Size of all data: 2,1 GiB
Used Storage: 17,1 GiB

Can anyone explain that?

best

---

### Post by cortman on 2012-06-08
Did you check (with an operating system) how much free space was on  the HDD before you started?
I guarentee it wasn't the full 320 GB. Manufacturers calculate 1000 MB = 1 GB for rating HDD sizes, while the actual equation is 1024 MB = 1 GB. Plus they block off room for firmware and controller space.
As far as the 17 GB, check /var/log and make sure you don't have any enormous logfiles in there.

---

### Post by Paqman on 2012-06-08
Formatting the drive also takes up some space, even before you install the OS.

---

### Post by rapk on 2012-06-08
Okay, thank you so far!

---

