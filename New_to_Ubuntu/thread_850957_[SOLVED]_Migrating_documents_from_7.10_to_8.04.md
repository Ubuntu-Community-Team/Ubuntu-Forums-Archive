---
title: "[SOLVED] Migrating documents from 7.10 to 8.04"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by deepblue80 on 2008-07-06
Hi 
i have an 80 gb ide hdd running Ubuntu 7.. i recently put in a new 250 GB sata hdd and installed ubuntu 8.04. how can i get my data from the previous 80 gb hdd when i boot from the new hdd running 8.04. i can see the 80gb as file media, in unmounted state. is it just copy and paste?

---

### Post by billgoldberg on 2008-07-06
> **deepblue80 said:**
> Hi 
i have an 80 gb ide hdd running Ubuntu 7.. i recently put in a new 250 GB sata hdd and installed ubuntu 8.04. how can i get my data from the previous 80 gb hdd when i boot from the new hdd running 8.04. i can see the 80gb as file media, in unmounted state. is it just copy and paste?

Yes.

If you double click the icon, the drive should mount, then you can copy all data you want to the 250gb drive.

---

### Post by kestrel1 on 2008-07-06
You shouldn't have a problem, just mount the 80GB drive & copy the files over.

---

### Post by sayakb on 2008-07-06
Ofcourse. Just copy and paste. 
Suppose the old HDD has a device link /dev/sdb1
So mount it by:
```
sudo mkdir /media/disk
sudo mount /dev/sdb1 /media/disk
```Now goto Places->Computer->disk->home->your previous username (in 7.10)
And copy everything to 8.04 home folder. (ie to /home/username/)

EDIT: Or.. err. just mount the partition by double clicking on it ;)

---

### Post by deepblue80 on 2008-07-06
thank ya all, thats what i thought initially but it crashed the first time. so i double checked. its working bril now :-)

---

### Post by sayakb on 2008-07-06
If GUI  seems to be crashing, you can copy it via the CLI:
```
cp -Riv /media/disk/home/oldusername /home/username
```

---

