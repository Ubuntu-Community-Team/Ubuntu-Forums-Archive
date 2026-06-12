---
title: "cant get /home partition to set up"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by heddleston on 2008-06-07
i've already set up my dual boot, and it runs perfectly. when i installed, however, i didnt setup a separate //home partion. i've followed psychocat's guide, but its still not working. the error im getting is when it's trying to shrink the filesystem- 

resie2fs 1.40.8 (13-mar-2008_
please run 'e2fsck -f /dev/sda6' first

any ideas?

---

### Post by jrusso2 on 2008-06-07
If your trying to shrink resierFS partition I am not sure it can be done.

---

### Post by bodhi.zazen on 2008-06-07
You need to first unmount the partition, then ```
sudo e2fsck -f /dev/sda6
```

Then proceed (with resize2fs). Alternately you can fire up a live CD and use gparted.

---

