---
title: "formating problems"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by trigsenior on 2008-06-01
hi, 

I have an external hard drive which is fat 16 but for some reason it says it only has 15 mb on it when there is over 400 gb free . It is emty so i don t mind re-formating it , but when i use gparted it keeps trying to make two partitions ?  

i was wondering maby i should use ext2 but can windows read ext2 ?

---

### Post by shifty_powers on 2008-06-01
windows cannot read ext2 natively, but drivers are available


[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by sayakb on 2008-06-01
> **trigsenior said:**
> hi, 

I have an external hard drive which is fat 16 but for some reason it says it only has 15 mb on it when there is over 400 gb free . It is emty so i don t mind re-formating it , but when i use gparted it keeps trying to make two partitions ?  

i was wondering maby i should use ext2 but can windows read ext2 ?

Perhaps GParted makes one smaller 8-15MB trailing unpartitioned free space and the rest as the partition you created. Can you post a screenshot?

---

### Post by trigsenior on 2008-06-01
thanxs for reply i just formated to fat 32

---

### Post by shifty_powers on 2008-06-01
you are aware that ubuntu now natively reads/writes to ntfs as well, yes? ;)

---

