---
title: "Small useable disk size after install?"
date: 2024-01-17
forum: New to Ubuntu
---

### Post by z1iceman on 2024-01-17
Just loaded on [COLOR=#333333][FONT=&quot]Ubuntu [/FONT][/COLOR]**22.04.3 LTS **on a Toshiba laptop and told to take over the whole disk. It did that on a 256 SSD, but 200+ gig to a the root / directory and only 19g to a useable partition. I can see the root partition and all the system folders but cannot create any folders are otherwise use it for docs, sheets, etc?

Not sure why it partitioned things this way. I did not get a problem to size things during install. 

Can I reclaim some utilize some of that extra space that was allocated to  /  ?

---

### Post by Dennis N on 2024-01-17
If you are using UEFI, a default install makes just one partition (root), of maximum possible size, besides the efi system partition, so this is normal. The root partition includes a home folder for your documents. If you want a certain size for the root partition, then you have to use manual partitioning to specify the size.

---

### Post by MAFoElffen on 2024-01-17
Could you please post the result of this posted within CODE Tags?
```

lsblk -e7 -o name,label,size,fstype,fsused,mountpoint,model

```
And please tell me which of the Erase all options you used to install.

---

