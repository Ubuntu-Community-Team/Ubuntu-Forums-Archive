---
title: "Partition"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by su_penguin on 2008-06-04
When installing 7.04 from the Live CD you're prompted to choose which partition to install the OS on. For some strange reason there aren't any drive selections to choose from. I have a VIsta hdd that I'd like to format to place Ubuntu on but, it doesn't show up in the menu to be formatted. Any help will be appreciated. 

-Pengu

---

### Post by iaculallad on 2008-06-04
Boot using you're LiveCD, goto terminal and paste the output of this command:

```
sudo fdisk -l
```

---

### Post by oedha on 2008-06-04
make sure you have shutdown your vista properly

---

### Post by Sef on 2008-06-04
> I have a VIsta hdd that I'd like to format to place Ubuntu on but, it doesn't show up in the menu to be formatted. Any help will be appreciated.

Use the Vista partitioner to shrink the Vista partition.

---

